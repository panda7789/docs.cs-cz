---
title: In (generický modifikátor) – Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: 9c0f7d454767112e1e309af81407b5fdef22eee9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004866"
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="2d90f-102">In (generický modifikátor) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d90f-102">In (Generic Modifier) (Visual Basic)</span></span>

<span data-ttu-id="2d90f-103">Pro parametry obecného typu Určuje klíčové slovo `In`, že parametr typu je kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="2d90f-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>

## <a name="remarks"></a><span data-ttu-id="2d90f-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d90f-104">Remarks</span></span>

<span data-ttu-id="2d90f-105">Kontravariance umožňuje použít méně odvozený typ, než který je určen obecným parametrem.</span><span class="sxs-lookup"><span data-stu-id="2d90f-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="2d90f-106">To umožňuje implicitní převod tříd, které implementují rozhraní variant a implicitní převod typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="2d90f-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>

<span data-ttu-id="2d90f-107">Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="2d90f-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="2d90f-108">Pravidly</span><span class="sxs-lookup"><span data-stu-id="2d90f-108">Rules</span></span>

<span data-ttu-id="2d90f-109">V obecných rozhraních a delegátech můžete použít klíčové slovo `In`.</span><span class="sxs-lookup"><span data-stu-id="2d90f-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>
  
<span data-ttu-id="2d90f-110">Parametr typu může být deklarovaný jako kontravariantní v obecném rozhraní nebo delegátu, pokud se používá jenom jako typ argumentů metody a nepoužívá se jako návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="2d90f-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="2d90f-111">parametry `ByRef` nemohou být kovariantní nebo kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="2d90f-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>

<span data-ttu-id="2d90f-112">Kovariance a kontravariance jsou podporovány pro typy odkazů a nejsou podporovány pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="2d90f-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>

<span data-ttu-id="2d90f-113">V Visual Basic nelze deklarovat události v kontravariantních rozhraních bez určení typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="2d90f-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="2d90f-114">Také kontravariantní rozhraní nemohou mít vnořené třídy, výčty nebo struktury, ale mohou mít vnořená rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d90f-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>

## <a name="behavior"></a><span data-ttu-id="2d90f-115">Předvídatelně</span><span class="sxs-lookup"><span data-stu-id="2d90f-115">Behavior</span></span>

<span data-ttu-id="2d90f-116">Rozhraní, které má parametr kontravariantního typu, umožňuje svým metodám přijímat argumenty méně odvozených typů než hodnoty určené parametrem typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d90f-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="2d90f-117">Například vzhledem k tomu, že v .NET Framework 4 v rozhraní <xref:System.Collections.Generic.IComparer%601> typ T je kontravariantní, můžete přiřadit objekt typu `IComparer(Of Person)` k objektu typu `IComparer(Of Employee)` bez použití jakýchkoli speciálních metod převodu, pokud `Employee` dědí z `Person`.</span><span class="sxs-lookup"><span data-stu-id="2d90f-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Employee` inherits from `Person`.</span></span>

<span data-ttu-id="2d90f-118">Kontravariantnímu delegátu lze přiřadit jiný delegát stejného typu, ale s menším odvozeným parametrem obecného typu.</span><span class="sxs-lookup"><span data-stu-id="2d90f-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

## <a name="example---contravariant-generic-interface"></a><span data-ttu-id="2d90f-119">Příklad – kontravariantní obecné rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d90f-119">Example - contravariant generic interface</span></span>

<span data-ttu-id="2d90f-120">Následující příklad ukazuje, jak deklarovat, rozšiřuje a implementovat kontravariantní obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d90f-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="2d90f-121">Také ukazuje, jak lze použít implicitní převod pro třídy, které implementují toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d90f-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]

## <a name="example---contravariant-generic-delegate"></a><span data-ttu-id="2d90f-122">Příklad – kontravariantní obecný delegát</span><span class="sxs-lookup"><span data-stu-id="2d90f-122">Example - contravariant generic delegate</span></span>

<span data-ttu-id="2d90f-123">Následující příklad ukazuje, jak deklarovat, vytvářet instance a vyvolat kontravariantního obecného delegáta.</span><span class="sxs-lookup"><span data-stu-id="2d90f-123">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="2d90f-124">Také ukazuje, jak lze implicitně převést typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="2d90f-124">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="2d90f-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d90f-125">See also</span></span>

- [<span data-ttu-id="2d90f-126">Odchylky obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d90f-126">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="2d90f-127">Mimo</span><span class="sxs-lookup"><span data-stu-id="2d90f-127">Out</span></span>](out-generic-modifier.md)
