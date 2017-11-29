---
title: "#<a name=\"region-c-reference\"></a>oblast (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#region'
helpviewer_keywords: '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cce4a8ac79c4687280e28618d8863d16cd193a3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="region-c-reference"></a><span data-ttu-id="a6428-102">#region (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a6428-102">#region (C# Reference)</span></span>
<span data-ttu-id="a6428-103">`#region`Umožňuje zadat blok kódu, který můžete rozbalit nebo sbalit při použití [osnovy](/visualstudio/ide/outlining) funkce z editoru kódu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a6428-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="a6428-104">V souborech delší kódu je vhodnější moci sbalení a skrytí jeden nebo více oblastí tak, aby se mohli zaměřit části souboru, který aktuálně pracujete na.</span><span class="sxs-lookup"><span data-stu-id="a6428-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="a6428-105">Následující příklad ukazuje, jak definovat oblasti:</span><span class="sxs-lookup"><span data-stu-id="a6428-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="a6428-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6428-106">Remarks</span></span>  
 <span data-ttu-id="a6428-107">A `#region` bloku musí být ukončena s [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) – direktiva.</span><span class="sxs-lookup"><span data-stu-id="a6428-107">A `#region` block must be terminated with a [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="a6428-108">A `#region` bloku se nesmí překrývat s [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) bloku.</span><span class="sxs-lookup"><span data-stu-id="a6428-108">A `#region` block cannot overlap with a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) block.</span></span> <span data-ttu-id="a6428-109">Ale `#region` bloku mohou být použity v `#if` bloku a `#if` bloku mohou být použity v `#region` bloku.</span><span class="sxs-lookup"><span data-stu-id="a6428-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6428-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6428-110">See Also</span></span>  
 [<span data-ttu-id="a6428-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a6428-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a6428-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a6428-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a6428-113">C# direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="a6428-113">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
