---
title: New – omezení - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 7c788be52010cdfadbd3c03f9e570815d25bdbef
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401485"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="50859-102">New – omezení (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="50859-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="50859-103">`new` Omezení určuje, že argument typu v deklaraci obecné třídy musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="50859-103">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="50859-104">Použít `new` omezení, typ nemůže být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="50859-104">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="50859-105">Použít `new` omezení parametru typu, když obecné třídy vytvoří nové instance daného typu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="50859-105">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="50859-106">Při použití `new()` omezení s jinými omezeními, musí se zadat poslední:</span><span class="sxs-lookup"><span data-stu-id="50859-106">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="50859-107">Další informace najdete v tématu [omezení parametrů typů](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="50859-107">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="50859-108">Můžete také použít `new` – klíčové slovo do [vytvořit instanci typu](../operators/new-operator.md) nebo stejně jako [modifikátoru deklarace člena](new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="50859-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="50859-109">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="50859-109">C# language specification</span></span>

<span data-ttu-id="50859-110">Další informace najdete v tématu [omezení parametru typu](~/_csharplang/spec/classes.md#type-parameter-constraints) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="50859-110">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="50859-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50859-111">See also</span></span>

- [<span data-ttu-id="50859-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="50859-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="50859-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="50859-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="50859-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="50859-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="50859-115">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="50859-115">Generics</span></span>](../../programming-guide/generics/index.md)
