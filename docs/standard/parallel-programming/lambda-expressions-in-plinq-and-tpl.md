---
title: "Výrazy lambda v PLINQ a TPL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79ab0f4427e0f37259f88cd3ec0762d1582481f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="a4e4d-102">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="a4e4d-102">Lambda Expressions in PLINQ and TPL</span></span>
<span data-ttu-id="a4e4d-103">Task Parallel Library (TPL) obsahuje mnoho způsobů, které provést jednu z <xref:System.Func%601?displayProperty=nameWithType> nebo <xref:System.Action?displayProperty=nameWithType> rodiny delegátů jako vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-103">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="a4e4d-104">Používání těchto delegátů předávat logika vlastní program paralelní smyčky, úlohy nebo dotazu.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-104">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="a4e4d-105">Příklady kódu pro TPL a také PLINQ použití výrazů lambda vytváření instancí těchto delegáti jako vložené bloky kódu.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-105">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="a4e4d-106">Toto téma obsahuje stručný úvod do Func a Action a ukazuje, jak použití výrazů lambda v knihovně Task Parallel Library a PLINQ.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-106">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>  
  
 <span data-ttu-id="a4e4d-107">**Poznámka:** Další informace o delegáti obecně platí, najdete v části [delegáti](../../csharp/programming-guide/delegates/index.md) a [delegáti](../../visual-basic/programming-guide/language-features/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="a4e4d-107">**Note** For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="a4e4d-108">Další informace o výrazy lambda v jazyce C# a [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], najdete v části [výrazy Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) a [výrazy Lambda](~/docs/visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a4e4d-108">For more information about lambda expressions in C# and [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], see [Lambda Expressions](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) and [Lambda Expressions](~/docs/visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="func-delegate"></a><span data-ttu-id="a4e4d-109">Func – delegát</span><span class="sxs-lookup"><span data-stu-id="a4e4d-109">Func Delegate</span></span>  
 <span data-ttu-id="a4e4d-110">A `Func` delegáta zapouzdří metodu, která vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-110">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="a4e4d-111">V Func podpis vždy parametr typu poslední nebo úplně vpravo určuje návratový typ.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-111">In a Func signature, the last or rightmost type parameter always specifies the return type.</span></span> <span data-ttu-id="a4e4d-112">Jednou z běžných příčin chyb kompilátoru je pokus o předat ve dvou vstupních parametrů <xref:System.Func%602?displayProperty=nameWithType>; ve skutečnosti tento typ trvá jen jeden vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-112">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="a4e4d-113">Knihovna tříd Framework definuje 17 verzích `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, a tak dále až prostřednictvím <xref:System.Func%6017?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-113">The Framework Class Library defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>  
  
## <a name="action-delegate"></a><span data-ttu-id="a4e4d-114">Delegát akce</span><span class="sxs-lookup"><span data-stu-id="a4e4d-114">Action Delegate</span></span>  
 <span data-ttu-id="a4e4d-115">A <xref:System.Action?displayProperty=nameWithType> zapouzdřuje metody delegáta (Sub v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) nevrátí hodnotu, nebo vrátí [void](~/docs/csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="a4e4d-115">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) that does not return a value, or returns [void](~/docs/csharp/language-reference/keywords/void.md).</span></span> <span data-ttu-id="a4e4d-116">Parametry typu v podpisu typ akce, představují pouze vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-116">In an Action type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="a4e4d-117">Knihovna tříd Framework jako Func, definuje 17 verze akce, na verzi, která nemá žádné parametry typu prostřednictvím na verzi, která obsahuje 16 parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-117">Like Func, the Framework Class Library defines 17 versions of Action, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4e4d-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4e4d-118">Example</span></span>  
 <span data-ttu-id="a4e4d-119">Následující příklad <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> metoda ukazuje, jak express delegáty Func a Action pomocí výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="a4e4d-119">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="a4e4d-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4e4d-120">See Also</span></span>  
 [<span data-ttu-id="a4e4d-121">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="a4e4d-121">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
