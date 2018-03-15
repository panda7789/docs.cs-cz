---
title: "in (generický modifikátor) (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2af4e27034af0067e81a52c81991edaf5a5415d8
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="8521c-102">in (generický modifikátor) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8521c-102">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="8521c-103">Pro parametry obecného typu `in` – klíčové slovo určuje, že parametr typu je kontravariant.</span><span class="sxs-lookup"><span data-stu-id="8521c-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="8521c-104">Můžete použít `in` – klíčové slovo v obecném rozhraní a delegáti.</span><span class="sxs-lookup"><span data-stu-id="8521c-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="8521c-105">Kontravariance umožňuje používat méně odvozený typ, než je určeno obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="8521c-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="8521c-106">To umožňuje implicitní převod tříd, které implementují rozhraní variant a implicitní převod typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="8521c-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="8521c-107">Kovariance a kontravariance v parametry obecného typu jsou podporovány pro odkazové typy, ale nejsou podporovány u typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="8521c-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="8521c-108">Typ lze deklarovat kontravariant v obecné rozhraní nebo delegáta, pouze v případě, že definuje typ parametry metody a ne návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="8521c-108">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="8521c-109">`In`, `ref`, a `out` parametry musí být výchozí, což znamená, ani jeden z nich jsou kovariantní nebo kontravariant.</span><span class="sxs-lookup"><span data-stu-id="8521c-109">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>
  
 <span data-ttu-id="8521c-110">Rozhraní, které má parametr typu kontravariant umožňuje její metody tak, aby přijímal argumenty odvozených typů menší než je zadáno v parametru typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8521c-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="8521c-111">Například v <xref:System.Collections.Generic.IComparer%601> rozhraní T typu je kontravariant, můžete jim přiřadit objekt `IComparer<Person>` typ na objekt `IComparer<Employee>` typu bez použití žádné speciální převod metody, pokud `Employee` dědí `Person`.</span><span class="sxs-lookup"><span data-stu-id="8521c-111">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>  
  
 <span data-ttu-id="8521c-112">Delegát kontravariant může být přiřazen jiný delegát stejného typu, ale s méně odvozený parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="8521c-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
 <span data-ttu-id="8521c-113">Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="8521c-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="contravariant-generic-interface"></a><span data-ttu-id="8521c-114">Kontravariant obecné rozhraní</span><span class="sxs-lookup"><span data-stu-id="8521c-114">Contravariant generic interface</span></span>   

 <span data-ttu-id="8521c-115">Následující příklad ukazuje, jak deklarovat, rozšířit a implementovat obecné rozhraní kontravariant.</span><span class="sxs-lookup"><span data-stu-id="8521c-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="8521c-116">Také ukazuje, jak můžete použít implicitní převod pro třídy, které toto rozhraní implementovat.</span><span class="sxs-lookup"><span data-stu-id="8521c-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="contravariant-generic-delegate"></a><span data-ttu-id="8521c-117">Kontravariant – obecný delegát</span><span class="sxs-lookup"><span data-stu-id="8521c-117">Contravariant generic delegate</span></span>  

 <span data-ttu-id="8521c-118">Následující příklad ukazuje, jak deklarování, vytváření instancí a vyvolání obecný delegát kontravariant.</span><span class="sxs-lookup"><span data-stu-id="8521c-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="8521c-119">Také ukazuje, jak můžete implicitně převést typem delegáta.</span><span class="sxs-lookup"><span data-stu-id="8521c-119">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8521c-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8521c-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8521c-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="8521c-121">See Also</span></span>  
 [<span data-ttu-id="8521c-122">out</span><span class="sxs-lookup"><span data-stu-id="8521c-122">out</span></span>](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [<span data-ttu-id="8521c-123">Kovariance a kontravariance</span><span class="sxs-lookup"><span data-stu-id="8521c-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="8521c-124">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="8521c-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
