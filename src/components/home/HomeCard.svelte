<script>
  import { onMount } from "svelte";
  import axios from "axios";
  import moment from "moment";
  import "moment/locale/ko";
  import { ProcessViewCount, ProcessUploadDate } from "../../utils";

  export let data;
  export let apiKey;

  let thumbnailUrl;

  onMount(async () => {
    try {
      const response = await axios.get(
        "https://www.googleapis.com/youtube/v3/channels",
        {
          params: {
            //url 뒤에 붙는 값
            part: "snippet",
            id: data.snippet.channelId,
            fields: "items(snippet(thumbnails))",
            key: apiKey,
          },
        }
      );
      thumbnailUrl = response.data.items[0].snippet.thumbnails.default.url;
    } catch (e) {
      // 오류 발생
      console.error("error : ", e);
    }
  });
</script>

<a href={`https://www.youtube.com/watch?v=${data.id}`} class="card">
  <img
    class="thumbnail"
    src={data.snippet.thumbnails.medium.url}
    alt={`${data.snippet.title}의 썸네일`}
  />
  <div class="info">
    <a href={`https://www.youtube.com/channel/${data.snippet.channelId}`}>
      <img
        class="channelImg"
        src={thumbnailUrl}
        alt={`${data.snippet.channelTitle} 프로필 사진`}
      />
    </a>

    <div>
      <div class="title">{data.snippet.title}</div>
      <div class="uploader">{data.snippet.channelTitle}</div>
      <div class="flex">
        <div class="view">
          {ProcessViewCount(data.statistics.viewCount)}
        </div>
        <div class="date">
          {ProcessUploadDate(moment(data.snippet.publishedAt))}
        </div>
      </div>
    </div>
  </div>
</a>

<style>
  .card {
    text-decoration: none;
    cursor: pointer;
  }
  .thumbnail {
    width: 100%;
    object-fit: fill;
    border-radius: 12px;
    overflow: hidden;
  }
  .info {
    display: flex;
    margin-top: 12px;
  }
  .channelImg {
    width: 36px;
    height: 36px;
    border-radius: 18px;
    margin-right: 12px;
  }
  .title {
    color: #030303;
  }
  .uploader {
    font-size: 14px;
    margin-top: 8px;
  }
  .flex {
    display: flex;
  }
  .view {
    font-size: 14px;
  }
  .view::after {
    content: "•";
    margin: 0 4px;
  }
  .date {
    font-size: 14px;
  }
  .title {
    /* 2줄이 넘을 경우 ... 표시 */
    display: -webkit-box;
    overflow: hidden;
    line-clamp: 2;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
  }
</style>
