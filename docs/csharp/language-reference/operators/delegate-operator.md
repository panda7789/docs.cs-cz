---
title: operátor delegáta – odkaz jazyka C#
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 1dd27fe5fdfdc1bc8a63e1298da00d252e800a72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847336"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="91133-102">operátor delegáta (odkaz C# )</span><span class="sxs-lookup"><span data-stu-id="91133-102">delegate operator (C# reference)</span></span>

<span data-ttu-id="91133-103">Operátor `delegate` vytvoří anonymní metodu, kterou lze převést na typ delegáta:</span><span class="sxs-lookup"><span data-stu-id="91133-103">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](snippets/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> <span data-ttu-id="91133-104">Počínaje C# 3, lambda výrazy poskytují stručnější a expresivní způsob, jak vytvořit anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="91133-104">Beginning with C# 3, lambda expressions provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="91133-105">Pomocí [operátoru =>](lambda-operator.md) vytvořte výraz lambda:</span><span class="sxs-lookup"><span data-stu-id="91133-105">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>
>
> [!code-csharp-interactive[lambda expression](snippets/DelegateOperator.cs#Lambda)]
>
> <span data-ttu-id="91133-106">Další informace o funkcích výrazů lambda, například zachycení vnějších proměnných, naleznete v [tématu Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="91133-106">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="91133-107">Při použití `delegate` operátoru můžete vynechat seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="91133-107">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="91133-108">Pokud tak učiníte, vytvořená anonymní metoda může být převedena na typ delegáta s libovolným seznamem parametrů, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="91133-108">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](snippets/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="91133-109">To je jediná funkce anonymnímetody, která není podporována lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="91133-109">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="91133-110">Ve všech ostatních případech lambda výraz je upřednostňovaný způsob, jak psát vřádkový kód.</span><span class="sxs-lookup"><span data-stu-id="91133-110">In all other cases, a lambda expression is a preferred way to write inline code.</span></span>

<span data-ttu-id="91133-111">Klíčové `delegate` slovo můžete také použít k deklarování [typu delegáta](../builtin-types/reference-types.md#the-delegate-type).</span><span class="sxs-lookup"><span data-stu-id="91133-111">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="91133-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="91133-112">C# language specification</span></span>

<span data-ttu-id="91133-113">Další informace naleznete v části [Anonymní výrazy funkcí](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="91133-113">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="91133-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="91133-114">See also</span></span>

- [<span data-ttu-id="91133-115">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="91133-115">C# reference</span></span>](../index.md)
- [<span data-ttu-id="91133-116">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="91133-116">C# operators</span></span>](index.md)
- [<span data-ttu-id="91133-117">= operátor></span><span class="sxs-lookup"><span data-stu-id="91133-117">=> operator</span></span>](lambda-operator.md)
