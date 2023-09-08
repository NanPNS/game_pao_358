<script>
export default {
  data() {
    return {
      selectedHands: [],
      count: 0,
      score: { hand1: 0, hand2: 0 },
      handOptions: ["rock", "scissors", "paper", "love"], // เพิ่ม "love" เข้าไป
      
    };
  },
  methods: {
    playGame() {
      this.selectedHands = [];
      for (let i = 0; i < 2; i++) {
        const randomIndex = Math.floor(Math.random() * this.handOptions.length);
        this.selectedHands.push(`${this.handOptions[randomIndex]}${i + 1}`);
      }
      
      const winner = this.determineWinner();
    if (winner === "hand1") {
      this.score.hand1++; 
    } else if (winner === "hand2") {
      this.score.hand2++; 
    }
    
    this.count++;
  },
    determineWinner() {
      const hand1 = this.selectedHands[0].slice(0, -1);
      const hand2 = this.selectedHands[1].slice(0, -1);
      
      if (hand1 === hand2) {
        return null;
      } else if (hand1 === "love" || hand2 === "love") {
        return "hand1"; 
      } else if (
        (hand1 === "rock" && hand2 === "scissors") ||
        (hand1 === "scissors" && hand2 === "paper") ||
        (hand1 === "paper" && hand2 === "rock")
      ) {
        return "hand1"; 
      } else {
        return "hand2"; 
      }
    },
    
    resetGame() {
      this.selectedHands = [];
      this.count = 0;
      this.score.hand1 = 0;
      this.score.hand2 = 0;
    }
  },
};
</script>
<template>
  <div class="container">
    <div class="glassmorphism"></div>
  </div>
  <div class="Game">Game เป่ายิ้งฉุบ</div>

  <div class="game-container">
    <img class="all"
          src="/img/All.png" 
          alt="all_logo" />
    <div class="hand-container">
      

      <div class="hand1">ทีม สีฟ้า
        <img v-if="selectedHands.includes('rock1')" 
        src="/img/hand-rock-svgrepo-com.svg" 
        alt="rock_logo" 
        class="img"/>

        <img v-if="selectedHands.includes('scissors1')" 
        src="/img/hand-peace-svgrepo-com.svg" 
        alt="peace_logo" 
        class="img"/>

        <img v-if="selectedHands.includes('paper1')" 
        src="/img/hand-paper-svgrepo-com.svg" 
        alt="paper_logo" 
        class="img"/>

        <img v-if="selectedHands.includes('love1')" 
        src="/img/love-svgrepo-com.svg" 
        alt="paper_logo" 
        class="img"/>
      
      </div>

      <div class="hand2">ทีม สีแดง
        <img v-if="selectedHands.includes('rock2')" 
        src="/img/hand-rock-svgrepo-com.svg"  
        alt="rock_logo" 
        class="img"/>

        <img v-if="selectedHands.includes('scissors2')" 
        src="/img/hand-peace-svgrepo-com.svg" 
        alt="peace_logo" 
        class="img"/>

        <img v-if="selectedHands.includes('paper2')" 
        src="/img/hand-paper-svgrepo-com.svg" 
        alt="paper_logo" 
        class="img"/>

        <img v-if="selectedHands.includes('love2')" 
        src="/img/love-svgrepo-com.svg" 
        alt="paper_logo" 
        class="img"/>

      </div>

    </div>
    <div class="score-board">
      <p class="blue">แต้ม สีฟ้า: {{ score.hand1 }}</p>
      <p class="red">แต้ม สีแดง: {{ score.hand2 }}</p>
    </div>
    <button @click="playGame">เป่า ยิ้งง ฉุบ รอบที่ {{ count }}</button>
  </div>
    
  
    <div class = "restart"> 
    <button @click="resetGame">เริ่มใหม่</button>
    </div> 
    
</template>

<style >
:root {
  color-scheme: light dark;
  color: rgba(255, 255, 255, 0.87);
  background-image: url(https://i.pinimg.com/564x/c4/f5/07/c4f5071c83bef83ada21d34b3ae1c49b.jpg);
  

}

body {
  margin: auto;
  padding: auto;
  width: 90%;
  height: 80%;
  border-top: 2px solid #ffffff75;
  border-left: 2px solid #ffffff75;
  box-shadow: 5px 5px 12px #00000072;
  background: rgba(0, 0, 0, 0.145);
  border-radius: 30px;
 
  backdrop-filter: blur(20px);
  

}

button {
  margin: 20px;
  border-radius: 8px;
  border: 1px solid transparent;
  padding: 20px;
  font-size: 40px;
  border-top: 2px solid #ffffff75;
  border-left: 2px solid #ffffff75;
  box-shadow: 5px 5px 12px #00000072;
  color: #000000;
  
 

  background-color: #ffffff;

  transition: border-color 0.25s;
}

.card {
  padding: 2em;
}

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  text-align: center;
}

.hand1{
  border-radius: 30px;
  background-color: #8457ff;
  font-size: 40px;


}
.hand2{
  border-radius: 30px;
  background-color: #ff5757;
  font-size: 40px;


}
.logo {
  width: 20px; /* ปรับขนาดความกว้างตามต้องการ */
  height: auto; /* ความสูงจะปรับตามอัตราส่วนของ SVG */
  padding: 20px;
  margin: 10px; 
}
.hand-container {
  display: flex;
  justify-content: space-between;
  
}
.all{
  border-radius: 10px;
  margin: auto;
  height: 100px;
  padding-bottom: 20px;


}
.img{
  height: 300px;
}


.blue{
  color: #ffffff;
  font-size: 30px;
  background: linear-gradient( #9169ff , #8457ff , #593aad );
  border-radius: 30px;
  box-shadow: 5px 5px 12px #00000072;



}
.red{
  color: #ffffff;
  font-size: 30px;
  background: linear-gradient( #ff6262 , #f74c4c , #a33737 );

  border-radius: 30px;
  box-shadow: 5px 5px 12px #00000072;


}
.score-board{
  text-align: center;
  margin: 20px;




}
.Game{
  color: #ffffff;
  font-size: 30px;
  font-style: normal;
  border-top: 2px solid #ffffff75;
  border-block: 2px solid #ffffff75;
  margin: 20px;





}
</style>

