<template>
  <section id="bod">
    <div id="box" v-if="!bool">
      <h3 class="dont">0 birthdays today</h3>
      <b-button class="buton" @click="clear">Clear All</b-button>
    </div>
    <div id="box" v-if="bool">
      <p style="align-center" v-if="correct.length">{{ k }} BIRTHDAYS TODAY!</p>
      <div v-for="friend in correct" :key="friend">
        <div class="parinte">
          <article v-if="correct.length">
            <img class="person" :src="friend.img" alt="logo" />
            <!-- css flex-->
          </article>
          <!--  <pv-for="(nume, index) in correct" :key ="index" >{{ nume }} </p> -->
          <article>
            <h4 class="nume">
              {{ friend.name }}
            </h4>
            <p class="age">{{ friend.age }} years</p>
          </article>
        </div>

        <!--  <article class="audo">
        <audio  controls>
    <source :src="friend.muzik" type="audio/mpeg"> 
    Your browser does not support the audio element.
  </audio>
        </article> -->
      </div>
      <h3 v-if="!correct.length" class="dont">0 birthdays today</h3>
      <b-button class="buton" @click="clear">Clear All</b-button>
    </div>
  </section>
</template>

<script>
import ellisimg from "C:/ELLIS - PROGRAMARE/PROIECTE VUE/bday/src/assets/ellis.jpg";
import faneimg from "C:/ELLIS - PROGRAMARE/PROIECTE VUE/bday/src/assets/fane.jpg";
import simonimg from "C:/ELLIS - PROGRAMARE/PROIECTE VUE/bday/src/assets/simon.jpg";
import bogdanimg from "C:/ELLIS - PROGRAMARE/PROIECTE VUE/bday/src/assets/bogdan.jpg";
import emiimg from "C:/ELLIS - PROGRAMARE/PROIECTE VUE/bday/src/assets/emiimg.jpg";
import tudorimg from "C:/ELLIS - PROGRAMARE/PROIECTE VUE/bday/src/assets/tudor.jpg";
import tonyimg from "C:/ELLIS - PROGRAMARE/PROIECTE VUE/bday/src/assets/tonyimg.jpg";
import titelimg from "C:/ELLIS - PROGRAMARE/PROIECTE VUE/bday/src/assets/titelimg.jpg";
import danaimg from "C:/ELLIS - PROGRAMARE/PROIECTE VUE/bday/src/assets/dana.jpg";
import gabiimg from "C:/ELLIS - PROGRAMARE/PROIECTE VUE/bday/src/assets/gabi.jpg";
import aud from "C:/ELLIS - PROGRAMARE/PROIECTE VUE/bday/src/assets/adimutu.mp3";
export default {
  data() {
    return {
      friends: [
        {
          name: "Ellis",
          zi: 15,
          luna:9,
          age: 16,
          img: ellisimg,
          muzik: aud,
        },
        {
          name: "Fane",
          zi: 25,
          luna: 4,
          age: 20,
          img: faneimg,
          muzik: aud,
        },
        {
          name: "simon",
          zi: 25,
          luna: 3,
          age: 16,
          img: simonimg,
          muzik: aud,
        },
        {
          name: "Bogdan",
          zi: 22,
          luna: 2,
          age: 21,
          img: bogdanimg,
          muzik: aud,
        },
        {
          name: "Tudor",
          zi: 13,
          luna: 4,
          age: 17,
          img: tudorimg,
          muzik: aud,
        },
        {
          name: "Emanuel",
          zi: 27,
          luna: 8,
          age: 23,
          img: emiimg,
          muzik: aud,
        },
        {
          name: "Titel",
          zi: 5,
          luna: 7,
          age: 22,
          img: titelimg,
          muzik: aud,
        },
        {
          name: "Toni",
          zi: 29,
          luna: 4,
          age: 16,
          img: tonyimg,
          muzik: aud,
        },
        {
          name: "Gabriel",
          zi: 8,
          luna: 1,
          age: 46,
          img: gabiimg,
          muzik: aud,
        },
        {
          name: "Dana",
          zi: 3,
          luna: 4,
          age: 36,
          img: danaimg,
          muzik: aud,
        },
        /* {
          name: "Mamo",
          zi: 12
          luna: 4,
          age: 59,
          img: mamoimg,
        }, */
      ],
      correct: [],
      k: 0,
      bool: true,
    };
  },

  mounted() {
    var dateObj = new Date();
    var month = dateObj.getMonth() + 1; //months from 1-12
    var day = dateObj.getDate();
    var anNou = dateObj.getFullYear();

    for (var i = 0; i < this.friends.length; i++) {
      if (this.friends[i].zi == day && this.friends[i].luna == month) {
        //this.correct.push();
        this.k++;
        if (2021 == anNou) {
          this.correct.push({
            name: this.friends[i].name,
            img: this.friends[i].img,
            age: this.friends[i].age + 1,
            muzik: this.friends[i].muzik,
          });
        }
        if (anNou > 2021) {
          let dif = anNou - 2021;
          this.correct.push({
            name: this.friends[i].name,
            img: this.friends[i].img,
            age: this.friends[i].age + dif,
          });
        }
      }
    }
  },
  methods: {
    clear() {
      this.bool = false;
    },
  },
};
</script>

<style>
.parinte {
  display: flex;
  margin-bottom: 10px;
  flex-flow: row;

  column-gap: 0.75rem;
}
.person {
  width: 75px;
  height: 75px;
  object-fit: cover;
  border-radius: 50%;
  box-shadow: 0 5px 15px rgb(0 0 0 / 10%);
}
.nume {
  color: rgb(16, 42, 66);
  line-height: 1;
  letter-spacing: 0.1ch;
  margin-top: 10px;
}
.age {
  color: #888888;
}
.audo {
  display: flex;
}

#box {
  background-color: #ffffff;
  box-shadow: 1px 7px 8px 2px #888888;
  text-align: center;
  height: auto;
  width: 450px;
  padding: 1.5rem 2rem;
  border-radius: 10px;
}

#bod {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  background-color: #f28ab2;
  line-height: 1.5;
}
body {
  margin: 0;
  padding: 0;
}

.dont {
  margin-right: 150px;
}

.buton {
  background-color: #f28ab2 !important;
  width: 400px;
  margin-top: 19px;
}
.buton:hover {
  background-color: #f28ab2 !important; /*sa ramana roz, suprascriere */
  width: 400px;
  margin-top: 19px;
}
</style>
