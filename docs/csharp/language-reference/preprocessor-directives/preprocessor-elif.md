---
title: '#elif – C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: 00a9298be6ecd6f5e775d930190ddb6e227e4711
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587226"
---
# <a name="elif-c-reference"></a><span data-ttu-id="7481a-102">#elif (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7481a-102">#elif (C# Reference)</span></span>
<span data-ttu-id="7481a-103">Výraz `#elif` umožňuje vytvořit složenou podmíněnou direktivu.</span><span class="sxs-lookup"><span data-stu-id="7481a-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="7481a-104">`#elif` Výraz bude vyhodnocen, pokud ani předchozí [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ani žádné předchozí volitelné `#elif` vyhodnotit výrazy direktivy `true`.</span><span class="sxs-lookup"><span data-stu-id="7481a-104">The `#elif` expression will be evaluated if neither the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="7481a-105">Je-li výraz `#elif` vyhodnocen jako `true`, vyhodnotí kompilátor kód mezi výrazem `#elif` a další podmíněnou direktivou.</span><span class="sxs-lookup"><span data-stu-id="7481a-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="7481a-106">Příklad:</span><span class="sxs-lookup"><span data-stu-id="7481a-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="7481a-107">K vyhodnocení více symbolů lze použít operátory `==` (rovnost), `!=` (nerovnost), `&&` (a) a `||` (nebo).</span><span class="sxs-lookup"><span data-stu-id="7481a-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="7481a-108">Symboly a operátory je také možné seskupovat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="7481a-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7481a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7481a-109">Remarks</span></span>  
 <span data-ttu-id="7481a-110">Výraz `#elif` je ekvivalentní tomuto:</span><span class="sxs-lookup"><span data-stu-id="7481a-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="7481a-111">Pomocí `#elif` je jednodušší, protože každý `#if` vyžaduje [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), že `#elif` lze použít bez odpovídajícího `#endif`.</span><span class="sxs-lookup"><span data-stu-id="7481a-111">Using `#elif` is simpler, because each `#if` requires a [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="7481a-112">Zobrazit [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) příklad, jak používat `#elif`.</span><span class="sxs-lookup"><span data-stu-id="7481a-112">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7481a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7481a-113">See also</span></span>

- [<span data-ttu-id="7481a-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7481a-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="7481a-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7481a-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="7481a-116">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="7481a-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
