<template lang="pug">
    .header
      .burger(@click='$emit("turnMenu")' :class="{active: activeBurger}")
        span
      nuxt-link(to="/")
        .name
            img(src='~/assets/images/logo.png')
      .menu-lg
        ul.parent-ul
          li
            nuxt-link(to="/") Главная
          li.dropdown-item Каталог
            ul.child-ul(:class="{active: catDroodown}")
              li
                nuxt-link(to="/categories/fruits") Фрукты
          li
            nuxt-link(to="/about") О Компании
          li
            nuxt-link(to="/delivery") Доставка
          li
            nuxt-link(to="/contacts") Контакты
      .buttons
        a(href="#") Заказать звонок
    </template>
    
    <script>
    export default {
      name: 'HeaderComponent',
      props: {
          activeBurger: {
            type: Boolean,
            default: false
          },
      },
      data() {
        return{
            catDroodown: false,
            collectionsDropdown: false
        }
  },
    }
    </script>
    
    <style lang="scss" scoped>
    .header{
      width: 100%;
      padding: 20px 16px;
      position: sticky;
      top: 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: #fff;
      border-bottom: 1px solid rgb(230, 230, 230);
      z-index: 20;
      @media(min-width: 992px){
        padding: 20px 32px;
      }
      .name{
        color: #666A86;
        font-size: 24px;
      }
      .burger{
        width: 30px;
        height: 25px;
        position: relative;
        @media(min-width: 992px){
          display: none;
        }
        cursor: pointer;
        &::before{
          content: '';
          position: absolute;
          width: 30px;
          height: 3px;
          background: #666A86;
          transition: all .5s ease;
        }
        &::after{
          content: '';
          position: absolute;
          width: 30px;
          height: 3px;
          background: #666A86;
          bottom: 0;
          transition: all .5s ease;
        }
        span{
          width: 25px;
          height: 3px;
          background: #666A86;
          position: absolute;
          top: 11px;
          transition: all .5s ease;
        }
        &.active{
          span{
                display: none;
              }
            &:before{
              transform: rotate(40deg);
              bottom: 10px;
              background: rgb(124, 36, 36);
            }
            &:after{
              transform: rotate(-40deg);
              top: 12px;
              background: rgb(124, 36, 36);
            }
        }
        }
      .menu-lg{
        display: none;
        @media(min-width: 992px){
          display: block;
        }
        .parent-ul {
          list-style: none;
          margin: 0;
          padding-left: 0;
          display: flex;
        }
        li {
          color: #000;
          display: block;
          position: relative;
          transition-duration: 0.5s;
          padding: 10px;
          font-size: 12px;
          text-transform: uppercase;
          letter-spacing: .1rem;
          font-weight: bold;
          a {
            color: #000;
            text-transform: uppercase;
            font-size: 12px;
            letter-spacing: .1rem;
            font-weight: bold;
            transition: all .5s ease;
            &:hover{
              color: #fff
            }
          }
          &:hover{
            background: #A2999E;
            color: #fff;
              cursor: pointer;
          }
        }
        .child-ul {
          background: #A2999E;
          visibility: hidden;
          opacity: 0;
          position: absolute;
          transition: all 1s ease;
          pointer-events: none;
          left: 0;
          width: 200px;
          padding: 10px;
          transform: matrix(1, 0, 0, 1, 3, -20);
          a{
            width: 100%;
            display: block;
            color: #fff;
            transition: all .5s ease;
            &:hover{
              color: brown;
            }
          }
        }
        ul li:hover > ul,
        ul li ul:hover {
          visibility: visible;
          pointer-events: all;
          opacity: 1;
          transform: matrix(1, 0, 0, 1, 0, 10);
        }
      }
      .mob-sm{
        display: flex;
        justify-content: space-between;
        align-items: center;
      }
    }
    </style>