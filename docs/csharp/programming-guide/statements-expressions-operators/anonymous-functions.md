---
title: Anonymní funkce – programovací průvodce C#
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: cfb0190ee263e65e8130a8925f76357a382eafa3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711997"
---
# <a name="anonymous-functions-c-programming-guide"></a><span data-ttu-id="a0e83-102">Anonymní funkce (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a0e83-102">Anonymous functions (C# Programming Guide)</span></span>

<span data-ttu-id="a0e83-103">Anonymní funkce je "inline" příkaz nebo výraz, který lze použít všude tam, kde je očekáván typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="a0e83-103">An anonymous function is an "inline" statement or expression that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="a0e83-104">Můžete ji použít k inicializaci pojmenovaného delegáta nebo předat jej namísto pojmenovaného typu delegáta jako parametr metody.</span><span class="sxs-lookup"><span data-stu-id="a0e83-104">You can use it to initialize a named delegate or pass it instead of a named delegate type as a method parameter.</span></span>

<span data-ttu-id="a0e83-105">K vytvoření anonymní funkce můžete použít [výraz lambda](lambda-expressions.md) nebo [anonymní metodu.](../../language-reference/operators/delegate-operator.md)</span><span class="sxs-lookup"><span data-stu-id="a0e83-105">You can use a [lambda expression](lambda-expressions.md) or an [anonymous method](../../language-reference/operators/delegate-operator.md) to create an anonymous function.</span></span> <span data-ttu-id="a0e83-106">Doporučujeme používat lambda výrazy, protože poskytují stručnější a expresivní způsob psaní vřádkového kódu.</span><span class="sxs-lookup"><span data-stu-id="a0e83-106">We recommend using lambda expressions as they provide more concise and expressive way to write inline code.</span></span> <span data-ttu-id="a0e83-107">Na rozdíl od anonymních metod mohou být některé typy výrazů lambda převedeny na typy stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="a0e83-107">Unlike anonymous methods, some types of lambda expressions can be converted to the expression tree types.</span></span>

## <a name="the-evolution-of-delegates-in-c"></a><span data-ttu-id="a0e83-108">Vývoj delegátů v C\#</span><span class="sxs-lookup"><span data-stu-id="a0e83-108">The Evolution of Delegates in C\#</span></span>

 <span data-ttu-id="a0e83-109">V C# 1.0 jste vytvořili instanci delegáta explicitně inicializovat s metodou, která byla definována jinde v kódu.</span><span class="sxs-lookup"><span data-stu-id="a0e83-109">In C# 1.0, you created an instance of a delegate by explicitly initializing it with a method that was defined elsewhere in the code.</span></span> <span data-ttu-id="a0e83-110">C# 2.0 představil koncept anonymní metody jako způsob, jak psát nepojmenované bloky vřádlých prohlášení, které mohou být provedeny v vyvolání delegáta.</span><span class="sxs-lookup"><span data-stu-id="a0e83-110">C# 2.0 introduced the concept of anonymous methods as a way to write unnamed inline statement blocks that can be executed in a delegate invocation.</span></span> <span data-ttu-id="a0e83-111">C# 3.0 představil lambda výrazy, které jsou podobné v pojetí anonymní metody, ale výraznější a stručnější.</span><span class="sxs-lookup"><span data-stu-id="a0e83-111">C# 3.0 introduced lambda expressions, which are similar in concept to anonymous methods but more expressive and concise.</span></span> <span data-ttu-id="a0e83-112">Tyto dvě funkce jsou souhrnně *označovány*jako anonymní funkce .</span><span class="sxs-lookup"><span data-stu-id="a0e83-112">These two features are known collectively as *anonymous functions*.</span></span> <span data-ttu-id="a0e83-113">Obecně platí, že aplikace, které cílí na verzi 3.5 a novější rozhraní .NET Framework, by měly používat výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="a0e83-113">In general, applications that target version 3.5 and later of the .NET Framework should use lambda expressions.</span></span>  
  
 <span data-ttu-id="a0e83-114">Následující příklad ukazuje vývoj vytvoření delegáta z C# 1.0 do C# 3.0:</span><span class="sxs-lookup"><span data-stu-id="a0e83-114">The following example demonstrates the evolution of delegate creation from C# 1.0 to C# 3.0:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="a0e83-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a0e83-115">C# language specification</span></span>

<span data-ttu-id="a0e83-116">Další informace naleznete v části [Anonymní výrazy funkcí](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a0e83-116">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a0e83-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0e83-117">See also</span></span>

- [<span data-ttu-id="a0e83-118">Příkazy, výrazy a operátory</span><span class="sxs-lookup"><span data-stu-id="a0e83-118">Statements, Expressions, and Operators</span></span>](./index.md)
- [<span data-ttu-id="a0e83-119">Lambda výrazy</span><span class="sxs-lookup"><span data-stu-id="a0e83-119">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="a0e83-120">Delegáty</span><span class="sxs-lookup"><span data-stu-id="a0e83-120">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="a0e83-121">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="a0e83-121">Expression Trees (C#)</span></span>](../concepts/expression-trees/index.md)
