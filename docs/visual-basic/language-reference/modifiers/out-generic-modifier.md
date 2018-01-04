---
title: "Out (generický modifikátor) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e54504cd65b78846af41692f39899140a6d99b5
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="fd38a-102">Out (generický modifikátor) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd38a-102">Out (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="fd38a-103">Pro parametry obecného typu `Out` – klíčové slovo určuje, že typu je kovariant.</span><span class="sxs-lookup"><span data-stu-id="fd38a-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd38a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd38a-104">Remarks</span></span>  
 <span data-ttu-id="fd38a-105">Kovariance umožňuje používat více odvozený typ, než je určeno obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="fd38a-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="fd38a-106">To umožňuje implicitní převod tříd, které implementují rozhraní variant a implicitní převod typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="fd38a-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="fd38a-107">Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="fd38a-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="fd38a-108">Pravidla</span><span class="sxs-lookup"><span data-stu-id="fd38a-108">Rules</span></span>  
 <span data-ttu-id="fd38a-109">Můžete použít `Out` – klíčové slovo v obecném rozhraní a delegáti.</span><span class="sxs-lookup"><span data-stu-id="fd38a-109">You can use the `Out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="fd38a-110">Obecná rozhraní parametr typu lze deklarovat kovariantní splňuje tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="fd38a-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="fd38a-111">Parametr typu je použit pouze jako návratový typ metody rozhraní a nepoužívá jako typ metoda argumenty.</span><span class="sxs-lookup"><span data-stu-id="fd38a-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fd38a-112">Existuje jedna výjimka tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="fd38a-112">There is one exception to this rule.</span></span> <span data-ttu-id="fd38a-113">Pokud v kovariantní rozhraní máte obecný delegát kontravariant jako parametru metody, můžete jako parametr obecného typu kovariantní typ pro tento delegát.</span><span class="sxs-lookup"><span data-stu-id="fd38a-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="fd38a-114">Další informace o kovariantní a obecní delegáti kontravariant, najdete v části [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylky pro Func a obecní delegáti akce](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="fd38a-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
-   <span data-ttu-id="fd38a-115">Parametr typu není používána jako obecná omezení pro metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fd38a-115">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
 <span data-ttu-id="fd38a-116">V obecný delegát parametr typu lze deklarovat kovariantní, pokud je použit pouze jako návratový typ. metoda a nepoužívá se metoda argumenty.</span><span class="sxs-lookup"><span data-stu-id="fd38a-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
 <span data-ttu-id="fd38a-117">Kovariance a kontravariance jsou podporovány pro odkazové typy, ale nejsou podporovány u typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="fd38a-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="fd38a-118">V jazyce Visual Basic nelze deklarovat události v kovariantní rozhraní bez zadání typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="fd38a-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="fd38a-119">Navíc kovariantní rozhraní vnořené třídy, výčty a struktury, ale mohou mít vnořené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fd38a-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="fd38a-120">Chování</span><span class="sxs-lookup"><span data-stu-id="fd38a-120">Behavior</span></span>  
 <span data-ttu-id="fd38a-121">Rozhraní, které má kovariantní typ parametru umožňuje její metody vrátit více odvozené typy než je zadáno v parametru typu.</span><span class="sxs-lookup"><span data-stu-id="fd38a-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="fd38a-122">Například protože v rozhraní .NET Framework 4 v <xref:System.Collections.Generic.IEnumerable%601>T typu je kovariant, můžete přiřadit objekt `IEnumerabe(Of String)` typ na objekt `IEnumerable(Of Object)` typu bez použití žádné speciální převod metody.</span><span class="sxs-lookup"><span data-stu-id="fd38a-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerabe(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="fd38a-123">Kovariantní delegát může být přiřazen jiné delegáta stejného typu, ale s více odvozené parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="fd38a-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd38a-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd38a-124">Example</span></span>  
 <span data-ttu-id="fd38a-125">Následující příklad ukazuje, jak deklarovat, rozšířit a kovariantní obecná rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fd38a-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="fd38a-126">Také ukazuje, jak používat implicitní převod pro třídy, které implementují rozhraní, které je kovariant.</span><span class="sxs-lookup"><span data-stu-id="fd38a-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="fd38a-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd38a-127">Example</span></span>  
 <span data-ttu-id="fd38a-128">Následující příklad ukazuje, jak deklarování, vytváření instancí a vyvolání kovariantní obecný delegát.</span><span class="sxs-lookup"><span data-stu-id="fd38a-128">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="fd38a-129">Také ukazuje, jak můžete použít implicitní převod pro typy delegáta.</span><span class="sxs-lookup"><span data-stu-id="fd38a-129">It also shows how you can use implicit conversion for delegate types.</span></span>  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fd38a-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd38a-130">See Also</span></span>  
 [<span data-ttu-id="fd38a-131">Odchylky obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd38a-131">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="fd38a-132">V</span><span class="sxs-lookup"><span data-stu-id="fd38a-132">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
