---
description: '#Reference elif-C#'
title: '#Reference elif-C#'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: 3aa9082b392b352091b9fde74a85f9dd155ad7b1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132284"
---
# <a name="elif-c-reference"></a><span data-ttu-id="07892-103">#elif (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="07892-103">#elif (C# Reference)</span></span>
<span data-ttu-id="07892-104">Výraz `#elif` umožňuje vytvořit složenou podmíněnou direktivu.</span><span class="sxs-lookup"><span data-stu-id="07892-104">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="07892-105">`#elif`Výraz bude vyhodnocen, pokud ani předchozí [#if](./preprocessor-if.md) ani žádné předchozí, nepovinné `#elif` výrazy direktivy vyhodnoceny na `true` .</span><span class="sxs-lookup"><span data-stu-id="07892-105">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="07892-106">Je-li výraz `#elif` vyhodnocen jako `true`, vyhodnotí kompilátor kód mezi výrazem `#elif` a další podmíněnou direktivou.</span><span class="sxs-lookup"><span data-stu-id="07892-106">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="07892-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="07892-107">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="07892-108">K vyhodnocení více symbolů lze použít operátory `==` (rovnost), `!=` (nerovnost), `&&` (a) a `||` (nebo).</span><span class="sxs-lookup"><span data-stu-id="07892-108">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="07892-109">Symboly a operátory je také možné seskupovat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="07892-109">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07892-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07892-110">Remarks</span></span>  
 <span data-ttu-id="07892-111">Výraz `#elif` je ekvivalentní tomuto:</span><span class="sxs-lookup"><span data-stu-id="07892-111">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="07892-112">Použití `#elif` je jednodušší, protože každý `#if` vyžaduje [#endif](./preprocessor-endif.md), zatímco `#elif` lze použít bez odpovídajícího `#endif` .</span><span class="sxs-lookup"><span data-stu-id="07892-112">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="07892-113">Příklad použití naleznete v tématu [#if](./preprocessor-if.md) `#elif` .</span><span class="sxs-lookup"><span data-stu-id="07892-113">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07892-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="07892-114">See also</span></span>

- [<span data-ttu-id="07892-115">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="07892-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="07892-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="07892-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="07892-117">C# – direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="07892-117">C# Preprocessor Directives</span></span>](./index.md)
