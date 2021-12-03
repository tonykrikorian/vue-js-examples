/* eslint-disable quotes */ /* eslint-disable quotes */ /* eslint-disable quotes */ /*
eslint-disable quotes */
<template>
  <div>
    <div class="top-row">
      <div class="top part">
        <img v-bind:src="availabeParts.heads[selectedHeadIndex].src" title="head" />
        <button v-on:click="selectPrevHead()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextHead()" class="next-selector">&#9658;</button>
      </div>
    </div>
    <div class="middle-row">
      <div class="left part">
        <img :src="selectedRobot.leftArm.src" title="left arm" />
        <button @click="selectNextLeftArm()" class="prev-selector">&#9650;</button>
        <button @click="selectPrevLeftArm()" class="next-selector">&#9660;</button>
      </div>
      <div class="center part">
        <img :src="selectedRobot.torso.src" title="left arm" />
        <button @click="selectPrevTorso()" class="prev-selector">&#9668;</button>
        <button @click="selectNextTorso()" class="next-selector">&#9658;</button>
      </div>
      <div class="right part">
        <img :src="selectedRobot.rightArm.src" title="left arm" />
        <button @click="selectPrevRightArm()" class="prev-selector">&#9650;</button>
        <button @click="selectNextRightArm()" class="next-selector">&#9660;</button>
      </div>
    </div>
    <div class="bottom-row">
      <div class="bottom part">
        <img :src="selectedRobot.bottom.src" title="left arm" />
        <button @click="selectPrevBottom()" class="prev-selector">&#9668;</button>
        <button @click="selectNextBottom()" class="next-selector">&#9658;</button>
      </div>
    </div>
  </div>
</template>

<script>
// eslint-disable-next-line quotes
import availabeParts from "../data/parts";

const parts = availabeParts.heads;

function getPreviousValidIndex(index, length) {
  const deprecatedIndex = index - 1;
  return deprecatedIndex < 0 ? length - 1 : deprecatedIndex;
}
function getNextValidIndex(index, length) {
  const incrementedIndex = index + 1;
  return incrementedIndex > length - 1 ? 0 : incrementedIndex;
}

export default {
  // eslint-disable-next-line quotes
  name: "RobotBuilder",
  data() {
    return {
      availabeParts,
      selectedHeadIndex: 0,
      selectedLeftArmIndex: 0,
      selectedTorsoIndex: 0,
      selectedRightArmIndex: 0,
      selectedBottomIndex: 0,
    };
  },
  computed: {
    selectedRobot() {
      return {
        head: availabeParts.heads[this.selectedHeadIndex],
        leftArm: availabeParts.arms[this.selectedLeftArmIndex],
        torso: availabeParts.torsos[this.selectedTorsoIndex],
        rightArm: availabeParts.arms[this.selectedRightArmIndex],
        bottom: availabeParts.bases[this.selectedBottomIndex],
      };
    },
  },
  methods: {
    selectNextHead() {
      // eslint-disable-next-line quotes
      this.selectedHeadIndex = getNextValidIndex(this.selectedHeadIndex, parts.length);
    },
    selectPrevHead() {
      this.selectedHeadIndex = getPreviousValidIndex(this.selectedHeadIndex, parts.length);
    },

    selectNextLeftArm() {
      this.selectedLeftArmIndex = getNextValidIndex(
        this.selectedLeftArmIndex,
        // eslint-disable-next-line comma-dangle
        parts.length
      );
    },
    selectPrevLeftArm() {
      this.selectedLeftArmIndex = getPreviousValidIndex(
        // eslint-disable-next-line comma-dangle
        this.selectedLeftArmIndex,
        // eslint-disable-next-line comma-dangle
        parts.length
      );
    },

    selectNextTorso() {
      this.selectedTorsoIndex = getNextValidIndex(
        this.selectedTorsoIndex,
        // eslint-disable-next-line comma-dangle
        parts.length
      );
    },
    selectPrevTorso() {
      this.selectedTorsoIndex = getPreviousValidIndex(
        // eslint-disable-next-line comma-dangle
        this.selectedTorsoIndex,
        // eslint-disable-next-line comma-dangle
        parts.length
      );
    },
    selectNextRightArm() {
      this.selectedRightArmIndex = getNextValidIndex(
        this.selectedRightArmIndex,
        // eslint-disable-next-line comma-dangle
        parts.length
      );
    },
    selectPrevRightArm() {
      this.selectedRightArmIndex = getPreviousValidIndex(
        // eslint-disable-next-line comma-dangle
        this.selectedRightArmIndex,
        // eslint-disable-next-line comma-dangle
        parts.length
      );
    },
    selectNextBottom() {
      this.selectedBottomIndex = getNextValidIndex(
        this.selectedBottomIndex,
        // eslint-disable-next-line comma-dangle
        parts.length
      );
    },
    selectPrevBottom() {
      this.selectedBottomIndex = getPreviousValidIndex(
        // eslint-disable-next-line comma-dangle
        this.selectedBottomIndex,
        // eslint-disable-next-line comma-dangle
        parts.length
      );
    },
  },
};
</script>

<style>
.part {
  position: relative;
  width: 165px;
  height: 165px;
  border: 3px solid #aaa;
}
.part img {
  width: 165px;
}
.top-row {
  display: flex;
  justify-content: space-around;
}
.middle-row {
  display: flex;
  justify-content: center;
}
.bottom-row {
  display: flex;
  justify-content: space-around;
  border-top: none;
}
.head {
  border-bottom: none;
}
.left {
  border-right: none;
}
.right {
  border-left: none;
}
.left img {
  transform: rotate(-90deg);
}
.right img {
  transform: rotate(90deg);
}
.bottom {
  border-top: none;
}
.prev-selector {
  position: absolute;
  z-index: 1;
  top: -3px;
  left: -28px;
  width: 25px;
  height: 171px;
}
.next-selector {
  position: absolute;
  z-index: 1;
  top: -3px;
  right: -28px;
  width: 25px;
  height: 171px;
}
.center .prev-selector,
.center .next-selector {
  opacity: 0.8;
}
.left .prev-selector {
  top: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.left .next-selector {
  top: auto;
  bottom: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.right .prev-selector {
  top: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  top: auto;
  bottom: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  right: -3px;
}
</style>
