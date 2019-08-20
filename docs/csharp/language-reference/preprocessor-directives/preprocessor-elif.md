---
title: '#elif – C# reference'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: b04db4bd23a459043efec59b8ebf9d322defbcf7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608581"
---
# <a name="elif-c-reference"></a><span data-ttu-id="d0be2-102">#elif (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d0be2-102">#elif (C# Reference)</span></span>
<span data-ttu-id="d0be2-103">Výraz `#elif` umožňuje vytvořit složenou podmíněnou direktivu.</span><span class="sxs-lookup"><span data-stu-id="d0be2-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="d0be2-104">Výraz bude vyhodnocen, pokud ani předchozí [#if](./preprocessor-if.md) ani žádné `#elif` předchozí, nepovinné výrazy direktivy vyhodnoceny na. `true` `#elif`</span><span class="sxs-lookup"><span data-stu-id="d0be2-104">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="d0be2-105">Je-li výraz `#elif` vyhodnocen jako `true`, vyhodnotí kompilátor kód mezi výrazem `#elif` a další podmíněnou direktivou.</span><span class="sxs-lookup"><span data-stu-id="d0be2-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="d0be2-106">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d0be2-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="d0be2-107">K vyhodnocení více symbolů lze použít operátory `==` (rovnost), `!=` (nerovnost), `&&` (a) a `||` (nebo).</span><span class="sxs-lookup"><span data-stu-id="d0be2-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="d0be2-108">Symboly a operátory je také možné seskupovat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="d0be2-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0be2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0be2-109">Remarks</span></span>  
 <span data-ttu-id="d0be2-110">Výraz `#elif` je ekvivalentní tomuto:</span><span class="sxs-lookup"><span data-stu-id="d0be2-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="d0be2-111">Použití `#elif` je jednodušší, protože každý `#if` vyžaduje [#endif](./preprocessor-endif.md), zatímco `#elif` lze použít bez odpovídajícího. `#endif`</span><span class="sxs-lookup"><span data-stu-id="d0be2-111">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="d0be2-112">Příklad [](./preprocessor-if.md) použití `#elif`naleznete v tématu #if.</span><span class="sxs-lookup"><span data-stu-id="d0be2-112">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0be2-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0be2-113">See also</span></span>

- [<span data-ttu-id="d0be2-114">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="d0be2-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d0be2-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d0be2-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d0be2-116">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="d0be2-116">C# Preprocessor Directives</span></span>](./index.md)
