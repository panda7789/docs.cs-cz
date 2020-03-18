---
title: '#region – odkaz jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 48e8a6796c3b07b348fd988a9b8501ee496b8ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173390"
---
# <a name="region-c-reference"></a><span data-ttu-id="a3c84-102">#region (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a3c84-102">#region (C# Reference)</span></span>
<span data-ttu-id="a3c84-103">`#region`umožňuje určit blok kódu, který můžete rozbalit nebo sbalit při použití funkce [osnovy](/visualstudio/ide/outlining) Editoru kódu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a3c84-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="a3c84-104">V delších souborech kódu je vhodné sbalit nebo skrýt jednu nebo více oblastí, abyste se mohli zaměřit na část souboru, na které právě pracujete.</span><span class="sxs-lookup"><span data-stu-id="a3c84-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="a3c84-105">Následující příklad ukazuje, jak definovat oblast:</span><span class="sxs-lookup"><span data-stu-id="a3c84-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="a3c84-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3c84-106">Remarks</span></span>  
 <span data-ttu-id="a3c84-107">Blok `#region` musí být ukončen direktivou [#endregion.](./preprocessor-endregion.md)</span><span class="sxs-lookup"><span data-stu-id="a3c84-107">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="a3c84-108">Blok `#region` se nemůže překrývat s [#if](./preprocessor-if.md) blokem.</span><span class="sxs-lookup"><span data-stu-id="a3c84-108">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="a3c84-109">Blok však může být vnořen `#if` do `#if` bloku a blok `#region` může být vnořen do bloku. `#region`</span><span class="sxs-lookup"><span data-stu-id="a3c84-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3c84-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3c84-110">See also</span></span>

- [<span data-ttu-id="a3c84-111">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a3c84-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a3c84-112">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a3c84-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a3c84-113">Direktivy preprocesoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a3c84-113">C# Preprocessor Directives</span></span>](./index.md)
