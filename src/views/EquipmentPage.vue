<template>
  <div class="page" style="color: white;">
    
    <v-btn @click="dialog=true"></v-btn>

    <v-dialog v-model="dialog" width="auto">
      <div class="fdial">
        <h4 style="margin-top: 10px; margin-bottom: 10px;">Цель</h4>

        <v-text-field label="Введите цель бронирования" v-model="name" hide-details="auto"></v-text-field>

        <h4 style="text-align: left; margin-top: 10px; margin-bottom: 10px;">
          Выберите время
        </h4>
        <v-btn :style="backcol[0]" @click="changeBaccol(0)" class="ftime">08:00 - 09:00</v-btn>
        <v-btn :style="backcol[1]" @click="changeBaccol(1)" class="ftime">09:00 - 10:00</v-btn>
        <v-btn :style="backcol[2]" @click="changeBaccol(2)" class="ftime">10:00 - 11:00</v-btn>
        <v-btn :style="backcol[3]" @click="changeBaccol(3)" class="ftime">11:00 - 12:00</v-btn>
        <v-btn :style="backcol[4]" @click="changeBaccol(4)" class="ftime">12:00 - 13:00</v-btn>
        <v-btn :style="backcol[5]" @click="changeBaccol(5)" class="ftime">13:00 - 14:00</v-btn>
        <v-btn :style="backcol[6]" @click="changeBaccol(6)" class="ftime">14:00 - 15:00</v-btn>
        <v-btn :style="backcol[7]" @click="changeBaccol(7)" class="ftime">15:00 - 16:00</v-btn>
        <v-btn :style="backcol[8]" @click="changeBaccol(8)" class="ftime">16:00 - 17:00</v-btn>

        <hr style="margin-bottom: 10px;">

        <h4 style="margin-bottom: 10px;">Дополнительная информация</h4>
        <v-text-field label="Добавить комментарий" v-model="name" hide-details="auto"></v-text-field>

        <div class="forbd">
          <v-btn @click="sendInvitation"
            style="width: 200px; margin-right: 20px; border-radius: 10px;">Забронировать</v-btn>
          <v-btn @click="dialog = false" style="width: 200px; border-radius: 10px;">Отмена</v-btn>
        </div>
      </div>
    </v-dialog>
  </div>
  <RightSideСalendar />
</template>

<script>
import RightSideСalendar from '../components/RightSideСalendar.vue';
import { mapGetters } from "vuex";

export default {
  components: {
    RightSideСalendar
  },
  data() {
    return {
      dialog: false,
      faces: [],
      inform: "",
      backcol: [
        "", "", "", "", "", "", "", "", ""
      ]
    }
  },
  computed: {
    ...mapGetters(["getPeoples", "getEquipment"]),
  },
  methods: {
    openInfo(info) {
      this.inform = info;
    },
    chengeTheme(emp) {
      if (emp == 1) {
        return "background-color: #C0C0C0";
      }
      else
        return "";
    },
    changeBaccol(N) {
      if (this.backcol[N] == "") {
        this.backcol[N] = "background-color: #C0C0C0;";
      }
      else {
        this.backcol[N] = "";
      }
    },
    addEl(newEl) {
      if (this.faces.length < 2) {
        this.faces.push(newEl);
      }
    },
    check() {
      if (this.faces.length == 2) {
        alert("Ошибка! Может быть только 2 исполнителя.");
      }
    },
    deleteEl(delEl) {
      this.faces.splice(delEl, 1);
    },
    sendInvitation() {
      alert("Бронь закреплена!");
      this.dialog = false;
    },
  }
}
</script>

<style scoped>
.infoDial {
  text-align: center;
  background-color: #ececec;
  width: 400px;
  padding: 20px;
  border-radius: 10px;
}
.elem {
  display: flex;
  color: black;
  margin-right: 5px;
  margin: 6px;
  border-radius: 10px;
  height: 40px;
  justify-content: center;
  align-items: center;
  padding: 10px;
  border: 2px solid #C0C0C0;
}

.parent {
  flex-wrap: wrap;
  display: flex;
  justify-content: center;
  align-items: center;
}

.child1 {
  width: 130%;
  background-color: #ececec;
  flex-wrap: wrap;
  display: flex;
  justify-content: center;
  align-items: center;

}

.child2 {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}

.ttit {
  display: flex;
  align-items: left;
  margin-top: 140px;
  margin-left: 2%;
  color: black;
}

.dbtn {
  display: flex;
  align-items: left;
}

.top-half {
  background-color: #C0C0C0;
  height: 65%;
}

.bottom-half {
  background-color: #ececec;
  height: 35%;
  display: flex;
}

.bottom-half>div {
  margin-right: 10px;
}

.container {
  height: 300px;
  width: 100%;
  border-radius: 10px;
  overflow: hidden;
}

.page {
  margin-top: 4.5%;
  color: azure;
  margin-left: 3.4%;
  width: 70%;
}

.forbd {
  margin-top: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.forp {
  border-radius: 10px;
  background-color: #C0C0C0;
  padding: 6px;
}

.faces-container {
  height: 50px;
  display: flex;
  align-items: center;
}

.ftime {
  width: 150px;
  margin-right: 10px;
  margin-bottom: 10px;
  border-radius: 10px;
}

.fdial {
  background-color: #ececec;
  width: 520px;
  padding: 20px;
  border-radius: 10px;
}</style>
   