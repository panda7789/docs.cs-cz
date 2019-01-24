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
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a><span data-ttu-id="32137-102">Atribut &#39; &lt;attributename&gt; &#39; nejde použít více než jednou.</span><span class="sxs-lookup"><span data-stu-id="32137-102">Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times</span></span>
<span data-ttu-id="32137-103">Atribut lze použít pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="32137-103">The attribute can only be applied once.</span></span> <span data-ttu-id="32137-104">`AttributeUsage` Atribut určuje, zda atribut lze použít více než jednou.</span><span class="sxs-lookup"><span data-stu-id="32137-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="32137-105">**ID chyby:** BC30663</span><span class="sxs-lookup"><span data-stu-id="32137-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="32137-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="32137-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="32137-107">Ujistěte se, že atribut je použit pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="32137-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="32137-108">Pokud používáte vlastní atributy, které jste vytvořili, zvažte možnost změnit jejich `AttributeUsage` atribut umožňuje více použití atributu, stejně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="32137-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="32137-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32137-109">See also</span></span>
- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="32137-110">Vytváření vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="32137-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="32137-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="32137-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
