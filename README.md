# SafeLoginLdapWeb
Com essas classes e configurações' LDAP ' ' Spring Boot Security': temos um sistema de acesso múltiplo com controle de permissões de acesso baseado em roles, que permite a autenticação em diferentes fontes de dados e o controle granular de acesso a diferentes módulos e funcionalidades do sistema 

classe LDAPAuthenticationService que conterá o método ldapAuthenticate para autenticar o usuário no servidor LDAP 192.168.15.2. Caso a autenticação falhe, o método deve retornar false.

classe DatabaseAuthenticationService com o método databaseAuthenticate para autenticar o usuário no banco de dados usando a tabela Tb_User. Antes de chamar este método, deve-se fazer um ping no servidor 192.168.15.1 para verificar se há conexão. Caso não haja conexão, o método deve retornar false.

classe UserPermissionService com o método getUserPermissions,Para conferir o Role do usuário, que receberá como parâmetro o usuário autenticado e retornará uma lista de permissões (módulos, classes e botões) que o usuário possui acesso.

classes e botões de acordo com as permissões do Role,Para liberar os acessos nos módulos, pode-se criar uma classe PermissionInterceptor que interceptará as requisições e verificará se o usuário possui as permissões necessárias para acessar o módulo, classe ou botão solicitado. Se o usuário não possuir as permissões necessárias, o interceptor deve redirecioná-lo para uma página de acesso negado.

As classes de acesso (como LDAPAuthenticationService e DatabaseAuthenticationService) devem ser separadas das classes de permissões de acesso (como UserPermissionService e PermissionInterceptor) para manter a modularidade e facilitar a manutenção do código.

classe controllerRoules correspondente ( XXXXXXController, XXXXXController, XXXXXController, XXXXXXController, XXXXXController, XXXXXController e DashboardController) os 'xxxxx' representam os modulos do seu sistema. ou as classes do sistema, assim cada Methodo controlara os Roules de acesso a eles dentro de si, evitando codigos espalhados e desorganisdos na aplicação com os métodos necessários para cada rota (@RequestMapping) e botão a ser liberado. Esses métodos devem ser protegidos pelo interceptor de permissões (PermissionInterceptor) para garantir que apenas os usuários com as permissões corretas tenham acesso.
