---
title: Out (generický modifikátor) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: 367cbd373df2a38a56e5362f66bedd5c0ec24efb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522754"
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="16323-102">Out (generický modifikátor) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16323-102">Out (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="16323-103">Pro parametry obecného typu `Out` – klíčové slovo určuje, že typ je kovariantní.</span><span class="sxs-lookup"><span data-stu-id="16323-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16323-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16323-104">Remarks</span></span>  
 <span data-ttu-id="16323-105">Kovariance umožňuje použít více odvozený typ, než je určeno obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="16323-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="16323-106">To umožňuje implicitní převod z třídy, které implementují rozhraní variant a implicitní převod delegujících typů.</span><span class="sxs-lookup"><span data-stu-id="16323-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="16323-107">Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="16323-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="16323-108">pravidla</span><span class="sxs-lookup"><span data-stu-id="16323-108">Rules</span></span>  
 <span data-ttu-id="16323-109">Můžete použít `Out` – klíčové slovo v obecných rozhraních a delegátech.</span><span class="sxs-lookup"><span data-stu-id="16323-109">You can use the `Out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="16323-110">Obecná rozhraní mohou být deklarovány parametr typu kovariantní, pokud splňuje následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="16323-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="16323-111">Parametr typu je použít jenom jako návratový typ metody rozhraní a nelze použít jako typ argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="16323-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="16323-112">Existuje jedna výjimka tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="16323-112">There is one exception to this rule.</span></span> <span data-ttu-id="16323-113">Pokud kovariantní rozhraní mají kontravariantní obecného delegáta jako parametr metody, můžete jako parametr obecného typu kovariantního typu pro tohoto delegáta.</span><span class="sxs-lookup"><span data-stu-id="16323-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="16323-114">Další informace o kovariantního a obecných delegátů kontravariantní, naleznete v tématu [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylku pro delegáty Func a Action obecný](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="16323-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
-   <span data-ttu-id="16323-115">Parametr typu se nepoužívá jako obecná omezení pro metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="16323-115">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
 <span data-ttu-id="16323-116">V obecného delegátu parametr typu mohou být deklarovány kovariantní, pokud je použita pouze jako návratový typ metody a není možné použít u argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="16323-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
 <span data-ttu-id="16323-117">Kovariance a kontravariance jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="16323-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="16323-118">V jazyce Visual Basic nelze deklarovat události v kovariantní rozhraní bez zadání typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="16323-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="16323-119">Také kovariantní rozhraní nemůžou být vnořené třídy, výčty a struktury, ale mohou být vnořené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="16323-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="16323-120">Chování</span><span class="sxs-lookup"><span data-stu-id="16323-120">Behavior</span></span>  
 <span data-ttu-id="16323-121">Rozhraní, které má parametr kovariantního typu umožňuje její metody k vrácení více odvozené typy než je zadáno parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="16323-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="16323-122">Například protože v rozhraní .NET Framework 4, v <xref:System.Collections.Generic.IEnumerable%601>, typ T je kovariantní, můžete přiřadit objektu `IEnumerabe(Of String)` typu na objekt `IEnumerable(Of Object)` typ bez použití jakékoli speciální převod metody.</span><span class="sxs-lookup"><span data-stu-id="16323-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerabe(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="16323-123">Kovariantní delegát může být přiřazen jiný delegát stejného typu, ale s více odvozeného parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="16323-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16323-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="16323-124">Example</span></span>  
 <span data-ttu-id="16323-125">Následující příklad ukazuje, jak deklarovat, rozšíření a implementovat kovariantní obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="16323-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="16323-126">Také ukazuje, jak použít implicitní převod pro třídy, které implementují kovariantního rozhraní.</span><span class="sxs-lookup"><span data-stu-id="16323-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="16323-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="16323-127">Example</span></span>  
 <span data-ttu-id="16323-128">Následující příklad ukazuje, jak deklarovat, vytváření instancí a vyvolání kovariantního obecného delegáta.</span><span class="sxs-lookup"><span data-stu-id="16323-128">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="16323-129">Také ukazuje, jak můžete použít implicitní převod pro typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="16323-129">It also shows how you can use implicit conversion for delegate types.</span></span>  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="16323-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16323-130">See also</span></span>
- [<span data-ttu-id="16323-131">Odchylky obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="16323-131">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="16323-132">V</span><span class="sxs-lookup"><span data-stu-id="16323-132">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
