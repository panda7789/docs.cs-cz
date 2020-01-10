---
title: in (generický modifikátor) – C# referenční informace
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 57da13f6dc6719166b9051afeb2532ba5fbeff3a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713476"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="7330e-102">in (generický modifikátor) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7330e-102">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="7330e-103">Pro parametry obecného typu Určuje klíčové slovo `in`, že parametr typu je kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="7330e-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="7330e-104">Klíčové slovo `in` lze použít v obecných rozhraních a delegátech.</span><span class="sxs-lookup"><span data-stu-id="7330e-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="7330e-105">Kontravariance umožňuje použít méně odvozený typ, než který je určen obecným parametrem.</span><span class="sxs-lookup"><span data-stu-id="7330e-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="7330e-106">To umožňuje implicitní převod tříd, které implementují kontravariantní rozhraní a implicitní převod typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="7330e-106">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="7330e-107">Kovariance a kontravariance v parametrech obecného typu jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="7330e-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="7330e-108">Typ může být deklarovaný jako kontravariantní v obecném rozhraní nebo delegátu jenom v případě, že definuje typ parametrů metody a nikoli návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="7330e-108">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="7330e-109">parametry `In`, `ref`a `out` musí být invariantní, což znamená, že nejsou ani kovariantní ani kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="7330e-109">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="7330e-110">Rozhraní, které má parametr kontravariantního typu, umožňuje svým metodám přijímat argumenty méně odvozených typů než hodnoty určené parametrem typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7330e-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="7330e-111">Například v rozhraní <xref:System.Collections.Generic.IComparer%601> typ T je kontravariantní, můžete přiřadit objekt `IComparer<Person>` typu objektu `IComparer<Employee>`ho typu bez použití jakýchkoli speciálních metod převodu, pokud `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="7330e-111">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="7330e-112">Kontravariantnímu delegátu lze přiřadit jiný delegát stejného typu, ale s menším odvozeným parametrem obecného typu.</span><span class="sxs-lookup"><span data-stu-id="7330e-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="7330e-113">Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="7330e-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="7330e-114">Kontravariantní obecné rozhraní</span><span class="sxs-lookup"><span data-stu-id="7330e-114">Contravariant generic interface</span></span>

<span data-ttu-id="7330e-115">Následující příklad ukazuje, jak deklarovat, rozšiřuje a implementovat kontravariantní obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7330e-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="7330e-116">Také ukazuje, jak lze použít implicitní převod pro třídy, které implementují toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7330e-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="7330e-117">Kontravariantní obecný delegát</span><span class="sxs-lookup"><span data-stu-id="7330e-117">Contravariant generic delegate</span></span>

<span data-ttu-id="7330e-118">Následující příklad ukazuje, jak deklarovat, vytvářet instance a vyvolat kontravariantního obecného delegáta.</span><span class="sxs-lookup"><span data-stu-id="7330e-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="7330e-119">Také ukazuje, jak lze implicitně převést typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="7330e-119">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="7330e-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7330e-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7330e-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7330e-121">See also</span></span>

- [<span data-ttu-id="7330e-122">out</span><span class="sxs-lookup"><span data-stu-id="7330e-122">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="7330e-123">Kovariance a kontravariance</span><span class="sxs-lookup"><span data-stu-id="7330e-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="7330e-124">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="7330e-124">Modifiers</span></span>](index.md)
