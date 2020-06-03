---
title: New – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 6f6d1b663d03dc9b3adf0e7055dcffacc79d83dc
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795336"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="b1e9f-102">New – omezení (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b1e9f-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="b1e9f-103">`new`Omezení určuje, že argument typu v deklaraci obecné třídy musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="b1e9f-103">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="b1e9f-104">Chcete-li použít `new` omezení, typ nemůže být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="b1e9f-104">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="b1e9f-105">Použijte `new` omezení na parametr typu, když obecná třída vytvoří nové instance typu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b1e9f-105">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="b1e9f-106">Použijete-li `new()` omezení s jinými omezeními, musí být zadána jako poslední:</span><span class="sxs-lookup"><span data-stu-id="b1e9f-106">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="b1e9f-107">Další informace najdete v tématu [omezení parametrů typu](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b1e9f-107">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="b1e9f-108">Klíčové slovo lze použít také `new` k [vytvoření instance typu](../operators/new-operator.md) nebo jako [Modifikátor deklarace člena](new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="b1e9f-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b1e9f-109">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b1e9f-109">C# language specification</span></span>

<span data-ttu-id="b1e9f-110">Další informace naleznete v části [omezení parametrů typu](~/_csharplang/spec/classes.md#type-parameter-constraints) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="b1e9f-110">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b1e9f-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1e9f-111">See also</span></span>

- [<span data-ttu-id="b1e9f-112">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b1e9f-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b1e9f-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b1e9f-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b1e9f-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b1e9f-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b1e9f-115">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="b1e9f-115">Generics</span></span>](../../programming-guide/generics/index.md)
