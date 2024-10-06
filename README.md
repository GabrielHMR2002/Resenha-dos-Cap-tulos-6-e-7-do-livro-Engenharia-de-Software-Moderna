## Resenha dos Capítulos 6 e 7 do livro Engenharia de Software Moderna 

## 6 Padrões de Projeto: 

Começando o capítulo podemos ver a abordagem da origem dos padrões de projeto no desenvolvimento de software, inspirados nas ideias do arquiteto Cristopher Alexander. Adaptados pela Gang of Four em 1995, esses padrões oferecem soluções reutilizáveis para problemas recorrentes em design de software, promovendo flexibilidade e extensibilidade. Além de facilitar a implementação de sistemas próprios e a compreensão de sistemas de terceiros, os padrões de projeto criaram um vocabulário comum entre desenvolvedores. O texto explora três categorias principais de padrões – criacionais, estruturais e comportamentais – e destaca a importância de projetar sistemas com foco em futuras mudanças, evitando a necessidade de grandes reprojetos. 

O capítulo sobre o padrão Fábrica começa abordando um problema comum em sistemas que precisam criar objetos de diferentes tipos, dependendo de certas condições. No exemplo, as funções estão criando diretamente objetos TCPChannel, o que se torna um problema quando há a necessidade de usar outro protocolo, como UDP, pois o código não está preparado para essa flexibilidade. Aqui, o autor destaca o princípio Aberto/Fechado, e como o código, do jeito que está, violaria essa regra.  

Achei interessante a forma como o padrão Fábrica resolve isso, encapsulando a criação dos objetos dentro de um método estático que faz essa "mágica" de criar os canais de comunicação sem que as funções saibam o que está sendo criado exatamente. Assim, é possível mudar de TCP para UDP de forma simples, alterando apenas o método fábrica. Essa solução é simples e eficiente, além de aplicar o princípio de preferir interfaces a classes concretas, o que eu vejo como uma boa prática para manter o código flexível. 

O padrão Singleton, por outro lado, sempre me pareceu um pouco mais polêmico, e o capítulo deixa isso claro. Ele resolve o problema de ter várias instâncias de uma classe Logger espalhadas pelo código, garantindo que apenas uma única instância exista e seja reutilizada. A ideia faz sentido quando pensamos em um recurso que deve ser único, como o próprio arquivo de log mencionado. Porém, entendo a crítica ao Singleton, principalmente porque ele se assemelha a uma variável global disfarçada, o que pode levar a um acoplamento forte entre as classes. Isso pode complicar bastante os testes automáticos, já que o estado da aplicação pode depender de um Singleton em qualquer parte do código. É um padrão útil, mas acho que deve ser usado com cuidado. 

No capítulo sobre o padrão Proxy, a discussão aborda a introdução de um intermediário entre o cliente e o objeto base, usando a classe BookSearch como exemplo. O conceito é fascinante porque, à medida que a popularidade do serviço de pesquisa de livros cresce, a necessidade de otimizar o desempenho por meio de um sistema de cache se torna evidente. O autor destaca a importância de manter a classe BookSearch coesa e aderente ao Princípio da Responsabilidade Única, evitando misturar a lógica de pesquisa com a implementação do cache. Isso é algo que eu valorizo muito no desenvolvimento, pois a clareza e a separação de responsabilidades em um sistema são fundamentais para a manutenção e escalabilidade. 

A solução proposta, que envolve a utilização de um proxy, é uma maneira inteligente de agregar funcionalidades não-funcionais, como o cache, sem comprometer a integridade da classe original. O proxy serve como um guardião, verificando se o livro já está em cache antes de realizar uma pesquisa mais demorada. Esse modelo não só melhora a performance, mas também permite que a classe BookSearch permaneça focada em suas responsabilidades principais. A ideia de usar interfaces para ocultar a complexidade da implementação é algo que realmente ressoa comigo. Isso promove um desacoplamento que facilita a troca de implementações e a adição de novas funcionalidades sem perturbar o funcionamento do sistema. No geral, o capítulo reforça a importância de padrões de projeto na construção de software robusto e bem estruturado, e essa abordagem me inspira a aplicar essas ideias em meus próprios projetos. 

No capítulo sobre o padrão Adaptador, a análise da situação em que um sistema precisa controlar diferentes projetores multimídia é muito pertinente. O autor utiliza exemplos de projetores de marcas distintas, como Samsung e LG, para ilustrar como as interfaces de controle podem ser incompatíveis devido a métodos e parâmetros diferentes. Essa situação reflete um desafio comum no desenvolvimento de software, onde integramos sistemas de diferentes fornecedores. A proposta de utilizar um adaptador para unificar a interface de controle é uma solução elegante que demonstra como é possível conectar componentes que, à primeira vista, parecem não compatíveis. A implementação da classe AdaptadorProjetorSamsung, que traduz o método turnOn da classe ProjetorSamsung para a interface Projetor, exemplifica como os padrões de design podem facilitar a integração de sistemas existentes sem necessidade de modificar seu código. 

A utilização do padrão Adaptador não apenas simplifica o uso dos projetores, mas também mantém a flexibilidade do sistema, permitindo que novos projetores sejam facilmente integrados por meio de suas próprias classes adaptadoras. Essa abordagem reforça a importância da reutilização de código e a adaptação às mudanças, algo que considero essencial em projetos de software modernos. A forma como o autor apresenta o problema e a solução me fez refletir sobre a aplicação prática desse padrão em projetos que já presenciei. 

Na sequência, a introdução do padrão Fachada fornece uma visão sobre como simplificar a interface de um sistema complexo. O exemplo do interpretador de uma linguagem mostra claramente como a criação de uma classe Fachada pode ocultar a complexidade de interações internas, permitindo que os desenvolvedores utilizem uma interface mais intuitiva e direta. A transformação de várias chamadas de métodos em uma única linha de código ilustra como a Fachada pode não apenas reduzir o esforço de programação, mas também melhorar a legibilidade e a manutenção do código. Essa abordagem ressoa comigo, pois valorizo soluções que reduzem a curva de aprendizado para novos desenvolvedores e promovem uma experiência mais fluida ao interagir com sistemas complexos. Em suma, tanto o padrão Adaptador quanto o Fachada são ferramentas valiosas que facilitam a integração e a interação com sistemas variados, promovendo um design mais limpo e eficiente. 

Avançando um pouco para o próximo capítulo, o autor aborda dois padrões importantes: o Padrão Decorador e o Padrão Strategy, ambos oferecendo soluções para problemas comuns no desenvolvimento de software. 

O Padrão Decorador é uma abordagem muito eficiente para a adição de funcionalidades a classes existentes, evitando a complexidade que vem com o uso excessivo da herança. O exemplo do sistema de comunicação remota ilustra bem esse ponto. Em vez de criar um número insustentável de subclasses para cada combinação de funcionalidades opcionais — como buffers, compactação e logging — o Decorador permite que o cliente adicione essas funcionalidades dinamicamente, por meio de composição. Isso não só simplifica o design, mas também melhora a manutenção do código. A ideia de encapsular as funcionalidades em decoradores e delegar chamadas para os canais subjacentes promove um código mais limpo e modular.  

Por outro lado, o Padrão Strategy é essencial para garantir que classes possam ser estendidas sem a necessidade de modificar seu código fonte. O exemplo da classe MyList, que inicialmente utilizava apenas o algoritmo de ordenação Quicksort, destaca a importância da flexibilidade na escolha dos algoritmos. Com o Strategy, o cliente pode definir e alterar a estratégia de ordenação conforme suas necessidades, respeitando o princípio Aberto/Fechado. Isso é um exemplo claro de como encapsular algoritmos em suas próprias classes e torná-los intercambiáveis pode levar a um design de software mais robusto e adaptável. 

Ambos os padrões promovem uma melhor organização do código e facilitam a manutenção e a extensão de funcionalidades, o que é fundamental em projetos que precisam se adaptar rapidamente às mudanças. A ênfase no uso de composição em vez de herança no Decorador, assim como a capacidade de alternar algoritmos de forma flexível no Strategy, são lições valiosas para qualquer desenvolvedor que deseja criar sistemas escaláveis e de fácil manutenção. Esse capítulo realmente destaca a importância de entender e aplicar esses padrões para melhorar a qualidade do software e a eficiência no desenvolvimento. 

O padrão Observador se destaca como uma solução elegante para a implementação de sistemas que requerem a comunicação entre um sujeito e vários observadores. Um exemplo prático apresentado é o de um sistema de monitoramento de uma estação meteorológica, onde temos a classe Temperatura representando os dados que mudam e as classes TermometroCelsius e TermometroFahrenheit, que servem como visualizadores desses dados. A necessidade de manter a separação entre a lógica do modelo (Temperatura) e a interface de visualização (Termometro) é um ponto crucial, pois essa separação permite uma maior flexibilidade. A frequência com que as interfaces podem mudar — desde a atual interface textual até futuras interfaces web ou mobile — reforça a importância dessa abordagem. 

Ao implementar o padrão Observador, conseguimos evitar o acoplamento excessivo entre os sujeitos e os observadores. Isso é feito através da utilização de uma classe base Subject, que gerencia a lista de observadores e os notifica sempre que ocorre uma mudança de estado. Assim, quando a temperatura é alterada, todos os termômetros associados são automaticamente atualizados. Este mecanismo de notificação não só permite reuso em outras classes como PressaoAtmosferica e Barometro, mas também assegura que o sistema permaneça escalável e fácil de manter. 

A simplicidade e eficácia do padrão Observador estão em sua capacidade de permitir que um sujeito não conheça diretamente seus observadores. Isso promove um design mais limpo e um código que pode ser facilmente expandido com novos tipos de observadores, sem a necessidade de alterações significativas na classe do sujeito. Como tal, o padrão se mostra altamente eficaz para sistemas dinâmicos que requerem notificação em tempo real e interações entre múltiplos componentes. 

Outro padrão relevante discutido é o Template Method, que fornece uma estrutura clara para a implementação de algoritmos com etapas que podem variar. O exemplo utilizado envolve a classe Funcionario, que define um método template para calcular o salário líquido de um funcionário, enquanto permite que subclasses como FuncionarioPublico e FuncionarioCLT implementem os cálculos específicos de descontos. Isso garante que o algoritmo geral permaneça intacto, enquanto as particularidades de cada tipo de funcionário são tratadas nas subclasses. 

Esse padrão é particularmente útil para garantir a consistência em processos comuns, permitindo que partes do código permaneçam estáveis e reutilizáveis, mesmo quando novas subclasses são introduzidas. A implementação de métodos abstratos dentro da classe base, que devem ser definidos pelas subclasses, é uma característica que reforça a ideia de que a lógica básica do algoritmo deve ser compartilhada, enquanto os detalhes são deixados para serem definidos conforme necessário. 

O conceito de inversão de controle mencionado no contexto do Template Method também é importante, pois permite que uma estrutura mais antiga chame métodos de subclasses mais novas. Essa flexibilidade é fundamental em frameworks e sistemas orientados a objetos, permitindo que desenvolvedores adicionem funcionalidades sem modificar o código existente. 

Por fim, o padrão Visitor é apresentado como uma solução para um problema comum em sistemas que operam sobre hierarquias de classes, como a do sistema de estacionamento discutido. Aqui, a classe base Veiculo e suas subclasses Carro, Onibus e Motocicleta são utilizadas para armazenar dados sobre veículos. O desafio surge quando é necessário realizar operações em todos os veículos, como imprimir informações ou persistir dados, sem modificar diretamente as classes das quais essas operações dependem. 

O padrão Visitor permite adicionar novas operações a classes existentes sem modificar suas implementações. Para isso, cada classe de veículo deve implementar um método accept, que aceita um objeto do tipo Visitor e chama o método apropriado. Essa abordagem permite que operações diferentes sejam realizadas sobre diferentes tipos de veículos sem a necessidade de conhecimento prévio do tipo específico, simulando o que se conhece como "double dispatch". 

Com a implementação do padrão Visitor, torna-se possível explorar a estrutura polimórfica do sistema de forma robusta e flexível, já que as operações podem ser adicionadas ou alteradas sem afetar a estrutura das classes de veículo. Assim, o padrão se torna uma ferramenta valiosa para manter o código limpo e adaptável, facilitando a introdução de novas funcionalidades no futuro. 

O capítulo 6 destaca a importância dos padrões de projeto na flexibilidade e adaptabilidade dos sistemas de software. Padrões como Fábrica, Decorador e Strategy permitem personalizar e parametrizar a funcionalidade das classes, facilitando a troca de objetos e a configuração de algoritmos. Contudo, a adoção desses padrões vem com um custo. É crucial analisar se a implementação de um padrão é realmente necessária; por exemplo, questionar se há a necessidade de criar objetos de tipos diferentes ou se algoritmos alternativos serão requeridos.  

Além disso, o uso excessivo de padrões pode levar à "paternite", onde a complexidade do sistema aumenta sem uma justificativa clara. John Ousterhout ressalta que a super-aplicação de padrões pode ser prejudicial, argumentando que nem todo problema precisa ser resolvido dessa maneira. O exemplo de decoradores na abertura de arquivos em Java ilustra bem essa questão, pois, em muitos casos, a implementação de funcionalidades adicionais pode complicar desnecessariamente a solução. Em suma, os padrões de projeto são valiosos, mas sua aplicação deve ser feita com cautela e reflexão sobre a necessidade real em cada situação. 

## 7 Arquitetura 

O capítulo seguinte do livro aborda a arquitetura de software, definindo-a como um projeto em alto nível que foca em componentes maiores, como pacotes e serviços. Ele apresenta duas definições principais: uma que enfatiza a relevância dos componentes para o sistema e outra que destaca decisões de projeto de impacto duradouro, como a escolha da linguagem e do banco de dados, que são difíceis de reverter. 

São discutidos padrões arquiteturais, como Arquitetura em Camadas, MVC e Microsserviços, e a diferença entre padrões e estilos arquiteturais. O capítulo também menciona o debate entre Tanenbaum e Torvalds sobre arquiteturas de sistemas operacionais, ressaltando como decisões arquitetônicas afetam a complexidade e o desempenho a longo prazo. 

Por fim, enfatiza a importância de analisar criticamente as decisões arquitetônicas e evitar a "paternite", ou uso excessivo de padrões, que pode gerar complexidade desnecessária. Uma escolha fundamentada de padrões é essencial para o sucesso do projeto de software. 

Avançando, o livro explora a Arquitetura em Camadas, um dos padrões arquiteturais mais utilizados desde as décadas de 60 e 70. Nesse modelo, as classes são organizadas em camadas hierárquicas, onde uma camada pode interagir apenas com a camada imediatamente inferior. Essa estrutura ajuda a reduzir a complexidade do desenvolvimento, permitindo que o sistema seja dividido em componentes menores. Além disso, a disciplina nas dependências entre as camadas facilita a manutenção e evolução do sistema, tornando mais simples a troca de uma camada por outra ou o reúso de camadas em diferentes contextos. 

A arquitetura em três camadas é uma aplicação comum desse padrão, especialmente em sistemas de informação corporativos. Essa arquitetura é composta pela camada de apresentação, que é responsável pela interação com o usuário, exibindo informações e processando entradas. A seguir, temos a camada de lógica de negócio, que implementa as regras do sistema, garantindo que as operações realizadas atendam às normas estabelecidas. Por fim, a camada de banco de dados armazena os dados manipulados pelo sistema, possibilitando a persistência das informações. 

Em geral, essa arquitetura é distribuída, com a camada de apresentação rodando nos clientes, enquanto as outras camadas operam em um servidor. É importante ressaltar que, embora existam sistemas em duas camadas, onde a interface e a lógica de negócio estão unidas, essa abordagem pode resultar em desvantagens, pois exige que os clientes tenham maior poder de processamento. A proposta de Dijkstra, elaborada em 1968, reafirma a importância de uma estrutura hierárquica em projetos de maior porte, confirmando a relevância da Arquitetura em Camadas na construção de sistemas robustos e escaláveis. 

Seguindo em frente, podemos falar do MVC, na minha opinião, o padrão arquitetural MVC (Model-View-Controller) é uma abordagem que se consolidou ao longo do tempo e continua relevante. Ele nasceu em um momento em que as interfaces gráficas estavam começando a ganhar espaço, lá no final dos anos 70, com o Smalltalk-80, uma das primeiras linguagens orientadas a objetos. O interessante é que, desde o início, o MVC trouxe uma separação clara entre a interface gráfica e a lógica do sistema, o que acabou se mostrando uma solução inteligente para organizar as responsabilidades dentro de um software. 

No modelo MVC, o sistema é dividido em três partes fundamentais: a Visão, que cuida da interface com o usuário; o Controlador, que age como intermediário, interpretando as interações do usuário e decidindo o que deve ser feito; e o Modelo, que guarda os dados e as regras de negócio. Essa divisão é muito prática porque permite que cada parte seja desenvolvida e modificada sem interferir nas outras. Por exemplo, se quisermos mudar a interface, podemos fazê-lo sem mexer na lógica dos dados. 

Uma das grandes vantagens do MVC é essa possibilidade de separar o trabalho. Desenvolvedores que trabalham com a parte visual, o front-end, podem se concentrar na interface e na experiência do usuário, enquanto outros podem focar na lógica de negócio e na manipulação dos dados, sem precisar entender a fundo a parte de apresentação. Isso faz o processo de desenvolvimento mais eficiente e organizado. 

Além disso, o MVC permite que um mesmo conjunto de dados (o Modelo) seja exibido de maneiras diferentes, o que é uma ideia muito boa. Imagine um relógio, por exemplo. Ele pode ser mostrado como um relógio analógico ou digital, mas a fonte dos dados — a hora e os minutos — é a mesma. Essa flexibilidade de poder ter múltiplas visões para um mesmo modelo é algo que torna o padrão ainda mais útil. 

Outro ponto que considero importante é a testabilidade que o MVC proporciona. Como o Modelo está separado da Visão, fica mais fácil testar a lógica do sistema sem precisar se preocupar com a interface gráfica, que muitas vezes é mais difícil de automatizar em testes. Isso traz uma vantagem clara quando o assunto é manutenção e evolução do sistema, pois fica mais simples identificar e corrigir problemas na lógica de negócio. 

O que também chama atenção no MVC é como ele influenciou as arquiteturas mais recentes, especialmente com a chegada da web nos anos 2000. Muitos frameworks populares, como Spring, Django e Ruby on Rails, adaptaram o conceito de MVC para sistemas web, organizando os componentes em Visão, Controlador e Modelo, o que lembra um pouco a arquitetura de três camadas. No entanto, apesar das semelhanças, o MVC traz essa abordagem mais voltada para o controle e apresentação dos dados, enquanto a arquitetura em três camadas é mais focada na separação lógica entre a interface, a lógica de aplicação e a persistência de dados. 

Em resumo, considero o MVC uma arquitetura que, além de bem pensada, é extremamente flexível e eficiente em alguns casos. Ela permite uma organização clara do código e favorece a especialização no desenvolvimento, além de proporcionar uma manutenção mais tranquila e um sistema mais fácil de testar. Mesmo com o avanço da tecnologia e o surgimento de novas abordagens, o MVC se mantém relevante, especialmente pela sua capacidade de adaptação a diferentes tipos de sistemas e plataformas. 

Seguindo em frente, os microsserviços surgiram como uma solução eficaz para os desafios de escalabilidade e lançamento frequente de software, algo difícil de se alcançar com uma arquitetura monolítica. Mesmo usando metodologias ágeis, como Scrum, os sistemas monolíticos tendem a criar gargalos na produção, já que todos os módulos rodam juntos em um único processo. Isso aumenta o risco de uma mudança em um módulo afetar outros, o que leva as empresas a adotarem processos rigorosos e demorados para lançar novas versões. 

O grande diferencial dos microsserviços é que eles permitem que cada módulo seja executado de forma independente, em processos separados. Com isso, as chances de interferência entre os módulos caem, e as equipes podem evoluir seus serviços de forma mais ágil e isolada, facilitando o lançamento contínuo de novas funcionalidades. Além disso, microsserviços oferecem uma escalabilidade muito mais eficiente, já que podemos replicar apenas os módulos com problemas de desempenho, sem a necessidade de duplicar todo o sistema. 

Outra vantagem importante é a flexibilidade tecnológica, onde cada microsserviço pode ser desenvolvido com diferentes linguagens e tecnologias, conforme as necessidades específicas. Além disso, eles também aumentam a tolerância a falhas: se um serviço cair, os outros continuam funcionando, o que não acontece em sistemas monolíticos. Na minha visão isso são pontos muito importantes e relevantes. 

A computação em nuvem tornou os microsserviços ainda mais acessíveis, permitindo que empresas escalem seus serviços rapidamente sem a necessidade de infraestrutura própria. Isso tudo reflete a tendência de que as arquiteturas de software sigam a organização das equipes, como aponta a Lei de Conway. 

Em uma arquitetura de microsserviços, a independência entre os serviços deve se estender aos dados que eles gerenciam. Ou seja, cada microsserviço deve ser responsável pelos dados que utiliza para oferecer seu serviço, evitando o compartilhamento de um banco de dados comum entre diferentes serviços. Isso é fundamental porque o uso de um banco de dados compartilhado pode gerar gargalos que dificultam a evolução do sistema. 

Se cada microsserviço possuir seu próprio banco de dados, as equipes responsáveis por eles poderão fazer alterações e evoluções de forma mais ágil, sem depender de um administrador central para aprovar mudanças no banco. Isso reduz a burocracia e acelera a tomada de decisões, favorecendo a autonomia das equipes. Contudo, implementar essa independência de dados pode aumentar a complexidade do sistema, especialmente quando há a necessidade de garantir que operações que envolvem múltiplos bancos de dados sejam realizadas de forma atômica. 

Sendo assim, podemos comentar da Arquiteturas orientadas, nela as mensagens utilizam um intermediário, conhecido como fila de mensagens, para mediar a comunicação entre clientes e servidores. Nessa abordagem, os clientes atuam como produtores, inserindo mensagens na fila, enquanto os servidores são os consumidores, retirando as mensagens para processá-las. Essa comunicação é assíncrona, permitindo que clientes continuem suas operações após enviar as mensagens, sem esperar a resposta imediata dos servidores. 

A fila de mensagens segue o princípio FIFO (First In, First Out), garantindo que as mensagens sejam consumidas na ordem em que foram inseridas. É fundamental que esse serviço seja robusto, com alta disponibilidade e persistência, de modo que, mesmo em caso de falhas no servidor, as mensagens não sejam perdidas. 

Esse modelo proporciona dois tipos de desacoplamento: no espaço e no tempo. O desacoplamento no espaço significa que clientes e servidores não precisam se conhecer, enquanto o desacoplamento no tempo permite que eles operem independentemente, sem necessidade de estarem disponíveis simultaneamente. Isso torna as arquiteturas baseadas em mensagens flexíveis e escaláveis, pois múltiplos servidores podem consumir mensagens da mesma fila. 

Como exemplo, uma empresa de telecomunicações pode utilizar uma fila de mensagens para integrar seus sistemas de vendas e engenharia. Quando uma venda é realizada, uma mensagem com os detalhes do serviço contratado é enviada à fila, e o sistema de engenharia a processa para ativar o serviço. Isso garante que, mesmo que o sistema de engenharia esteja sobrecarregado, o sistema de vendas continue funcionando, sem esperar pela ativação imediata do serviço. 

O capítulo aborda a arquitetura de software, definindo-a como decisões de projeto de alto nível que influenciam a estrutura e o comportamento do sistema. Padrões como Arquitetura em Camadas, MVC e Microsserviços são discutidos, destacando suas vantagens em termos de separação de responsabilidades, flexibilidade e escalabilidade. Também são explorados os desafios e complexidades que surgem com o uso inadequado de padrões arquiteturais. 

No final, é discutido o anti-padrão "big ball of mud", que descreve sistemas sem uma organização clara, dificultando sua manutenção e escalabilidade. O exemplo de um sistema bancário ilustra como essa má arquitetura pode gerar dificuldades significativas na evolução e no gerenciamento de software, mesmo com tentativas de mitigação. 
