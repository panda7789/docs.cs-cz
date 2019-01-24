---
title: Atribut &#39; &lt;attributename&gt; &#39; nejde použít více než jednou.
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: 6609ce299799bc3c4b78d48478e99e4d4101dd72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565160"
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a>Atribut &#39; &lt;attributename&gt; &#39; nejde použít více než jednou.
Atribut lze použít pouze jednou. `AttributeUsage` Atribut určuje, zda atribut lze použít více než jednou.  
  
 **ID chyby:** BC30663  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že atribut je použit pouze jednou.  
  
2.  Pokud používáte vlastní atributy, které jste vytvořili, zvažte možnost změnit jejich `AttributeUsage` atribut umožňuje více použití atributu, stejně jako v následujícím příkladu.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.AttributeUsageAttribute>
- [Vytváření vlastních atributů](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
