---
title: '#odkaz na C# oblast'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 723a904d18955caceea9e0d485ab51f84366c66e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715121"
---
# <a name="region-c-reference"></a><span data-ttu-id="6c72d-102">#region (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6c72d-102">#region (C# Reference)</span></span>
<span data-ttu-id="6c72d-103">`#region` umožňuje zadat blok kódu, který lze rozbalit nebo sbalit při použití funkce [sbalení](/visualstudio/ide/outlining) editoru Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="6c72d-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="6c72d-104">V případě delších souborů kódu je možné sbalit nebo skrýt jednu nebo více oblastí, abyste se mohli soustředit na část souboru, na kterém právě pracujete.</span><span class="sxs-lookup"><span data-stu-id="6c72d-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="6c72d-105">Následující příklad ukazuje, jak definovat oblast:</span><span class="sxs-lookup"><span data-stu-id="6c72d-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="6c72d-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c72d-106">Remarks</span></span>  
 <span data-ttu-id="6c72d-107">Blok `#region` musí být ukončen direktivou [#endregion](./preprocessor-endregion.md) .</span><span class="sxs-lookup"><span data-stu-id="6c72d-107">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="6c72d-108">Blok `#region` se nemůže překrývat s blokem [#if](./preprocessor-if.md) .</span><span class="sxs-lookup"><span data-stu-id="6c72d-108">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="6c72d-109">Blok `#region` ale může být vnořený do `#if` bloku a blok `#if` může být vnořený do `#region` bloku.</span><span class="sxs-lookup"><span data-stu-id="6c72d-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c72d-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c72d-110">See also</span></span>

- [<span data-ttu-id="6c72d-111">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="6c72d-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6c72d-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6c72d-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6c72d-113">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="6c72d-113">C# Preprocessor Directives</span></span>](./index.md)
