---
title: Anonymní funkce – Průvodce programováním v C#
description: Přečtěte si o anonymních funkcích. Můžete použít výraz lambda nebo anonymní metodu pro vytvoření anonymní funkce.
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 1fde7d535054f09d55018a010468776622ebfba7
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063260"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="0b26e-104">Anonymní funkce (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="0b26e-104">Anonymous functions (C# Programming Guide)</span></span>

<span data-ttu-id="0b26e-105">Anonymní funkce je "vložený" příkaz nebo výraz, který lze použít všude, kde je očekáván typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="0b26e-105">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="0b26e-106">Můžete ji použít k inicializaci pojmenovaného delegáta nebo ho předat místo pojmenovaného typu delegáta jako parametr metody.</span><span class="sxs-lookup"><span data-stu-id="0b26e-106">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>

<span data-ttu-id="0b26e-107">Můžete použít [výraz lambda](../../language-reference/operators/lambda-expressions.md) nebo [anonymní metodu](../../language-reference/operators/delegate-operator.md) pro vytvoření anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="0b26e-107">You can use a [lambda expression](../../language-reference/operators/lambda-expressions.md) or an [anonymous method](../../language-reference/operators/delegate-operator.md) to create an anonymous function.</span></span> <span data-ttu-id="0b26e-108">Doporučujeme použít výrazy lambda, protože poskytují výstižnější a výrazný způsob psaní vloženého kódu.</span><span class="sxs-lookup"><span data-stu-id="0b26e-108">We recommend using lambda expressions as they provide more concise and expressive way to write inline code.</span></span> <span data-ttu-id="0b26e-109">Na rozdíl od anonymních metod lze některé typy výrazů lambda převést na typy stromu výrazů.</span><span class="sxs-lookup"><span data-stu-id="0b26e-109">Unlike anonymous methods, some types of lambda expressions can be converted to the expression tree types.</span></span>

## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="0b26e-110">Vývoj delegátů v jazyce C\#</span><span class="sxs-lookup"><span data-stu-id="0b26e-110">The Evolution of Delegates in C\#</span></span>

 <span data-ttu-id="0b26e-111">V C# 1,0 jste vytvořili instanci delegáta explicitně inicializací s metodou, která byla definována jinde v kódu.</span><span class="sxs-lookup"><span data-stu-id="0b26e-111">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="0b26e-112">C# 2,0 představil koncept anonymních metod jako způsob zápisu nepojmenovaných bloků vložených příkazů, které mohou být provedeny při volání delegáta.</span><span class="sxs-lookup"><span data-stu-id="0b26e-112">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="0b26e-113">C# 3,0 představil výrazy lambda, které jsou podobné v konceptu anonymním metodám, ale častěji a stručnější.</span><span class="sxs-lookup"><span data-stu-id="0b26e-113">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="0b26e-114">Tyto dvě funkce se společně nazývají *anonymní funkce*.</span><span class="sxs-lookup"><span data-stu-id="0b26e-114">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="0b26e-115">Obecně platí, že aplikace, které cílí na .NET Framework 3,5 nebo novější, by měly používat výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="0b26e-115">In general, applications that target .NET Framework 3.5 or later should use lambda expressions.</span></span>  
  
 <span data-ttu-id="0b26e-116">Následující příklad ukazuje vývoj vytvoření delegáta z C# 1,0 na C# 3,0:</span><span class="sxs-lookup"><span data-stu-id="0b26e-116">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0b26e-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0b26e-117">C# language specification</span></span>

<span data-ttu-id="0b26e-118">Další informace naleznete v části [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0b26e-118">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0b26e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b26e-119">See also</span></span>

- [<span data-ttu-id="0b26e-120">Příkazy, výrazy a operátory</span><span class="sxs-lookup"><span data-stu-id="0b26e-120">Statements, Expressions, and Operators</span></span>](./index.md)
- [<span data-ttu-id="0b26e-121">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="0b26e-121">Lambda Expressions</span></span>](../../language-reference/operators/lambda-expressions.md)
- [<span data-ttu-id="0b26e-122">Delegáty</span><span class="sxs-lookup"><span data-stu-id="0b26e-122">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="0b26e-123">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="0b26e-123">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
