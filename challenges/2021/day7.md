Mi amigo Dani está trabajando en una tienda y con la llegada de las navidades tiene el almacén hecho un desastre y no encuentra nada.

Vamos a crear una función `contains` que recibe dos parámetros: un objeto que define el almacén y el producto que buscamos.

La función debe devolver un booleano que indique si se encuentra el string como valor en algún nivel del objeto. Veamos unos ejemplos:

```js
const almacen = {
  'estanteria1': {
    'cajon1': {
      'producto1': 'coca-cola',
      'producto2': 'fanta',
      'producto3': 'sprite'
    }
  },
  'estanteria2': {
    'cajon1': 'vacio',
    'cajon2': {
      'producto1': 'pantalones',
      'producto2': 'camiseta' // <- ¡Está aquí!
    }
  }
}

contains(almacen, 'camiseta') // true
```

```js
const otroAlmacen = {
  'baul': {
    'fondo': {
      'objeto': 'cd-rom',
      'otro-objeto': 'disquette',
      'otra-cosa': 'mando'
    }
  }
}

contains(otroAlmacen, 'gameboy') // false
```

Ten en cuenta que la tienda es enorme. Tiene diferentes almacenes y, como has visto en los ejemplos, cada uno puede tener diferentes organizaciones.Lo importante es buscar que el producto está en los almacenes.<br ><br >

## **Solución**

```js
export default function contains(store, product) {
  if (Object.entries(store).length === 0) {
    return false;
  }

  const ITERATOR = (element) => {
    const LENGTH = Object.keys(element).length;

    if (LENGTH && product.length) {
      let FILTERED_VALUES = {};

      for (const v in element) {
        if (element == product && typeof element === "string") return true;
        if (element[v] === product && typeof element === "object") return true;

        typeof element[v] === "object" && Object.keys(element[v]).length
          ? (FILTERED_VALUES = { ...element[v], ...FILTERED_VALUES })
          : null;
      }

      return ITERATOR(FILTERED_VALUES);
    }

    return false;
  };

  return Object.values(store)
    .map((elm) => ITERATOR(elm))
    .at(-1);
}
```