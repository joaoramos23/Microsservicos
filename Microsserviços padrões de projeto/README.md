<h1>Microsserviços: padrões de projetos</h1>

Como funciona a Web:
- A internet funciona através de um protocolo conhecido como HTTP.

Problemas de uma aplicação monolitica: 
- Demora no deploy.
- Falhas podem derrubar o sistema todo.
- 1 projeto = 1 tecnologia.

Deploy: significa enviar mudanças ou atualizações de um ambiente de implantação para outro, podendo ser o principal ou algum intermediário.

Arquitetura de microsserviços:
- Abordagem arquitetônica e organizacional do desenvolvimento de software na qual o software cosiste em pequenos serviços independentes que se comunicam usando API's bem definidas. 
- Serviços pertencem a pequenas equipes autossuficientes.

Vantagens microsserviços:
- Projetos independentes = tecnologias independentes.
- Falha em 1 serviço é isolada.
- Deploys menores e mais rápidos.

Desvantagens microsserviços:
- Maior complexidade de desenvolvimento e infra.
- Debug mais complexo.
- Comunicação entre os serviços deve ser bem pensada.
- Diversar tecnologias pode ser um problema.
- Monitoramento é crucial e mais complexa.

Tipos de microsserviços:
- Data service.
- Business service.
- Translation service.
- Edge service.

Serviços de domínio:
- Domain-driven Design.
- Comece modelando seu domínio, não pensando na persistência.
- Avalie as ações que serçao disponibilizadas.
- Construa o serviço, pensando primeiro no cantrato.
- REST e RPC podem andar juntos.

Serviços de negócio:
- Em determinados momentos as operações precisam de mais de um modelo do nosso domínio para serem corretamente reporesentadas em um serviço.
- Processo do dominhio do negócio:
	- Provem uma funcionalidade do negócio de mais alto nível.
	- Permite encpsular domínios relacionados.
- Criando um serviço de negócio:
	- Identifique o processo que você pretende expor.
	- Identifique os domínios que serão necessário nesse serviço.
	- Defina a API que será utilizada, focando no domínio e não nos dados.
	- Consuma serviços de domínio para executar os processos.

Strangler pattern:
- Quebrar um monolito, tirando as funcionalidades dele.
- Podemos começar isolando os dados.
- Ou podemos começar isolando o domínio.

Sidecar pattern:
- Determine o processo comum.
- Construa um módulo compartilhável.
- Aplique esse sidecar nos serviços que precisam dele.

API Gateway:
- Problema: Clientes acessando livremente os serviços geram caos.
- Gateway fornece um proxy, uma fachada, para as necessidades reais.
- Desvantagem: Esse portão de entrada pode ser tornar um ponto central de falha.

Comportamentos do Gateway:
- Simplesmente autorizar e redirecionar os requests.
- Uso de Decorator para adicionar informações necessárias aos requests.
- Limitar acesso ou conteúdo trafegado.

 Process aggregator pattern:
- Serviços de negócio agregam serviços de domínio.
- Process aggreagatros agregam serviços de negócio.
- Agragadores fazem as chamadas para os serviços necessários e montam a respota correta.
- Pode (e deve) ter lógica de processamento.

Construindo um agregador:
- Defina um novo modelo para representar os dados agregados.
- A partir deste modelo, pense na API que fornecerá as operações.

Edge pattern:
- Gateway específico para determinados(s) clientes(s).
- Foco nas necessidades reais de determinados clientes.

Construindo uma ponta:
- Identifique o cliente e suas necessidades.
- Construa contratos específicos para o cliente.
- Modifique os dados que são transferidos para garantir a otimização do processo.
- Existe a possibilidade de ter apenas Edges.

Single service database:
- Problema: Escalabilidade do serviço e do banco são fortemente relacionados.
- Solução: Cada serviço (que precisar) terá seu próprio banco de dados.

CQRS(Command Query Responsibility Segregation):
- Com leitura e escrita separados, cada parte pode realizar operações mais complexas.
- O modelo de leitura pode ter informações agregadas de outros domínios.
- O modelo de escrita pode ter dados sendo automaticamente gerados.
- Aumenta a complexicdade de um sistema.

Asynchronous eventing:
- Determinados problemas NÂO PODEM ser resolvidos na hora (em tempo real).
- Um serviço emite um evento que será tratado em seu devido tempo.
- Tecnologias como mensagerias e serviços de stream de dados brilham.

Agregando logs:
- Formatos de log devem ser compartilhados entre os serviços.
- Uma taxonomia comum deve ser compartilhada.
- Logs de monolitos são agregados por padrão.
- Parte da tarefa de agregação pode ser o parsing dos logs para categorizar corretamente.

Rastreando chamadas:
- Uma parte importante de realizar logs é rastrear as chamadas de uma execução.
- Devemos poder reconstruir uma operação a partir de um identificador.
- Isso é o equivalente à call stack de um sistema monolítico.
- Use padrões de trace ID para gerar os logs.
- Use ferramentas de gereciamento (APMs) para visualizar.


Agregando métricas:
- Enquanto logs precisam de desenvolvimento, métricas "só" precisam de instrumentação.
- Métricas nos permitem saber o que está acontecendo em determinado momento.
- Construa ou use dashboards de alto nível para ter uma fácil visão do status atual da aplicação.
- Depois, tenha dash boards específicos para cada serviço, com mais detalhes.
