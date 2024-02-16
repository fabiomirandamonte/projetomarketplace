Obs.: Projeto em fase de conclusão.

Um breve resumo sobre o projeto e as tecnologias utilizadas.

Meu projeto é um marketplace inovador, criado com o objetivo de proporcionar uma plataforma eficiente e dinâmica para compradores e vendedores. No backend, utilizei uma série de tecnologias essenciais para garantir a robustez e a segurança da aplicação. O uso do CORS permite que a API seja acessada por diferentes origens, enquanto o dotenv gerencia variáveis de ambiente de forma organizada. O Express é a espinha dorsal do servidor, facilitando o roteamento e o tratamento de requisições HTTP. A autenticação é realizada de forma segura com o JSON Web Token, garantindo a proteção dos dados dos usuários. Para armazenar e gerenciar os dados, optei pelo MySQL2, aproveitando sua confiabilidade e desempenho. Além disso, o uso do Nodemon agiliza o processo de desenvolvimento, permitindo atualizações automáticas sempre que houver alterações no código.

No frontend, concentrei-me em oferecer uma experiência de usuário fluida e intuitiva, utilizando as tecnologias HTML e CSS para a estruturação e estilização do site. Para isso, adotei um conjunto de tecnologias modernas e poderosas. O Axios é responsável por realizar requisições HTTP de forma assíncrona, garantindo uma comunicação eficiente entre o frontend e o backend. A integração do QRCode permite a geração e leitura de códigos QR, agregando valor ao processo de compra e venda. O Vue.js é o framework principal utilizado para construir a interface do usuário, oferecendo um desenvolvimento ágil e componentizado. O Vue Router e o Vuex complementam o Vue.js, facilitando a navegação e o gerenciamento do estado da aplicação. Por fim, o Vite proporciona uma experiência de desenvolvimento rápida e eficiente, garantindo tempos de compilação mínimos e recarregamento instantâneo durante o desenvolvimento.

Para garantir a funcionalidade e a estabilidade do sistema, utilizei o Cypress, uma ferramenta de teste de ponta a ponta que permite a escrita e execução de testes automatizados de forma simples e eficaz. Com o Cypress, pude criar cenários de teste abrangentes para verificar a integridade do sistema em diferentes condições, garantindo uma experiência consistente e livre de erros para os usuários.

Para a gestão do banco de dados MySQL, recorri ao DBeaver, uma ferramenta robusta e versátil que simplifica a criação e manutenção do esquema de dados. Utilizando consultas SQL e visualizando os resultados de forma intuitiva, pude modelar e administrar o banco de dados de maneira eficiente, garantindo a integridade e a confiabilidade dos dados.

No cerne de todo esse ecossistema tecnológico está o JavaScript, a linguagem de programação que unifica todas as partes do projeto. Sua versatilidade e ampla adoção na indústria tornaram possível a construção de um marketplace sólido e escalável, capaz de atender às necessidades dos usuários e se adaptar às demandas do mercado em constante evolução.


# Clientes
### Listar clientes
curl --location 'http://localhost:3000/cliente' \
--header 'Authorization: Bearer {{token}}'

### Login
curl --location 'http://localhost:3000/login' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email": "fulano@gmail.com",
    "senha": "123456"
  }'
