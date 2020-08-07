---
title: Delegate – operátor – reference jazyka C#
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: f7cd7caf11d9f076a5d6e82aae696c914bd60e44
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916848"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="9dc2a-102">Delegate – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9dc2a-102">delegate operator (C# reference)</span></span>

<span data-ttu-id="9dc2a-103">`delegate`Operátor vytvoří anonymní metodu, která může být převedena na typ delegáta:</span><span class="sxs-lookup"><span data-stu-id="9dc2a-103">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](snippets/shared/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> <span data-ttu-id="9dc2a-104">Počínaje jazykem C# 3 výrazy lambda poskytují výstižnější a výrazný způsob vytvoření anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="9dc2a-104">Beginning with C# 3, lambda expressions provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="9dc2a-105">Použijte [operátor =>](lambda-operator.md) pro vytvoření výrazu lambda:</span><span class="sxs-lookup"><span data-stu-id="9dc2a-105">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>
>
> [!code-csharp-interactive[lambda expression](snippets/shared/DelegateOperator.cs#Lambda)]
>
> <span data-ttu-id="9dc2a-106">Další informace o funkcích výrazů lambda, například zachycení vnějších proměnných, naleznete v tématu [lambda Expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="9dc2a-106">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="9dc2a-107">Při použití `delegate` operátoru můžete seznam parametrů vynechat.</span><span class="sxs-lookup"><span data-stu-id="9dc2a-107">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="9dc2a-108">Pokud to uděláte, můžete vytvořenou anonymní metodu převést na typ delegáta s libovolným seznamem parametrů, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="9dc2a-108">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](snippets/shared/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="9dc2a-109">To je jediná funkce anonymních metod, které výrazy lambda nepodporují.</span><span class="sxs-lookup"><span data-stu-id="9dc2a-109">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="9dc2a-110">Ve všech ostatních případech je výraz lambda upřednostňovaným způsobem, jak psát vložený kód.</span><span class="sxs-lookup"><span data-stu-id="9dc2a-110">In all other cases, a lambda expression is a preferred way to write inline code.</span></span>

<span data-ttu-id="9dc2a-111">Pomocí `delegate` klíčového slova také deklarujete [typ delegáta](../builtin-types/reference-types.md#the-delegate-type).</span><span class="sxs-lookup"><span data-stu-id="9dc2a-111">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9dc2a-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9dc2a-112">C# language specification</span></span>

<span data-ttu-id="9dc2a-113">Další informace naleznete v části [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="9dc2a-113">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9dc2a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9dc2a-114">See also</span></span>

- [<span data-ttu-id="9dc2a-115">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="9dc2a-115">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9dc2a-116">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="9dc2a-116">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="9dc2a-117">=> – operátor</span><span class="sxs-lookup"><span data-stu-id="9dc2a-117">=> operator</span></span>](lambda-operator.md)
