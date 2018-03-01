---
title: "Atribut & č. 39; &lt;attributename&gt;& č. 39; nelze použít více než jednou."
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords:
- BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 216cf54fd164ca95b6378517a679b5b54183559f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a><span data-ttu-id="8397d-102">Atribut & č. 39; &lt;attributename&gt;& č. 39; nelze použít více než jednou.</span><span class="sxs-lookup"><span data-stu-id="8397d-102">Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times</span></span>
<span data-ttu-id="8397d-103">Atribut lze použít pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="8397d-103">The attribute can only be applied once.</span></span> <span data-ttu-id="8397d-104">`AttributeUsage` Atribut určuje, zda atribut můžete použít více než jednou.</span><span class="sxs-lookup"><span data-stu-id="8397d-104">The `AttributeUsage` attribute determines whether an attribute can be applied more than once.</span></span>  
  
 <span data-ttu-id="8397d-105">**ID chyby:** BC30663</span><span class="sxs-lookup"><span data-stu-id="8397d-105">**Error ID:** BC30663</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8397d-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8397d-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="8397d-107">Ujistěte se, že atribut se použije pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="8397d-107">Make sure the attribute is only applied once.</span></span>  
  
2.  <span data-ttu-id="8397d-108">Pokud používáte vlastní atributy, které jste vytvořili, zvažte změnu jejich `AttributeUsage` atribut umožňuje více atributů využití, stejně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8397d-108">If you are using custom attributes you developed, consider changing their `AttributeUsage` attribute to allow multiple attribute usage, as with the following example.</span></span>  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8397d-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="8397d-109">See Also</span></span>  
 <xref:System.AttributeUsageAttribute>  
 [<span data-ttu-id="8397d-110">Vytváření vlastních atributů</span><span class="sxs-lookup"><span data-stu-id="8397d-110">Creating Custom Attributes</span></span>](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="8397d-111">AttributeUsage</span><span class="sxs-lookup"><span data-stu-id="8397d-111">AttributeUsage</span></span>](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
