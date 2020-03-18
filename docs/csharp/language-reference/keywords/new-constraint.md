---
title: nové omezení – odkaz jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: cd67aeb82d736b8941b0637494089723e7815505
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713358"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="3ea9c-102">nové omezení (odkaz Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3ea9c-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="3ea9c-103">Omezení `new` určuje, že argument typu v deklaraci obecné třídy musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="3ea9c-103">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="3ea9c-104">Chcete-li `new` použít omezení, typ nemůže být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="3ea9c-104">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="3ea9c-105">Použijte `new` omezení na parametr typu, když obecná třída vytvoří nové instance typu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3ea9c-105">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="3ea9c-106">Při použití `new()` omezení s jinými omezeními musí být zadáno jako poslední:</span><span class="sxs-lookup"><span data-stu-id="3ea9c-106">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="3ea9c-107">Další informace naleznete [v tématu Omezení parametrů typu](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="3ea9c-107">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="3ea9c-108">Klíčové slovo můžete také použít k [vytvoření instance typu](../operators/new-operator.md) nebo jako [modifikátor deklarace člena](new-modifier.md). `new`</span><span class="sxs-lookup"><span data-stu-id="3ea9c-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3ea9c-109">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3ea9c-109">C# language specification</span></span>

<span data-ttu-id="3ea9c-110">Další informace naleznete v části [Omezení parametrů typu](~/_csharplang/spec/classes.md#type-parameter-constraints) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="3ea9c-110">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3ea9c-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ea9c-111">See also</span></span>

- [<span data-ttu-id="3ea9c-112">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3ea9c-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="3ea9c-113">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3ea9c-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3ea9c-114">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="3ea9c-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3ea9c-115">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="3ea9c-115">Generics</span></span>](../../programming-guide/generics/index.md)
