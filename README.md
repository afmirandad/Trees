# Árbol Binario — Explicación paso a paso y ejemplo en C

Este repositorio contiene una explicación paso a paso sobre qué es un árbol binario y un ejemplo en C (`tree.c`) que implementa las operaciones básicas.

## ¿Qué es un árbol binario?

Un árbol binario es una estructura de datos recursiva donde cada nodo tiene como máximo dos hijos: izquierdo y derecho. Se usa para representar jerarquías y permite operaciones eficientes de búsqueda, inserción y recorrido.

## Contenido del archivo `tree.c`

El archivo `tree.c` incluye:

- Definición de la estructura `Node` con un campo `key` (entero) y punteros `left` y `right`.
- Función `create_node` para reservar memoria y crear un nodo nuevo.
- Función `insert` (recursiva) para insertar una clave manteniendo la propiedad de árbol binario de búsqueda (BST): a la izquierda van claves menores; a la derecha, mayores o iguales.
- Función `search` para buscar una clave (retorna el puntero al nodo o NULL si no existe).
- Recorridos: `inorder`, `preorder`, `postorder`, con explicación de cuándo se visitan los nodos.
- `free_tree` para liberar la memoria del árbol (recorrido postorden).
- Un `main` que crea un árbol de ejemplo, inserta claves, imprime los recorridos y busca claves de ejemplo.

## Explicación paso a paso (resumen)

1. Empezamos con `root = NULL`.
2. Para insertar una clave, si el nodo actual es `NULL` se crea uno nuevo. Si no, comparamos la clave con `node->key`:
   - Si es menor, vamos recursivamente al subárbol izquierdo.
   - Si es mayor o igual, vamos recursivamente al subárbol derecho.
3. Para buscar, usamos la misma idea: comparar y avanzar a la rama adecuada hasta encontrar o llegar a `NULL`.
4. Los recorridos imprimen las claves en diferentes órdenes:
   - Inorder (izquierda, raíz, derecha): para BST resulta en orden ascendente.
   - Preorder (raíz, izquierda, derecha): útil para copiar el árbol.
   - Postorder (izquierda, derecha, raíz): útil para liberar memoria.

## Cómo compilar y ejecutar (Windows, pwsh)

Asegúrate de tener instalado un compilador C (por ejemplo MinGW-w64 `gcc` o `clang`). En PowerShell (pwsh) desde la carpeta que contiene `tree.c` ejecuta:

```powershell
# Compilar con gcc
gcc -std=c11 -O2 -Wall -Wextra -o tree.exe tree.c

# Ejecutar
.\tree.exe
```

Si usas MSVC (Developer Command Prompt), el comando sería diferente; aquí usamos `gcc` por ser común y sencillo.

## Ejemplo de salida esperada

El programa insertará las claves: 50, 30, 70, 20, 40, 60, 80. Se deberían imprimir los recorridos y el resultado de búsquedas (por ejemplo 60 encontrado, 25 no encontrado).

## Mini gráfica (representación del árbol)

La siguiente es una representación ASCII del árbol binario resultante tras insertar las claves de ejemplo en ese orden:

```text
            50
          /  \
       30    70
      /  \  /  \
   20  40 60  80
```

Notas:
- Las ramas muestran la relación padre -> hijo izquierdo/derecho.
- En un BST (árbol binario de búsqueda) las claves menores que la raíz están a la izquierda; las mayores o iguales, a la derecha.

## Siguientes pasos (opcional)

- Añadir eliminación de un nodo (delete) con sus tres casos.
- Implementar balanceo (AVL o Red-Black) si necesitas operaciones garantizadas en O(log n).
- Agregar pruebas unitarias.

---

Archivo creado automáticamente: `tree.c` contiene comentarios con explicación línea a línea.
