# Artigos ABNT em Markdown

Esse projeto é um template para a escrita de artigos científicos, seguindo as normas da ABNT (a maior parte delas, pelo menos), com Markdown e conversão automática para PDF (via Pandoc e Github Actions), além de versionamento por Git.

Não entrarei em detalhes de como tudo funciona porque esse texto não se propõe em ser um evangelho em prol do texto puro, nem um tutorial. Esse template é voltado para quem entende os prós e contras de não se usar um processador de texto como _Word_.

No atual estágio temos a maior parte das necessidades impostas pelas normas implementadas.

## :eyeglasses: Como usar

Clique no botão verde logo acima **Use this templete**. O Github irá perguntar qual será o nome do repositório e se ele será público ou privado.

Clone o projeto no seu computador e escreva seu texto alterando os arquivos **.md**. A numeração dos arquivos precisam seguir a ordem em que eles estarão no texto final. Você pode criar quantos arquivos **.md** forem necessários (lembre-se apenas de manter a numeração sequencial) e pode também optar por escrever seu texto inteiro apenas em um único arquivo, nesse caso você não precisa da numeração.

O arquivo **\_config.md** contém as informações pré-textuais e pós-textuais do seu texto como título, autor, resumo, etc., além de algumas outras configurações. Esses itens são todos opcionais nessa aplicação. Exemplo: se seu artigo não tiver um resumo em inglês, você pode apagar o **abstract** e as **keywords** sem nenhum problema.

A bibliografia usa tanto o padrão de citação do [Pandoc](https://pandoc.org/MANUAL.html#citations).

Você pode (e deve) fazer _commits_ ao longo da sua redação a fim de manter uma ordem lógica no versionamento do seu trabalho e gerar um PDF é tão simples quanto criar uma _tag_:

`git tag 0.1`

Onde "0.1" é a versão atribuída por você. Ela deve ser única e sequencial. Uma recomendação é seguir a lógica x.y.z onde z são as correções, y são adições menores e x as edição maiores. Mas isso fica a seu critério.

Após tagear seu texto, faça o _push_ da _tag_ com `git push --tags` e pronto. A conversão é feita nos servidores do Github e após cerca de 2 minutos (normalmente 1 minuto) um PDF totalmente formatado estará esperando por você na área de releases, dentro do seu repositório do Github.

## :collision: Inconsistências das normas

Se você chegou a se dar o trabalho de ler as normas técnicas que regem a produção de textos científicos, percebeu que a maior parte das regras que te ensinaram nas aulas de metodologia científica são falsas e incorretas. As normas não definem uma série de coisas (mais sobre esse assunto num [texto que escrevi no meu blog](https://dsoares.me/blog/2020-04-02-artigos-cientificos-com-a-nova-norma/)) e os eventos acadêmicos e os periódicos tem o péssimo hábito de complicar ainda mais nossas vidas nos impondo as mais esdruxulas regras sem sentido. Logo, esse template, do jeito que está, pode não servir para todas as ocasiões, mas em breve adicionarei mais opções de customização.

Outro ponto é a numeração automática das seções da parte textual. Ela segue a minha interpretação onde a _Introdução_ e as _Consideração finais_ não são numeradas. Isso é controlado pelo elemento `{-}` (padrão do próprio Pandoc) logo após os títulos em questão e podem ser retirados sem nenhum problema.

## :computer: Requisitos para rodar localmente

Você pode rodar a conversão localmente, mas precisará de alguns softwares para isso. Olhe o arquivo `conversor.yml` dentro de `.github/workflows` que lá tem as dependências e o comando completo de conversão.

## :sparkles: Implementações futuras

- [ ] uma forma fácil de alterar o tamanho dos títulos
- [x] correção das legendas das imagens e melhoria das legendas de tabelas
- [ ] ~~geração de arquivos docx~~ :broken_heart:
  - não parece ser possível gerar um `docx` personalizado, mas é possível gerar um `odt`;
  - em tese é possível modificar o [arquivo OpenDocument](https://www.libreoffice.org/discover/what-is-opendocument/) [padrão do Pandoc](https://github.com/jgm/pandoc/blob/master/data/templates/default.opendocument) para gerar um `odt` melhor que o formato nativo, mas demandaria bastante trabalho em entender como funciona o formato;
  - outro problema é que o filtro [pandoc_abnt](https://github.com/limarka/pandoc_abnt), usado para gerar as legendas das imagens e tabelas com as normas ABNT no formato `pdf`, [ainda não é compatível](https://github.com/limarka/pandoc_abnt/issues/25) com a geração de `odt`;
  - uma alternativa mais viável é converter manualmente, usando o Pandoc, em `docx` ou `odt` e adicionar a formatação manualmente. :persevere:
