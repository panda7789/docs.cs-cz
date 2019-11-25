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
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="aea44-102">Atribut\<attributeName > se nedá použít víckrát.</span><span class="sxs-lookup"><span data-stu-id="aea44-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="aea44-103">Atribut lze použít pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="aea44-103">The attribute can only be applied once.</span></span> <span data-ttu-id="aea44-104">Atribut `AttributeUsage` určuje, zda lze atribut použít více než jednou.</span><span class="sxs-lookup"><span data-stu-id="aea44-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="aea44-105">**ID chyby:** BC30663</span><span class="sxs-lookup"><span data-stu-id="aea44-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aea44-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="aea44-106">To correct this error</span></span>  
  
1. <span data-ttu-id="aea44-107">Ujistěte se, že je atribut použit pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="aea44-107">Make sure the attribute is only applied once.</span></span>  
  
2. <span data-ttu-id="aea44-108">Pokud používáte vlastní atributy, které jste vyvinuli, zvažte změnu jejich `AttributeUsage` atributu tak, aby povolovala použití více atributů, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="aea44-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aea44-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aea44-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="aea44-110">Vytváření vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="aea44-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="aea44-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="aea44-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
