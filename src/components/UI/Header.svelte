<script>
  import { Link } from "svelte-routing";
  import natube_logo from "../../assets/natube_logo.png";

  export let toggleMenu;
</script>

<div class="header">
  <div class="tab">
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <div class="icon" on:click={toggleMenu}>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="w-6 h-6"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"
        />
      </svg>
    </div>
    <Link to="/">
      <img src={natube_logo} alt="로고" class="logo" />
    </Link>
  </div>

  <div class="center-tab">
    <input class="input" placeholder="검색" />
    <div class="search-icon">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="w-6 h-6"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z"
        />
      </svg>
    </div>
  </div>
  <div class="tab">
    <div class="search-icon-mini">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="w-6 h-6"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z"
        />
      </svg>
    </div>
    <div class="icon">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="w-6 h-6"
        color="rgba(128, 128, 128, 0.8)"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M12 6.75a.75.75 0 110-1.5.75.75 0 010 1.5zM12 12.75a.75.75 0 110-1.5.75.75 0 010 1.5zM12 18.75a.75.75 0 110-1.5.75.75 0 010 1.5z"
        />
      </svg>
    </div>

    <div class="icon">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="w-6 h-6"
        color="#065fd4"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M17.982 18.725A7.488 7.488 0 0012 15.75a7.488 7.488 0 00-5.982 2.975m11.963 0a9 9 0 10-11.963 0m11.963 0A8.966 8.966 0 0112 21a8.966 8.966 0 01-5.982-2.275M15 9.75a3 3 0 11-6 0 3 3 0 016 0z"
        />
      </svg>
    </div>
    <div class="login">로그인</div>
  </div>
</div>

<style>
  .header {
    display: flex;
    position: fixed;
    top: 0;
    width: 100%;
    height: 56px;
    padding: 0 16px;
    background-color: white;
    align-items: center;
    justify-content: space-between;
    box-sizing: border-box;
  }
  .tab {
    display: flex;
    align-items: center;
  }
  .icon {
    width: 24px;
    height: 24px;
    padding: 8px;
    cursor: pointer;
  }
  .icon:first-child:hover {
    border-radius: 24px;
    background-color: rgba(0, 0, 0, 0.1);
  }
  .logo {
    padding-left: 16px;
  }
  .center-tab {
    display: flex;
    align-items: center;
    flex: 0 1 640px;
    padding: 0px 4px 0px 16px;
  }
  .input {
    height: 40px;
    font-size: 16px;
    border: 1px solid #d3d3d3;
    border-radius: 40px 0 0 40px;
    padding: 0px 4px 0px 16px;
    margin-left: 32px;
    box-sizing: border-box;
    flex: 1;
  }
  .search-icon {
    width: 24px;
    height: 24px;
    padding: 7px 20px;
    border: 1px solid #d3d3d3;
    border-left: 0px solid #d3d3d3;
    border-radius: 0 40px 40px 0;
    background-color: #f8f8f8;
    cursor: pointer;
  }
  .search-icon-mini {
    display: none;
    width: 24px;
    height: 24px;
    padding: 8px;
    cursor: pointer;
  }
  .login {
    color: #065fd4;
    text-decoration: line-through;
  }

  @media screen and (max-width: 990px) {
    .login {
      display: none;
    }
    .search-icon {
      margin-right: 20px;
    }
  }
  @media screen and (max-width: 620px) {
    .center-tab {
      display: none;
    }
    .search-icon-mini {
      display: block;
    }
    .login {
      display: none;
    }
  }
</style>
