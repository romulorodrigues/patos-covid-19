# Patos COVID-19
Esta é uma simples aplicação para exibir dados sobre o coronavírus na cidade de Patos - PB. Os dados apresentados são: número de casos confirmados, número de mortes, população estimada e taxa de mortalidade (mortes / confirmados).

Você pode adaptar para a sua cidade! É muito simples!

Link da aplicação: https://romulorodrigues.github.io/patos-covid-19/

# Uso

- Baixe o repositório como arquivo zip ou faça um clone;
- No método getData do componente Home, altere o "state" na url para o seu estado. No meu caso, usei PB (Paraíba).
- Ex: https://brasil.io/api/dataset/covid19/caso/data?is_last=True&state=PB.
- Mais informações:

Fonte: Secretarias de Saúde das Unidades Federativas, dados tratados por Álvaro Justen e colaboradores/Brasil.IO.
Brasil.IO: boletins epidemiológicos da COVID-19 por município por dia, disponível em: https://brasil.io/dataset/covid19/ (última atualização: 12-05-2020, acesso em 13-05-2020).

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
