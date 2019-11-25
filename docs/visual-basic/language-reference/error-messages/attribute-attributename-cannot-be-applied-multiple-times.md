---
title: Atribut '<attributename>' nelze použít několikrát.
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: f2f4dc428a247275f9919c4a8b6e6944a558eef0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968230"
---
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a>Atribut\<attributeName > se nedá použít víckrát.

Atribut lze použít pouze jednou. Atribut `AttributeUsage` určuje, zda lze atribut použít více než jednou.  
  
 **ID chyby:** BC30663  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, že je atribut použit pouze jednou.  
  
2. Pokud používáte vlastní atributy, které jste vyvinuli, zvažte změnu jejich `AttributeUsage` atributu tak, aby povolovala použití více atributů, jako v následujícím příkladu.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.AttributeUsageAttribute>
- [Vytváření vlastních atributů](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
