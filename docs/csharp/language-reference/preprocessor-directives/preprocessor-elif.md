---
title: '#elif – C# reference'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: c78818f40b76414d289af6c704ff019b63befe37
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712569"
---
# <a name="elif-c-reference"></a><span data-ttu-id="99045-102">#elif (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="99045-102">#elif (C# Reference)</span></span>
<span data-ttu-id="99045-103">Výraz `#elif` umožňuje vytvořit složenou podmíněnou direktivu.</span><span class="sxs-lookup"><span data-stu-id="99045-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="99045-104">Výraz `#elif` bude vyhodnocen, pokud není předchozí [#if](./preprocessor-if.md) ani předchozí, volitelné, `#elif` výrazy direktivy vyhodnoceny na `true`.</span><span class="sxs-lookup"><span data-stu-id="99045-104">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="99045-105">Je-li výraz `#elif` vyhodnocen jako `true`, vyhodnotí kompilátor kód mezi výrazem `#elif` a další podmíněnou direktivou.</span><span class="sxs-lookup"><span data-stu-id="99045-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="99045-106">Příklad:</span><span class="sxs-lookup"><span data-stu-id="99045-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="99045-107">K vyhodnocení více symbolů lze použít operátory `==` (rovnost), `!=` (nerovnost), `&&` (a) a `||` (nebo).</span><span class="sxs-lookup"><span data-stu-id="99045-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="99045-108">Symboly a operátory je také možné seskupovat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="99045-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99045-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99045-109">Remarks</span></span>  
 <span data-ttu-id="99045-110">Výraz `#elif` je ekvivalentní tomuto:</span><span class="sxs-lookup"><span data-stu-id="99045-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="99045-111">Použití `#elif` je jednodušší, protože každý `#if` vyžaduje [#endif](./preprocessor-endif.md), zatímco `#elif` lze použít bez odpovídajícího `#endif`.</span><span class="sxs-lookup"><span data-stu-id="99045-111">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="99045-112">Příklad použití `#elif`naleznete v tématu [#if](./preprocessor-if.md) .</span><span class="sxs-lookup"><span data-stu-id="99045-112">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99045-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99045-113">See also</span></span>

- [<span data-ttu-id="99045-114">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="99045-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="99045-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="99045-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="99045-116">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="99045-116">C# Preprocessor Directives</span></span>](./index.md)
