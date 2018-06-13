---
title: '#oblast (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 88632b04ec8932e22f5bf7a23b8f0edf14d89f27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274962"
---
# <a name="region-c-reference"></a><span data-ttu-id="39747-102">#region (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="39747-102">#region (C# Reference)</span></span>
<span data-ttu-id="39747-103">`#region` Umožňuje zadat blok kódu, který můžete rozbalit nebo sbalit při použití [osnovy](/visualstudio/ide/outlining) funkce z editoru kódu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="39747-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="39747-104">V souborech delší kódu je vhodnější moci sbalení a skrytí jeden nebo více oblastí tak, aby se mohli zaměřit části souboru, který aktuálně pracujete na.</span><span class="sxs-lookup"><span data-stu-id="39747-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="39747-105">Následující příklad ukazuje, jak definovat oblasti:</span><span class="sxs-lookup"><span data-stu-id="39747-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="39747-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39747-106">Remarks</span></span>  
 <span data-ttu-id="39747-107">A `#region` bloku musí být ukončena s [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) – direktiva.</span><span class="sxs-lookup"><span data-stu-id="39747-107">A `#region` block must be terminated with a [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="39747-108">A `#region` bloku se nesmí překrývat s [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) bloku.</span><span class="sxs-lookup"><span data-stu-id="39747-108">A `#region` block cannot overlap with a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) block.</span></span> <span data-ttu-id="39747-109">Ale `#region` bloku mohou být použity v `#if` bloku a `#if` bloku mohou být použity v `#region` bloku.</span><span class="sxs-lookup"><span data-stu-id="39747-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39747-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="39747-110">See Also</span></span>  
 [<span data-ttu-id="39747-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="39747-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="39747-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="39747-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="39747-113">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="39747-113">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
