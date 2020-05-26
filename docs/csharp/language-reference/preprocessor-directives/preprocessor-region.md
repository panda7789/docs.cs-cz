---
title: '#region – Referenční dokumentace jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 66583d6e067b006b03130d8ff842b56bf57bcebc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802767"
---
# <a name="region-c-reference"></a><span data-ttu-id="e2100-102">#region (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e2100-102">#region (C# Reference)</span></span>
<span data-ttu-id="e2100-103">`#region`umožňuje zadat blok kódu, který lze rozbalit nebo sbalit při použití funkce [sbalení](/visualstudio/ide/outlining) editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="e2100-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the code editor.</span></span> <span data-ttu-id="e2100-104">V případě delších souborů kódu je možné sbalit nebo skrýt jednu nebo více oblastí, abyste se mohli soustředit na část souboru, na kterém právě pracujete.</span><span class="sxs-lookup"><span data-stu-id="e2100-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="e2100-105">Následující příklad ukazuje, jak definovat oblast:</span><span class="sxs-lookup"><span data-stu-id="e2100-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="e2100-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2100-106">Remarks</span></span>  
 <span data-ttu-id="e2100-107">`#region`Blok musí být ukončen direktivou [#endregion](./preprocessor-endregion.md) .</span><span class="sxs-lookup"><span data-stu-id="e2100-107">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="e2100-108">`#region`Blok se nemůže překrývat s [#ifm](./preprocessor-if.md) blokem.</span><span class="sxs-lookup"><span data-stu-id="e2100-108">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="e2100-109">`#region`Blok však může být vnořen v `#if` bloku a `#if` blok může být vnořen do `#region` bloku.</span><span class="sxs-lookup"><span data-stu-id="e2100-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2100-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2100-110">See also</span></span>

- [<span data-ttu-id="e2100-111">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e2100-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e2100-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e2100-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e2100-113">C# – direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="e2100-113">C# Preprocessor Directives</span></span>](./index.md)
