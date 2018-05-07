---
title: Atribut &#39; &lt;attributename&gt; &#39; nelze použít více než jednou.
ms.date: 07/20/2015
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
ms.openlocfilehash: df97a4e391406661db98eb1c958c0e12e45b6c49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a>Atribut &#39; &lt;attributename&gt; &#39; nelze použít více než jednou.
Atribut lze použít pouze jednou. `AttributeUsage` Atribut určuje, zda atribut můžete použít více než jednou.  
  
 **ID chyby:** BC30663  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že atribut se použije pouze jednou.  
  
2.  Pokud používáte vlastní atributy, které jste vytvořili, zvažte změnu jejich `AttributeUsage` atribut umožňuje více atributů využití, stejně jako v následujícím příkladu.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.AttributeUsageAttribute>  
 [Vytváření vlastních atributů](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
