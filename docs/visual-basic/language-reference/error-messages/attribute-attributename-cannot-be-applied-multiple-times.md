---
title: Atribut '<attributename>' nelze použít několikrát.
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: da4a766e2617308cb33b9673a88db9e7a954152a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935314"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a>Atribut '\<attributename >' nelze použít více než jednou.
Atribut lze použít pouze jednou. `AttributeUsage` Atribut určuje, zda atribut lze použít více než jednou.  
  
 **ID chyby:** BC30663  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, že atribut je použit pouze jednou.  
  
2. Pokud používáte vlastní atributy, které jste vytvořili, zvažte možnost změnit jejich `AttributeUsage` atribut umožňuje více použití atributu, stejně jako v následujícím příkladu.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.AttributeUsageAttribute>
- [Vytváření vlastních atributů](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
