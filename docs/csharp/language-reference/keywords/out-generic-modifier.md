---
title: "out (generický modifikátor) (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 25019408387bbf085475482c74a3fc6001321b24
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="306b7-102">out (generický modifikátor) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="306b7-102">out (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="306b7-103">Pro parametry obecného typu `out` – klíčové slovo určuje, že parametr typu je kovariant.</span><span class="sxs-lookup"><span data-stu-id="306b7-103">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="306b7-104">Můžete použít `out` – klíčové slovo v obecném rozhraní a delegáti.</span><span class="sxs-lookup"><span data-stu-id="306b7-104">You can use the `out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="306b7-105">Kovariance umožňuje používat více odvozený typ, než je určeno obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="306b7-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="306b7-106">To umožňuje implicitní převod tříd, které implementují rozhraní variant a implicitní převod typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="306b7-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="306b7-107">Kovariance a kontravariance jsou podporovány pro odkazové typy, ale nejsou podporovány u typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="306b7-107">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="306b7-108">Rozhraní, které má kovariantní typ parametru umožňuje její metody vrátit více odvozené typy než je zadáno v parametru typu.</span><span class="sxs-lookup"><span data-stu-id="306b7-108">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="306b7-109">Například protože v rozhraní .NET Framework 4 v <xref:System.Collections.Generic.IEnumerable%601>T typu je kovariant, můžete přiřadit objekt `IEnumerable(Of String)` typ na objekt `IEnumerable(Of Object)` typu bez použití žádné speciální převod metody.</span><span class="sxs-lookup"><span data-stu-id="306b7-109">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="306b7-110">Kovariantní delegát může být přiřazen jiné delegáta stejného typu, ale s více odvozené parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="306b7-110">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
 <span data-ttu-id="306b7-111">Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="306b7-111">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="306b7-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="306b7-112">Example</span></span>  
 <span data-ttu-id="306b7-113">Následující příklad ukazuje, jak deklarovat, rozšířit a kovariantní obecná rozhraní.</span><span class="sxs-lookup"><span data-stu-id="306b7-113">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="306b7-114">Také ukazuje, jak používat implicitní převod pro třídy, které implementují rozhraní, které je kovariant.</span><span class="sxs-lookup"><span data-stu-id="306b7-114">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 <span data-ttu-id="306b7-115">Obecná rozhraní parametr typu lze deklarovat kovariantní splňuje tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="306b7-115">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="306b7-116">Parametr typu je použit pouze jako návratový typ metody rozhraní a nepoužívá jako typ metoda argumenty.</span><span class="sxs-lookup"><span data-stu-id="306b7-116">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="306b7-117">Existuje jedna výjimka tohoto pravidla.</span><span class="sxs-lookup"><span data-stu-id="306b7-117">There is one exception to this rule.</span></span> <span data-ttu-id="306b7-118">Pokud v kovariantní rozhraní máte obecný delegát kontravariant jako parametru metody, můžete jako parametr obecného typu kovariantní typ pro tento delegát.</span><span class="sxs-lookup"><span data-stu-id="306b7-118">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="306b7-119">Další informace o kovariantní a obecní delegáti kontravariant, najdete v části [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylky pro Func a obecní delegáti akce](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="306b7-119">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
-   <span data-ttu-id="306b7-120">Parametr typu není používána jako obecná omezení pro metody rozhraní.</span><span class="sxs-lookup"><span data-stu-id="306b7-120">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="306b7-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="306b7-121">Example</span></span>  
 <span data-ttu-id="306b7-122">Následující příklad ukazuje, jak deklarování, vytváření instancí a vyvolání kovariantní obecný delegát.</span><span class="sxs-lookup"><span data-stu-id="306b7-122">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="306b7-123">Také ukazuje, jak implicitně převést typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="306b7-123">It also shows how to implicitly convert delegate types.</span></span>  
  
 [!code-csharp[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 <span data-ttu-id="306b7-124">V obecný delegát typu lze deklarovat kovariantní, pokud je použit pouze jako návratový typ. metoda a nepoužívá se metoda argumenty.</span><span class="sxs-lookup"><span data-stu-id="306b7-124">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="306b7-125">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="306b7-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="306b7-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="306b7-126">See Also</span></span>  
 [<span data-ttu-id="306b7-127">Odchylky obecných rozhraní</span><span class="sxs-lookup"><span data-stu-id="306b7-127">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="306b7-128">v</span><span class="sxs-lookup"><span data-stu-id="306b7-128">in</span></span>](../../../csharp/language-reference/keywords/in-generic-modifier.md)  
 [<span data-ttu-id="306b7-129">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="306b7-129">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
