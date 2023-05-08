<h1>Microsserviços: padrões de projetos</h1>

<h3>Como funciona a Web:</h3>
<ul>
<li>A internet funciona através de um protocolo conhecido como HTTP.</li>
</ul>
<h3>Problemas de uma aplicação monolitica:</h3>
<ul>
<li>Demora no deploy.<br></li>
<li>Falhas podem derrubar o sistema todo.<br></li>
<li>1 projeto = 1 tecnologia.<br></li>
</ul>
<br><strong>Deploy:</strong> significa enviar mudanças ou atualizações de um ambiente de implantação para outro, podendo ser o principal ou algum intermediário.<br>

<h3>Arquitetura de microsserviços:</h3>
<ul>
<li>Abordagem arquitetônica e organizacional do desenvolvimento de software na qual o software cosiste em pequenos serviços independentes que se comunicam usando API's bem definidas.<br></li>
<li>Serviços pertencem a pequenas equipes autossuficientes.<br></li>
</ul>
<h3>Vantagens microsserviços:</h3>
<ul>
<li>Projetos independentes = tecnologias independentes.<br></li>
<li>Falha em 1 serviço é isolada.<br></li>
<li>Deploys menores e mais rápidos.<br></li>
</ul>
<h3>Desvantagens microsserviços:</h3>
<ul>
<li>Maior complexidade de desenvolvimento e infra.<br></li>
<li>Debug mais complexo.<br></li>
<li>Comunicação entre os serviços deve ser bem pensada.<br></li>
<li>Diversar tecnologias pode ser um problema.<br></li>
<li>Monitoramento é crucial e mais complexa.<br></li>
</ul>
<h3>Tipos de microsserviços:</h3>
<ul>
<li>Data service.<br></li>
<li>Business service.<br></li>
<li>Translation service.<br></li>
<li>Edge service.<br></li>
</ul>
<h3>Serviços de domínio:</h3>
<ul>
<li>Domain-driven Design.</li>
<li>Comece modelando seu domínio, não pensando na persistência.</li>
<li>Avalie as ações que serçao disponibilizadas.</li>
<li>Construa o serviço, pensando primeiro no cantrato.</li>
<li>REST e RPC podem andar juntos.</li>
</ul>
<h3>Serviços de negócio:</h3>
<ul>
<li>Em determinados momentos as operações precisam de mais de um modelo do nosso domínio para serem corretamente reporesentadas em um serviço.</li>
<li><strong>Processo do dominhio do negócio</strong>:
	<ul>
	<li>Provem uma funcionalidade do negócio de mais alto nível.</li>
	<li>Permite encpsular domínios relacionados.</li>
	</ul>
</li>
<li><strong>Criando um serviço de negócio:</strong>
	<ul>
	<li>Identifique o processo que você pretende expor.</li>
	<li>Identifique os domínios que serão necessário nesse serviço.</li>
	<li>Defina a API que será utilizada, focando no domínio e não nos dados.</li>
	<li>Consuma serviços de domínio para executar os processos.</li>
	</ul>
</li>
</ul>
<h3>Strangler pattern:</h3>
<ul>
<li>Quebrar um monolito, tirando as funcionalidades dele.</li>
<li>Podemos começar isolando os dados.</li>
<li>Ou podemos começar isolando o domínio.</li>
</ul>
<h3>Sidecar pattern:</h3>
<ul>
<li>Determine o processo comum.</li>
<li>Construa um módulo compartilhável.</li>
<li>Aplique esse sidecar nos serviços que precisam dele.</li>
</ul>
<h3>API Gateway:</h3>
<ul>
<li>Problema: Clientes acessando livremente os serviços geram caos.</li>
<li>Gateway fornece um proxy, uma fachada, para as necessidades reais.</li>
<li>Desvantagem: Esse portão de entrada pode ser tornar um ponto central de falha.</li>
</ul>
<h3>Comportamentos do Gateway:</h3>
<ul>
<li>Simplesmente autorizar e redirecionar os requests.</li>
<li>Uso de Decorator para adicionar informações necessárias aos requests.</li>
<li>Limitar acesso ou conteúdo trafegado.</li>
</ul>
<h3>Process aggregator pattern:</h3>
<ul>
<li>Serviços de negócio agregam serviços de domínio.</li>
<li>Process aggreagatros agregam serviços de negócio.</li>
<li>Agragadores fazem as chamadas para os serviços necessários e montam a respota correta.</li>
<li>Pode (e deve) ter lógica de processamento.</li>
</ul>
<h3>Construindo um agregador:</h3>
<ul>
<li>Defina um novo modelo para representar os dados agregados.</li>
<li>A partir deste modelo, pense na API que fornecerá as operações.</li>
</ul>
<h3>Edge pattern:</h3>
<ul>
<li>Gateway específico para determinados(s) clientes(s).</li>
<li>Foco nas necessidades reais de determinados clientes.</li>
</ul>
<h3>Construindo uma ponta:</h3>
<ul>
<li>Identifique o cliente e suas necessidades.</li>
<li>Construa contratos específicos para o cliente.</li>
<li>Modifique os dados que são transferidos para garantir a otimização do processo.</li>
<li>Existe a possibilidade de ter apenas Edges.</li>
</ul>

<h3>Single service database:</h3>
<ul>
<li>Problema: Escalabilidade do serviço e do banco são fortemente relacionados.</li>
<li>Solução: Cada serviço (que precisar) terá seu próprio banco de dados.</li>
</ul>
<h3>CQRS(Command Query Responsibility Segregation):</h3>
<ul>
<li>Com leitura e escrita separados, cada parte pode realizar operações mais complexas.</li>
<li>O modelo de leitura pode ter informações agregadas de outros domínios.</li>
<li>O modelo de escrita pode ter dados sendo automaticamente gerados.</li>
<li>Aumenta a complexicdade de um sistema.</li>
</ul>
<h3>Asynchronous eventing:</h3>
<ul>
<li>Determinados problemas NÂO PODEM ser resolvidos na hora (em tempo real).</li>
<li>Um serviço emite um evento que será tratado em seu devido tempo.</li>
<li>Tecnologias como mensagerias e serviços de stream de dados brilham.</li>
</ul>
<h3>Agregando logs:</h3>
<ul>
<li>Formatos de log devem ser compartilhados entre os serviços.</li>
<li>Uma taxonomia comum deve ser compartilhada.</li>
<li>Logs de monolitos são agregados por padrão.</li>
<li>Parte da tarefa de agregação pode ser o parsing dos logs para categorizar corretamente.</li>
</ul>
<h3>Rastreando chamadas:</h3>
<ul>
<li>Uma parte importante de realizar logs é rastrear as chamadas de uma execução.</li>
<li>Devemos poder reconstruir uma operação a partir de um identificador.</li>
<li>Isso é o equivalente à call stack de um sistema monolítico.</li>
<li>Use padrões de trace ID para gerar os logs.</li>
<li>Use ferramentas de gereciamento (APMs) para visualizar.</li>
</ul>
<h3>Agregando métricas:</h3>
<ul>
<li>Enquanto logs precisam de desenvolvimento, métricas "só" precisam de instrumentação.</li>
<li>Métricas nos permitem saber o que está acontecendo em determinado momento.</li>
<li>Construa ou use dashboards de alto nível para ter uma fácil visão do status atual da aplicação.</li>
<li>Depois, tenha dash boards específicos para cada serviço, com mais detalhes.</li>
</ul>
