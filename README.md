# Web-services-de-autentica-o-e-verifica-o-de-acesso-com-JWT-hash-e-salt
Devem ser implementados os 3 web services abaixo:

POST /registrar -> Realiza o registro de um novo usuário. Deve impedir o registro de usuários já registrados. O serviço deve receber no corpo da requisição o nome, e-mail e senha do usuário (nome, email, senha). A senha deve ser armazenada no banco de dados utilizando a abordagem de salt e hash (https://www.brunobrito.net.br/seguranca-salt-hash-senha/). O serviço deve enviar como resposta uma mensagem textual apropriada sinalizando o que ocorreu: usuário registrado com sucesso, usuário já existente ou erro no servidor. Os HTTP statuses apropriados devem ser utilizados nas respostas;
POST /login -> Realiza o login de um usuário previamente registrado. O serviço deve receber no corpo da requisição o e-mail e a senha do usuário (email, senha). A senha deve ser verificada usando a abordagem de salt e hash. Caso o usuário esteja registrado no banco de dados e sua senha esteja correta, o serviço deve retornar um token JWT baseado no e-mail do usuário e na chave secreta do seu backend, a qual você deve definir. Saiba mais sobre JWT neste link (https://www.devmedia.com.br/como-o-jwt-funciona/40265). Caso o usuário não esteja registrado no sistema OU a sua senha seja inválida, o serviço deve retornar uma mensagem sinalizando que as credenciais de usuário são inválidas. Utilize HTTPs statuses adequados para as suas respostas;
GET /verificar -> Verifica se o token JWT do usuário ainda é válido. No seu backend, o token deve ter período de validade de 5 minutos. O serviço deve receber no corpo da requisição o token (token) JWT do usuário. O serviço deve retornar como resposta a flag acessoLiberado com o valor true caso o token ainda seja válido (não expirou) ou false caso contrário (expirado).


Os dados do usuário devem ser gravados no MongoDB, utilizando Mongoose, utilizando o seguinte modelo de dados:

nome: String
email: String
hash: String
salt: String
Todos os campos devem ser obrigatórios.
