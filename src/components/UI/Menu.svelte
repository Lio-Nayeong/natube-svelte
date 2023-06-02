<script>
  import { Link } from "svelte-routing";
  import IconLock from "./IconLock.svelte";

  export let activeMenu;

  const NAVIGATION_MENUS_2 = ["보관함", "시청 기록"];
  const NAVIGATION_MENUS_3 = ["인기", "음악", "영화", "게임", "스포츠", "학습"];
</script>

<div class="menu">
  <div class="line onMini">
    <Link to="/">
      <div class={activeMenu === "home" ? "focused" : "link"}>
        <div class="icon">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            fill="currentColor"
            class="w-6 h-6"
          >
            <path
              d="M11.47 3.84a.75.75 0 011.06 0l8.69 8.69a.75.75 0 101.06-1.06l-8.689-8.69a2.25 2.25 0 00-3.182 0l-8.69 8.69a.75.75 0 001.061 1.06l8.69-8.69z"
            />
            <path
              d="M12 5.432l8.159 8.159c.03.03.06.058.091.086v6.198c0 1.035-.84 1.875-1.875 1.875H15a.75.75 0 01-.75-.75v-4.5a.75.75 0 00-.75-.75h-3a.75.75 0 00-.75.75V21a.75.75 0 01-.75.75H5.625a1.875 1.875 0 01-1.875-1.875v-6.198a2.29 2.29 0 00.091-.086L12 5.43z"
            />
          </svg>
        </div>
        <div class="text">홈</div>
      </div>
    </Link>
    <div class="unavailable link">
      <IconLock />
      <div class="text">Shorts</div>
    </div>
    <Link to="/subscription">
      <div class={activeMenu === "subscription" ? "focused" : "link"}>
        <IconLock />
        <div class="text">구독</div>
      </div>
    </Link>
  </div>

  <div class="line onMini">
    {#each NAVIGATION_MENUS_2 as menu}
      <div class="unavailable">
        <IconLock />
        <div class="text">{menu}</div>
      </div>
    {/each}
  </div>

  <div class="line offMini">
    <div>탐색</div>
    {#each NAVIGATION_MENUS_3 as menu}
      <div class="unavailable">
        <IconLock />
        <div class="text">{menu}</div>
      </div>
    {/each}
  </div>

  <div class="offMini">
    <p class="footer">
      정보 보도자료 저작권
      <br />
      문의하기 크리에이터
      <br />
      광고 개발자
      <br />
      <br />
      약관 개인정보처리방침
      <br />
      정책 및 안전
      <br />
      NaTube 작동의 원리
      <br />
      새로운 기능 테스트하기
    </p>
  </div>
</div>

<style>
  .menu {
    position: fixed;
    width: 230px;
    height: 100%;
    top: 56px;
    padding: 12px;
    box-sizing: border-box;
    background-color: white;
  }
  .link,
  .focused,
  .unavailable {
    display: flex;
    height: 40px;
    padding: 0 16px;
    font-size: 14px;
    text-decoration: none;
    align-items: center;
  }
  .line {
    border-bottom: 1px solid rgba(0, 0, 0, 0.1);
    margin-bottom: 12px;
    padding-bottom: 12px;
  }
  .line > div:first-child {
    padding: 2px 16px;
  }
  .link {
    background-color: white;
    color: black;
  }
  .link:hover {
    border-radius: 10px;
    background-color: rgba(0, 0, 0, 0.05);
  }
  .icon {
    width: 24px;
    height: 24px;
    margin-right: 24px;
  }
  .focused {
    border-radius: 10px;
    background-color: rgba(0, 0, 0, 0.05);
    color: black;
  }
  .focused:hover {
    border-radius: 10px;
    background-color: rgba(0, 0, 0, 0.15);
  }
  .unavailable {
    background-color: white;
    color: rgba(128, 128, 128, 0.8);
  }
  .text {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    /* text-decoration: none; */
  }

  @media screen and (max-width: 990px) {
    .offMini {
      display: none;
    }
    .line {
      border-bottom: 0px;
      margin-bottom: 0px;
      padding-bottom: 0px;
    }
    .menu {
      width: 72px;
    }
    .link,
    .focused {
      flex-direction: column;
      height: 67px;
    }
    .icon {
      margin: 6px;
    }
    .text {
      margin: 0px;
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
      font-size: 10px;
    }
  }
  @media screen and (max-width: 620px) {
    .menu {
      display: none;
    }
  }
  .footer {
    font-size: 13px;
    color: #606060;
    padding: 2px 16px;
  }
</style>
