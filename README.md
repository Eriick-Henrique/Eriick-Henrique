<h5 align="left">Sobre Mim<br><br>Olá! Meu nome é Erick Henrique, tenho 31 anos e estou atualmente cursando Análise e Desenvolvimento de Sistemas. Com um grande interesse em tecnologia e inovação, decidi seguir uma carreira na área de desenvolvimento de software, com um foco particular no front-end.<br><br>Durante meus estudos, tenho me aprofundado nas principais tecnologias e ferramentas utilizadas no desenvolvimento web, como HTML, CSS, JavaScript e frameworks populares como React. Estou sempre em busca de novos conhecimentos e técnicas para aprimorar minhas habilidades e entregar interfaces de usuário que sejam não apenas funcionais, mas também intuitivas e visualmente atraentes.<br><br>Além dos estudos, dedico meu tempo a explorar projetos práticos, onde posso aplicar o que estou aprendendo e enfrentar desafios reais. Acredito que a prática é essencial para o crescimento na área de desenvolvimento, e estou constantemente em busca de oportunidades para colaborar em projetos que possam agregar valor ao meu portfólio e à comunidade de desenvolvedores.<br><br>Estou animado com as possibilidades que o futuro reserva na área de desenvolvimento front-end e estou empenhado em me tornar um profissional competente, capaz de transformar ideias em soluções digitais impactantes. Se você quiser saber mais sobre o meu trabalho ou colaborar em algum projeto, sinta-se à vontade para entrar em contato!</h5>

###

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Eriick-Henrique&hide_title=false&hide_rank=false&show_icons=true&include_all_commits=true&count_private=true&disable_animations=false&theme=dark&locale=pt-br&hide_border=false" height="150" alt="stats graph"  />
  <img src="https://github-readme-stats.vercel.app/api/top-langs?username=Eriick-Henrique&locale=pt-br&hide_title=false&layout=compact&card_width=320&langs_count=5&theme=dark&hide_border=false" height="169" alt="languages graph"  />
</div>

###

<div align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" height="40" alt="javascript logo"  />
  <img width="20" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/typescript/typescript-original.svg" height="40" alt="typescript logo"  />
  <img width="20" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" height="40" alt="react logo"  />
  <img width="20" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" height="40" alt="html5 logo"  />
  <img width="20" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" height="40" alt="css3 logo"  />
</div>

###

<div align="left">
  <a href="https://www.instagram.com/erickhenriquee__/" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Instagram&logo=instagram&label=&color=E4405F&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="instagram logo"  />
  </a>
  <a href="erickhjdev@gmail.com" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Gmail&logo=gmail&label=&color=D14836&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="gmail logo"  />
  </a>
  <a href="https://www.linkedin.com/in/erick-henrique-de-jesus-0025422b0/" target="_blank">
    <img src="https://img.shields.io/static/v1?message=LinkedIn&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="linkedin logo"  />
  </a>
</div>

###

<img src="https://raw.githubusercontent.com/Eriick-Henrique/Eriick-Henrique/output/snake.svg" alt="Snake animation" />

###
name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - master

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
