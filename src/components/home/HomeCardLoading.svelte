<div class="card">
  <div class="thumbnail" />
  <div class="info">
    <div class="channel" />
    <div class="flex">
      <div class="title" />
      <div class="content" />
    </div>
  </div>
</div>

<style>
  .card {
    text-decoration: none;
    /* cursor: pointer; */
  }
  .thumbnail {
    display: flex;
    /* flex: 0 0 300px; */
    width: 100%;
    height: 180px;
    object-fit: fill;
    border-radius: 12px;
    background-color: rgba(0, 0, 0, 0.15);
  }
  .info {
    display: flex;
    margin-top: 12px;
  }
  .channel {
    width: 36px;
    height: 36px;
    border-radius: 18px;
    margin-right: 12px;
    background-color: rgba(0, 0, 0, 0.1);
  }
  .flex {
    display: flex;
    flex-direction: column;
  }
  .title {
    width: 190px;
    height: 18px;
    border-radius: 3px;
    background-color: rgba(0, 0, 0, 0.1);
  }
  .content {
    width: 150px;
    height: 18px;
    border-radius: 3px;
    background-color: rgba(0, 0, 0, 0.1);
    margin-top: 8px;
  }
</style>
