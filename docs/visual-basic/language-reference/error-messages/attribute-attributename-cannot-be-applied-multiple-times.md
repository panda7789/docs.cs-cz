---
title: Atribut '<attributename>' nelze použít několikrát.
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 14145f165adf5ccd20298a70ca5596488b488b0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409956"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a>Atribut '\<attributename>' nelze použít několikrát.

Atribut lze použít pouze jednou. `AttributeUsage`Atribut určuje, zda lze atribut použít více než jednou.  
  
 **ID chyby:** BC30663  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, že je atribut použit pouze jednou.  
  
2. Pokud používáte vlastní atributy, které jste vyvinuli, zvažte změnu jejich `AttributeUsage` atributu tak, aby povolovala použití více atributů, jako v následujícím příkladu.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.AttributeUsageAttribute>
- [Vytváření vlastních atributů](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../programming-guide/concepts/attributes/attributeusage.md)
