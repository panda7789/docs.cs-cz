---
title: Out (generický modifikátor)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: 28ae7d6fd51170aa822072fc2f5357443f51a353
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392090"
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="2a5dc-102">Out (generický modifikátor) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a5dc-102">Out (Generic Modifier) (Visual Basic)</span></span>

<span data-ttu-id="2a5dc-103">Pro parametry obecného typu `Out` Určuje klíčové slovo, že typ je kovariantní.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a5dc-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2a5dc-104">Remarks</span></span>

<span data-ttu-id="2a5dc-105">Kovariance umožňuje použít více odvozený typ, než který je určen obecným parametrem.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="2a5dc-106">To umožňuje implicitní převod tříd, které implementují rozhraní variant a implicitní převod typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>

<span data-ttu-id="2a5dc-107">Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="2a5dc-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="2a5dc-108">Pravidla</span><span class="sxs-lookup"><span data-stu-id="2a5dc-108">Rules</span></span>

<span data-ttu-id="2a5dc-109">Klíčové slovo lze použít `Out` v obecných rozhraních a delegátech.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-109">You can use the `Out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="2a5dc-110">V obecném rozhraní může být parametr typu deklarován kovariantou, pokud splňuje následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="2a5dc-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="2a5dc-111">Parametr typu se používá jenom jako návratový typ metod rozhraní a nepoužívá se jako typ argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2a5dc-112">Toto pravidlo obsahuje jednu výjimku.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-112">There is one exception to this rule.</span></span> <span data-ttu-id="2a5dc-113">Pokud v kovariantovém rozhraní máte kontravariantního obecného delegáta jako parametr metody, můžete použít kovariantní typ jako parametr obecného typu pro tohoto delegáta.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="2a5dc-114">Další informace o kovariantních a kontravariantních obecných delegátech naleznete v tématu [Variance v delegátech](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [použití variance pro obecné delegáty Func a Action](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="2a5dc-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="2a5dc-115">Parametr typu se nepoužívá jako obecné omezení pro metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-115">The type parameter is not used as a generic constraint for the interface methods.</span></span>

<span data-ttu-id="2a5dc-116">V obecném delegátu může být parametr typu deklarován kovariantou, pokud je použit pouze jako návratový typ metody a nepoužívá se pro argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

<span data-ttu-id="2a5dc-117">Kovariance a kontravariance jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="2a5dc-118">V Visual Basic nemůžete deklarovat události v kovariantních rozhraních bez určení typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="2a5dc-119">I kovariantní rozhraní nemohou mít vnořené třídy, výčty ani struktury, ale mohou mít vnořená rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>

## <a name="behavior"></a><span data-ttu-id="2a5dc-120">Chování</span><span class="sxs-lookup"><span data-stu-id="2a5dc-120">Behavior</span></span>

<span data-ttu-id="2a5dc-121">Rozhraní, které má parametr kovariantního typu, umožňuje jeho metodám vracet více odvozených typů než hodnoty určené parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="2a5dc-122">Například vzhledem k tomu, že v .NET Framework 4 <xref:System.Collections.Generic.IEnumerable%601> je typ T typu kovariance, můžete přiřadit objekt `IEnumerable(Of String)` typu k objektu `IEnumerable(Of Object)` typu bez použití jakýchkoli speciálních metod převodu.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="2a5dc-123">Spoluvariantnímu delegátu se dá přiřadit jiný delegát stejného typu, ale s více odvozeným parametrem obecného typu.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="2a5dc-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a5dc-124">Example</span></span>

<span data-ttu-id="2a5dc-125">Následující příklad ukazuje, jak deklarovat, rozšiřuje a implementovat kovariantní obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="2a5dc-126">Také ukazuje, jak použít implicitní převod pro třídy, které implementují kovariantní rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="2a5dc-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a5dc-127">Example</span></span>

<span data-ttu-id="2a5dc-128">Následující příklad ukazuje, jak deklarovat, vytvářet instance a vyvolat kovariantní obecný delegát.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-128">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="2a5dc-129">Také ukazuje, jak lze použít implicitní převod pro typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="2a5dc-129">It also shows how you can use implicit conversion for delegate types.</span></span>

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="2a5dc-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a5dc-130">See also</span></span>

- [<span data-ttu-id="2a5dc-131">Odchylky obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="2a5dc-131">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="2a5dc-132">V</span><span class="sxs-lookup"><span data-stu-id="2a5dc-132">In</span></span>](in-generic-modifier.md)
