/* eslint-disable vue/require-v-for-key */
<template>
  <div class="header">
    <div class="header__container">
      <p class="header__title">Новый гороскоп на 2021 год!</p>
      <p class="header__text">Узнайте, что Вас ждёт.</p>
    </div>
  </div>
  <div class="container">
    <form @submit.prevent="sendData">
      <div v-show="display === 1" class="display">
        <div class="goroskop">
          <div class="goroskop-circle" id="goroskop-circle"></div>
        </div>

        <h1 class="display__title">Узнайте, как 2021 год изменит жизнь каждого из нас!</h1>
        <h3 class="display__text">К сожалению, 2020 год принес нам немало неприятностей, даже откровенных проблем и несчастий. Не смотря на это, 3 знака зодиака очень скоро обретут долгожданное счастье! 2021 год затронет своими потрясениями каждого из нас.</h3>
      
        <div class="form__header">
          <h2 class="form__header-title">Укажите свой пол:</h2>
        </div>

        <div class="form__input">
          <div>
            <input v-model="formData.gender" type="radio" id="female" name="gender" value="Женщина">
            <label for="female">Женщина</label>
          </div>

          <div>
            <input v-model="formData.gender" type="radio" id="male" name="gender" value="Мужчина">
            <label for="male">Мужчина</label>
          </div>
        </div>

        <button v-if="formData.gender" type="button" @click="changeDisplay">ДАЛЕЕ</button>
      </div>

      <div v-show="display === 2" class="display">
        <div class="range">
          <div class="range-line-2"></div>
        </div>
          <div class="form__header">
            <h2 class="form__header-title">В какое время суток Вы чувствуете себя наиболее комфортно?</h2>
          </div>
          <div class="form__input-l">
            <div>
              <input v-model="formData.dayTime" type="radio" id="morning" name="dayTime" value="Утро">
              <label for="morning">Утро</label>
            </div>
            <div>
              <input v-model="formData.dayTime" type="radio" id="night" name="dayTime" value="Ночь">
              <label for="night">Ночь</label>
            </div>            
            <div>
              <input v-model="formData.dayTime" type="radio" id="evening" name="dayTime" value="Вечер">
              <label for="evening">Вечер</label>
            </div>
            <div>
              <input v-model="formData.dayTime" type="radio" id="noon" name="dayTime" value="День">
              <label for="noon">День</label>
            </div>
          </div>
          
          <button v-if="formData.dayTime" type="button" @click="changeDisplay">ДАЛЕЕ</button>
      </div>

      <div v-show="display === 3" class="display">
        <div class="range">
          <div class="range-line-3"></div>
        </div>
          <div class="form__header">
            <h2 class="form__header-title">Подскажите, мучает ли Вас бессонница последнее время?</h2>
          </div>
          <div class="form__input-l">
            <div>
              <input v-model="formData.insomnia" type="radio" id="insomnia_yes" name="insomnia" value="Да">
              <label for="insomnia_yes">Да</label>
            </div>

            <div>
              <input v-model="formData.insomnia" type="radio" id="insomnia_no" name="insomnia" value="Нет">
              <label for="insomnia_no">Нет</label>
            </div>
            
            <div>
              <input v-model="formData.insomnia" type="radio" id="insomnia_sometime" name="insomnia" value="Иногда">
              <label for="insomnia_sometime">Иногда</label>        
            </div>
          </div>

          <button v-if="formData.insomnia" type="button" @click="changeDisplay">ДАЛЕЕ</button>
      </div>

      <div v-show="display === 4" class="display">
        <div class="range">
          <div class="range-line-4"></div>
        </div>
          <div class="form__header">
            <h2 class="form__header-title">Чувствуете ли Вы в последнее время, что вам никак не удается осуществить ваши планы?</h2>
          </div>
          <div class="form__input-l">
            <div>
              <input v-model="formData.makesPlan" type="radio" id="plan_yes" name="makesPlan" value="Да">
              <label for="plan_yes">Да</label>
            </div>
            
            <div>
              <input v-model="formData.makesPlan" type="radio" id="plan_no" name="makes-plan" value="Нет">
              <label for="plan_no">Нет</label>
            </div>
            
            <div>
              <input v-model="formData.makesPlan" type="radio" id="plan_sometime" name="makes-plan" value="Иногда">
              <label for="plan_sometime">Иногда</label>        
            </div>
          </div>

          <button v-if="formData.makesPlan" type="button" @click="changeDisplay">ДАЛЕЕ</button>
      </div>

      <div v-show="display === 5" class="display">
        <div class="range">
          <div class="range-line-5"></div>
        </div>
          <div class="form__header">
            <h2 class="form__header-title">Какой Вы видите свою жизнь через 5 лет?</h2>
          </div>
          <div class="form__input-l">
            <div>
              <input v-model="formData.FiveYearsAgo" type="radio" id="home" name="FiveYearsAgo" value="Брак, семья, дети, дом">
              <label for="home">Брак, семья, дети, дом</label>
            </div>
            
            <div>
              <input v-model="formData.FiveYearsAgo" type="radio" id="travel" name="FiveYearsAgo" value="Путешествия по Миру">
              <label for="travel">Путешествия по Миру</label>
            </div>
            
            <div>
              <input v-model="formData.FiveYearsAgo" type="radio" id="job" name="FiveYearsAgo" value="Успешная карьера">
              <label for="job">Успешная карьера</label>
            </div>
            
            <div>
              <input v-model="formData.FiveYearsAgo" type="radio" id="all" name="FiveYearsAgo" value="Всё вместе">
              <label for="all">Всё вместе</label>
            </div>
          </div>

          <button v-if="formData.FiveYearsAgo" type="button" @click="changeDisplay">ДАЛЕЕ</button>
      </div>

      <div v-show="display === 6" class="display">
        <div class="range">
          <div class="range-line-6"></div>
        </div>
          <div class="form__header">
            <h2 class="form__header-title">Введите дату своего рождения:</h2>
          </div>
          <div class="form__input-l">
            <select v-model="formData.day">
              <option selected disabled>Число</option>
              <option v-for="n in 31" :key="n">{{n}}</option>
            </select>
            
            <select v-model="formData.month">
              <option selected disabled>Месяц</option>
              <option v-for="n in 12" :key="n">{{n}}</option>
            </select>
            
            <select v-model="formData.year">
              <option selected disabled>Год</option>
              <option v-for="n in 100" :key="n">{{n}}</option>
            </select>
          </div>

          <div class="zodiak__box">
            <img @click="setZodiak" class="zodiak__box__item" src="./assets/zodiak/1_Capricorn.png" alt="Capricorn">
            <img @click="setZodiak" class="zodiak__box__item" src="./assets/zodiak/2_Aquarius.png" alt="Aquarius">
            <img @click="setZodiak" class="zodiak__box__item" src="./assets/zodiak/3_Pisces.png" alt="Pisces">
            <img @click="setZodiak" class="zodiak__box__item" src="./assets/zodiak/4_aries.png" alt="Aries">
            <img @click="setZodiak" class="zodiak__box__item" src="./assets/zodiak/5_Taurus.png" alt="Taurus">
            <img @click="setZodiak" class="zodiak__box__item" src="./assets/zodiak/6_Gemini.png" alt="Gemini">
            <img @click="setZodiak" class="zodiak__box__item" src="./assets/zodiak/7_Rak.png" alt="Rak">
            <img @click="setZodiak" class="zodiak__box__item" src="./assets/zodiak/8_Leo.png" alt="Leo">
            <img @click="setZodiak" class="zodiak__box__item" src="./assets/zodiak/9_Virgo.png" alt="Virgo">
            <img @click="setZodiak" class="zodiak__box__item" src="./assets/zodiak/10_Libra.png" alt="Libra">
            <img @click="setZodiak" class="zodiak__box__item" src="./assets/zodiak/11_Scorpio.png" alt="Scorpio">
            <img @click="setZodiak" class="zodiak__box__item" src="./assets/zodiak/12_Sagittarius.png" alt="Sagittarius">
          </div>
          
          <button v-if="formData.day && formData.month && formData.year && formData.zodiak" type="submit" @click="changeDisplayWST">ДАЛЕЕ</button>
      </div>
    </form>

      <div v-show="display === 7" class="display">
        <h2 class="progress__title">Обработка Ваших данных:</h2>
        <div class="progress">
          <div class="progress__line-bg">
            <div class="progress__line" id="progress__line"></div>
          </div>
        </div>

        <div class="display7">
          <div class="display7__item">
            <p>Анализ введенных данных . . . . . . .</p>
            <p id="p1">Выполнено!</p>
          </div>
          <div class="display7__item">
            <p>Коррекция астрологического знака . . . . . . . </p>
            <p id="p2">Выполнено!</p>
          </div>
          <div class="display7__item">
            <p>Расчет вариаций ответов . . . . . . . </p>
            <p id="p3">Выполнено!</p>
          </div>
          <div class="display7__item">
            <p>Генерация предсказания . . . . . . . </p>
            <p id="p4">Выполнено!</p>
          </div>
          <div class="display7__item">
            <p>Сохранение результата . . . . . . . </p>
            <p id="p5">Выполнено!</p>
          </div>
          <div class="display7__item">
            <p>Поиск свободного оператора . . . . . . . </p>
            <p id="p6">Выполнено!</p>
          </div>
          <div class="display7__item">
            <p>Начала озвучки и записи аудио-сообщения . . . . . . . </p>
            <h3 id="p7">ИДЁТ ЗАПИСЬ!</h3>
            <p id="p8">Выполнено!</p>
          </div>
            <h3 id="p9">ГОТОВО!</h3>
        </div>
      </div>

      <div v-show="display === 8" class="display">
        <h2>Спасибо за Ваши ответы!</h2>
        <h2 class="display__title">Поздравляем! Прослушать свой персональный гороскоп возможно уже сейчас!</h2>
        <h2>2021 год Вас ошарашит!</h2>
        <h3>
          Вас ждёт то, чего Вы никак не ожидали. Первые известия Вы получите совсем скоро, возможно это 17-18 ноября!
          Что бы прослушать аудио-сообщение, необходимо нажать на кнопку ниже и позвонить со своего мобильного телефона. Позвоните и Прослушайте очень серьезную информацию!
        </h3>

        <button @click="showing">Звонить и слушать</button>
        
        <div v-if="show" class="fetchingData">
          <h2>Данные API</h2>
          <div class="fetchingData__item">
            <p class="fetchingData__item-title">Name:</p><p>{{fetchingData.name}}</p>
          </div>
          <div class="fetchingData__item">
            <p class="fetchingData__item-title">Height:</p><p>{{fetchingData.height}}</p>
          </div>
          <div class="fetchingData__item">
            <p class="fetchingData__item-title">Mass:</p><p>{{fetchingData.mass}}</p>
          </div>
          <div class="fetchingData__item">
            <p class="fetchingData__item-title">Hair color:</p><p>{{fetchingData.hair_color}}</p>
          </div>
          <div class="fetchingData__item">
            <p class="fetchingData__item-title">Skin color:</p><p>{{fetchingData.skin_color}}</p>
          </div>
          <div class="fetchingData__item">
            <p class="fetchingData__item-title">Eye color:</p><p>{{fetchingData.eye_color}}</p>
          </div>
          <div class="fetchingData__item">
            <p class="fetchingData__item-title">Birth year:</p><p>{{fetchingData.birth_year}}</p>
          </div>
          <div class="fetchingData__item">
            <p class="fetchingData__item-title">Gender:</p><p>{{fetchingData.gender}}</p>
          </div>
          <div class="fetchingData__item">
            <p class="fetchingData__item-title">Homeworld:</p><p>{{homeworld.name}}</p>
          </div>
          <div class="fetchingData__item">
            <p class="fetchingData__item-title">Films:</p>
            <p>{{films[0].title}}</p>
            <p>, {{films[1].title}}</p>
            <p>, {{films[2].title}}</p>
            <p>, {{films[5].title}}</p>
          </div>
          <div class="fetchingData__item">
            <p class="fetchingData__item-title">Vehicles:</p>
            <p>{{vehicle_14.name}}</p>
            <p>, {{vehicle_30.name}}</p>
          </div>
          <div class="fetchingData__item">
            <p class="fetchingData__item-title">Starships:</p>
            <p>{{starship_12.name}}</p>
            <p>, {{starship_22.name}}</p>
          </div>
        <div v-if="show">
        ___________________________________________________________________
          <h2>Данные формы</h2>
            <p>gender: {{formData.gender}}</p>
            <p>dayTime: {{formData.dayTime}}</p>
            <p>insomnia: {{formData.insomnia}}</p>
            <p>makesPlan: {{formData.makesPlan}}</p>
            <p>FiveYearsAgo: {{formData.FiveYearsAgo}}</p>
            <p>day: {{formData.day}}</p>
            <p>month: {{formData.month}}</p>
            <p>year: {{formData.year}}</p>
            <p>zodiak: {{formData.zodiak}}</p>
        </div>
        </div>


        <p class="footer__text">TERMENI SI CONDITII: ACESTA ESTE UN SERVICIU DE DIVERTISMENT. PRIN FOLOSIREA LUI DECLARATI CA AVETI 18</p>
      </div>
  </div>
  <div class="footer">
    <p class="footer__text">2020 © HOROSCOP PERSONAL</p>
  </div>
</template>

<script>
export default {
  data () {
    return {
      display: 1,
      rotate: 0,
      show: false,
      formData: {
        gender: '',
        dayTime: '',
        insomnia: '',
        makesPlan: '',
        FiveYearsAgo: '',
        day: '',
        month: '',
        year: '',
        zodiak: ''
      },
      fetchingData: {},
      homeworld: {},
      films: [],
      vehicle_14: {},
      vehicle_30: {},
      starship_12: {},
      starship_22: {}
    }
  },
  methods: {
    setZodiak(event) {
      this.formData.zodiak = event.target.alt;
    },
    sendData() {
      console.log(this.formData);
    },
    changeDisplay() {
      this.display++;
    },
    changeDisplayWST() {
      this.display++;
      setTimeout(this.progress, 500);
      setTimeout(this.changeDisplay, 6500);
    },
    rotated() {
      let rotate = 0;
      let id = setInterval(rotateCircle, 150);
      function rotateCircle() {
        if (this.display > 1) {
          clearInterval(id);
        } else {
        rotate++;
        document.getElementById('goroskop-circle').style.transform = 'rotate(' + rotate + 'deg)';
        }
      }
    },
    progress() {
      let width = 1;
      let id = setInterval(progressStatus, 60);
      function progressStatus() {
        if (width >= 100) {
          clearInterval(id);
        } else {
          width++;
          document.getElementById('progress__line').style.width = width + '%';
          document.getElementById('progress__line').innerHTML = width * 1 + '%';
        }
        if (width >= 20) {
          document.getElementById('p1').style.display = 'inherit';
        } 
        if (width >= 25) {
          document.getElementById('p2').style.display = 'inherit';
        } 
        if (width >= 30) {
          document.getElementById('p3').style.display = 'inherit';
        } 
        if (width >= 35) {
          document.getElementById('p4').style.display = 'inherit';
        } 
        if (width >= 40) {
          document.getElementById('p5').style.display = 'inherit';
        } 
        if (width >= 45) {
          document.getElementById('p6').style.display = 'inherit';
        } 
        if (width >= 50) {
          document.getElementById('p7').style.display = 'inherit';
        } 
        if (width >= 90) {
          document.getElementById('p7').style.display = 'none';
          document.getElementById('p8').style.display = 'inherit';
          document.getElementById('p9').style.display = 'inherit';
        } 
      }
    },
    async fetchData() {
      try {
        const response = await fetch('https://swapi.dev/api/people/1/')
          .then(response => response.json());
        this.fetchingData = response;
      } catch (e) {
        alert(e)
      }
    },
    async fetchHomeworld() {
      try {
        const response = await fetch('https://swapi.dev/api/planets/1/')
          .then(response => response.json());
        this.homeworld = response;
      } catch (e) {
        alert(e)
      }
    },
    async fetchFilms() {
      try {
        const response = await fetch('https://swapi.dev/api/films/')
          .then(response => response.json());
        this.films = response.results;
      } catch (e) {
        alert(e)
      }
    },
    async fetchVehicles_14() {
      try {
        const response = await fetch('https://swapi.dev/api/vehicles/14/')
          .then(response => response.json());
        this.vehicle_14 = response
      } catch (e) {
        alert(e)
      }
    },
    async fetchVehicles_30() {
      try {
        const response = await fetch('https://swapi.dev/api/vehicles/30/')
          .then(response => response.json());
        this.vehicle_30 = response
      } catch (e) {
        alert(e)
      }
    },
    async fetchStarship_12() {
      try {
        const response = await fetch('https://swapi.dev/api/starships/12/')
          .then(response => response.json());
        this.starship_12 = response;
      } catch (e) {
        alert(e)
      }
    },
    async fetchStarship_22() {
      try {
        const response = await fetch('https://swapi.dev/api/starships/22/')
          .then(response => response.json());
        this.starship_22 = response;
      } catch (e) {
        alert(e)
      }
    },
    fetching() {
      this.fetchData();
      this.fetchHomeworld();
      this.fetchFilms();
      this.fetchVehicles_14();
      this.fetchVehicles_30();
      this.fetchStarship_12();
      this.fetchStarship_22();
    },
    showing() {
      this.show = true;
    }
  },
  mounted() {
    this.fetching();
    this.rotated();
  }
}
</script>
