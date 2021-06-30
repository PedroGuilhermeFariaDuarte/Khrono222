# Khrono222
Um algoritmo para ler código de barras da loggi

# O algoritmo

```js
function handlerBarcode() {
    try {
      const references = [
        {
          name: 'Joia',
          code: '000',
          description: 'produto'
        },
        {
          name: 'Vendedor',
          code: '999',
          description: 'vendedor'
        },
        {
          name: 'Sudeste',
          code: '888',
          descrtption: 'local_origem'
        },
        {
          name: 'Sudeste',
          code: '333',
          description: 'local_destino'
        },
        {
          name: 'Sudeste',
          code: '555',
          description: 'dono'
        }
      ]

      const referencesFounded =  [];

      const barCode = [
        {
          barcode: '888333555999000',
          // Separando o codigo de barras em grupos de três caracteres
          barCodeParsed: '888333555999000'?.replace(/(\d{3})(\d{3})(\d{3})(\d{3})(\d{3})/, '$1.$2.$3.$4.$5').split('.') || []
          // Outros dados, por exemplo: vendedor: Khrono222
        }
      ]

      if (references.length <= 0) {
        throw new Error('Nenhuma referência foi definida')
      }

      // Percorre as referencias
      for (let i = 0; i <= references.length; i++) {
        const reference = references[ i ]
        for (let j = 0; j <= barCode.length; j++) {
          // Verifica se o codigo foi lido
          if (barCode[ j ]?.barCodeParsed.length <= 0) {
            continue
          }

          for (let w = 0; w <= barCode[ j ]?.barCodeParsed?.length; w++) {
            // Verifica se o codigo existe
            if (barCode[ j ]?.barCodeParsed[ w ] === reference?.code) {
              referencesFounded.push(reference)
            }
          }
        }
      }

      console.log('Result: ', referencesFounded)

      return ''
    } catch (error) {
      console.log(`HandlerBarcode: ${error.message}`)
    }
  }
```js
