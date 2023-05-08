<h1>Microsserviços: explorando os conceitos</h1>

<strong>O que compoe um microserviço:</strong> cada microsserviço deve ser o dono e gerenciar seus próprios dados.

<strong>Microsserviços são independentes:</strong> um microsserviço expõe alguma forma de comunicação (uma API). Isso é o contrato entre este microsserviço e seus clientes.
- Apenas faça modificações aditivas.
- Versionamento de APIs.
- Manter equipes separadas, donas de cada serviço.

Pense antes de implementar:
- Desenhe um fluxo real usando uma arquitetura de microsserviços. Desta forma os problemas de cada abordagem surgirão.

Onde manter o microsserviços:
- Máquinas virtuais.
- Sistemas em Cloud.
- Containers.

Etapas necessárias para criar um novo serviço:
- Configurar repositório para versionarmos nosso código.
- Escolher entre monorepositório ou multirepositório.
- Integração e entrega contínuas (CI e CD).
- Devemos ter todo o processo automatizado e teste devem não só existir, mas devem ser confiáveis.
- Um padrão sempre deve ser seguido para que todas as equipes estejam aptas a criar novos serviços.

Padronizando a criação.
<strong>Diversas tarefas devem ser realizadas de forma semelhante entre os serviços:</strong>
<ul>
<li>Criação de logs:</li>
	<ul>
	<li>Formato.</li>
	<li>Destino.</li>
	</ul>
<li>Verificações de status (health checks).</li>
<li>Monitoramento de métricas.</li>
<li>Busca por configuração e secrets.</li>
</ul>

<h3>Comunicação entre serviços:</h3>
<h4> Possíveis problemas:</h4>
- Dependências descontroladas.
- Falhas em cascata.
- Performance prejudicada. 

Comunicação direta:
- Diversos cenários nos obrigam a realizar "chamadas" e esperar por suas respostas.
- Isso é o que conhecemos como comunicação síncrona.

Como se comunicar (direta):
- HTTP (API RESTful).
- gRPC.
- Protocolos personalizados.

Comunicação indireta:
- Existem cenários onde a resposta não precisa ser obtida imediatamente.

Como se comunicar (indireta):
- CQRS (background tasks).
- Eventos (mensageria).

Falhas em comunicação síncrona:
- Circuit breaker.
- Cache.

Falhas em comunicação assíncrona:
- Simples Retry.
- Retry com back-off.
- Fila de mensagens mortas.
- Mensagens devem poder ser lidas fora de ordem.
- Mensagens devem poder ser recebidas repetidamente (idempotência).

Autenticação:
- Cada requisição deve informar quem é o cliente. A partir dessa informação, nossa aplicação pode decidir se a operação será realizada ou não.

Técnicas de autenticação:
- Basic HTTP.
- Tokens (JWT).
- OAuth.
- OpenID Connect.

Release pipeline:
- Uma release pipeline é uma linha de processos executados para gerar a entrega de um projeto.
- Nesta pipeline podem estar processos de build, verificações, testes, etc.

O microsserviço pode ser implantado em vários ambientes:
- Desenvolvimento.
- Staging / QA:
	<ul>
	<li>Testes de perfomace.</li>
	<li>Smoke tests.</li>
	</ul>
- Homologação.
- Produção: 
	<ul>
	<li>Por cliente.</li>
	<li>Por região.</li>
	</ul>

Configurações parametrizadas:
- Configurações do ambiente em si:
	<ul>
	<li>Quantidade de recursos.</li>
	<li>Localização.</li>
	</ul>
- Configurações da aplicação:
	<ul>
	<li>Destino de log.</li>
	<li>Dependência.</li>
	<li>Dados de acesso.</li>
	</ul>

Estratégias de releases:
- Rolling upgrade.
- Blue-green.
- Feature toggle.
