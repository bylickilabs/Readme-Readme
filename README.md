|Your ✨ _special_ ✨ Readme Snake|
|---|

|I. By default your ReadMe repository will be located at the URL: https://github.com/{{username}}/{{username}}|
|---|
---

|II. Go to "Action"|
|---|

![1](https://user-images.githubusercontent.com/109308073/204129101-b406238f-270e-4ceb-84cc-71bc65daae71.jpg)
---

|III. Setup the Workflow|
|---|

![2](https://user-images.githubusercontent.com/109308073/204129164-50d49336-40cd-4518-8018-5422afde137c.jpg)
---

|IV. Create the main.yml File|
|---|

- It will create a main.yml file:

![3](https://user-images.githubusercontent.com/109308073/204129449-979a92aa-2947-47a3-9ee2-e8637a131c00.jpg)
---

|V. inside the main.yml file and paste the following code:|
|---|

name: Generate Snake

on:
  schedule:
    - cron: "* */1 * * *"
  workflow_dispatch:
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: Platane/snk@master
        id: snake-gif
        with:
          github_user_name: bylickilabs
          gif_out_path: dist/github-contribution-grid-snake.gif
          svg_out_path: dist/github-contribution-grid-snake.svg
      - run: git status
      - name: Push changes
        uses: ad-m/github-push-action@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          branch: master
          force: true
      - uses: crazy-max/ghaction-github-pages@v3
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          
          
