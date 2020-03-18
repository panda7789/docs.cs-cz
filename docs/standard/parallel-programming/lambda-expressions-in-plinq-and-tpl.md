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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77452997"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="69660-102">Výrazy lambda v PLINQ a TPL</span><span class="sxs-lookup"><span data-stu-id="69660-102">Lambda Expressions in PLINQ and TPL</span></span>

<span data-ttu-id="69660-103">Paralelní knihovna úloh (TPL) obsahuje mnoho <xref:System.Func%601?displayProperty=nameWithType> metod, které berou jednu z nebo <xref:System.Action?displayProperty=nameWithType> rodiny delegátů jako vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="69660-103">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="69660-104">Tyto delegáty slouží k předání vlastní programové logiky paralelní smyčce, úkolu nebo dotazu.</span><span class="sxs-lookup"><span data-stu-id="69660-104">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="69660-105">Příklady kódu pro TPL, stejně jako PLINQ použít lambda výrazy k vytvoření instance těchto delegátů jako bloky vřádkový kód.</span><span class="sxs-lookup"><span data-stu-id="69660-105">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="69660-106">Toto téma obsahuje stručný úvod do Func a akce a ukazuje, jak používat lambda výrazy v paralelní knihovny úloh a PLINQ.</span><span class="sxs-lookup"><span data-stu-id="69660-106">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>

> [!NOTE]
> <span data-ttu-id="69660-107">Další informace o delegátech obecně naleznete v tématu [Delegáti](../../csharp/programming-guide/delegates/index.md) a [delegáti](../../visual-basic/programming-guide/language-features/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="69660-107">For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="69660-108">Další informace o výrazech lambda v jazyce C# a visual basicu naleznete v [tématu Lambda Expressions](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="69660-108">For more information about lambda expressions in C# and Visual Basic, see [Lambda Expressions](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="func-delegate"></a><span data-ttu-id="69660-109">Delegát Func</span><span class="sxs-lookup"><span data-stu-id="69660-109">Func Delegate</span></span>

<span data-ttu-id="69660-110">Delegát `Func` zapouzdřuje metodu, která vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="69660-110">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="69660-111">V `Func` podpisu parametr posledního nebo zcela pravého typu vždy určuje návratový typ.</span><span class="sxs-lookup"><span data-stu-id="69660-111">In a `Func` signature, the last, or rightmost, type parameter always specifies the return type.</span></span> <span data-ttu-id="69660-112">Jednou z běžných příčin chyb kompilátoru je pokus <xref:System.Func%602?displayProperty=nameWithType>o předání dvou vstupních parametrů do ; ve skutečnosti tento typ trvá pouze jeden vstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="69660-112">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="69660-113">Rozhraní .NET definuje 17 `Func` <xref:System.Func%601?displayProperty=nameWithType>verzí <xref:System.Func%602?displayProperty=nameWithType> <xref:System.Func%603?displayProperty=nameWithType>aplikace : , <xref:System.Func%6017?displayProperty=nameWithType>, a tak dále až do .</span><span class="sxs-lookup"><span data-stu-id="69660-113">.NET defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>

## <a name="action-delegate"></a><span data-ttu-id="69660-114">Delegát akce</span><span class="sxs-lookup"><span data-stu-id="69660-114">Action Delegate</span></span>

<span data-ttu-id="69660-115">Delegát <xref:System.Action?displayProperty=nameWithType> zapouzdřuje metodu (Sub v jazyce Visual Basic), která nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="69660-115">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in Visual Basic) that does not return a value.</span></span> <span data-ttu-id="69660-116">V `Action` podpisu typu představují parametry typu pouze vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="69660-116">In an `Action` type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="69660-117">Stejně jako `Func`rozhraní .NET definuje `Action`17 verzí aplikace od verze, která nemá žádné parametry typu, až po verzi, která má 16 parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="69660-117">Like `Func`, .NET defines 17 versions of `Action`, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>

## <a name="example"></a><span data-ttu-id="69660-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="69660-118">Example</span></span>

<span data-ttu-id="69660-119">Následující příklad pro <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> metodu ukazuje, jak vyjádřit delegáty Func a Action pomocí výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="69660-119">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a><span data-ttu-id="69660-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="69660-120">See also</span></span>

- [<span data-ttu-id="69660-121">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="69660-121">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
