---
title: Výrazy lambda v PLINQ a TPL
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: 4e5be295a52edc1a7f0a0a3aa98f55335ae3e31b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452997"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="c95d3-102">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="c95d3-102">Lambda Expressions in PLINQ and TPL</span></span>

<span data-ttu-id="c95d3-103">Task Parallel Library (TPL) obsahuje mnoho metod, které přebírají jednu z <xref:System.Func%601?displayProperty=nameWithType> nebo <xref:System.Action?displayProperty=nameWithType> rodinu delegátů jako vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="c95d3-103">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="c95d3-104">Tyto delegáty můžete použít k předání vlastní logiky programu do paralelní smyčky, úkolu nebo dotazu.</span><span class="sxs-lookup"><span data-stu-id="c95d3-104">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="c95d3-105">Příklady kódu pro TPL a PLINQ používají lambda výrazy k vytváření instancí těchto delegátů jako vložené bloky kódu.</span><span class="sxs-lookup"><span data-stu-id="c95d3-105">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="c95d3-106">Toto téma obsahuje stručný úvod do funkce Func a Action a ukazuje, jak používat výrazy lambda v Task Parallel Library a PLINQ.</span><span class="sxs-lookup"><span data-stu-id="c95d3-106">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>

> [!NOTE]
> <span data-ttu-id="c95d3-107">Další informace o delegátech obecně naleznete v tématu [Delegáti](../../csharp/programming-guide/delegates/index.md) a [Delegáti](../../visual-basic/programming-guide/language-features/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="c95d3-107">For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="c95d3-108">Další informace o výrazech lambda v C# a Visual Basic naleznete v tématu [lambda Expressions](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) a [lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="c95d3-108">For more information about lambda expressions in C# and Visual Basic, see [Lambda Expressions](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="func-delegate"></a><span data-ttu-id="c95d3-109">Delegát Func</span><span class="sxs-lookup"><span data-stu-id="c95d3-109">Func Delegate</span></span>

<span data-ttu-id="c95d3-110">Delegát `Func` zapouzdřuje metodu, která vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c95d3-110">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="c95d3-111">V `Func` signatura, poslední, nebo úplně vpravo, parametr Type vždy určuje návratový typ.</span><span class="sxs-lookup"><span data-stu-id="c95d3-111">In a `Func` signature, the last, or rightmost, type parameter always specifies the return type.</span></span> <span data-ttu-id="c95d3-112">Jednou z běžných příčin chyb kompilátoru je pokus o předání dvou vstupních parametrů <xref:System.Func%602?displayProperty=nameWithType>; ve skutečnosti tento typ používá pouze jeden vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="c95d3-112">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="c95d3-113">Rozhraní .NET definuje 17 verzí `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>a tak dále až <xref:System.Func%6017?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c95d3-113">.NET defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>

## <a name="action-delegate"></a><span data-ttu-id="c95d3-114">Delegát akce</span><span class="sxs-lookup"><span data-stu-id="c95d3-114">Action Delegate</span></span>

<span data-ttu-id="c95d3-115">Delegát <xref:System.Action?displayProperty=nameWithType> zapouzdřuje metodu (sub v Visual Basic), která nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c95d3-115">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in Visual Basic) that does not return a value.</span></span> <span data-ttu-id="c95d3-116">V signatuře typu `Action` parametry typu reprezentují pouze vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="c95d3-116">In an `Action` type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="c95d3-117">Podobně jako `Func`rozhraní .NET definuje 17 verzí `Action`, od verze, která nemá parametry typu, prostřednictvím verze, která má 16 parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="c95d3-117">Like `Func`, .NET defines 17 versions of `Action`, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>

## <a name="example"></a><span data-ttu-id="c95d3-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="c95d3-118">Example</span></span>

<span data-ttu-id="c95d3-119">Následující příklad metody <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> ukazuje, jak vyjádřit delegáty Func i akce pomocí výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="c95d3-119">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a><span data-ttu-id="c95d3-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c95d3-120">See also</span></span>

- [<span data-ttu-id="c95d3-121">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="c95d3-121">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
