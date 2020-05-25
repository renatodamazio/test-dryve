<template>
  <div class="wrapper">
    <NavBar></NavBar>
    <main>
      <header></header>
      <section><nuxt /></section>
      <footer></footer>  
    </main>
  </div>
</template>
<script>
export default {
  components: {
    NavBar: () => import('../components/nav.vue')
  }
}
</script>
<style lang="scss">
  * {
    padding: 0;
    margin: 0;
    font-size: 16px;
    word-spacing: 1px;
    -ms-text-size-adjust: 100%;
    -webkit-text-size-adjust: 100%;
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
    box-sizing: border-box;
    text-decoration: none;
    font-family: 'Inter', sans-serif;
  }

  .material-icons {
    vertical-align: middle;
  }

  .md-card.md-theme-default, .md-list {
    box-shadow: none;
    border-radius: 4px;
    border: solid 1px rgba(0, 0, 0, 0.12);
  }

  .md-table-head-label {
    font-size: 10px;
    font-weight: 500;
  }

  .md-table .md-table-fixed-header {
    height: 0px;
  }

  .md-field[variant='outlined'] {
      background: #fff !important;
      border-radius: 4px;
      padding: 0px 16px;
      margin-bottom: 0;
      min-height: 36px;
      border: solid 1px rgba(0, 0, 0, 0.38) !important;
  }

  .md-field.md-theme-default:after {
    display: none;
  }

  a {
    color: #0065ff;
    font-size: 14px;
    font-weight: 500;
    transition: .500s ease-in-out;

    &:hover {
      text-decoration: none;
    }
  }

  html, body, #__nuxt, #__layout {
    width: 100%;
    height: 100%;
    font-family: 'Inter', sans-serif;
  }
  
  .wrapper {
    display: flex;
    flex-direction: row;
    height: 100%;
  }

  header {
    height: 70px;
    width: 100%;
    background: #fff;
  }

  main {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    background: #f3f4f6;
    
    section {
      width: 100%;
      height: 100%;
      padding: 30px;
      overflow: auto;
    }
  }

  ul li {
    list-style: none;
  }

  .main-header {
    display: flex;
    margin-bottom: 30px;
  }

  .content {
    display: flex;
    background: #fff;
    padding: 20px;
  }

  .right-align {
    text-align: right;
  }

  .center-align {
    text-align: center;
  }

  .mb-30 {
    margin-bottom: 30px;
  }

  .left-align {
    text-align: left;
  }

      .md-headline {
        font-size: 14px;
        font-weight: 500;
        font-stretch: normal;
        font-style: normal;
        line-height: 1.71;
        letter-spacing: 0.1px;
        color: rgba(0, 0, 0, 0.87);
    }
    .table-title {
        font-size: 10px;
        font-weight: 500;
        font-stretch: normal;
        font-style: normal;
        line-height: 1.6;
        letter-spacing: 1.5px;
        color: rgba(0, 0, 0, 0.87);
    }
    table {
        tbody {
            td.md-table-cell {
             color: #768095;
             padding: 12px 0px;
             
              .table-figure {
                    max-width: 80px;
                    max-height: 60px;
                    border-radius: 4px;
                    border: solid 1px #e0e0e0;
                    overflow: hidden;
                    
                    img {
                        object-fit: cover;
                        width: 80px;
                    }
                }

                strong {
                    color: #1e2c4c;
                    font-size: 12px;
                    font-weight: bold;
                    width: 100%;
                    clear: both;
                    margin-bottom: 5px;
                }

                .infos {
                    width: 240px;
                    padding-left: 10px;
                }

                p {
                    font-size: 10px;
                    font-weight: normal;
                    font-stretch: normal;
                    font-style: normal;
                    line-height: 1;
                    letter-spacing: 0.33px;
                    color: #768095;
                    margin-bottom: 5px;

                    &.center-align {
                        text-align: center;
                        margin-bottom: 18px;
                    }
                }

                .chip {
                    font-size: 12px;
                    width: 176px;
                    height: 26px;
                    border-radius: 13px;
                    padding: 5px 17px;
                    background-color: #f3f7ff;
                }
            }
        }
    }

    .pl-20 {
      padding-left: 20px;
    }

    .pr-20 {
      padding-right: 20px;
    }

    .md-layout.md-gutter>.md-layout-item {
      padding-right: 10px;
      padding-left: 10px;
    }

    .table-footer {
        .md-layout {
            font-size: 11px;
            font-weight: normal;
            font-stretch: normal;
            font-style: normal;
            line-height: normal;
            letter-spacing: normal;
            color: #a5abb7;

            .md-layout-item {
              font-size: 11px;
            }

            span {
              font-size: 10px;
            }

            .md-field {
              min-height: 10px;
            }

            .md-icon.md-icon.md-theme-default.md-icon-font {
              margin: 0 !important;
            }
        }

        input {
          text-align: center;
        }
    }

    .md-table-cell-container {
        padding-left: 0;
    }

</style>
