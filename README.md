# Workshop Spring Boot & JPA (Web Services)

## Sobre o Projeto
Este repositório contém uma API RESTful completa desenvolvida como um sistema de e-commerce/pedidos. O objetivo principal deste projeto foi consolidar os fundamentos de desenvolvimento back-end em Java com **Spring Boot**, aplicando os conceitos de boas práticas de mercado, injeção de dependência e desacoplamento de camadas.

A aplicação simula o fluxo completo de um fechamento de compra, gerenciando dados de usuários, pedidos, itens de pedidos, pagamentos e categorização de produtos.

*Projeto prático desenvolvido durante o curso de Java Completo do Prof. Nelio Alves na Udemy.*

## Tecnologias Utilizadas
* **Java**
* **Spring Boot 3**
* **Spring Data JPA** (Hibernate)
* **Banco de Dados H2** (Perfil de teste)
* **PostgreSQL** (Perfil de produção)
* **Maven**

## Conceitos Avançados Praticados

Olhando além do CRUD básico, usei este projeto para dominar os seguintes cenários de nível profissional:

* **Mapeamento de Chave Composta (Composite Primary Key):** Implementação da classe de associação `OrderItem` utilizando uma chave primária composta (`OrderItemPK`) com `@Embeddable` e `@EmbeddedId`, permitindo relacionar de forma limpa tabelas N:N com atributos extras.
* **Tratamento Global de Exceções:** Criação de uma camada dedicada exclusivamente para interceptar e tratar erros de requisições (`@ControllerAdvice` e `@ExceptionHandler`). Implementei respostas customizadas e limpas para cenários de:
  * Recurso Não Encontrado (`ResourceNotFoundException` -> `404 Not Found`).
  * Erros de Integridade de Banco de Dados ao tentar deletar entidades vinculadas (`DatabaseException` -> `400 Bad Request`).
* **Instanciação Automática (Database Seeding):** Configuração de um perfil de testes (`TestConfig`) que popula o banco de dados H2 automaticamente na inicialização da API, facilitando testes manuais imediatos via Postman.
* **Estados e Ciclos de Vida:** Controle semântico do status do pedido através de tipos enumerados (`OrderStatus`) e mapeamento correto de relacionamentos um-para-um dependentes, como o vínculo entre Pedido (`Order`) e Pagamento (`Payment`).

## Modelo de Domínio (Entidades Mapeadas)
* **User:** Clientes do sistema.
* **Order:** Pedidos realizados, associados a um cliente e a um status.
* **Product** & **Category:** Produtos da loja e suas respectivas categorias (Mapeamento Many-to-Many).
* **OrderItem:** Entidade intermediária que gerencia a quantidade e o preço dos produtos em cada pedido.
* **Payment:** Dados do pagamento efetuado para disparar a conclusão do pedido.

## Como executar localmente

### Pré-requisitos
* Java JDK instalado.
* Maven instalado (ou utilizar o wrapper `./mvnw` incluso).

### Instruções
1. Clone o repositório:
```bash
   git clone [https://github.com/diegosidarta/workshop-springboot-jpa.git](https://github.com/diegosidarta/workshop-springboot-jpa.git)
