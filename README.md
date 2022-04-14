# Clean architecture - Android


There are some important questions to make when you begin the study of the clean architecture, below are a few of them focusing the Android app development.

- Why it’s important to use architecture patterns in software
- What *Clean Architecture* is
- What *SOLID* principles of development are
- When to use Clean Architecture and SOLID principles
- How to implement Clean Architecture on Android

The common goal to Software Architecture Study is manage the complexity of the applications in general.

<img src="https://github.com/CaioCrevelaro/clean-architecture-android/blob/master/assets/images/clean-architecture-graph.png" alt="clean-architecture-graph" style="zoom: 50%;" />

Considering the observation starts from the outer border of the graph, farther the circle, most abstract is the structure. The structures shown at the graph above were presented at the table below according to the Abstraction Principle that specifies the farther circle should contain business logic whereas the closer circle should contain the implementation details.



| Blue Layer (most concrete) | Green Layer | Red Layer | Yellow Layer (most abstract) |
| :------------------------: | :---------: | :-------: | :--------------------------: |
|          Devices           | Controllers | Use Cases |           Entities           |
|       DB (Data base)       |  Gateways   |           |                              |
|    External interfaces     | Presenters  |           |                              |
|    UI (User interface)     |             |           |                              |
|            Web             |             |           |                              |



It's significant to point out the "Dependency Rule" of the Clean Architecture says that each circle is related only and just only to its nearest inward circle.

```mermaid
graph TD

classDef orange fill:#FFA500,stroke:#000000,stroke-width:2px,color:#000000;
classDef yellow fill:#FFD700,stroke:#000000,stroke-width:2px,color:#000000;
classDef green fill:#BADA55,stroke:#000000,stroke-width:2px,color:#000000;
classDef purple fill:#8A2BE2,stroke:#FFF,stroke-width:2px,color:#FFF;
classDef blue fill:#326CE5,stroke:#FFF,stroke-width:2px,color:#FFF;
classDef gray fill:#DDDDDD,stroke:#000000,stroke-width:2px,color:#000000;

a11(ACTIVITY/<br>FRAGMENT):::yellow;
a21(VIEWMODEL):::green;
a31(USECASE):::orange;
a41(REPOSITORY):::purple;
a51[(CACHE)]:::gray;
a52(API):::blue;


a11 --> a21 --> |LiveData| a31 --> a41;
a41 --> a51;
a41 --> a52;

```

<header>
    <nav>
    </nav>
</header>


<details class = "references">
    <summary>Referências</summary>
    <ul>
        <li>
            <a href = "https://books.google.com.br/books?id=CBQ-EAAAQBAJ&printsec=frontcover&hl=pt-BR#v=onepage&q&f=false">The Official Guide to Mermaid.js</a>
        </li>
        <li>
            <a href = "https://kubernetes.io/docs/contribute/style/diagram-guide/">Diagram guide (Kubernetes)</a>
        </li>
    <ul>
</details>

# _Graphs in Markdown (Mermaid)_

<hr>

### Shapes

```mermaid
graph LR


id1{{Hexagon shape}}
id2((Circle shape));
id3(Rounded rectangle shape);
id4[Rectangle shape];
id5{Diamond shape};
id6[[Subroutine shape]];
id7[(Database shape)];
id8([Stadium shape]);
id9>Assymetric shape];
id10[/Paralelogram shape/];
id11[\Alternate paralelogram shape\];
id12[/Trapezoid shape\];
id13[\Alternate trapezoid shape/];


%% Flow %%

id2 --> id3 --> id9 --> id11;
id2 --> id4 --> id8 --> id12;
id2 --> id13 --> id5 --> id10;
id1 --> id2;
id1 ---> id6;
id6 --> id7;


```

### Decision points

```mermaid
graph TD

id1(You want to eat cookies);
id2{There is any <br> cookie at your place?}
id3(Go get your cookie);
id4(Enjoy your meal);

id5{Would you like to go <br> to supermarket?};
id6(Go to supermarket);
id7(Buy cookies);
id8(Fill sadness);

id1 --> id2;
id2 -. Yes .-> id3;
id3 --> id4;

id2 -- No --> id5;
id5 -. Yes .-> id6;
id6 --> id7;
id7 --> id4;

id5 -- No ---> id8;

```

### Graphs

#### - _graph LR_

<br>

```mermaid
graph LR 

%% Use can use 'graph' or 'flowchart' %%

id1((A));
id2((B));
id3((C));
id4((D));
id5((E));

id1 --> id2;
id2 --> id3;
id3 --> id4;
id4 --->id5;

id1 --> id4
id3 --> id2

``` 

#### - _graph RL_

<br>

```mermaid
graph RL

id1((A));
id2((B));
id3((C));
id4((D));
id5((E));

id1 --> id2;
id2 --> id3;
id3 --> id4;
id4 ---> id5;

id1 --> id4
id3 --> id2

```

#### - _graph TD_

<br>

```mermaid
graph TD

id1((A));
id2((B));
id3((C));
id4((D));
id5((E));

id1 --> id2;
id1 --> id3;
id1 ---> id4;

id3 --> id4;
id3 --> id5

```

#### - _graph BT_

<br>

```mermaid
graph BT

id1{{Hexagon shape}}
id2((Circle shape));
id3(Rounded rectangle shape);
id4[Rectangle shape];
id5{Diamond shape};
id6[[Subroutine shape]];
id7[(Database shape)];
id8([Stadium shape]);
id9>Assymetric shape];
id10[/Paralelogram shape/];
id11[\Alternate paralelogram shape\];
id12[/Trapezoid shape\];
id13[\Alternate trapezoid shape/];

id2 --> id3 --> id9 --> id11;
id2 --> id4 --> id8 --> id12;
id2 --> id13 --> id5 --> id10;
id1 --> id2;
id1 ---> id6;
id6 --> id7;

```

### Chaining

<br>

```mermaid
graph TD

id1((A));
id2((B));
id3((C));
id4((D));
id5((E));

id1 --> id2 & id3 & id4 & id5;

```

<br>

```mermaid
graph TD

id1((A));
id2((B));
id3((C));
id4((D));
id5((E));
id6((F));
id7((G));
id8((H));
id9((I));

id1 & id2 --> id3 & id4 & id5 --> id6 & id7 & id8 & id9;

```

### Edges

<br>

```mermaid
graph LR

a((A)) --> b((B))

```

<br>

```mermaid
graph LR

a((A)) --- b((B))

```

<br>

```mermaid
graph LR

a((A)) --x b((B))

```

<br>

```mermaid
graph LR

a((A)) --o b((B))

```

<br>

```mermaid
graph LR

a((A)) <==> b((B))

```

### Thickness 

```mermaid
graph LR

    a1((A)) -.- a2((B));

    a3((C)) -.-> a4((D));

```

### Subgraphs

<br>

```mermaid
graph RL

id1((A));
id2((B));
id3((C));
id4((D));
id5((E));

subgraph Subgráfico 1
    id1 --> id3;
    id1 --> id4;
    end

subgraph Subgráfico 2
    F --> id3 --> G
    end

id1 --> id2 --> F --> G --> id4;
id3 --> id4;
id3 --> id5

```

## Test

```mermaid
graph LR

a1((A));
click a1 "https://google.com" "tooltip" _self

a2((B));

a1 --> a2

```
















