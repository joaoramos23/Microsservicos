<h1>Microsserviços: explorando os conceitos</h1>

<strong>O que compoe um microserviço:</strong> cada microsserviço deve ser o dono e gerenciar seus próprios dados.

<strong>Microsserviços são independentes:</strong> um microsserviço expõe alguma forma de comunicação (uma API). Isso é o contrato entre este microsserviço e seus clientes.
<ul>
<li>Apenas faça modificações aditivas.</li>
<li>Versionamento de APIs.</li>
<li>Manter equipes separadas, donas de cada serviço.</li>
</ul>
<h3>Pense antes de implementar:</h3>
<ul>
<li>Desenhe um fluxo real usando uma arquitetura de microsserviços. Desta forma os problemas de cada abordagem surgirão.</li>
</ul>
<h3>Onde manter o microsserviços:</h3>
<ul>
<li>Máquinas virtuais.</li>
<li>Sistemas em Cloud.</li>
<li>Containers.</li>
</ul>
<h3>Etapas necessárias para criar um novo serviço:</h3>
<ul>
<li>Configurar repositório para versionarmos nosso código.</li>
<li>Escolher entre monorepositório ou multirepositório.</li>
<li>Integração e entrega contínuas (CI e CD).</li>
<li>Devemos ter todo o processo automatizado e teste devem não só existir, mas devem ser confiáveis.</li>
<li>Um padrão sempre deve ser seguido para que todas as equipes estejam aptas a criar novos serviços.</li>
</ul>
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
<ul>
<li>Dependências descontroladas.</li>
<li>Falhas em cascata.</li>
<li>Performance prejudicada.</li>
</ul>
<h3>Comunicação direta:</h3>
<ul>
<li>Diversos cenários nos obrigam a realizar "chamadas" e esperar por suas respostas.</li>
<li>Isso é o que conhecemos como comunicação síncrona.</li>
</ul>
<h3>Como se comunicar (direta):</h3>
<ul>
<li>HTTP (API RESTful).</li>
<li>gRPC.</li>
<li>Protocolos personalizados.</li>
</ul>
<h3>Comunicação indireta:</h3>
<ul>	
<li>Existem cenários onde a resposta não precisa ser obtida imediatamente.</li>
</ul>
<h3>Como se comunicar (indireta):</h3>
<ul>	
<li>CQRS (background tasks).</li>
<li>Eventos (mensageria).</li>
</ul>
<h3>Falhas em comunicação síncrona:</h3>
<ul>	
<li>Circuit breaker.</li>
<li>Cache.</li>
</ul>
<h3>Falhas em comunicação assíncrona:</h3>
<ul>	
<li>Simples Retry.</li>
<li>Retry com back-off.</li>
<li>Fila de mensagens mortas.</li>
<li>Mensagens devem poder ser lidas fora de ordem.</li>
<li>Mensagens devem poder ser recebidas repetidamente (idempotência).</li>
</ul>
<h3>Autenticação:</h3>
<ul>
<li>Cada requisição deve informar quem é o cliente. A partir dessa informação, nossa aplicação pode decidir se a operação será realizada ou não.</li>
</ul>
<h3>Técnicas de autenticação:</h3>
<ul>	
<li>Basic HTTP.</li>
<li>Tokens (JWT).</li>
<li>OAuth.</li>
<li>OpenID Connect.</li>
</ul>
<h3>Release pipeline:</h3>
<ul>
<li>Uma release pipeline é uma linha de processos executados para gerar a entrega de um projeto.</li>
<li>Nesta pipeline podem estar processos de build, verificações, testes, etc.</li>
</ul>
<h3>O microsserviço pode ser implantado em vários ambientes:</h3>
<ul>
<li>Desenvolvimento.</li>
<li>Staging / QA:</li>
	<ul>
	<li>Testes de perfomace.</li>
	<li>Smoke tests.</li>
	</ul>
<li>Homologação.</li>
<li>Produção:</li>
	<ul>
	<li>Por cliente.</li>
	<li>Por região.</li>
	</ul>
</ul>
<h3>Configurações parametrizadas:</h3>
<ul>
<li>Configurações do ambiente em si:</li>
	<ul>
	<li>Quantidade de recursos.</li>
	<li>Localização.</li>
	</ul>
<li>Configurações da aplicação:</li>
	<ul>
	<li>Destino de log.</li>
	<li>Dependência.</li>
	<li>Dados de acesso.</li>
	</ul>
</ul>
<h3>Estratégias de releases:</h3>
<ul>
<li>Rolling upgrade.</li>
<li>Blue-green.</li>
<li>Feature toggle.</li>
</ul>
