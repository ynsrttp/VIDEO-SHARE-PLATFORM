<template>
  <v-app :dark="theme">
    <v-navigation-drawer v-model="drawer" app clipped flating temporary>
      <v-list  style="margin-top: 50px;">
        <v-row class="ma-2 mb-3">
        <v-icon style="font-weight: bolder;" class="mx-4" large>mdi-video</v-icon>
      <v-toolbar-title class="align-center">
        <span style="font-weight: bolder;" class="title">YOUTUBE</span>
      </v-toolbar-title>
        </v-row>
        <v-list-item v-for="item in items" :key="item.icon" link>
          <v-list-item-action style="margin-left: 9px;">
            <v-icon style="font-weight: bolder;">{{ item.icon }}</v-icon>
            <v-list-item-title class="ma-4">{{ item.text }}</v-list-item-title>
          </v-list-item-action>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar app clipped-left>
      <v-app-bar-nav-icon @click="drawer=!drawer"/>
      <v-icon class="mx-4" large>mdi-video</v-icon>
      <v-toolbar-title class="align-center">
        <span class="title">YOUTUBE</span>
      </v-toolbar-title>      
      <v-text-field class="mb-8" style="height: 25px;" solo placeholder="Ara..." single-line append icon="mdi-magnify" color="white"/>
    <v-spacer/>
    <v-btn class="m1-0" icon>
      <v-icon>mdi-apps</v-icon>
    </v-btn>
    <v-btn class="ma-2" icon>
      <v-icon>mdi-bell</v-icon>
    </v-btn>
    <div>
      <v-menu style="position: absolute; left: 93%; top: 7%;" v-model="menu" :close-on-content-click="false" :nudge-width="250" offset-x>
        <template v-slot:activator="{on}">
          <v-avatar size="40" @click="menu = !menu">
            <img v-on="on" src="https://raw.githubusercontent.com/github/explore/cebd63002168a05a6a642f309227eefeccd92950/topics/vue/vue.png"/>
          </v-avatar>    
        </template>
        <v-card> 
          <v-list>
            <v-list-item>
              <v-list-item-avatar></v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title style="font-size: 14px; font-weight: bolder">Yunus Ortatepe</v-list-item-title>
                <v-list-item-subtitle>@ynsrttp</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-list>
          <v-divider/>
          <v-list>
            <v-list-item>
              <v-list-item-action>
                <v-icon>mdi-cog</v-icon>
              </v-list-item-action>
              <v-list-item-title>Ayarlar</v-list-item-title>
            </v-list-item>
          </v-list>
          <v-list>
            <v-list-item>
              <v-list-item-action>
                <v-switch v-model="theme" color="black"/>
              </v-list-item-action>
              <v-list-item-title>Dark Theme</v-list-item-title>
            </v-list-item>
          </v-list>
          <v-card-actions>
            <v-spacer/>
            <v-btn color="primary" text @click="menu=false">
              Çıkış            
            </v-btn>
          </v-card-actions>
        </v-card>      
      </v-menu>
    </div>     
    </v-app-bar>
    <v-content>
      <v-container style="margin-top: 50px;">
        <v-row class="mb-4 mt-7">
          <v-col  sm="6" md="4" lg="3" xl="2" v-for="(item,index) in 200" :key="index">
            <v-card>
              <v-img height="200px" :src="`https://picsum.photos/500/300?image=${(index+1)}`" :lazy-src="`https://picsum.photos/10/6?image=${(index+1)}`"></v-img>
              <v-card-subtitle class="">Number {{ item }}</v-card-subtitle>
              <v-card-text class="text--primary"><div>Baslık Alanı</div><div>Baslik İçerigi</div></v-card-text>
              <v-card-actions>
                <v-btn color="orange" text>Kaydet</v-btn>
                <v-btn color="orange" text>Paylas</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    menu:false,
    theme:false,
    drawer:false,
    items:[
      {icon:"mdi-trending-up", text:"Popüler İçerik"},
      {icon:"mdi-youtube-subscription", text:"Takip"},
      {icon:"mdi-history", text:"Geçmiş"},
      {icon:"mdi-playlist-play", text:"Oynatma Listesi"},
      {icon:"mdi-clock", text:"Alarm"},
    ]

  }),

  watch:{
    theme:function(next){
      this.$vuetify.theme.dark=next;
    }
  }
};
</script>


