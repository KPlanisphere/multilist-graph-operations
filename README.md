# Multilist Graph Operations

This project implements a multilayer graph structure in C++ with various operations to manipulate and traverse the graph. The program includes functions to insert nodes and edges, display the graph, perform breadth-first and depth-first searches, and an option for Kruskal's algorithm (not implemented yet). It also features a menu-driven interface for user interaction.

## Features

- **Insert Node**: Adds a new node to the graph.
- **Insert Edge**: Adds an edge between two nodes.
- **Display Graph**: Prints the adjacency list of the graph.
- **Breadth-First Search (BFS)**: Traverses the graph using BFS starting from a specified node.
- **Depth-First Search (DFS)**: Traverses the graph using DFS starting from a specified node.
- **Menu Interface**: Provides a user-friendly menu to perform the above operations.
- **Placeholder for Kruskal's Algorithm**: An option for Kruskal's algorithm, to be implemented.

## Usage

Compile the program using a C++ compiler and run the executable. You will be presented with a menu to choose from various operations.

### Example Commands

1. **Insert Node**: Prompts the user to enter a value for the new node.
2. **Insert Edge**: Prompts the user to enter the start and end nodes for the edge.
3. **Display Graph**: Displays the adjacency list of the graph.
4. **Breadth-First Search**: Prompts the user to enter the starting node for BFS.
5. **Depth-First Search**: Prompts the user to enter the starting node for DFS.
6. **Kruskal's Algorithm**: Placeholder for future implementation.
7. **Exit**: Terminates the program.

## Code Snippets

### Insert Node
```cpp
void insertarNodo() {
    Nodo aux, new_nodo = new struct nodo;
    cout << "\n VALOR DEL NODO: ";
    cin >> new_nodo->info;
    new_nodo->sig = NULL;
    new_nodo->ady = NULL;
    new_nodo->visitado = false;

    if (head == NULL) {
        head = new_nodo;
    } else {
        aux = head;
        while (aux->sig != NULL) {
            aux = aux->sig;
        }
        aux->sig = new_nodo;
    }
    totalnodos++;
}
```

### Insert Edge
```cpp
void agregarArista(Nodo& aux, Nodo& aux2, Arista& nuevo) {
    Arista saveNoditos;
    if (aux->ady == NULL) {
        aux->ady = nuevo;
        nuevo->destino = aux2;
    } else {
        saveNoditos = aux->ady;
        while (saveNoditos->sig != NULL) {
            saveNoditos = saveNoditos->sig;
        }
        nuevo->destino = aux2;
        saveNoditos->sig = nuevo;
    }
    cout << "\n [!] UNION AGREGADA CORRECTAMENTE [!]";
}
```

### Breadth-First Search

```cpp
void RecorridoAncho(char raiz) {
    queue<Nodo> cola;
    Nodo aux, x, y;
    Arista aux2, ndito = NULL;
    aux = head;
    clearCola(cola);
    clearTrueVisit(aux);

    while (aux != NULL) {
        if (aux->info == raiz) {
            break;
        }
        aux = aux->sig;
    }
    y = head;
    aux->visitado = true;
    cola.push(aux);
    cout << "\n BFS: ";

    while (!cola.empty()) {
        x = cola.front();
        aux2 = x->ady;
        cout << x->info << "  ";
        cola.pop();

        while (x->ady != NULL) {
            ndito = x->ady;
            while (ndito != NULL) {
                while (y != NULL) {
                    if (y->info == ndito->destino->info) {
                        if (y->visitado == false) {
                            y->visitado = true;
                            cola.push(y);
                        }
                    }
                    y = y->sig;
                }
                ndito = ndito->sig;
                y = head;
            }
            x->ady = x->ady->sig;
        }
        x->ady = aux2;
    }
}
```

### Menu Interface

```cpp
void menu() {
    cout << "\n\t - - - - LISTA DE LISTAS - MULTILISTAS - - - -" << endl;
    cout << "\t\t\t   (+ KRUSKAN)\n" << endl;

    cout << " [1] INSERTAR UN NODO" << endl;
    cout << " [2] INSERTAR UNA ARISTA" << endl;
    cout << " [3] MOSTRAR  GRAFO" << endl;
    cout << " [4] RECORRIDO A LO ANCHO" << endl;
    cout << " [5] RECORRIDO A LO PROFUNDO" << endl;
    cout << " [6] KRUSKAN" << endl;
    cout << " [7] SALIR" << endl;

    cout << "\n INGRESE OPCION: ";
}
```

## How to Run

1. Clone the repository:
    ```bash
    git clone https://github.com/KPlanisphere/multilist-graph-operations.git
    ```
2. Navigate to the project directory:
    ```bash
    cd multilist-graph-operations
    ```
3. Compile the code:
    ```bash
    g++ MLista.cpp -o multilist_graph
    ```
4. Run the executable:
    ```bash
    ./multilist_graph
    ```
