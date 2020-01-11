<template>
  <div id="app" class="chat-container scrollingContainer animated zoomIn">
    <div class="header">
      <div class="header__avatar">
        <img src="./assets/avatar.png" class="avatar" />
      </div>
      <div class="header__caption">
        <div class="header-right">
          <div class="header-right__image">
            <img src="./assets/message-icon.png" class="message-image" />
          </div>
          <div class="header-right__text">
            <h1 class="chat-header-container-image__caption_h1">Павел Гордеев</h1>
            <h3 class="chat-header-container-image__caption_h3">Цепная Реакция</h3>
          </div>
        </div>
      </div>
    </div>
    <div class="chat-content" style="padding-bottom:0px;">
      <div class="chat-content-container">
        <div class="chat-content-list">
          <div class="chat-content-item manager" id="replica-0" v-if="count >= 0">
            <div class="chat-content-desc">
              <img class="chat-content-desc-image" src="./assets/avatar.png" alt />
              <div class="chat-content-desc-item">
                <p>
                  <vue-typed-js
                    :type-speed="20"
                    @onComplete="onComplete"
                    :showCursor="false"
                    :strings="['Здравствуйте, меня зовут Павел Гордеев. Я бесплатный финансовый консультант, представляю компанию Цепная Реакция. Хочу проконсультировать Вас по поводу дополнительного пассивного заработка практически без затрат личного времени.']"
                  >
                    <span class="typing"></span>
                  </vue-typed-js>
                </p>
              </div>
            </div>
          </div>
          <div class="chat-content-item manager" id="replica-1" v-if="count >= 1">
            <div class="chat-content-desc">
              <img class="chat-content-desc-image" src="./assets/avatar.png" alt />
              <div class="chat-content-desc-item">
                <p>
                  <vue-typed-js
                    :type-speed="20"
                    :strings="['Вы мужчина или женщина?']"
                    @onComplete="onComplete"
                    :showCursor="false"
                  >
                    <span class="typing"></span>
                  </vue-typed-js>
                </p>
              </div>
            </div>
          </div>
          <div
            class="chat-content-item user"
            id="user-replica-0"
            style="display: block; text-align: right;"
            v-if="count >= 3"
          >{{ gender }}</div>
          <div class="chat-content-item manager" id="replica-1" v-if="count >= 3">
            <div class="chat-content-desc">
              <img class="chat-content-desc-image" src="./assets/avatar.png" alt />
              <div class="chat-content-desc-item">
                <p>
                  <vue-typed-js
                    :type-speed="20"
                    :strings="['Каков Ваш средний ежемесячный заработок в рублях?']"
                    @onComplete="onComplete"
                    :showCursor="false"
                  >
                    <span class="typing"></span>
                  </vue-typed-js>
                </p>
              </div>
            </div>
          </div>
          <div
            class="chat-content-item user"
            id="user-replica-0"
            style="display: block; text-align: right;"
            v-if="price != 0"
          >{{ price }} рублей</div>
          <div class="chat-content-item manager" id="replica-1" v-if="price != 0">
            <div class="chat-content-desc">
              <img class="chat-content-desc-image" src="./assets/avatar.png" alt />
              <div class="chat-content-desc-item">
                <p>
                  <vue-typed-js
                    :type-speed="20"
                    :strings="['Сколько времени в день Вы готовы уделять дополнительному заработку?']"
                    @onComplete="onComplete"
                    :showCursor="false"
                  >
                    <span class="typing"></span>
                  </vue-typed-js>
                </p>
              </div>
            </div>
          </div>
          <div
            class="chat-content-item user"
            id="user-replica-0"
            style="display: block; text-align: right;"
            v-if="time != 0"
          >{{ time }}</div>

          <div class="chat-content-item manager" id="replica-1" v-if="(count >= 5) && (time != 0)">
            <div class="chat-content-desc">
              <img class="chat-content-desc-image" src="./assets/avatar.png" alt />
              <div class="chat-content-desc-item">
                <p>
                  <vue-typed-js
                    :type-speed="20"
                    :strings="[`Спасибо! Согласно нашим расчетам Вы можете зарабатывать дополнительно ${result}$ в день без усилий.`]"
                    @onComplete="onComplete"
                    :showCursor="false"
                  >
                    <span class="typing"></span>
                  </vue-typed-js>
                </p>
              </div>
            </div>
          </div>

          <div class="chat-content-item manager" id="replica-1" v-if="count >= 6">
            <div class="chat-content-desc">
              <img class="chat-content-desc-image" src="./assets/avatar.png" alt />
              <div class="chat-content-desc-item">
                <p>
                  <vue-typed-js
                    :type-speed="20"
                    :strings="['Для этого не нужно никаких дополнительных знаний.']"
                    @onComplete="onComplete"
                    :showCursor="false"
                  >
                    <span class="typing"></span>
                  </vue-typed-js>
                </p>
              </div>
            </div>
          </div>

          <div class="chat-content-item manager" id="replica-1" v-if="count >= 7">
            <div class="chat-content-desc">
              <img class="chat-content-desc-image" src="./assets/avatar.png" alt />
              <div class="chat-content-desc-item">
                <p>
                  <vue-typed-js
                    :type-speed="20"
                    :strings="['От Вас требуется только желание улучшить свою жизнь.']"
                    @onComplete="onComplete"
                    :showCursor="false"
                  >
                    <span class="typing"></span>
                  </vue-typed-js>
                </p>
              </div>
            </div>
          </div>

          <div class="chat-content-item manager" id="replica-1" v-if="count >= 8">
            <div class="chat-content-desc">
              <img class="chat-content-desc-image" src="./assets/avatar.png" alt />
              <div class="chat-content-desc-item">
                <p>
                  <vue-typed-js
                    :type-speed="20"
                    :strings="[`Если вам интересен дополнительный заработок в размере ${result} $ в месяц - нажмите кнопку ниже.`]"
                    @onComplete="onComplete"
                    :showCursor="false"
                  >
                    <span class="typing"></span>
                  </vue-typed-js>
                </p>
              </div>
            </div>
          </div>
        </div>

        <div class="chat-content-buttons-gender" style="display: block;" v-if="count == 2">
          <div class="chat-content-buttons-gender-block">
            <span class="gender" id="chooseGender" gender="m" @click="setGender('Mужчина')">Мужчина</span>
          </div>
          <div class="chat-content-buttons-gender-block">
            <span class="gender" id="chooseGender" gender="f" @click="setGender('Женщина')">Женщина</span>
          </div>
        </div>
        <div class="form-group" id="selectMoney" v-if="(price == 0) && count == 4">
          <div class="form-group-inline">
            <select name="money" required class="custom-select select-money" v-model="price">
              <option value="0">Рублей</option>
              <option value="10000">10 000</option>
              <option value="20000">20 000</option>
              <option value="30000">30 000</option>
              <option value="40000">40 000</option>
              <option value="50000">50 000 и более</option>
            </select>
          </div>
        </div>
        <div class="form-group" id="selectHours" v-if="(time == 0) && (count == 5)">
          <div class="form-group-inline" style="display:flex; justify-content:center;">
            <div
              class="form-group-inline growth"
              style="margin-right:20px; display:flex; align-items:center"
            >
              <select
                name="hours"
                class="custom-select select-hours"
                required
                style="margin-left:10px;"
                v-model="time"
              >
                <option value="0">Часов</option>
                <option>не более 1 часа</option>
                <option>не более 3 часов</option>
                <option>не более 5 часов</option>
                <option>более 5 часов</option>
              </select>
            </div>
          </div>
        </div>
        <div class="wrapper-button phone" v-if="count == 9">
          <a href="#" style="color:white; text-decoration:none;" onclick>
            <span style="cursor:pointer;" class="ref" id="secondPage">Узнать подробнее</span>
          </a>
        </div>
        <div id="botscroll">

        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { VueTypedJs } from "vue-typed-js";
import {scroller} from 'vue-scrollto/src/scrollTo'

export default {
  name: "app",
  data() {
    return {
      count: 0,
      gender: "",
      price: 0,
      time: 0
    };
  },
  components: {
    VueTypedJs,
  },
  methods: {
    onComplete: function() {
      this.count++;
      const firstScrollTo = scroller()
      firstScrollTo('#botscroll')
    },
    setGender(gender) {
      this.onComplete();
      this.gender = gender;
    }
  },
  computed: {
    result(){
        var hours = 1;
        if (this.time == 'не более 1 часа') {
            hours = 1;
        }
        if (this.time == 'не более 3 часов') {
            hours = 3;
        }
        if (this.time == 'не более 5 часов') {
            hours = 5;
        }
        if (this.time == 'более 5 часов') {
            hours = 8;
        }
        const result = Math.sqrt(this.price * hours).toFixed(2);
        return result;
    }
  }
};
</script>

<style lang="scss">

@import "~animate.css/animate.css";


select:active, select:focus{
  outline:none
}

body {
  margin: 0;
  background-color: #1e1d2b;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: #e3e3e3;
      min-height: 100vh;
      height: auto;
  // margin-top: 60px;
}
.header {
  display: flex;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 75px;
  justify-content: flex-start;
  background: linear-gradient(to top, #d26713 0, #f0ad62 100%);
}
.header__avatar {
  width: auto;
  display: flex;
  margin: auto 0px;
  justify-content: center;
  margin-left: 10px;
}
.header__caption {
  margin-left: 10px;
}
.header-right__text {
  text-align: left;
}
.header-right {
  display: flex;
  width: auto;
  align-items: center;
  height: 100%;
}
.header-right__image {
  margin-right: 10px;
}
.chat-header-container-image__caption_h1 {
  margin: 0;
  font-size: 1.8em;
  color: white;
  font-weight: 400;
  @media screen and (max-width: 1000px) {
    font-size: 1.4em;
  }
}
.chat-header-container-image__caption_h3 {
  margin: 0;
  font-size: 0.9em;
  font-weight: 400;
  color: #efefef;
  @media screen and (max-width: 1000px) {
    font-size: 0.7em;
  }
}
.avatar {
  display: flex !important;
  width: 54px;
  height: 54px;
  max-width: 54px;
}
.message-image {
  display: flex !important;
  width: 32px;
  height: 32px;
  max-width: 32px;
}
.chat-content {
  padding: 75px 0 85px 0;
}
.chat-content-container {
  padding: 15px 0;
}
.chat-content-list {
  position: relative;
  // text-align: center;
  margin: 0;
  padding: 0;
  border: 0;
}
.chat-content-item {
  width: auto;
  padding: 10px 15px;
  display: block;
}
.chat-content-item .chat-content-desc {
  position: relative;
  width: auto;
}

.chat-content-item .chat-content-desc-item p {
  position: relative;
  display: inline-block;
  text-align: left;
  background-color: #fff;
  padding: 20px;
  border-radius: 5px;
  color: rgb(0, 0, 0);
  font: 12px/120% Tahoma, Geneva, sans-serif;
  font-size: 22px;
  margin: 0;
  @media (max-width: 600px) {
    font-size: 14px;
    padding: 10px;
  }
}
.chat-content-item .chat-content-desc-image {
  position: absolute;
  top: 50%;
  left: 0;
  transform: translateY(-50%);
  max-height: 40px;
  margin-bottom: 6px;
  margin-right: 15px;
}
.chat-content-item .chat-content-desc-item {
  display: block;
  font-weight: 300;
  text-align: left;
  margin: 0 0 0 auto;
  width: auto;
  padding-left: 60px;
}
.chat-content-item .chat-content-desc-item p:after {
  position: absolute;
  content: "";
  left: -22px;
  top: 50%;
  transform: translateY(-50%);
  width: 6px;
  height: 0px;
  border: 8px solid transparent;
  border-right-color: #fff;
  box-sizing: inherit;
}
.chat-container {
  
}
.chat-content-buttons-gender {
  z-index: 1;
  width: 100%;
  text-align: center;
  font-size: 0;
}
.chat-content-buttons-gender-block {
  font-size: 16px;
  cursor: pointer;
  display: inline-block;
  min-width: 130px;
  border-radius: 2px;
  background: #4267b2;
  color: #fff;
  padding: 0 8px;
  margin: 60px 5px;
}
.chat-content-buttons-gender-block span {
  display: block;
  padding: 20px 0;
}

.chat-content-item.user {
  position: relative;
  background-color: #3fc726;
  color: #fff;
  padding: 20px;
  max-width: 60%;
  border-radius: 5px;
  font-size: 22px;
  margin-left: auto;
  margin-right: 1rem;
  display: block;
  text-align: right;
  @media screen and (max-width: 600px) {
    font-size: 1em !important;
    vertical-align: top !important;
  }
}
.chat-content-item.user:before {
  position: absolute;
  content: "";
  right: -16px;
  top: 50%;
  transform: translateY(-50%);
  width: 6px;
  height: 0px;
  border: 6px solid transparent;
  border-left-color: #3fc726;
}

.custom-select {
  font-size: 18px;
  font-weight: 300;
  appearance: none;
  box-shadow: 0 2px 0 rgba(0, 0, 0, 0.4);
  border-radius: 10px;
  background: url(./assets/arrow_down.png) no-repeat right 10px center, #d0d0d0;
  background-size: 10px;
  padding: 7px 30px 7px 15px;
  min-height: 34px;
}
.wrapper-button {
  text-align: center;
  width: 320px;
  padding: 30px 0px 30px 0px;
  margin: 0 auto;
}

.wrapper-button.phone .ref,
.wrapper-button.phone button {
  vertical-align: middle;
  background: #40c043;
  display: inline-block;
  max-width: 527px;
  width: 100%;
  font-family: Roboto;
  font-size: 18px;
  text-transform: uppercase;
  color: #fff;
  font-weight: 500;
  text-shadow: none;
  text-decoration: none;
  outline: 0;
  border-radius: 60px;
  padding: 20px 0;
  line-height: 1;
  letter-spacing: -1.3px;
  box-shadow: 0 12px 24px rgba(64, 192, 67, 0.52);
  border: none;
}
</style>
