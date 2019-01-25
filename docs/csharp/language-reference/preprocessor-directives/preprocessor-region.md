---
title: '#oblast – C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: adaa58fc47da557a31270e99ff8a1dae3d0731bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724028"
---
# <a name="region-c-reference"></a><span data-ttu-id="3006f-102">#region (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3006f-102">#region (C# Reference)</span></span>
<span data-ttu-id="3006f-103">`#region` Umožňuje určit blok kódu, které můžete rozbalit nebo sbalit při použití [sbalování](/visualstudio/ide/outlining) funkce z editoru kódu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3006f-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="3006f-104">V souborech kódu delší dobu je vhodné sbalit nebo skrýt jedné nebo více oblastí, aby vám umožní soustředit se u souboru, který jste právě pracujete.</span><span class="sxs-lookup"><span data-stu-id="3006f-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="3006f-105">Následující příklad ukazuje, jak definovat oblasti:</span><span class="sxs-lookup"><span data-stu-id="3006f-105">The following example shows how to define a region:</span></span>  
  
```csharp
#region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a><span data-ttu-id="3006f-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3006f-106">Remarks</span></span>  
 <span data-ttu-id="3006f-107">A `#region` bloku musí být ukončen direktivou [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) směrnice.</span><span class="sxs-lookup"><span data-stu-id="3006f-107">A `#region` block must be terminated with a [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="3006f-108">A `#region` bloku se nesmí překrývat s [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) bloku.</span><span class="sxs-lookup"><span data-stu-id="3006f-108">A `#region` block cannot overlap with a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) block.</span></span> <span data-ttu-id="3006f-109">Ale `#region` bloku může být vnořena v `#if` bloku a `#if` bloku může být vnořena v `#region` bloku.</span><span class="sxs-lookup"><span data-stu-id="3006f-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3006f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3006f-110">See also</span></span>

- [<span data-ttu-id="3006f-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3006f-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="3006f-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3006f-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3006f-113">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="3006f-113">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
