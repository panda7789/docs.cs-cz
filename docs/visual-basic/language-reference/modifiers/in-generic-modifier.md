---
title: In (generický modifikátor) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: d1d9209cd583ac96ece59660ad29c76a66d3395a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597429"
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="65147-102">In (generický modifikátor) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65147-102">In (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="65147-103">Pro parametry obecného typu `In` – klíčové slovo určuje, že parametr typu je kontravariant.</span><span class="sxs-lookup"><span data-stu-id="65147-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65147-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65147-104">Remarks</span></span>  
 <span data-ttu-id="65147-105">Kontravariance umožňuje používat méně odvozený typ, než je určeno obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="65147-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="65147-106">To umožňuje implicitní převod tříd, které implementují rozhraní variant a implicitní převod typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="65147-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="65147-107">Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="65147-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="65147-108">Pravidla</span><span class="sxs-lookup"><span data-stu-id="65147-108">Rules</span></span>  
 <span data-ttu-id="65147-109">Můžete použít `In` – klíčové slovo v obecném rozhraní a delegáti.</span><span class="sxs-lookup"><span data-stu-id="65147-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="65147-110">Parametr typu lze deklarovat kontravariant v obecné rozhraní nebo delegáta, pokud je použit pouze jako typ metoda argumenty a nejsou používány jako návratový typ. metoda.</span><span class="sxs-lookup"><span data-stu-id="65147-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="65147-111">`ByRef` parametry nemohou mít kovariantní nebo kontravariant.</span><span class="sxs-lookup"><span data-stu-id="65147-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>  
  
 <span data-ttu-id="65147-112">Kovariance a kontravariance jsou podporovány pro odkazové typy a není podporována u typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="65147-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>  
  
 <span data-ttu-id="65147-113">V jazyce Visual Basic nelze deklarovat události v rozhraní kontravariant bez zadání typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="65147-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="65147-114">Navíc kontravariant rozhraní vnořené třídy, výčty a struktury, ale mohou mít vnořené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="65147-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="65147-115">Chování</span><span class="sxs-lookup"><span data-stu-id="65147-115">Behavior</span></span>  
 <span data-ttu-id="65147-116">Rozhraní, které má parametr typu kontravariant umožňuje její metody tak, aby přijímal argumenty odvozených typů menší než je zadáno v parametru typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="65147-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="65147-117">Například protože v rozhraní .NET Framework 4 v <xref:System.Collections.Generic.IComparer%601> rozhraní T typu je kontravariant, můžete jim přiřadit objekt `IComparer(Of Person)` typ na objekt `IComparer(Of Employee)` typu bez použití žádné speciální převod metody, pokud `Person` dědí `Employee`.</span><span class="sxs-lookup"><span data-stu-id="65147-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Person` inherits `Employee`.</span></span>  
  
 <span data-ttu-id="65147-118">Delegát kontravariant může být přiřazen jiný delegát stejného typu, ale s méně odvozený parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="65147-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65147-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="65147-119">Example</span></span>  
 <span data-ttu-id="65147-120">Následující příklad ukazuje, jak deklarovat, rozšířit a implementovat obecné rozhraní kontravariant.</span><span class="sxs-lookup"><span data-stu-id="65147-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="65147-121">Také ukazuje, jak můžete použít implicitní převod pro třídy, které toto rozhraní implementovat.</span><span class="sxs-lookup"><span data-stu-id="65147-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="65147-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="65147-122">Example</span></span>  
 <span data-ttu-id="65147-123">Následující příklad ukazuje, jak deklarování, vytváření instancí a vyvolání obecný delegát kontravariant.</span><span class="sxs-lookup"><span data-stu-id="65147-123">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="65147-124">Také ukazuje, jak můžete implicitně převést typem delegáta.</span><span class="sxs-lookup"><span data-stu-id="65147-124">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-vb[vbVarianceKeywords#2](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="65147-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="65147-125">See Also</span></span>  
 [<span data-ttu-id="65147-126">Odchylky obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="65147-126">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="65147-127">na více systémů</span><span class="sxs-lookup"><span data-stu-id="65147-127">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
