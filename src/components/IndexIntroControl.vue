<script setup lang="ts">
const props = defineProps({
  isLogined: {
    type: Boolean,
    required: true,
  },
  login: {
    type: Function,
    required: true,
  },
});

// const nip07exists = ref('nostr' in window);
const nip07exists = true;
</script>
<template>
  <div class="p-index-signin" v-if="!props.isLogined" :style="(!nip07exists) ? { display: 'none' } : {}">
    <h2 class="p-index-signin__head">この画面からつぶやく</h2>
    <div class="p-index-signin__body">
      <input class="p-index-signin__btn" type="button" value="NIP-07でログイン" v-on:click="(_$event) => props.login()" />
    </div>
  </div>
  <div class="p-index-intro">
    <h2 class="p-index-intro__head"><span>このリレーについて</span></h2>
    <p class="p-index-intro__text">
      wss://srtrelay.c-stellar.netは、しりとりが成立していないと投稿できない特殊リレーです。詳しいルールは以下の通り。
    </p>
    <ul>
      <li>ひらがな・カタカナのみ投稿可</li>
      <li>「゛」・「゜」がつく文字で終わる場合、それを除いた文字から続けてもよい</li>
      <li>「ぁ」などの小文字で終わる場合、それを大きくした文字から続けてもよい</li>
      <li>
        特別に許されている接続
        <ul>
          <li>「ゐ」→「い」</li>
          <li>「ゑ」→「え」</li>
          <li>「を」→「お」</li>
          <li>「<span class="vu">ゔ</span>」→「ぶ」</li>
        </ul>
      </li>
      <li>「ー」(のばす音)で終わる場合、その前の文字から続ける</li>
    </ul>
    <h2 class="p-index-intro__head">ライセンス、ソースコードなど</h2>
    <p class="p-index-intro__text">このサイトのソースコードは<a href="https://github.com/imksoo/nostr-global-viewer"
        class="p-index-intro__text-link" target="_blank">GitHub</a>にあります。
    </p>
    <p class="p-index-intro__text">
      <a href="https://awayuki.github.io/emojis.html" target="_blank" class="p-index-intro__text-link">SUSHIYUKI
        emojis (©awayuki)</a> の絵文字素材や
      <a href="https://soundeffect-lab.info/" target="_blank" class="p-index-intro__text-link">効果音ラボ</a>
      の効果音素材を利用しています。
    </p>
  </div>
</template>
<style scoped lang="scss">
.p-index-signin {
  background: rgba(0, 0, 0, 0.6);
  border-radius: 6px;
  padding: 12px;
  display: flex;
  align-items: center;
  gap: 10px;
  margin-top: 1rem;

  &__head {
    color: #ffffff;
    font-size: 14px;
  }

  &__body {
    flex-grow: 1;
    border-left: 1px solid #fff;
    padding-left: 10px;
  }

  &__btn {
    background-color: #fc5fa1;
    color: #ffffff;
    display: block;
    width: 100%;
    box-sizing: border-box;
    padding: 0.5rem 1.4rem;
    border-radius: 2rem;
    transition: all 0.4s;
    border: none;
    line-height: 1;
    cursor: pointer;

    &:hover {
      background-color: #df3d81;
    }
  }
}

.p-index-intro {
  margin-top: 2rem;

  @media screen and (max-width: 880px) {
    margin-top: 0rem;
  }

  &__head {
    font-size: 1.4rem;
    color: gold;
    display: flex;
    gap: 0.4rem;
    align-items: center;
    margin: 2rem 0 1rem 0;

    &::before {
      content: "";
      flex-grow: 1;
      height: 2px;
      background-color: gold;
    }

    &::after {
      content: "";
      flex-grow: 1;
      height: 2px;
      background-color: gold;
    }

    span {
      width: max-content;
      flex-grow: 0;
      flex-shrink: 0;
    }
  }

  &__text {
    color: #ffffff;
    margin: 0;
    line-height: 1.8;
    margin-top: 0.3rem;
  }

  &__text-link {
    color: #fc5fa1;
    font-weight: bold;
  }

  &__text code {
    display: inline-block;
  }

  &__btn {
    background-color: #fc5fa1;
    color: #ffffff;
    display: block;
    padding: 0.5rem 1.4rem;
    border-radius: 2rem;
    transition: all 0.4s;
    line-height: 1;
    margin: 0 auto;
    width: max-content;
  }

  &__btn:hover {
    background-color: #df3d81;
  }

  .vu {
    font-family: sans-serif;
  }
}

@media screen and (max-width: 880px) {
  .p-index-post--signin {
    padding: 12px 0;
  }
}
</style>
