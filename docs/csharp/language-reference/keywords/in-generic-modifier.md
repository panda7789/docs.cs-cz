---
description: in (generický modifikátor) – Referenční dokumentace jazyka C#
title: in (generický modifikátor) – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: feae17be7bdf29f6bc90e8c85b3878d4714699f4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118452"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="20eb5-103">in (generický modifikátor) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="20eb5-103">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="20eb5-104">Pro parametry obecného typu `in` Určuje klíčové slovo, že parametr typu je kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="20eb5-104">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="20eb5-105">Klíčové slovo lze použít `in` v obecných rozhraních a delegátech.</span><span class="sxs-lookup"><span data-stu-id="20eb5-105">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="20eb5-106">Kontravariance umožňuje použít méně odvozený typ, než který je určen obecným parametrem.</span><span class="sxs-lookup"><span data-stu-id="20eb5-106">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="20eb5-107">To umožňuje implicitní převod tříd, které implementují kontravariantní rozhraní a implicitní převod typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="20eb5-107">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="20eb5-108">Kovariance a kontravariance v parametrech obecného typu jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="20eb5-108">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="20eb5-109">Typ může být deklarovaný jako kontravariantní v obecném rozhraní nebo delegátu jenom v případě, že definuje typ parametrů metody a nikoli návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="20eb5-109">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="20eb5-110">`In``ref`parametry, a `out` musí být invariantní, což znamená, že nejsou ani kovariantní nebo kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="20eb5-110">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="20eb5-111">Rozhraní, které má parametr kontravariantního typu, umožňuje svým metodám přijímat argumenty méně odvozených typů než hodnoty určené parametrem typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="20eb5-111">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="20eb5-112">Například v <xref:System.Collections.Generic.IComparer%601> rozhraní typ T je kontravariantní, můžete přiřadit objekt `IComparer<Person>` typu k objektu `IComparer<Employee>` typu bez použití jakýchkoli speciálních metod převodu, pokud `Employee` zdědí `Person` .</span><span class="sxs-lookup"><span data-stu-id="20eb5-112">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="20eb5-113">Kontravariantnímu delegátu lze přiřadit jiný delegát stejného typu, ale s menším odvozeným parametrem obecného typu.</span><span class="sxs-lookup"><span data-stu-id="20eb5-113">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="20eb5-114">Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="20eb5-114">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="20eb5-115">Kontravariantní obecné rozhraní</span><span class="sxs-lookup"><span data-stu-id="20eb5-115">Contravariant generic interface</span></span>

<span data-ttu-id="20eb5-116">Následující příklad ukazuje, jak deklarovat, rozšiřuje a implementovat kontravariantní obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="20eb5-116">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="20eb5-117">Také ukazuje, jak lze použít implicitní převod pro třídy, které implementují toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="20eb5-117">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="20eb5-118">Kontravariantní obecný delegát</span><span class="sxs-lookup"><span data-stu-id="20eb5-118">Contravariant generic delegate</span></span>

<span data-ttu-id="20eb5-119">Následující příklad ukazuje, jak deklarovat, vytvářet instance a vyvolat kontravariantního obecného delegáta.</span><span class="sxs-lookup"><span data-stu-id="20eb5-119">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="20eb5-120">Také ukazuje, jak lze implicitně převést typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="20eb5-120">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="20eb5-121">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="20eb5-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="20eb5-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="20eb5-122">See also</span></span>

- [<span data-ttu-id="20eb5-123">mimo</span><span class="sxs-lookup"><span data-stu-id="20eb5-123">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="20eb5-124">Kovariance a kontravariance</span><span class="sxs-lookup"><span data-stu-id="20eb5-124">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="20eb5-125">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="20eb5-125">Modifiers</span></span>](index.md)
