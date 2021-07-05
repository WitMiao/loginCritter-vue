<template>
  <div class="login-block">
    <div class="login-animate" :class="{ 'username-animate': isUserNameFocus, 'password-animate': isPasswordFocus }">
      <div class="left-ear" :style="{ left: getPosition(1.5, -1, 1) }"></div>
      <div class="right-ear" :style="{ left: getPosition(7.5, -1, 1) }"></div>
      <div class="head">
        <div class="left-eye" :class="{ doe: isDoe }" :style="{ left: getPosition(0.5, 1, 1.5) }"></div>
        <div class="right-eye" :class="{ doe: isDoe }" :style="{ left: getPosition(4, 1, 2) }"></div>
        <div class="face" :style="{ left: getPosition(1, 1, 1.5) }">
          <div class="nose" :style="{ left: getPosition(0.9, 1, 1) }"></div>
          <div class="mouth" :class="{ show: isPwdShow, doe: isDoe }"></div>
        </div>
      </div>
      <div class="body"></div>
      <div class="left-arm" :class="{ show: isPwdShow }"></div>
      <div class="right-arm" :class="{ show: isPwdShow }"></div>
    </div>
    <el-form>
      <el-form-item>
        <el-input
          v-model="username"
          placeholder="Username"
          @blur="isUserNameFocus = false"
          @focus="isUserNameFocus = true"
        ></el-input>
      </el-form-item>
      <el-form-item>
        <el-input
          v-model="password"
          :type="[isPwdShow ? 'text' : 'password']"
          placeholder="Password"
          @blur="isPasswordFocus = false"
          @focus="isPasswordFocus = true"
        >
          <i
            slot="suffix"
            :class="[isPwdShow ? 'el-icon-minus' : 'el-icon-view']"
            autocomplete="auto"
            @click="isPwdShow = !isPwdShow"
          />
        </el-input>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  name: 'loginCritter',
  data() {
    return {
      username: '',
      password: '',
      isUserNameFocus: false,
      isPasswordFocus: false,
      isPwdShow: false,
    };
  },
  computed: {
    isDoe() {
      return this.username.length >= 6;
    },
  },
  methods: {
    getPosition(init, plusOrMinus, max) {
      let leftLength = parseFloat((max / 36) * this.username.length);
      leftLength = leftLength > max ? max : leftLength;
      return this.isUserNameFocus ? init + plusOrMinus * leftLength + 'em' : '';
    },
  },
};
</script>

<style lang="less" scoped>
.login-block {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 5rem;
  width: 20em;
  height: 25em;
  background: #3dceba;
  border-radius: 10px;
  box-shadow: 0 0 16px #333;
}
.login-animate {
  width: 10em;
  height: 10em;
  border-radius: 5em;
  background: #cefefb;
  margin: 20px 0;
  position: relative;
  overflow: hidden;
  div {
    transition: all 0.5s;
    -o-transition: all 0.5s;
    -moz-transition: all 0.5s;
    -webkit-transition: all 0.5s;
  }
  .body {
    background-image: url(../assets/img/body.png);
    background-size: 100%;
    background-repeat: no-repeat;
    background-position: center;
    width: 6.5em;
    height: 6em;
    position: absolute;
    bottom: -2em;
    left: calc(50% - 3.25em);
    z-index: 0;
  }
  .head {
    position: relative;
    background-image: url(../assets/img/face.png);
    background-size: 100%;
    background-repeat: no-repeat;
    background-position: center;
    width: 7.5em;
    height: 7.25em;
    position: absolute;
    bottom: 1em;
    left: calc(50% - 3.75em);
    z-index: 1;
  }
  .left-ear {
    background-image: url(../assets/img/left-ear.png);
    background-size: 100%;
    background-repeat: no-repeat;
    background-position: center;
    width: 2em;
    height: 2em;
    position: absolute;
    bottom: 5.5em;
    left: calc(50% - 4em);
  }
  .right-ear {
    background-image: url(../assets/img/right-ear.png);
    background-size: 100%;
    background-repeat: no-repeat;
    background-position: center;
    width: 2em;
    height: 2em;
    position: absolute;
    bottom: 5.5em;
    left: calc(50% + 2em);
  }
  .left-eye {
    background-image: url(../assets/img/eye.png);
    background-size: 100%;
    background-repeat: no-repeat;
    background-position: center;
    width: 1em;
    height: 1em;
    position: absolute;
    bottom: 4em;
    left: calc(50% - 2.5em);
  }
  .right-eye {
    background-image: url(../assets/img/eye.png);
    background-size: 100%;
    background-repeat: no-repeat;
    background-position: center;
    width: 1em;
    height: 1em;
    position: absolute;
    bottom: 4em;
    left: calc(50% + 1.5em);
  }
  .face {
    background-image: url(../assets/img/muzzle.png);
    background-size: 100%;
    background-repeat: no-repeat;
    background-position: center;
    width: 4em;
    height: 4em;
    position: absolute;
    bottom: 0em;
    left: calc(50% - 2em);
  }
  .nose {
    background-image: url(../assets/img/nose.png);
    background-size: 100%;
    background-repeat: no-repeat;
    background-position: center;
    width: 1em;
    height: 1em;
    position: absolute;
    top: 0.5em;
    left: calc(50% - 0.5em);
  }
  .mouth {
    background-image: url(../assets/img/mouth-smile.png);
    background-size: 100%;
    background-repeat: no-repeat;
    background-position: center;
    width: 2em;
    height: 1em;
    position: absolute;
    bottom: 1em;
    left: calc(50% - 1em);
  }
  .left-arm {
    background-image: url(../assets/img/left-arm.png);
    background-size: 100%;
    background-repeat: no-repeat;
    background-position: center;
    width: 3em;
    height: 7em;
    position: absolute;
    bottom: -7.5em;
    left: 1em;
    z-index: 2;
    transition: bottom 0.5s;
  }
  .right-arm {
    background-image: url(../assets/img/right-arm.png);
    background-size: 100%;
    background-repeat: no-repeat;
    background-position: center;
    width: 3em;
    height: 7em;
    position: absolute;
    bottom: -7.5em;
    left: 6em;
    z-index: 2;
    transition: bottom 0.5s;
  }
}
.password-animate {
  .mouth.show {
    width: 1em;
    left: calc(50% - 0.5em);
    background-image: url(../assets/img/mouth-circle.png);
  }
  .left-arm.show {
    bottom: -1.7em !important;
  }
  .right-arm.show {
    bottom: -1.7em !important;
  }
  .left-arm {
    bottom: -0.5em;
  }
  .right-arm {
    bottom: -0.5em;
  }
}
.username-animate {
  .left-ear {
    left: 1.5em;
  }
  .right-ear {
    left: 7.5em;
  }
  .left-eye {
    left: 0.5em;
    bottom: 3.5em;
  }
  .left-eye.doe {
    background-image: url(../assets/img/eye-doe.png);
  }
  .right-eye.doe {
    background-image: url(../assets/img/eye-doe.png);
  }
  .right-eye {
    left: 4em;
    bottom: 3.5em;
  }
  .face {
    left: 1em;
  }
  .nose {
    left: 0.9em;
    top: 0.65em;
  }
  .mouth {
    bottom: 0.75em;
    background-image: url(../assets/img/mouth-half.png);
  }
  .mouth.doe {
    background-image: url(../assets/img/mouth-open.png);
    height: 2em;
    bottom: 0.5em;
  }
}
</style>
