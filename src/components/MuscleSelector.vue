<template>
  <div>
    <svg
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 439.63 404.91"
      v-html="svg"
      class="human"
      :style="`--outer-color: ${outerColor}; --select-color: ${selectColor}`"
    ></svg>
  </div>
</template>

<script>
import human from "@/svg/human.js";

export default {
  props: {
    selectColor: {
      type: String,
      default: "white",
    },
    bodyColor: {
      type: String,
      default: "#b2b2b2",
    },
    muscleColor: {
      type: String,
      default: "#b07f7f",
    },
    outerColor: {
      type: String,
      default: "#242b38",
    },
  },
  computed: {
    svg() {
      return human.getSvg(this.bodyColor, this.muscleColor);
    },
  },
  methods: {
    addHover() {
      document.querySelectorAll("svg.human g").forEach((item) => {
        var isMuscle = item.id !== "outer-color" && item.id !== "inner-color";
        if (isMuscle) {
          item.addEventListener("mouseenter", (e) => {
            var active = document.querySelector(".human-active-muscle");
            if (active) {
              active.classList.remove("human-active-muscle");
            }
            e.target.classList.add("human-active-muscle");
          });
        }
      });

      document
        .querySelector("svg.human>g#outer-color")
        .addEventListener("mouseout", () => {
          var active = document.querySelector(".human-active-muscle");
          if (active) {
            active.classList.remove("human-active-muscle");
          }
        });
    },
  },
  mounted() {
    this.addHover();
  },
};
</script>

<style>
svg.human > g#outer-color {
  fill: var(--outer-color);
}

.human-active-muscle > path {
  transition: fill 300ms;
  fill: var(--select-color);
}
</style>
