---
title: out – klíčové slovo (generický modifikátor) (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: fedbdb12c1da108d17636770fb5c628195dce0d4
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46528526"
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="fce77-102">out (generický modifikátor) (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="fce77-102">out (generic modifier) (C# Reference)</span></span>

<span data-ttu-id="fce77-103">Pro parametry obecného typu `out` – klíčové slovo určuje, že parametr typu je kovariant.</span><span class="sxs-lookup"><span data-stu-id="fce77-103">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="fce77-104">Můžete použít `out` – klíčové slovo v obecných rozhraních a delegátech.</span><span class="sxs-lookup"><span data-stu-id="fce77-104">You can use the `out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="fce77-105">Kovariance umožňuje použít více odvozený typ, než je určeno obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="fce77-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="fce77-106">To umožňuje implicitní převod z třídy, které implementují rozhraní variant a implicitní převod delegujících typů.</span><span class="sxs-lookup"><span data-stu-id="fce77-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="fce77-107">Kovariance a kontravariance jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="fce77-107">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="fce77-108">Rozhraní, které má parametr kovariantního typu umožňuje její metody k vrácení více odvozené typy než je zadáno parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="fce77-108">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="fce77-109">Například protože v rozhraní .NET Framework 4, v <xref:System.Collections.Generic.IEnumerable%601>, typ T je kovariantní, můžete přiřadit objektu `IEnumerable(Of String)` typu na objekt `IEnumerable(Of Object)` typ bez použití jakékoli speciální převod metody.</span><span class="sxs-lookup"><span data-stu-id="fce77-109">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="fce77-110">Kovariantní delegát může být přiřazen jiný delegát stejného typu, ale s více odvozeného parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="fce77-110">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

<span data-ttu-id="fce77-111">Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="fce77-111">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="example---covariant-generic-interface"></a><span data-ttu-id="fce77-112">Příklad: kovariantní obecné rozhraní</span><span class="sxs-lookup"><span data-stu-id="fce77-112">Example - covariant generic interface</span></span>

<span data-ttu-id="fce77-113">Následující příklad ukazuje, jak deklarovat, rozšíření a implementovat kovariantní obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fce77-113">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="fce77-114">Také ukazuje, jak použít implicitní převod pro třídy, které implementují kovariantního rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fce77-114">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

<span data-ttu-id="fce77-115">Obecná rozhraní mohou být deklarovány parametr typu kovariantní, pokud splňuje následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="fce77-115">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="fce77-116">Parametr typu je použít jenom jako návratový typ metody rozhraní a nelze použít jako typ argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="fce77-116">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="fce77-117">Existuje jedna výjimka tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="fce77-117">There is one exception to this rule.</span></span> <span data-ttu-id="fce77-118">Pokud kovariantní rozhraní mají kontravariantní obecného delegáta jako parametr metody, můžete jako parametr obecného typu kovariantního typu pro tohoto delegáta.</span><span class="sxs-lookup"><span data-stu-id="fce77-118">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="fce77-119">Další informace o kovariantního a obecných delegátů kontravariantní, naleznete v tématu [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylku pro delegáty Func a Action obecný](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="fce77-119">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="fce77-120">Parametr typu se nepoužívá jako obecná omezení pro metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fce77-120">The type parameter is not used as a generic constraint for the interface methods.</span></span>

## <a name="example---covariant-generic-delegate"></a><span data-ttu-id="fce77-121">Příklad: kovariantní obecného delegáta</span><span class="sxs-lookup"><span data-stu-id="fce77-121">Example - covariant generic delegate</span></span>

<span data-ttu-id="fce77-122">Následující příklad ukazuje, jak deklarovat, vytváření instancí a vyvolání kovariantního obecného delegáta.</span><span class="sxs-lookup"><span data-stu-id="fce77-122">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="fce77-123">Také ukazuje, jak pro implicitní převod na typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="fce77-123">It also shows how to implicitly convert delegate types.</span></span>

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

<span data-ttu-id="fce77-124">V obecný delegát typu mohou být deklarovány kovariantní, pokud je použita pouze jako návratový typ metody a není možné použít u argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="fce77-124">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fce77-125">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fce77-125">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="fce77-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fce77-126">See also</span></span>

- [<span data-ttu-id="fce77-127">Odchylky obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="fce77-127">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="fce77-128">in</span><span class="sxs-lookup"><span data-stu-id="fce77-128">in</span></span>](in-generic-modifier.md)
- [<span data-ttu-id="fce77-129">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="fce77-129">Modifiers</span></span>](modifiers.md)