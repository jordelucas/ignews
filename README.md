## Como executar

Primeiro, execute o servidor de desenvolvimento:

```bash
npm run dev
# ou
yarn dev
```

Acesse [http://localhost:3000](http://localhost:3000) no seu navegador para ver o resultado.

## Requisitos Técnicos

- Tecnologias estudadas no módulo:
  - Next.js (SSR, SSG);
  - TypeScript;
  - SASS;
  - CSS Module;
  - App JAMSTack:
    - Stripe
    - Prismic
    - FaunaDB
    - Next Auth

## Anotações feitas durante o desenvolvimento

#### FRAMEWORK

É importante isolar componentes conforme suas funcionalidades, de modo que não haja efeito colateral em outras partes da aplicação. Um dos principais responsáveis por causar esses efeitos são os estados dos componentes. Além disso, também é recomendado definir estilizações conforme o contexto. Nesse sentido, o next.js dá suporte nativo ao **css modules**. Portanto, a estilização dos elementos pode ser limitada aos respectivos escopos.

No next.js, as imagens devem ficar na pasta */public*. Caso seja necessário importar esses arquivos dentro de um *.tsx*, uma sugestão é utilizar o plugin **next-images**.

O next.js também possui o conceito de **file system routing**, de modo que as rotas são definidas de acordo com os nomes de arquivos e pastas. Portanto, não é necessária uma dependência externa para roteamento (React Router, por exemplo).

Em relação a segurança, vale recordar que todas as páginas geradas de forma estática não são protegidas. Além disso, o next.js não permite o uso de variáveis de ambiente pelo lado do cliente. Para tornar as chaves públicas, é necessário defini-las como *NEXT_PUBLIC_[...]*.

#### AUTENTICAÇÃO

São estratégicas de autenticação:
  - JWT (Storage)
  - Next Auth (Social)
  - Authentication as a Service (Terceiros): Cognito, Auth0, etc

#### DATABASE

Nessa aplicação utilizaremos o **FaunaDB**, que é um dos bancos de dados voltados para aplicações que rodam em ambientes *serverless* (o servidor não está rodando 24h). DynamoDB, Firebase e supaBase são outras alternativas. 

**Obs.:**
  - *Para desenvolvimento, é possível rodar uma instância do FaunaDB com o docker. Contudo, utilizaremos o de produção.*
  - *O uso do banco de dados só deve ser feito nas api routes ou nos métodos getServerSideProps (SSR) ou getStaticProps (SSG) do Next.js.*

#### PAGAMENTO

Nesta aplicação utilizaremos o Stripe, uma plataforma de pagamento que permite transação por meio de cartão de crédito (Visa, Master, etc).

#### WEBHOOKS

Webhooks são patterns utilizados para integração entre sistemas na web. Com o stripe, por exemplo, o webhook é responsável por avisar a nossa aplicação que algum evento aconteceu. Por exemplo, um cartão que em dada mensalidade não conseguiu ser identificado (bloqueado, sem limites, etc).

Para executar localmente, é necessário utilizar o **Stripe CLI**.

Para garantir que é realmente o nosso serviço externo que está tentando se comunicar com a aplicação, é fornecida uma key (*STRIPE_WEBHOOK_SECRET*). 

#### JAMStack

JAMStack é um conceito que veio à tona com a abordagem que estamos desenvolvendo, isto é, sem toda a infraestrutura de backend que em aplicações maiores teria.

#### CMS

CMS (Content Management System) é uma plataforma que geralmente fornece um painel de administração. Sendo o Wordpress e Magento alguns dos mais famosos.

Quanto ao Headless CMS, este segue o mesmo conceito, contudo, não possui a parte visual para quem vai consumir o conteúdo, se limitando apenas ao painel de gerenciamento, onde os dados são servidos por meio de API. São exemplos: Strapi, Ghost, Keystone, GraphCMS, Prismic CMS, Contentful, Shopify, Saleor, etc. Neste projeto utilizaremos o Prismic CMS.

Para criar os post localmente, é necessário instalar a Slice Machine.

## Sugestões de estudo

  - Onde obter emojis: https://emojipedia.org/
  - Leitura sobre autenticação no Next: https://nextjs.org/docs/authentication
  - Estudar sobre Layout Shift.
  - Monitoramento de erros (Sentry, Bugsnag, New Relic, etc).
