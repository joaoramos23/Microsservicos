<h1>Microsserviços: explorando os conceitos</h1>

<strong>O que compoe um microserviço:</strong> cada microsserviço deve ser o dono e gerenciar seus próprios dados.

<strong>Microsserviços são independentes:</strong> um microsserviço expõe alguma forma de comunicação (uma API). Isso é o contrato entre este microsserviço e seus clientes.
- Apenas faça modificações aditivas.
- Versionamento de APIs.
- Manter equipes separadas, donas de cada serviço.

<h3>Pense antes de implementar:</h3>
- Desenhe um fluxo real usando uma arquitetura de microsserviços. Desta forma os problemas de cada abordagem surgirão.

<h3>Onde manter o microsserviços:</h3>
- Máquinas virtuais.
- Sistemas em Cloud.
- Containers.

<h3>Etapas necessárias para criar um novo serviço:</h3>
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

<h3>Comunicação direta:</h3>
- Diversos cenários nos obrigam a realizar "chamadas" e esperar por suas respostas.
- Isso é o que conhecemos como comunicação síncrona.

<h3>Como se comunicar (direta):</h3>
- HTTP (API RESTful).
- gRPC.
- Protocolos personalizados.

<h3>Comunicação indireta:</h3>
- Existem cenários onde a resposta não precisa ser obtida imediatamente.

<h3>Como se comunicar (indireta):</h3>
- CQRS (background tasks).
- Eventos (mensageria).

<h3>Falhas em comunicação síncrona:</h3>
- Circuit breaker.
- Cache.

<h3>Falhas em comunicação assíncrona:</h3>
- Simples Retry.
- Retry com back-off.
- Fila de mensagens mortas.
- Mensagens devem poder ser lidas fora de ordem.
- Mensagens devem poder ser recebidas repetidamente (idempotência).

<h3>Autenticação:</h3>
- Cada requisição deve informar quem é o cliente. A partir dessa informação, nossa aplicação pode decidir se a operação será realizada ou não.

<h3>Técnicas de autenticação:</h3>
- Basic HTTP.
- Tokens (JWT).
- OAuth.
- OpenID Connect.

<h3>Release pipeline:</h3>
- Uma release pipeline é uma linha de processos executados para gerar a entrega de um projeto.
- Nesta pipeline podem estar processos de build, verificações, testes, etc.

<h3>O microsserviço pode ser implantado em vários ambientes:</h3>
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

<h3>Configurações parametrizadas:</h3>
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

<h3>Estratégias de releases:</h3>
- Rolling upgrade.
- Blue-green.
- Feature toggle.
