---
title: Out (generický modifikátor) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: 7ba774bfcd629a7518602d4b971e86a690b2dd83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598150"
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="db3a3-102">Out (generický modifikátor) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db3a3-102">Out (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="db3a3-103">Pro parametry obecného typu `Out` – klíčové slovo určuje, že typu je kovariant.</span><span class="sxs-lookup"><span data-stu-id="db3a3-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db3a3-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db3a3-104">Remarks</span></span>  
 <span data-ttu-id="db3a3-105">Kovariance umožňuje používat více odvozený typ, než je určeno obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="db3a3-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="db3a3-106">To umožňuje implicitní převod tříd, které implementují rozhraní variant a implicitní převod typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="db3a3-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="db3a3-107">Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="db3a3-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="db3a3-108">Pravidla</span><span class="sxs-lookup"><span data-stu-id="db3a3-108">Rules</span></span>  
 <span data-ttu-id="db3a3-109">Můžete použít `Out` – klíčové slovo v obecném rozhraní a delegáti.</span><span class="sxs-lookup"><span data-stu-id="db3a3-109">You can use the `Out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="db3a3-110">Obecná rozhraní parametr typu lze deklarovat kovariantní splňuje tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="db3a3-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="db3a3-111">Parametr typu je použit pouze jako návratový typ metody rozhraní a nepoužívá jako typ metoda argumenty.</span><span class="sxs-lookup"><span data-stu-id="db3a3-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="db3a3-112">Existuje jedna výjimka tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="db3a3-112">There is one exception to this rule.</span></span> <span data-ttu-id="db3a3-113">Pokud v kovariantní rozhraní máte obecný delegát kontravariant jako parametru metody, můžete jako parametr obecného typu kovariantní typ pro tento delegát.</span><span class="sxs-lookup"><span data-stu-id="db3a3-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="db3a3-114">Další informace o kovariantní a obecní delegáti kontravariant, najdete v části [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylky pro Func a obecní delegáti akce](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="db3a3-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
-   <span data-ttu-id="db3a3-115">Parametr typu není používána jako obecná omezení pro metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="db3a3-115">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
 <span data-ttu-id="db3a3-116">V obecný delegát parametr typu lze deklarovat kovariantní, pokud je použit pouze jako návratový typ. metoda a nepoužívá se metoda argumenty.</span><span class="sxs-lookup"><span data-stu-id="db3a3-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
 <span data-ttu-id="db3a3-117">Kovariance a kontravariance jsou podporovány pro odkazové typy, ale nejsou podporovány u typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="db3a3-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="db3a3-118">V jazyce Visual Basic nelze deklarovat události v kovariantní rozhraní bez zadání typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="db3a3-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="db3a3-119">Navíc kovariantní rozhraní vnořené třídy, výčty a struktury, ale mohou mít vnořené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="db3a3-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="db3a3-120">Chování</span><span class="sxs-lookup"><span data-stu-id="db3a3-120">Behavior</span></span>  
 <span data-ttu-id="db3a3-121">Rozhraní, které má kovariantní typ parametru umožňuje její metody vrátit více odvozené typy než je zadáno v parametru typu.</span><span class="sxs-lookup"><span data-stu-id="db3a3-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="db3a3-122">Například protože v rozhraní .NET Framework 4 v <xref:System.Collections.Generic.IEnumerable%601>T typu je kovariant, můžete přiřadit objekt `IEnumerabe(Of String)` typ na objekt `IEnumerable(Of Object)` typu bez použití žádné speciální převod metody.</span><span class="sxs-lookup"><span data-stu-id="db3a3-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerabe(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="db3a3-123">Kovariantní delegát může být přiřazen jiné delegáta stejného typu, ale s více odvozené parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="db3a3-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db3a3-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="db3a3-124">Example</span></span>  
 <span data-ttu-id="db3a3-125">Následující příklad ukazuje, jak deklarovat, rozšířit a kovariantní obecná rozhraní.</span><span class="sxs-lookup"><span data-stu-id="db3a3-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="db3a3-126">Také ukazuje, jak používat implicitní převod pro třídy, které implementují rozhraní, které je kovariant.</span><span class="sxs-lookup"><span data-stu-id="db3a3-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="db3a3-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="db3a3-127">Example</span></span>  
 <span data-ttu-id="db3a3-128">Následující příklad ukazuje, jak deklarování, vytváření instancí a vyvolání kovariantní obecný delegát.</span><span class="sxs-lookup"><span data-stu-id="db3a3-128">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="db3a3-129">Také ukazuje, jak můžete použít implicitní převod pro typy delegáta.</span><span class="sxs-lookup"><span data-stu-id="db3a3-129">It also shows how you can use implicit conversion for delegate types.</span></span>  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="db3a3-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="db3a3-130">See Also</span></span>  
 [<span data-ttu-id="db3a3-131">Odchylky obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="db3a3-131">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="db3a3-132">V</span><span class="sxs-lookup"><span data-stu-id="db3a3-132">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
