---
title: Delegate – operátor C# – reference
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 1fe281776bd75d8fa869065cd24e85f04fec849d
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331773"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="4edfa-102">Delegate – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="4edfa-102">delegate operator (C# reference)</span></span>

<span data-ttu-id="4edfa-103">`delegate` Operátor vytvoří anonymní metodu, která může být převedena na typ delegáta:</span><span class="sxs-lookup"><span data-stu-id="4edfa-103">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](~/samples/csharp/language-reference/operators/DelegateOperator.cs#AnonymousMethod)]

<span data-ttu-id="4edfa-104">Počínaje C# 3 [výrazy lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) poskytují výstižnější a výrazný způsob vytváření anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="4edfa-104">Beginning with C# 3, [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="4edfa-105">Použijte [operátor = >](lambda-operator.md) pro vytvoření výrazu lambda:</span><span class="sxs-lookup"><span data-stu-id="4edfa-105">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>

[!code-csharp-interactive[lambda expression](~/samples/csharp/language-reference/operators/DelegateOperator.cs#Lambda)]

<span data-ttu-id="4edfa-106">Při použití `delegate` operátoru můžete seznam parametrů vynechat.</span><span class="sxs-lookup"><span data-stu-id="4edfa-106">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="4edfa-107">Pokud to uděláte, můžete vytvořenou anonymní metodu převést na typ delegáta s libovolným seznamem parametrů, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="4edfa-107">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](~/samples/csharp/language-reference/operators/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="4edfa-108">To je jediná funkce anonymních metod, které výrazy lambda nepodporují.</span><span class="sxs-lookup"><span data-stu-id="4edfa-108">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="4edfa-109">Ve všech ostatních případech je výraz lambda upřednostňovaným způsobem, jak psát vložený kód.</span><span class="sxs-lookup"><span data-stu-id="4edfa-109">In all other cases, a lambda expression is a preferred way to write inline code.</span></span> <span data-ttu-id="4edfa-110">Další informace o funkcích výrazů lambda, například zachycení vnějších proměnných, naleznete v tématu [lambda Expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4edfa-110">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="4edfa-111">Pomocí `delegate` klíčového slova také deklarujete [typ delegáta](../builtin-types/reference-types.md#the-delegate-type).</span><span class="sxs-lookup"><span data-stu-id="4edfa-111">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4edfa-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4edfa-112">C# language specification</span></span>

<span data-ttu-id="4edfa-113">Další informace naleznete v části [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="4edfa-113">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4edfa-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4edfa-114">See also</span></span>

- [<span data-ttu-id="4edfa-115">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="4edfa-115">C# reference</span></span>](../index.md)
- [<span data-ttu-id="4edfa-116">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4edfa-116">C# operators</span></span>](index.md)
