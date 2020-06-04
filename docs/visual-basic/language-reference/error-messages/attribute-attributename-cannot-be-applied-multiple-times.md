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
# <a name="attribute-attributename-cannot-be-applied-multiple-times"></a><span data-ttu-id="4f2fd-102">Atribut '\<attributename>' nelze použít několikrát.</span><span class="sxs-lookup"><span data-stu-id="4f2fd-102">Attribute '\<attributename>' cannot be applied multiple times</span></span>

<span data-ttu-id="4f2fd-103">Atribut lze použít pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="4f2fd-103">The attribute can only be applied once.</span></span> <span data-ttu-id="4f2fd-104">`AttributeUsage`Atribut určuje, zda lze atribut použít více než jednou.</span><span class="sxs-lookup"><span data-stu-id="4f2fd-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="4f2fd-105">**ID chyby:** BC30663</span><span class="sxs-lookup"><span data-stu-id="4f2fd-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4f2fd-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="4f2fd-106">To correct this error</span></span>  
  
1. <span data-ttu-id="4f2fd-107">Ujistěte se, že je atribut použit pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="4f2fd-107">Make sure the attribute is only applied once.</span></span>  
  
2. <span data-ttu-id="4f2fd-108">Pokud používáte vlastní atributy, které jste vyvinuli, zvažte změnu jejich `AttributeUsage` atributu tak, aby povolovala použití více atributů, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4f2fd-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f2fd-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f2fd-109">See also</span></span>

- <xref:System.AttributeUsageAttribute>
- [<span data-ttu-id="4f2fd-110">Vytváření vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="4f2fd-110">Creating Custom Attributes</span></span>](../../programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="4f2fd-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="4f2fd-111">AttributeUsage</span></span>](../../programming-guide/concepts/attributes/attributeusage.md)
