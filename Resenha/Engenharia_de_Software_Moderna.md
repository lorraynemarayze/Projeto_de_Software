# Resenha dos Capítulos 6 e 7 do Livro: “Engenharia de Software Moderna”
> _Lorrayne Marayze Silva de Oliveira_

Nesta resenha, serão analisados os capítulos 6 e 7 do livro "Engenharia de Software Moderna", com foco nos padrões de projeto e na arquitetura de software. Serão explorados os principais conceitos, vantagens e desafios de cada abordagem, além de suas aplicações no desenvolvimento de software.

## Capítulo 6: Padrões de Projeto

Neste capítulo sobre Padrões de Projeto, a introdução explora a origem dos padrões, inspirados por Cristopher Alexander, que os aplicou inicialmente à arquitetura civil. A adaptação para o desenvolvimento de software foi feita por Erich Gamma e seus colegas no livro "Design Patterns", em 1995. A ideia central é resolver problemas recorrentes de projeto de software, oferecendo soluções genéricas e reutilizáveis, que acabam formando um vocabulário comum entre desenvolvedores.

O capítulo destaca que os padrões de projeto são úteis em dois cenários principais: ao implementar sistemas próprios e ao trabalhar com sistemas de terceiros. Ao adotar um padrão, o desenvolvedor aproveita soluções já testadas, o que facilita a criação de sistemas flexíveis e adaptáveis a mudanças futuras, conforme defendido pela Gangue dos Quatro.

Os autores introduzem dois dos padrões mais conhecidos: o Factory e o Singleton. O padrão Factory é descrito como uma solução para a criação de objetos de maneira flexível, permitindo que diferentes tipos de objetos sejam instanciados conforme a necessidade, sem que o código precise conhecer os detalhes das classes concretas. Já o padrão Singleton é explicado como uma forma de garantir que apenas uma instância de uma classe seja criada, sendo útil para recursos que devem ser únicos, como um logger, mas alertando para seu uso abusivo.

O capítulo também menciona a divisão dos padrões em três categorias: criacionais, estruturais e comportamentais. Essas categorias cobrem diferentes aspectos da criação de objetos, composição de classes e interação entre elas, respectivamente. Em resumo, a importância dos padrões de projeto vai além de fornecer soluções prontas; eles criam uma linguagem comum entre os desenvolvedores e garantem maior flexibilidade nos sistemas desenvolvidos.

O padrão Proxy, explica como usar um objeto intermediário para adicionar funcionalidades a um objeto base sem alterar sua implementação. No exemplo apresentado, o sistema de busca de livros precisa de um cache para melhorar o desempenho sem modificar a classe original `BookSearch`. Para isso, é criado um `BookSearchProxy`, que implementa a interface `BookSearchInterface` e atua como intermediário entre os clientes e o objeto base. O proxy verifica se o livro já está no cache antes de buscar na fonte original. Esse padrão garante que a responsabilidade de implementar o cache fique separada da lógica de pesquisa de livros, promovendo coesão e aderência ao Princípio da Responsabilidade Única. Além disso, o uso de interfaces permite que o cliente não saiba se está lidando com o proxy ou com o objeto base, mantendo o código flexível e extensível. Um dos pontos importantes do padrão é que ele pode ser aplicado para outras finalidades, como controlar o acesso a recursos ou otimizar o uso de memória.

No contexto de Engenharia de Software, essa abordagem é útil para evitar a complexidade e a manutenção de código quando diferentes funcionalidades precisam ser adicionadas a um sistema já em uso.

O capítulo 6.8 trata do Padrão de Projeto *Strategy*, e começa com o problema de uma classe `MyList` que está presa ao algoritmo de ordenação *Quicksort*. No entanto, os clientes desejam flexibilidade para escolher outros algoritmos de ordenação, o que leva à necessidade de abrir a classe para novos algoritmos sem alterar seu código. Para resolver isso, o *Strategy* é introduzido como uma forma de encapsular e tornar intercambiáveis diferentes algoritmos.

A ideia principal é que o algoritmo de ordenação seja separado da lógica da lista, permitindo que diferentes estratégias possam ser usadas sem modificar a classe original. Isso é feito ao transformar o algoritmo em um atributo configurável com um método *set*. Assim, o método `sort` passa a delegar a tarefa de ordenar para o algoritmo definido pela estratégia atual.

O código fornecido exemplifica como isso é implementado em Java, com classes abstratas para os algoritmos e suas implementações concretas, como *QuickSort* e *ShellSort*. Esse padrão promove o princípio *Aberto/Fechado*, permitindo a extensão do sistema sem mudanças no código existente, o que melhora a flexibilidade e manutenção.

Em seguida, o capítulo 6.9 aborda o Padrão de Projeto *Observador*, utilizando o exemplo de uma estação meteorológica que monitora a temperatura e atualiza termômetros quando há mudanças. O problema é que não se deseja acoplar a classe de modelo (Temperatura) à interface (Termômetro), já que a interface pode variar. O *Observador* soluciona esse problema ao criar uma relação de um-para-muitos, onde a classe de modelo (sujeito) notifica seus observadores quando seu estado muda.

O código exemplifica a implementação, onde *Temperatura* herda de uma classe *Subject*, que gerencia a adição de observadores e a notificação. A classe *TermometroCelsius* implementa a interface *Observer* e reage às mudanças de temperatura por meio do método `update`. Esse padrão permite que o sistema seja facilmente expandido com novos tipos de termômetros e outras medições, como pressão atmosférica e umidade.

No geral, esses dois padrões (Strategy e Observador) exemplificam maneiras de lidar com a flexibilidade em sistemas orientados a objetos, permitindo que componentes sejam modificados ou estendidos sem afetar o restante do código, promovendo uma arquitetura mais modular e de fácil manutenção.

No capítulo "Outros Padrões de Projeto", são apresentados dois padrões de projeto: Iterador e Builder. O padrão Iterador é útil para percorrer estruturas de dados sem conhecer o tipo concreto, utilizando métodos como `hasNext()` e `next()`. Isso torna possível a navegação por diferentes coleções de dados de maneira uniforme, permitindo múltiplas iterações simultâneas na mesma estrutura.

Já o padrão Builder é introduzido como uma solução para a criação de objetos com muitos atributos, sendo alguns opcionais. Ele evita a sobrecarga de construtores e oferece uma alternativa mais clara e organizada por meio de métodos `set`, que indicam quais atributos estão sendo configurados no momento da criação do objeto. Isso resolve o problema de confusão que poderia ocorrer ao tentar utilizar vários construtores ou `setters` diretamente na classe principal, mantendo o encapsulamento adequado. Um exemplo desse uso é aplicado à classe `Livro`, demonstrando como o Builder facilita a instância desses objetos.

Na sequência, o capítulo "Quando Não Usar Padrões de Projeto?" alerta para o uso exagerado de padrões, ressaltando que sua aplicação deve ser criteriosa. Por exemplo, o padrão Factory é útil quando é necessário criar diferentes tipos de objetos, mas pode ser desnecessário se o uso do operador `new` for suficiente. Da mesma forma, o padrão Strategy é vantajoso quando há necessidade de alternar algoritmos em uma classe, mas não deve ser implementado se essa variação não for necessária. O capítulo reforça a importância de avaliar cuidadosamente a real necessidade de um padrão, evitando o fenômeno da "paternite", onde o excesso de padrões adiciona complexidade ao projeto sem benefícios reais.

A discussão finaliza com uma crítica ao uso do padrão Decorator na abertura de arquivos em Java, como exemplificado com classes como `FileInputStream` e `BufferedInputStream`, que, de acordo com o autor, poderiam ser simplificadas em uma única classe, evitando complexidade desnecessária.

## Capítulo 7: Arquitetura

O capítulo sobre arquitetura de software introduz o conceito de que a arquitetura envolve as decisões de design mais importantes em um sistema, aquelas que dificilmente podem ser revertidas. A arquitetura não se trata apenas da organização de classes, mas de componentes maiores, como módulos e camadas. O capítulo aborda também diferentes padrões arquiteturais, como Arquitetura em Camadas, MVC, e Microsserviços, destacando como cada um resolve problemas específicos e as relações entre os componentes de um sistema.

Ao discutir a Arquitetura em Camadas, o capítulo explica como ela organiza sistemas em módulos hierárquicos, onde uma camada superior usa os serviços da camada inferior, facilitando a manutenção e evolução do sistema. Esse padrão tem exemplos claros na área de redes, com protocolos como HTTP e TCP, que seguem essa lógica hierárquica.

O padrão MVC é apresentado como uma solução para separar a interface de usuário da lógica de negócio e da manipulação de dados, o que torna a aplicação mais organizada e fácil de modificar. Já a Arquitetura de Microsserviços é explorada no contexto de sistemas distribuídos, onde a flexibilidade e o desacoplamento entre os serviços são vantajosos, mas trazem desafios como a complexidade de comunicação entre os componentes.

O capítulo também apresenta outros padrões, como o uso de Filas de Mensagens e o modelo Publish/Subscribe para garantir escalabilidade. Além disso, é discutido um exemplo de anti-padrão, conhecido como "big ball of mud", que ocorre quando a arquitetura se torna desorganizada e difícil de gerenciar. Ao final, o capítulo destaca a importância de tomar decisões arquiteturais adequadas desde o início, já que essas escolhas podem ter impactos duradouros na eficiência e evolução do sistema.

A arquitetura em três camadas, abordada no capítulo, é uma forma bastante utilizada em sistemas corporativos. Ela divide a aplicação em três partes: a camada de interface com o usuário, que lida com a interação e apresentação; a camada de lógica de negócios, que implementa as regras da aplicação; e a camada de banco de dados, onde são armazenados os dados. Essa separação permite uma organização mais clara e facilita o desenvolvimento distribuído, em que as camadas podem ser executadas em diferentes máquinas.

Na prática, isso traz vantagens como a possibilidade de distribuir o processamento entre o cliente e o servidor, o que otimiza a execução de tarefas. No entanto, também há a opção de uma arquitetura em duas camadas, onde a lógica e a interface são combinadas, mas isso exige maior capacidade de processamento do cliente.

Além da arquitetura em três camadas, o capítulo aborda o padrão MVC, que surgiu no final da década de 70 e tem foco em interfaces gráficas. O MVC também separa a aplicação em três partes: a Visão (interface gráfica), o Modelo (dados e regras de negócio) e o Controlador (gerenciamento de eventos). A diferença principal entre as duas arquiteturas está no foco: enquanto a arquitetura em três camadas organiza a aplicação como um todo, o MVC se concentra na separação das responsabilidades dentro da interface.

Uma parte interessante foi a relação entre o MVC e as aplicações web modernas, como as SPAs (Single Page Applications), que utilizam frameworks como Vue.js para proporcionar uma experiência mais interativa e rápida ao usuário. Com SPAs, a comunicação entre o servidor e o cliente é assíncrona, o que elimina a necessidade de recarregar a página inteira sempre que ocorre uma interação.

Esse capítulo, portanto, apresenta uma visão prática e histórica dessas arquiteturas, mostrando como a evolução das tecnologias moldou a forma como os sistemas são desenvolvidos, destacando a importância da separação de responsabilidades para facilitar o desenvolvimento e a manutenção de sistemas complexos.

No capítulo 7.4, o autor aborda a transição de arquiteturas monolíticas para microsserviços, destacando as vantagens e desafios desse modelo. O texto começa explicando que, apesar de muitas empresas adotarem metodologias ágeis, elas frequentemente enfrentam gargalos devido à natureza monolítica de seus sistemas. Essa arquitetura pode causar problemas, pois as mudanças em um módulo podem impactar outros, gerando riscos de falhas e a necessidade de processos rigorosos para lançamentos de novas versões.

A proposta dos microsserviços é desmembrar o sistema em processos independentes, permitindo que cada módulo opere sem a possibilidade de interferência direta nos dados dos outros. Isso não apenas reduz o risco de bugs, mas também torna o desenvolvimento e a implementação de novas funcionalidades mais ágeis, uma vez que cada equipe pode gerenciar suas próprias atualizações sem depender de um processo centralizado.

Além disso, a escalabilidade é destacada como um benefício importante. Com microsserviços, é possível replicar apenas os componentes que apresentam problemas de desempenho, ao contrário do que acontece com monolitos, que exigem a replicação de todo o sistema. Isso permite uma abordagem mais eficiente ao lidar com a carga de trabalho e a performance.

O capítulo também menciona a autonomia dos microsserviços em relação às tecnologias utilizadas, permitindo que diferentes módulos possam ser desenvolvidos com linguagens e frameworks variados, conforme as necessidades específicas. Isso contribui para um sistema mais flexível e inovador.

Entretanto, o texto alerta que a adoção de microsserviços traz uma complexidade adicional. A comunicação entre serviços requer o uso de protocolos de rede, o que pode aumentar a latência. Além disso, a gestão de dados deve ser feita de forma autônoma por cada microsserviço, evitando o compartilhamento de bancos de dados que pode criar gargalos.

Por fim, são apresentados alguns desafios associados aos microsserviços, como a complexidade da comunicação entre processos distribuídos e a necessidade de garantir transações atômicas em operações que envolvem múltiplos bancos de dados. Essas considerações são cruciais para entender se a migração para microsserviços é a escolha certa para uma determinada aplicação.

No capítulo 7.5, é abordado o conceito de Arquiteturas Orientadas a Mensagens, que se baseiam na comunicação entre clientes e servidores através de um serviço intermediário responsável por gerenciar filas de mensagens. Essa arquitetura apresenta os clientes como produtores de mensagens e os servidores como consumidores, utilizando uma estrutura FIFO (first in, first out) para garantir que as mensagens sejam processadas na ordem em que foram enviadas.

Uma característica importante dessas arquiteturas é a comunicação assíncrona. Uma vez que uma mensagem é colocada na fila, o cliente pode continuar com suas atividades sem precisar esperar pela resposta do servidor. Essa abordagem requer que o serviço de mensagens seja confiável e capaz de armazenar dados de forma persistente para evitar perdas em caso de falhas.

O capítulo também destaca o desacoplamento proporcionado por essas arquiteturas, tanto no espaço quanto no tempo. Isso significa que os clientes e servidores podem evoluir de maneira independente, já que não precisam conhecer uns aos outros, e também podem operar sem a necessidade de estarem online simultaneamente. Essas características são vantajosas para equipes de desenvolvimento, permitindo que trabalhem de forma mais autônoma.

Outro ponto mencionado é a escalabilidade das soluções baseadas em filas de mensagens. Ao adicionar mais servidores para consumir mensagens da mesma fila, é possível aumentar a capacidade de processamento do sistema. O exemplo de uma empresa de telecomunicações ilustra como esse tipo de arquitetura pode facilitar a comunicação entre diferentes sistemas, mesmo que não em tempo real.

O capítulo também introduz as arquiteturas publish/subscribe, onde as mensagens são denominadas eventos. Nessa abordagem, um publicador gera eventos que são enviados a assinantes interessados. Isso também promove o desacoplamento, permitindo que os sistemas operem de maneira mais flexível e resiliente. O exemplo de uma companhia aérea demonstra como essa arquitetura pode ser aplicada na prática, integrando diferentes sistemas que precisam ser notificados sobre eventos relevantes.

## Conclusão
Nos capítulos 6 e 7 do livro "Engenharia de Software Moderna", os autores explicam bem os padrões de projeto e a arquitetura de software, utilizando muitos exemplos práticos que ajudam a entender como essas técnicas podem ser aplicadas. As soluções apresentadas nos exemplos mostram maneiras de resolver problemas comuns que surgem no desenvolvimento de sistemas. Esses capítulos reforçam a importância de escolher as abordagens certas para cada situação e como a aplicação correta de padrões pode melhorar a eficiência e a manutenção do software. No final, a resolução apresentada deixa claro como o uso adequado dessas técnicas impacta diretamente na qualidade e na escalabilidade dos sistemas.

**Referência**

Engenharia de Software Moderna. Disponível em: <https://engsoftmoderna.info/>. Acesso em: 09 out. 2024.
