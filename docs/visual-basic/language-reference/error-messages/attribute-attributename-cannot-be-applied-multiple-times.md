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
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="0e864-102">Atribut '\<attributename >' nelze použít více než jednou.</span><span class="sxs-lookup"><span data-stu-id="0e864-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>
<span data-ttu-id="0e864-103">Atribut lze použít pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="0e864-103">The attribute can only be applied once.</span></span> <span data-ttu-id="0e864-104">`AttributeUsage` Atribut určuje, zda atribut lze použít více než jednou.</span><span class="sxs-lookup"><span data-stu-id="0e864-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="0e864-105">**ID chyby:** BC30663</span><span class="sxs-lookup"><span data-stu-id="0e864-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0e864-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0e864-106">To correct this error</span></span>  
  
1. <span data-ttu-id="0e864-107">Ujistěte se, že atribut je použit pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="0e864-107">Make sure the attribute is only applied once.</span></span>  
  
2. <span data-ttu-id="0e864-108">Pokud používáte vlastní atributy, které jste vytvořili, zvažte možnost změnit jejich `AttributeUsage` atribut umožňuje více použití atributu, stejně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0e864-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e864-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e864-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="0e864-110">Vytváření vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="0e864-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="0e864-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="0e864-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
