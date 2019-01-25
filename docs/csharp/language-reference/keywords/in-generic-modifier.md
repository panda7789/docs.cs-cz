---
title: in (generický modifikátor) - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: f736540a37d3226bccfc07749dcf06ca018663e8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694566"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="26c22-102">in (generický modifikátor) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="26c22-102">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="26c22-103">Pro parametry obecného typu `in` – klíčové slovo určuje, že parametr typu je kontravariant.</span><span class="sxs-lookup"><span data-stu-id="26c22-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="26c22-104">Můžete použít `in` – klíčové slovo v obecných rozhraních a delegátech.</span><span class="sxs-lookup"><span data-stu-id="26c22-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="26c22-105">Kontravariance umožňuje použít méně odvozený typ, než je určeno obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="26c22-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="26c22-106">To umožňuje implicitní převod z třídy, které implementují rozhraní kontravariantní a implicitní převod delegujících typů.</span><span class="sxs-lookup"><span data-stu-id="26c22-106">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="26c22-107">Kovariance a kontravariance v parametrech obecného typu jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="26c22-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="26c22-108">Typ mohou být deklarovány kontravariantní v obecné rozhraní nebo delegát pouze v případě, že definuje typ parametrů, metody a ne návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="26c22-108">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="26c22-109">`In`, `ref`, a `out` parametry musí být neutrální, to znamená jsou ani kovariantní nebo kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="26c22-109">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="26c22-110">Rozhraní, která má parametr kontravariantního typu umožňuje její metody pro přijímání argumentů méně odvozené typy než je zadáno parametrem typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="26c22-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="26c22-111">Například v <xref:System.Collections.Generic.IComparer%601> rozhraní, typ T je kontravariantní, můžete přiřadit objektu `IComparer<Person>` typu na objekt `IComparer<Employee>` typ bez použití jakékoli speciální převod metody, pokud `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="26c22-111">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="26c22-112">Kontravariantní delegát může být přiřazen jiný delegát stejného typu, ale s méně odvozený parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="26c22-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="26c22-113">Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="26c22-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="26c22-114">Kontravariantní obecné rozhraní</span><span class="sxs-lookup"><span data-stu-id="26c22-114">Contravariant generic interface</span></span>

<span data-ttu-id="26c22-115">Následující příklad ukazuje, jak deklarovat, rozšíření a implementovat obecné rozhraní kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="26c22-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="26c22-116">Také ukazuje, jak můžete použít implicitní převod pro třídy, které toto rozhraní implementují.</span><span class="sxs-lookup"><span data-stu-id="26c22-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="26c22-117">Kontravariantní obecného delegáta</span><span class="sxs-lookup"><span data-stu-id="26c22-117">Contravariant generic delegate</span></span>

<span data-ttu-id="26c22-118">Následující příklad ukazuje, jak deklarovat, vytváření instancí a vyvolání obecného delegátu kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="26c22-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="26c22-119">Profil také ukazuje, jak lze implicitně převést typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="26c22-119">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="26c22-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="26c22-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="26c22-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26c22-121">See also</span></span>

- [<span data-ttu-id="26c22-122">out</span><span class="sxs-lookup"><span data-stu-id="26c22-122">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="26c22-123">Kovariance a kontravariance</span><span class="sxs-lookup"><span data-stu-id="26c22-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="26c22-124">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="26c22-124">Modifiers</span></span>](modifiers.md)
