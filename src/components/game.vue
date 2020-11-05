<template>
  <div>
      <div>
      </div>
    <button @click="randomStart()" class="btn btn-danger btn-lg mb-2">Start</button>
    <div class="row">
      <div class="col">
        <button @click="randomDamage(1,20)" class="btn btn-primary mb-4">Attack</button>
        <button @click="randomDamageSP(50,80)" class="btn btn-info mb-4">SP Attack</button>
      </div>
    </div>
    <div class="container-fluid">
      <div class="row">
        <div class="col-3">
          <div class="btn btn-success" role="alert">Hero : {{randomPlayer}} HP : {{hp1}}</div>
          <img :src="image1" class="img-fluid" />
        </div>
        <div class="col-3">
          <div class="btn btn-success" role="alert">Monster : {{randomMonster}} HP : {{hp2}}</div>
          <img :src="image2" class="img-fluid" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      randomAttack: "1",
      randomSpAttack: "1",
      image1: "",
      image2: "",
      hp1: "",
      hp2: "",
      win: "https://p.kindpng.com/picc/s/172-1725246_you-win-png-human-action-transparent-png.png",
      lose: "https://p.kindpng.com/picc/s/172-1725306_carmine-hd-png-download.png",
      player: [
        {
          name: "Vivi",
          hp: 200,
          image: "https://cdn.icon-icons.com/icons2/1048/PNG/256/Vivi_icon-icons.com_76565.png",
        },
        {
          name: "Smoker",
          hp: 150,
          image:"https://cdn.icon-icons.com/icons2/1048/PNG/256/Smoker_icon-icons.com_76563.png",
        },
        {
          name: "Buggy",
          hp: 150,
          image: "https://cdn.icon-icons.com/icons2/1048/PNG/256/Buggy_le_Clown_icon-icons.com_76548.png",
        },
        {
          name: "Brook",
          hp: 200,
          image: "https://cdn.icon-icons.com/icons2/1048/PNG/256/Brook_icon-icons.com_76547.png",
        },
        {
          name: "Usopp",
          hp: 200,
          image: "https://cdn.icon-icons.com/icons2/1048/PNG/256/Usopp_icon-icons.com_76564.png",
        },
        {
          name: "Sanji",
          hp: 180,
          image: "https://cdn.icon-icons.com/icons2/1048/PNG/256/Sanji_icon-icons.com_76561.png",
        },
        {
          name: "Affro Luffy",
          hp: 180,
          image: "https://cdn.icon-icons.com/icons2/1048/PNG/256/Affro_Luffy_icon-icons.com_76546.png",
        },
        {
          name: "Chopper",
          hp: 150,
          image: "https://cdn.icon-icons.com/icons2/1048/PNG/256/Chopper_icon-icons.com_76549.png",
        },
        {
          name: "Zoro",
          hp: 200,
          image: "https://cdn.icon-icons.com/icons2/1048/PNG/256/Roronoa_Zoro_icon-icons.com_76560.png",
        },
        
      ],
      randomPlayer: "",
      monster: [
        {
          name: "Enerl",
          hp: 150,
          image: "https://cdn.icon-icons.com/icons2/1048/PNG/256/Ener_icon-icons.com_76551.png",
        },
        {
          name: "Nami",
          hp: 100,
          image: "https://cdn.icon-icons.com/icons2/1048/PNG/256/Nami_icon-icons.com_76556.png",
        },
        {
          name: "Robin",
          hp: 180,
          image: "https://cdn.icon-icons.com/icons2/1048/PNG/256/Nico_Robin_icon-icons.com_76557.png",
        },
        {
          name: "Shanks",
          hp: 180,
          image: "https://cdn.icon-icons.com/icons2/1048/PNG/256/Shanks_le_roux_icon-icons.com_76562.png",
        },
        {
          name: "mihawk",
          hp: 190,
          image: "https://freepngimg.com/thumb/one_piece/80943-mihawk-purple-treasure-dracule-one-cruise-piece.png",
        },
        {
          name: "monkey",
          hp: 100,
          image: "https://freepngimg.com/thumb/one_piece/84444-monkey-purple-character-luffy-unlimited-fictional-one.png",
        },
      ],
      randomMonster: "",
    };
  },

  props: {
    Label: String,
  },

  methods: {
    randomStart: function () {
      var chosenNumber1 = Math.floor(Math.random() * this.player.length);
      this.randomPlayer = this.player[chosenNumber1].name;
      this.hp1 = this.player[chosenNumber1].hp;
      this.image1 = this.player[chosenNumber1].image;

      var chosenNumber2 = Math.floor(Math.random() * this.monster.length);
      this.randomMonster = this.monster[chosenNumber2].name;
      this.hp2 = this.monster[chosenNumber2].hp;
      this.image2 = this.monster[chosenNumber2].image;
    },

    randomDamage: function (min, max) {
      this.randomAttack = Math.max(Math.floor(Math.random() * max) + 1, min);
      if (this.hp1 != 0 && this.hp2 != 0) {
        this.hp1 -= this.randomAttack;
      }
      if (this.hp1 != 0 && this.hp2 != 0) {
        this.hp2 -= this.randomAttack;
      }
      if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.image1 = this.lose;
      }
      if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.image2 = this.win;
      }
    },

    randomDamageSP: function (min, max) {
      this.randomAttack = Math.max(Math.floor(Math.random() * max) + 1, min);
      if (this.hp1 != 0 && this.hp2 != 0) {
        this.hp2 -= this.randomAttack;
      }
      if (this.hp1 <= 0) {
        this.hp1 = 0;
        this.image1 = this.lose;
      }
      if (this.hp2 <= 0) {
        this.hp2 = 0;
        this.image2 = this.win;
      }
    },
  },
};
</script>
