¡Es hora de poner el árbol de navidad en casa! 🎄

Para ello vamos a crear una función que recibe la altura del árbol, que será un entero positivo del 1 a, como máximo, 100.

Si le pasamos el argumento `5`, se pintaría esto:

    ____*____
    ___***___
    __*****__
    _*******_
    *********
    ____#____
    ____#____

Creamos un triángulo de asteriscos `*` con la altura proporcionada y, a los lados, usamos el guión bajo `_` para los espacios. Es muy importante que nuestro árbol siempre tenga la misma longitud por cada lado.
Todos los árboles, por pequeños o grandes que sean, tienen un tronco de dos líneas de `#`.

Otro ejemplo con un árbol de altura `3`:

    __*__
    _***_
    *****
    __#__
    __#__

Ten en cuenta que el árbol es un string y necesitas los saltos de línea `\n` para cada línea para que se forme bien el árbol.<br ><br >

---

## **Solución**

    export default function createXmasTree(height) {
      const TREE_SIZE = height;

      if (TREE_SIZE >= 1 && TREE_SIZE <= 100) {
        let tree = Array.from({ length: TREE_SIZE }).map((elm, index) => {
          return index > 0 ? "*".repeat(index * 2 + 1) : "*";
        });

        tree.push("#", "#");
        const LARGEST_VALUE = Math.max(...tree.map((elm) => elm.length));

        return tree
          .map((elm) => {
            const NUMBER_OF_UNDERSCORE = (LARGEST_VALUE - elm.length) / 2;
            const LINE = "_".repeat(NUMBER_OF_UNDERSCORE);

            return `${LINE}${elm}${LINE}`;
          })
          .join("\n");
      }

      return "El rango del tamaño del arbol es del 1 al 100";
    }