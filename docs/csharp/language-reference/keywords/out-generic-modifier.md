---
description: out – klíčové slovo (obecný modifikátor) – Referenční dokumentace jazyka C#
title: out – klíčové slovo (obecný modifikátor) – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 84f3647309c0772f6ae61d3614f8649fe277f153
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142333"
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="6972f-103">out (generický modifikátor) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6972f-103">out (generic modifier) (C# Reference)</span></span>

<span data-ttu-id="6972f-104">Pro parametry obecného typu `out` Určuje klíčové slovo, že parametr typu je kovariantní.</span><span class="sxs-lookup"><span data-stu-id="6972f-104">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="6972f-105">Klíčové slovo lze použít `out` v obecných rozhraních a delegátech.</span><span class="sxs-lookup"><span data-stu-id="6972f-105">You can use the `out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="6972f-106">Kovariance umožňuje použít více odvozený typ, než který je určen obecným parametrem.</span><span class="sxs-lookup"><span data-stu-id="6972f-106">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="6972f-107">To umožňuje implicitní převod tříd, které implementují kovariantní rozhraní a implicitní převod typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="6972f-107">This allows for implicit conversion of classes that implement covariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="6972f-108">Kovariance a kontravariance jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="6972f-108">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="6972f-109">Rozhraní, které má parametr kovariantního typu, umožňuje jeho metodám vracet více odvozených typů než hodnoty určené parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="6972f-109">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="6972f-110">Například vzhledem k tomu, že v .NET Framework 4 <xref:System.Collections.Generic.IEnumerable%601> je typ T typu kovariance, můžete přiřadit objekt `IEnumerable(Of String)` typu k objektu `IEnumerable(Of Object)` typu bez použití jakýchkoli speciálních metod převodu.</span><span class="sxs-lookup"><span data-stu-id="6972f-110">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="6972f-111">Spoluvariantnímu delegátu se dá přiřadit jiný delegát stejného typu, ale s více odvozeným parametrem obecného typu.</span><span class="sxs-lookup"><span data-stu-id="6972f-111">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

<span data-ttu-id="6972f-112">Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="6972f-112">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="example---covariant-generic-interface"></a><span data-ttu-id="6972f-113">Příklad: kovariantní obecné rozhraní</span><span class="sxs-lookup"><span data-stu-id="6972f-113">Example - covariant generic interface</span></span>

<span data-ttu-id="6972f-114">Následující příklad ukazuje, jak deklarovat, rozšiřuje a implementovat kovariantní obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6972f-114">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="6972f-115">Také ukazuje, jak použít implicitní převod pro třídy, které implementují kovariantní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6972f-115">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

<span data-ttu-id="6972f-116">V obecném rozhraní může být parametr typu deklarován kovariantou, pokud splňuje následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="6972f-116">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="6972f-117">Parametr typu se používá jenom jako návratový typ metod rozhraní a nepoužívá se jako typ argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="6972f-117">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6972f-118">Toto pravidlo obsahuje jednu výjimku.</span><span class="sxs-lookup"><span data-stu-id="6972f-118">There is one exception to this rule.</span></span> <span data-ttu-id="6972f-119">Pokud v kovariantovém rozhraní máte kontravariantního obecného delegáta jako parametr metody, můžete použít kovariantní typ jako parametr obecného typu pro tohoto delegáta.</span><span class="sxs-lookup"><span data-stu-id="6972f-119">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="6972f-120">Další informace o kovariantních a kontravariantních obecných delegátech naleznete v tématu [Variance v delegátech](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [použití variance pro obecné delegáty Func a Action](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="6972f-120">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="6972f-121">Parametr typu se nepoužívá jako obecné omezení pro metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6972f-121">The type parameter is not used as a generic constraint for the interface methods.</span></span>

## <a name="example---covariant-generic-delegate"></a><span data-ttu-id="6972f-122">Příklad – kovariance obecného delegáta</span><span class="sxs-lookup"><span data-stu-id="6972f-122">Example - covariant generic delegate</span></span>

<span data-ttu-id="6972f-123">Následující příklad ukazuje, jak deklarovat, vytvářet instance a vyvolat kovariantní obecný delegát.</span><span class="sxs-lookup"><span data-stu-id="6972f-123">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="6972f-124">Také ukazuje, jak implicitně převést typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="6972f-124">It also shows how to implicitly convert delegate types.</span></span>

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

<span data-ttu-id="6972f-125">V obecném delegátu může být typ deklarovaný jako kovariant, pokud se používá jenom jako návratový typ metody a nepoužívá se pro argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="6972f-125">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6972f-126">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6972f-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6972f-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="6972f-127">See also</span></span>

- [<span data-ttu-id="6972f-128">Odchylky obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="6972f-128">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="6972f-129">pro</span><span class="sxs-lookup"><span data-stu-id="6972f-129">in</span></span>](in-generic-modifier.md)
- [<span data-ttu-id="6972f-130">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="6972f-130">Modifiers</span></span>](index.md)
