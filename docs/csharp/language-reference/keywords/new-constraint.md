---
title: nové omezení – C# referenční informace
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: cd67aeb82d736b8941b0637494089723e7815505
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713358"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="9db27-102">New – omezeníC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="9db27-102">new constraint (C# Reference)</span></span>

<span data-ttu-id="9db27-103">Omezení `new` určuje, že argument typu v deklaraci obecné třídy musí mít veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="9db27-103">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="9db27-104">Chcete-li použít omezení `new`, typ nemůže být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="9db27-104">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="9db27-105">Použijte omezení `new` na parametr typu, když obecná třída vytvoří nové instance typu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9db27-105">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="9db27-106">Použijete-li omezení `new()` s jinými omezeními, je nutné ji zadat jako poslední:</span><span class="sxs-lookup"><span data-stu-id="9db27-106">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="9db27-107">Další informace najdete v tématu [omezení parametrů typu](../../programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="9db27-107">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="9db27-108">Pomocí klíčového slova `new` lze také [vytvořit instanci typu](../operators/new-operator.md) nebo jako [Modifikátor deklarace členů](new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="9db27-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9db27-109">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9db27-109">C# language specification</span></span>

<span data-ttu-id="9db27-110">Další informace naleznete v části [omezení parametrů typu](~/_csharplang/spec/classes.md#type-parameter-constraints) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="9db27-110">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9db27-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9db27-111">See also</span></span>

- [<span data-ttu-id="9db27-112">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="9db27-112">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="9db27-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9db27-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9db27-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9db27-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9db27-115">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="9db27-115">Generics</span></span>](../../programming-guide/generics/index.md)
