---
description: New – Referenční dokumentace jazyka C#
title: New – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: f7b097729fe973aba7b85c48e1b1033aade83080
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139447"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="ef074-103">New – omezení (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ef074-103">new constraint (C# Reference)</span></span>

<span data-ttu-id="ef074-104">`new`Omezení určuje, že argument typu v deklaraci obecné třídy musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="ef074-104">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="ef074-105">Chcete-li použít `new` omezení, typ nemůže být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="ef074-105">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="ef074-106">Použijte `new` omezení na parametr typu, když obecná třída vytvoří nové instance typu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ef074-106">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="ef074-107">Použijete-li `new()` omezení s jinými omezeními, musí být zadána jako poslední:</span><span class="sxs-lookup"><span data-stu-id="ef074-107">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="ef074-108">Další informace najdete v tématu [omezení parametrů typu](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="ef074-108">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="ef074-109">Klíčové slovo lze použít také `new` k [vytvoření instance typu](../operators/new-operator.md) nebo jako [Modifikátor deklarace člena](new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="ef074-109">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ef074-110">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ef074-110">C# language specification</span></span>

<span data-ttu-id="ef074-111">Další informace naleznete v části [omezení parametrů typu](~/_csharplang/spec/classes.md#type-parameter-constraints) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="ef074-111">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef074-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef074-112">See also</span></span>

- [<span data-ttu-id="ef074-113">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ef074-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ef074-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ef074-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ef074-115">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ef074-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ef074-116">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="ef074-116">Generics</span></span>](../../programming-guide/generics/index.md)
