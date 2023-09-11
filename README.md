# Git: Um Guia Completo para Iniciantes

Neste artigo, vou ensinar a você como usar o Git, uma poderosa ferramenta de controle de versão amplamente utilizada na indústria de desenvolvimento de software.

## Instalação

Antes de começarmos, é necessário instalar o Git em sua máquina. Você pode encontrar instruções detalhadas de instalação para diferentes sistemas operacionais no site oficial do Git: [https://git-scm.com/download/](https://git-scm.com/download/). Certifique-se de selecionar a versão adequada para o seu sistema.

> **Dica para Usuários do Windows:**
>
> Ao instalar o Git no Windows, preste atenção em duas etapas importantes, mas opcionais:
>
> - **Editor de código:** Antigamente, o Nano era o editor padrão, mas recomendo o uso do Nano por sua simplicidade.
> - **Branch padrão:** Recomendo selecionar a branch **main**, que é o novo nome dado às branches no GitHub.

## Utilização

Agora que o Git está instalado, é hora de colocar a mão na massa! Abra seu terminal (ou PowerShell) e navegue até a pasta onde deseja iniciar seu repositório Git. Vamos cobrir os principais passos: inicialização, configuração do destino, configuração do `.gitignore`, consulta de modificações, adição de modificações, comentário de modificações e, finalmente, o envio.

### Inicialização

Dentro da pasta desejada, execute o seguinte comando no terminal:

```bash
$ git init
```

Isso criará uma pasta oculta chamada `.git`, que armazena todas as informações relacionadas às modificações, status e branches. Graças a essa pasta, você pode trabalhar com mais segurança, sabendo que pode reverter para o último commit caso algo dê errado.

### Configurando o Destino

Antes de prosseguirmos, você precisa criar uma conta no GitHub, que é amplamente utilizado para hospedar repositórios Git. Você pode se inscrever aqui: [https://github.com/signup](https://github.com/signup).

Após criar sua conta, crie um novo repositório. Na página inicial do GitHub, clique no botão `+` no canto superior direito e selecione `New repository`. Dê um nome ao seu repositório e forneça uma breve descrição.

Com o repositório criado, copie a URL que termina com `.git`. Em seguida, no terminal, use o comando a seguir para configurar o destino do seu repositório local:

```bash
$ git remote add origin <url>.git
```

Agora, seu destino está configurado para o repositório no GitHub.

### Ignorando Arquivos com o .gitignore

O arquivo `.gitignore` é usado para listar os arquivos e pastas que você deseja ignorar ao fazer o commit. Crie um arquivo `.gitignore` na raiz do seu projeto e liste os arquivos ou pastas que deseja ignorar, por exemplo:

```plaintext
# Pastas
node_modules/
authcreds/
dados/db/

# Arquivos
*log
*lock*
```

Este padrão ajuda a manter seu repositório organizado.

> **Atenção:**
>
> Não inclua o arquivo `.gitignore` no próprio `.gitignore`, pois isso pode confundir outros colaboradores do projeto.

> **Dica:**
>
> Se você deseja gerar um arquivo `.gitignore` específico para seu projeto, visite [https://www.toptal.com/developers/gitignore](https://www.toptal.com/developers/gitignore).

### Consultando Modificações

Para verificar as modificações pendentes em seu projeto, execute o seguinte comando:

```bash
$ git status
```

Este comando exibirá os arquivos modificados (em vermelho) e os arquivos prontos para commit (em verde).

### Adicionando Modificações

Para adicionar as modificações ao commit, use o seguinte comando:

```bash
$ git add <arquivo/pasta/.>
```

Você pode especificar arquivos, pastas ou usar `.` para adicionar todas as modificações. Lembre-se de que apenas os arquivos modificados podem ser adicionados. Use `git status` para verificar os arquivos modificados.

### Comentando Modificações

Após adicionar as modificações, é importante fornecer um comentário descritivo para o commit. Você pode adicionar vários arquivos e, em seguida, comentá-los juntos usando o seguinte comando:

```bash
$ git commit -m "Motivo da modificação"
```

O comentário é obrigatório e ajuda a documentar as alterações feitas em cada commit.

### Push: Enviando para o Repositório Remoto

Finalmente, para enviar suas modificações para o repositório remoto (no GitHub, neste caso), utilize o comando:

```bash
$ git push
```

Na primeira vez, você precisará especificar o upstream (ramificação e destino) da seguinte forma:

```bash
$ git push -u origin main # Padrão do GitHub
```

## Tópicos Mais Avançados

Até agora, você aprendeu os conceitos básicos do Git. Existem muitos tópicos avançados que você pode explorar para se tornar um usuário Git mais experiente. Aqui estão alguns deles:

- **Branches**: As branches são usadas para desenvolver recursos separadamente antes de mesclá-los com o código principal. Você pode criar, listar, alternar e mesclar branches.

- **Merge e Rebase**: Esses comandos permitem incorporar as alterações de uma branch em outra. O merge combina as alterações, enquanto o rebase move as alterações de uma branch para outra de forma mais linear.

- **Resolução de Conflitos**: Quando duas branches têm alterações conflitantes, você precisará resolver esses conflitos manualmente antes de fazer um commit.

- **Clonagem de Repositório**: Você pode clonar repositórios existentes para colaborar com outros desenvolvedores ou trabalhar em diferentes máquinas.

- **Ferramentas Gráficas**: Além da linha de comando, existem várias ferramentas gráficas Git disponíveis, como o GitHub Desktop, que podem facilitar a interação com o Git.

## Links Úteis

Aqui estão alguns recursos adicionais que podem ajudá-lo a aprofundar seus conhecimentos sobre Git:

- [Documentação oficial do Git](https://git-scm.com/doc): A documentação oficial do Git é uma fonte valiosa de informações detalhadas.

- [Pro Git](https://git-scm.com/book/en/v2): Este livro online gratuito, disponível em vários idiomas, é uma excelente referência para aprender Git.

- [Git e GitHub para Iniciantes](https://www.youtube.com/watch?v=2alg7MQ6_sI): Um vídeo tutorial introdutório no YouTube.

## Conclusão

Parabéns! Agora você possui uma base sólida para começar a usar o Git em seus projetos de desenvolvimento de software. Lembre-se de que o Git é uma habilidade valiosa que pode abrir portas em diversas empresas, demonstrando habilidades de trabalho em equipe e organização de projetos.

## SSH: Autenticação Obrigatória

Se você chegou até aqui, provavelmente enfrentou problemas de autenticação. A documentação do GitHub explica como criar uma chave SSH e adicioná-la à sua conta. Siga as instruções em [GitHub Docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

Após criar sua chave SSH, retorne ao repositório no GitHub. Na página inicial, à esquerda da URL `.git`, você verá dois botões, `HTTPS` e `SSH`. Selecione `SSH` e copie a nova URL. No terminal, remova o destino atual e adicione a nova URL com os seguintes comandos:

```bash
$ git remote remove origin
$ git remote add origin <nova-ssh-url.git>
```

Em seguida, faça o push novamente com o comando `git push`.

---

<div align="center">
  <div>Made with 🤍 by Ahosall (Feh's)</div>
</div>
