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
ms.locfileid: "33584856"
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a><span data-ttu-id="b054e-102">Atribut &#39; &lt;attributename&gt; &#39; nelze použít více než jednou.</span><span class="sxs-lookup"><span data-stu-id="b054e-102">Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times</span></span>
<span data-ttu-id="b054e-103">Atribut lze použít pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="b054e-103">The attribute can only be applied once.</span></span> <span data-ttu-id="b054e-104">`AttributeUsage` Atribut určuje, zda atribut můžete použít více než jednou.</span><span class="sxs-lookup"><span data-stu-id="b054e-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="b054e-105">**ID chyby:** BC30663</span><span class="sxs-lookup"><span data-stu-id="b054e-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b054e-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b054e-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="b054e-107">Ujistěte se, že atribut se použije pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="b054e-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="b054e-108">Pokud používáte vlastní atributy, které jste vytvořili, zvažte změnu jejich `AttributeUsage` atribut umožňuje více atributů využití, stejně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b054e-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b054e-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="b054e-109">See Also</span></span>  
 <xref:System.AttributeUsageAttribute>  
 [<span data-ttu-id="b054e-110">Vytváření vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="b054e-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="b054e-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="b054e-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
