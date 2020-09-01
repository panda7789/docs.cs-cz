---
description: '#region – Referenční dokumentace jazyka C#'
title: '#region – Referenční dokumentace jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: ed40d895fedb9be271bb389a4f8de69d7ae3f266
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137939"
---
# <a name="region-c-reference"></a><span data-ttu-id="026b3-103">#region (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="026b3-103">#region (C# Reference)</span></span>
<span data-ttu-id="026b3-104">`#region` umožňuje zadat blok kódu, který lze rozbalit nebo sbalit při použití funkce [sbalení](/visualstudio/ide/outlining) editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="026b3-104">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the code editor.</span></span> <span data-ttu-id="026b3-105">V případě delších souborů kódu je možné sbalit nebo skrýt jednu nebo více oblastí, abyste se mohli soustředit na část souboru, na kterém právě pracujete.</span><span class="sxs-lookup"><span data-stu-id="026b3-105">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="026b3-106">Následující příklad ukazuje, jak definovat oblast:</span><span class="sxs-lookup"><span data-stu-id="026b3-106">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="026b3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="026b3-107">Remarks</span></span>  
 <span data-ttu-id="026b3-108">`#region`Blok musí být ukončen direktivou [#endregion](./preprocessor-endregion.md) .</span><span class="sxs-lookup"><span data-stu-id="026b3-108">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="026b3-109">`#region`Blok se nemůže překrývat s [#ifm](./preprocessor-if.md) blokem.</span><span class="sxs-lookup"><span data-stu-id="026b3-109">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="026b3-110">`#region`Blok však může být vnořen v `#if` bloku a `#if` blok může být vnořen do `#region` bloku.</span><span class="sxs-lookup"><span data-stu-id="026b3-110">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="026b3-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="026b3-111">See also</span></span>

- [<span data-ttu-id="026b3-112">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="026b3-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="026b3-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="026b3-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="026b3-114">C# – direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="026b3-114">C# Preprocessor Directives</span></span>](./index.md)
