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
  <div class="game-container">
    <img class="all"
          src="/img/All.png" 
          alt="all_logo" />
    <div class="hand-container">
      

      <div class="hand1">สีฟ้า
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

      <div class="hand2">สีแดง
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
  background-color: #242424;

}

body {
  margin: 0;
  display: flex;
  place-items: center;
  min-width: 200px;
  min-height: auto;
  background: #201f1f;
}

button {
  border-radius: 8px;
  border: 1px solid transparent;
  padding: 20px;
  font-size: 40px;
 

  background-color: #1a1a1a;

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
  background-color: #8457ff;
  font-size: 40px;


}
.hand2{
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
  height: 300px;
  padding:  30px;


}
.img{
  height: 300px;
}


.blue{
  color: #8457ff;
  font-size: 30px;

}
.red{
  color: #ff5757;
  font-size: 30px;


}
.score-board{
  text-align: center;
  margin: 20px;




}
</style>

