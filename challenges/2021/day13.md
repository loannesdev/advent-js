¡Hay demasiados regalos 🎁! Y envolverlos es una locura...

Vamos a crear una función que pasándole un array de regalos, nos devuelva otro array pero donde todos los regalos han sido envueltos con asteriscos tanto por arriba como por los lados.

Sólo tienes que tener en cuenta unas cosillas ✌️:

- Si el array está vacío, devuelve un array vacío
- Los regalos son emojis 🎁... por lo que tenlo en cuenta a la hora de contar su longitud...
- Por suerte, cada posición del array siempre tiene la misma longitud...

```js
wrapGifts(["📷", "⚽️"])
/* Resultado:
[ '****',
  '*📷*',
  '*⚽️*',
  '****'
]
*/

wrapGifts(["🏈🎸", "🎮🧸"])
/* Resultado:
[ '******',
  '*🏈🎸*',
  '*🎮🧸*',
  '******'
]
*/

wrapGifts(["📷"])
/* Resultado:
[ '****',
  '*📷*',
  '****'
]
*/
```
<br >

## **Solución**

```js
export default function wrapGifts(gifts) {
  const LENGTH = gifts.length;

  if (LENGTH) {
    const ASTERISK_FOR_GIFT = Math.max(...gifts.map((v) => v.length)) + 2;
    const ASTERISK_TOP_BOTTOM = "*".repeat(ASTERISK_FOR_GIFT);
    const CONTENT = gifts.map((elm) => `*${elm}*`);
    const GIFT = `${ASTERISK_TOP_BOTTOM},${CONTENT},${ASTERISK_TOP_BOTTOM}`;

    return GIFT.split(",");
  }

  return [];
}
```