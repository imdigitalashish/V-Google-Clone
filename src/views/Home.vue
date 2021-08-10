<template>
  <div class="home">
    <div class="home__header">
        <div class="home__headerLeft">
            <a routerLink="/search">About</a>
            <a routerLink="/search">Store</a>
        </div>
        <div class="home__headerRight">
            <a routerLink="/search">Gmail</a>
            <a routerLink="/search">Images</a>

        </div>
    </div>
    <div class="home__body">
        <img src="https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png" alt="">
        <div class="home__inputContainer">
            <!-- <app-search-box [hideButtons]=false></app-search-box> -->
            <HelloWorld />
        </div>
    </div>
</div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/SearchBoxComponent.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  }
}
</script>


<style>
.home {
    display: flex;
    flex-direction: column;
    height: 100vh;
    
}

.home__header {
    display: flex;
    justify-content: space-between;
    padding: 20px 30px;
    align-items: center;
}

.home__header a {
    text-decoration: inherit;
    margin-right: 20px;
    color: rgba(0, 0, 0, 0.87);
    font-size: 15px;   
}

.home__header a:hover {
    text-decoration: underline;
}

.home__headerRight {
    display: flex;
    justify-content: space-between;
    align-items: center;
    min-width: 13vw;
}

.home__headerRight > mat-icon {
    margin-right: 20px;

}

.home__body {

    flex: 1;
    display: flex;
    margin-top: 10%;
    flex-direction: column;
}

.home__body > img {
    object-fit: contain;
    height: 100px;
}


</style>