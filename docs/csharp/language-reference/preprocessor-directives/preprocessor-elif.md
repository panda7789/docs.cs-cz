---
title: "#<a name=\"elif-c-reference\"></a>elif (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#elif'
helpviewer_keywords: '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1512bbbc46ce15570507c8b51540eef607d55dc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="elif-c-reference"></a><span data-ttu-id="a8c3e-102">#elif (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a8c3e-102">#elif (C# Reference)</span></span>
<span data-ttu-id="a8c3e-103">Výraz `#elif` umožňuje vytvořit složenou podmíněnou direktivu.</span><span class="sxs-lookup"><span data-stu-id="a8c3e-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="a8c3e-104">`#elif` Výraz vyhodnotí, pokud předchozím [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ani žádný předcházející, volitelné, `#elif` direktivy výrazy vyhodnocení `true`.</span><span class="sxs-lookup"><span data-stu-id="a8c3e-104">The `#elif` expression will be evaluated if neither the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="a8c3e-105">Je-li výraz `#elif` vyhodnocen jako `true`, vyhodnotí kompilátor kód mezi výrazem `#elif` a další podmíněnou direktivou.</span><span class="sxs-lookup"><span data-stu-id="a8c3e-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="a8c3e-106">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a8c3e-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="a8c3e-107">K vyhodnocení více symbolů lze použít operátory `==` (rovnost), `!=` (nerovnost), `&&` (a) a `||` (nebo).</span><span class="sxs-lookup"><span data-stu-id="a8c3e-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="a8c3e-108">Symboly a operátory je také možné seskupovat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="a8c3e-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8c3e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8c3e-109">Remarks</span></span>  
 <span data-ttu-id="a8c3e-110">Výraz `#elif` je ekvivalentní tomuto:</span><span class="sxs-lookup"><span data-stu-id="a8c3e-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="a8c3e-111">Pomocí `#elif` je jednodušší, protože každý `#if` vyžaduje [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), zatímco `#elif` lze použít bez odpovídající `#endif`.</span><span class="sxs-lookup"><span data-stu-id="a8c3e-111">Using `#elif` is simpler, because each `#if` requires a [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="a8c3e-112">V tématu [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) příklad použití `#elif`.</span><span class="sxs-lookup"><span data-stu-id="a8c3e-112">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c3e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8c3e-113">See Also</span></span>  
 [<span data-ttu-id="a8c3e-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a8c3e-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a8c3e-115">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a8c3e-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a8c3e-116">C# direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="a8c3e-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
