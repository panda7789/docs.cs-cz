---
title: v (obecný modifikátor) - C# Odkaz
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 57da13f6dc6719166b9051afeb2532ba5fbeff3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713476"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="dae6e-102">in (generický modifikátor) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="dae6e-102">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="dae6e-103">Pro parametry obecného `in` typu klíčové slovo určuje, že parametr typu je kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="dae6e-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="dae6e-104">Klíčové `in` slovo můžete použít v obecných rozhraních a delegátech.</span><span class="sxs-lookup"><span data-stu-id="dae6e-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="dae6e-105">Contravariance umožňuje použít méně odvozený typ, než je zadán obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="dae6e-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="dae6e-106">To umožňuje implicitní převod tříd, které implementují rozhraní contravariant a implicitní převod typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="dae6e-106">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="dae6e-107">Kovariance a contravariance v parametrech obecného typu jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="dae6e-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="dae6e-108">Typ může být deklarován jako contravariant v obecném rozhraní nebo delegát pouze v případě, že definuje typ parametrů metody a nikoli návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="dae6e-108">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="dae6e-109">`In`, `ref`a `out` parametry musí být invariantní, což znamená, že nejsou ani kovariantní, ani kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="dae6e-109">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="dae6e-110">Rozhraní, které má parametr typu contravariant umožňuje jeho metody přijímat argumenty méně odvozených typů, než které jsou určeny parametrem typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dae6e-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="dae6e-111">Například v <xref:System.Collections.Generic.IComparer%601> rozhraní, typ T je contravariant, můžete `IComparer<Person>` přiřadit objekt typu `IComparer<Employee>` k objektu typu bez `Employee` použití `Person`speciálních metod převodu, pokud dědí .</span><span class="sxs-lookup"><span data-stu-id="dae6e-111">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="dae6e-112">Contravariantní delegát může být přiřazen jiný delegát stejného typu, ale s méně odvozené obecný typ parametru.</span><span class="sxs-lookup"><span data-stu-id="dae6e-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="dae6e-113">Další informace naleznete [v tématu Kovariance a Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="dae6e-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="dae6e-114">Kontravariantní obecné rozhraní</span><span class="sxs-lookup"><span data-stu-id="dae6e-114">Contravariant generic interface</span></span>

<span data-ttu-id="dae6e-115">Následující příklad ukazuje, jak deklarovat, rozšířit a implementovat kontravariantní obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dae6e-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="dae6e-116">Také ukazuje, jak můžete použít implicitní převod pro třídy, které implementují toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dae6e-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="dae6e-117">Kontravariantní obecný delegát</span><span class="sxs-lookup"><span data-stu-id="dae6e-117">Contravariant generic delegate</span></span>

<span data-ttu-id="dae6e-118">Následující příklad ukazuje, jak deklarovat, instanci a vyvolat kontravariantní obecný delegát.</span><span class="sxs-lookup"><span data-stu-id="dae6e-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="dae6e-119">Také ukazuje, jak můžete implicitně převést typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="dae6e-119">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="dae6e-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dae6e-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="dae6e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="dae6e-121">See also</span></span>

- [<span data-ttu-id="dae6e-122">ven</span><span class="sxs-lookup"><span data-stu-id="dae6e-122">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="dae6e-123">Kovariance a kontravariance</span><span class="sxs-lookup"><span data-stu-id="dae6e-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="dae6e-124">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="dae6e-124">Modifiers</span></span>](index.md)
