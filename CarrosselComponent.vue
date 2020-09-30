<template>
  <div class="slider-testes">
    <div class="slides">
      <!-- Para cada item do carrossel você deverá adicionar um slider-item . Além disso você deverá passar no atributo do método styleFirstItem um index para ele, começando de 0  -->
      <div class="slider-item" :style="styleFirstSliderItem(0)">
      <!-- Conteúdo  -->
        <div class="icon">
          <span>1 </span>
        </div>
        <h3>Teste de Interesse Profissional</h3>
        <p>
          Este teste tem como objetivo lhe orientar sobre as áreas de atuação
          que você tem mais interesse.
        </p>
        <el-button type="primary" round>Fazer Teste</el-button>
      </div>
      <div class="slider-item" :style="styleFirstSliderItem(1)">
        <div class="icon">
          <span>2 </span>
        </div>
        <h3>Teste de Afinidade Profissional</h3>
        <p>
          O objetivo deste teste é lhe orientar sobre quais são as áreas de atuação que você tem mais afinidade.
        </p>
        <el-button type="primary" round>Fazer Teste</el-button>
      </div>
      <div class="slider-item" :style="styleFirstSliderItem(2)">
        <div class="icon">
          <span>3 </span>
        </div>
        <h3>Português, Atualidades e Matemática</h3>
        <p>
          O PAM  serve para prepara-lo para os processos seletivos nos programas JOVEM APRENDIZ e ESTÁGIOS.
        </p>
        <el-button type="primary" round>Fazer Teste</el-button>
      </div>
    </div>
    <!-- Se o número de sliders for maior que 1 ele mostra os controles, se não, oculta  -->
    <div class="controllers" v-if="this.countSliders > 1">
      <el-button type="text" @click="alterSlide('prev')"
        ><i class="el-icon-arrow-left"></i
      ></el-button>
      <el-button type="text" @click="alterSlide('next')"
        ><i class="el-icon-arrow-right"></i
      ></el-button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
    // contador de sliders adicionados no html, não mexer
      countSliders: 0,
      // mostra qual item slider está sendo visualizado
      currentSlider: 1,
    };
  },
  // assim que montar o componente na tela, ele irá atualizar a quantidade de item slider no documento em countSliders 
  mounted() {
    this.countSliders = document.getElementsByClassName("slider-item").length;
  },
  methods: {
  // calcula o atributo left de cada item slider
    styleFirstSliderItem(index) {
    
    // aqui você altera pela soma da largura de .slider-item + margin-right destes elementos, neste caso (266 + 50)
      let spaceSliderItem = 316;

      if (this.currentSlider == 1) {
        return "left: " + 0 + "px;";
      } else {
        return (
          "left:" + -1 * spaceSliderItem * (this.currentSlider - 1) + "px;"
        );
      }
    },
    alterSlide(op) {
      if (op === "next") {
        if (this.currentSlider + 1 > this.countSliders) {
          this.currentSlider = 1;
        } else {
          this.currentSlider++;
        }
      }

      if (op === "prev") {
        if (this.currentSlider - 1 < 1) {
          this.currentSlider = this.countSliders;
        } else {
          this.currentSlider--;
        }
      }
    },
  },
};
</script>

<style lang="scss" scoped>
/* NÃO MEXER */
.slider-testes {
  position: relative;
  display: flex;
  flex-direction: column;
  margin-top: 50px;

  .slides {
    display: flex;
  }

  .controllers {
    text-align: center;
    margin-top: 20px;

    i {
      color: $corPrincipal;
      font-size: 40px;

      &:hover {
        cursor: pointer;
      }
    }
  }

  /* Aqui você pode mexer */
  .slider-item {
    width: 266px;
    height: 322px;
    box-sizing: border-box;
    padding: 20px;
    background: #ffffff;
    box-shadow: 0px 4px 20px rgba(0, 0, 0, 0.25);
    border-radius: 10px;
    position: relative;
    display: table;
    margin-right: 50px;
    transition: 0.3s all ease-in-out;

    h3 {
      font-style: normal;
      font-weight: 600;
      font-size: 15px;
      line-height: 28px;
      letter-spacing: 0.2em;
      color: #687777;
    }

    p {
      font-style: normal;
      font-weight: 300;
      font-size: 14px;
      line-height: 26px;
      letter-spacing: 0.2em;
      color: #848484;
    }

    .icon {
      position: absolute;
      height: 69px;
      width: 69px;
      right: -30px;
      margin-top: -45px;
      background: linear-gradient(253.58deg, #0dbfbe 1.55%, #0b8180 95.8%);
      box-shadow: 0px 12px 35px rgba(114, 114, 114, 0.34);
      border-radius: 50%;
      color: #fff;
      display: flex;
      align-items: center;
      justify-content: center;

      span {
        display: block;
        font-style: normal;
        font-weight: 800;
        font-size: 40px;
        line-height: 75px;
        letter-spacing: 0em;
        color: #ffffff;
      }
    }
  }
}
</style>
