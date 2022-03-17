<template>
  <v-container>
    <v-row class="text-center mt-3">
      <v-col>
        <v-row class="justify-center">
          ニックネームと回数を入力してね。
        </v-row>
        <v-row dense class="justify-center">
          <v-col cols="8" >
            <v-text-field
              label="ニックネーム"
              v-model="nickname"
              placeholder="ニックネームを入力"
              :rules="[required]"
              disabled
            ></v-text-field>
          </v-col>
          <v-col cols="4">
            <v-text-field
              label="回数"
              v-model="count"
              placeholder="回数を入力"
              maxlength="3"
              suffix="回"
              :rules="[required]"
            ></v-text-field>
          </v-col>
        </v-row>
        <v-row dense>
          <v-col
            class="d-flex"
            cols="12"
            sm="6"
          >
            <v-select
              v-model="message"
              :items="items"
              label="メッセージ何がいい？"
              dense
              :hint="`メッセージ内容+ニックネーム`"
              persistent-hint
            ></v-select>
          </v-col>
        </v-row>
        <v-row>
          <v-col>
            <v-dialog
              transition="dialog-bottom-transition"
              max-width="600"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-row class="justify-center">
                  <v-btn
                    color="primary"
                    v-bind="attrs"
                    v-on="on"
                  >実行</v-btn>
                </v-row>
              </template>
              <template v-slot:default="dialog">
                <v-card>
                  <v-toolbar
                    color="primary"
                    dark
                  >元気！？</v-toolbar>
                  <v-card-text class="mt-2">
                    <ul>
                     <li v-for="i in Number(count)" :key="i">{{message}}{{nickname}}！！</li>
                    </ul>
                  </v-card-text>
                  <v-card-actions class="justify-end">
                    <v-btn
                      text
                      @click="dialog.value = false"
                    >閉じる</v-btn>
                  </v-card-actions>
                </v-card>
              </template>
            </v-dialog>
          </v-col>
        </v-row>
        <v-row>
          <v-col>
            社会人になって{{countDate}}日が経過しました。
          </v-col>
        </v-row>
        <v-row dense>
          <v-col>
            もうすっかり大人だね！！
          </v-col>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',
    data(){
      return{
        count:null,
        message: null,
        nickname: "りこちゃん",
        button:false,
        required: value => !!value || '必ず入力してね。',
        items: ["頑張れ！！", "元気！？", "そういう日もあるよね、", "こっからっしょ！"]
      }
    },
    computed:{
      countDate(){
        const now = new Date();
        const work = new Date(2021, 3, 1);
        return Math.floor((now-work)/ 1000 / 60 / 60 / 24);
      },
    },
    methods:{
      enter(){
        this.button = true;
      },
    }
  }
</script>
