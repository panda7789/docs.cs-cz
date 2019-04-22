---
title: In (generický modifikátor) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: d8d503f0814a89c977cdc208eced026b2d8cb1fd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838926"
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="a31f6-102">In (generický modifikátor) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a31f6-102">In (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="a31f6-103">Pro parametry obecného typu `In` – klíčové slovo určuje, že parametr typu je kontravariant.</span><span class="sxs-lookup"><span data-stu-id="a31f6-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a31f6-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a31f6-104">Remarks</span></span>  
 <span data-ttu-id="a31f6-105">Kontravariance umožňuje použít méně odvozený typ, než je určeno obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="a31f6-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="a31f6-106">To umožňuje implicitní převod z třídy, které implementují rozhraní variant a implicitní převod delegujících typů.</span><span class="sxs-lookup"><span data-stu-id="a31f6-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="a31f6-107">Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="a31f6-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="a31f6-108">pravidla</span><span class="sxs-lookup"><span data-stu-id="a31f6-108">Rules</span></span>  
 <span data-ttu-id="a31f6-109">Můžete použít `In` – klíčové slovo v obecných rozhraních a delegátech.</span><span class="sxs-lookup"><span data-stu-id="a31f6-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="a31f6-110">Parametr typu mohou být deklarovány v obecné rozhraní nebo delegát Kontravariantní, pokud je použít jenom jako typ argumentů metody a nepoužívá se jako návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="a31f6-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="a31f6-111">`ByRef` parametry nemohou být kovariantní nebo kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="a31f6-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>  
  
 <span data-ttu-id="a31f6-112">Kovariance a kontravariance jsou podporovány pro typy odkazů a nejsou podporovány pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="a31f6-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>  
  
 <span data-ttu-id="a31f6-113">V jazyce Visual Basic nelze deklarovat události v rozhraní kontravariantní bez zadání typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="a31f6-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="a31f6-114">Také kontravariantní rozhraní nemůžou být vnořené třídy, výčty a struktury, ale mohou být vnořené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a31f6-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="a31f6-115">Chování</span><span class="sxs-lookup"><span data-stu-id="a31f6-115">Behavior</span></span>  
 <span data-ttu-id="a31f6-116">Rozhraní, která má parametr kontravariantního typu umožňuje její metody pro přijímání argumentů méně odvozené typy než je zadáno parametrem typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a31f6-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="a31f6-117">Například protože v rozhraní .NET Framework 4, v <xref:System.Collections.Generic.IComparer%601> rozhraní, typ T je kontravariantní, můžete přiřadit objektu `IComparer(Of Person)` typu na objekt `IComparer(Of Employee)` typ bez použití jakékoli speciální převod metody, pokud `Person` dědí `Employee`.</span><span class="sxs-lookup"><span data-stu-id="a31f6-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Person` inherits `Employee`.</span></span>  
  
 <span data-ttu-id="a31f6-118">Kontravariantní delegát může být přiřazen jiný delegát stejného typu, ale s méně odvozený parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="a31f6-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a31f6-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="a31f6-119">Example</span></span>  
 <span data-ttu-id="a31f6-120">Následující příklad ukazuje, jak deklarovat, rozšíření a implementovat obecné rozhraní kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="a31f6-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="a31f6-121">Také ukazuje, jak můžete použít implicitní převod pro třídy, které toto rozhraní implementují.</span><span class="sxs-lookup"><span data-stu-id="a31f6-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="a31f6-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="a31f6-122">Example</span></span>  
 <span data-ttu-id="a31f6-123">Následující příklad ukazuje, jak deklarovat, vytváření instancí a vyvolání obecného delegátu kontravariantní.</span><span class="sxs-lookup"><span data-stu-id="a31f6-123">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="a31f6-124">Profil také ukazuje, jak lze implicitně převést typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="a31f6-124">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a31f6-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a31f6-125">See also</span></span>

- [<span data-ttu-id="a31f6-126">Odchylky obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="a31f6-126">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="a31f6-127">navýšení kapacity</span><span class="sxs-lookup"><span data-stu-id="a31f6-127">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
