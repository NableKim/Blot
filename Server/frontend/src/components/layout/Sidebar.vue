<template>
  <aside class="main-sidebar">

    <!-- sidebar: style can be found in sidebar.less -->
    <section class="sidebar">
        <ul class="sidebar-menu">
            <li class="treeview active">
          <a>
              <span class="blank-line"></span>
            <i class="ri-stack-line"></i>
              <span class="blank"></span>
              <span class="treeview-title"><router-link to="/">메인화면</router-link></span>
          </a>
          <ul class="treeview-menu">
              <li><router-link to="/"><i class="fa fa-blank"></i><span class="blank"></span>메인화면</router-link></li>
          </ul>
        </li>
            
         <li class="treeview active">
          <a href="#">
              <span class="blank-line"></span>
            <i class="ri-newspaper-line"></i>
              <span class="blank"></span>
              <span class="treeview-title"><router-link to="/projadd">번역 프로젝트</router-link></span>
          </a>
          <ul class="treeview-menu">
            <li>
             <router-link to="/projadd"><i class="fa fa-blank"></i><span class="blank"></span>새로 만들기</router-link>
            </li>
              <li>
                  <router-link to="/taglist"><i class="fa fa-blank"></i><span class="blank"></span>태그별 보기</router-link>
            </li>
              <!--
              <li>
             <a href="index2.html"><i class="fa fa-blank"></i><span class="blank"></span>인기 프로젝트</a>
            </li>
              <li>
             <a href="index2.html"><i class="fa fa-blank"></i><span class="blank"></span>번역이 끝난 프로젝트</a>
            </li>
              -->
          </ul>
        </li>
            
  <li class="treeview active">
          <a href="#">
              <span class="blank-line"></span>
            <i class="ri-chat-smile-2-line"></i>
              <span class="blank"></span>
              <span class="treeview-title"><router-link to="/mylibrary">내 정보</router-link></span>
          </a>
          <ul class="treeview-menu">
            <li>
             <router-link to="/mylibrary"><i class="fa fa-blank"></i><span class="blank"></span>내 서재</router-link>
            </li>
              <li>
                  <router-link to="/myinfo"><i class="fa fa-blank"></i><span class="blank"></span>내 정보</router-link>
            </li>
          </ul>
        </li>
      </ul>
    </section>
    <!-- /.sidebar -->
  </aside>
</template>
<script>
export default {
  name: 'Sidebar',
  props: ['user'],
  data: {
  },
  methods: {
    logoutActive() {
      if (this.$session.has('username')) {
        // 세션 삭제
        this.$session.destroy()
        // 세션스토리지 삭제
        sessionStorage.removeItem('walletInstance')
        this.$store.commit('SET_IS_LOGGED_IN', false)
        this.$root.$emit('UserMenu')
        this.$router.replace(this.$route.query.redirect || '/')
        // this.$store.state.isLoggedIn
      }
    }
  },
  mounted: function() {
  }
}
</script>
<style>

/* BLOT : Resize Width */   
    .main-sidebar, .left-side {
        width:310px;
    }

/* BLOT : Sidebar Style */
    .skin-black-light .main-sidebar,
    .skin-black-light .left-side {
      background: url(/static/img/blurwp.png) no-repeat center center/cover;
      color:white; 
    }

    .treeview-menu > li > a{
        color:white;
    }
    
    .sidebar .blank-line {
        top: 0px;
        left: 50px;
        position: fixed;
        padding: 12px;
        height: 100%;
        background-color: white;
        box-shadow: 0 0 black;
        z-index:1000;
    }
    
    .sidebar-menu > li > a {
        display: table-cell;
        width:320px;
        vertical-align: middle;
        font-size: 14px;
        color: white;
        background: rgba(1,1,1,0.3);
        height:50px;
        font-weight:600;
    }

    .sidebar-menu > li > a > i {
        font-weight: 100;
        font-size:15px;
    }
    
    .sidebar .blank {
        padding: 15px;
        margin: 15px;
    }
    
    .fa, .fa-angle-left, .fa-fw {
        margin-bottom:20px;
    }
    
    .treeview-menu > li > a {
        font-size:12px;
        font-weight:100;
        padding: 3px 3px 3px 15px;
    }
    
    .treeview-menu > li > .active {
        // border-bottom:2px solid white;
        font-weight: 600;
    }
    
    .treeview > ul.treeview-menu {
        padding-top:5px;
        padding-bottom:20px;
    }
    
    .user-image.circle {
        width: 22px;
        height: 22px;
        border-radius: 50%;
        margin-left: 10px;
        margin-right: 10px;
        margin-top: -2px;
    }
    
/* Co-Pilot Style */
    .sidebar-menu > li > a {
        color:white;
      padding: 7px 7px 7px 17px;
    }

    .sidebar-menu li.active > a > .fa-angle-left,
    .sidebar-menu li.active > a > .pull-right-container > .fa-angle-left {
      animation-name: rotate;
      animation-duration: 0.2s;
      animation-fill-mode: forwards;
    }

    .treeview-title {
      z-index: 1;
    }

    @keyframes rotate {
      0% {
        transform: rotate(0deg);
      }

      100% {
        transform: rotate(-90deg);
      }
    } 
    .treeview-title a {
        color:white
    }
</style>
