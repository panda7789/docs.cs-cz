---
title: where (omezení obecného typu) (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f2b7b159689aa771d3f9d59e3b1dd340c85b1d79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="8d42b-102">where (omezení obecného typu) (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8d42b-102">where (generic type constraint) (C# Reference)</span></span>
<span data-ttu-id="8d42b-103">V definici obecného typu `where` klauzule slouží k určení omezení typy, které lze použít jako argumenty pro definované v deklaraci obecný parametr typu.</span><span class="sxs-lookup"><span data-stu-id="8d42b-103">In a generic type definition, the `where` clause is used to specify constraints on the types that can be used as arguments for a type parameter defined in a generic declaration.</span></span> <span data-ttu-id="8d42b-104">Můžou například deklarovat obecná třída `MyGenericClass`, tak, že parametr typu `T` implementuje <xref:System.IComparable%601> rozhraní:</span><span class="sxs-lookup"><span data-stu-id="8d42b-104">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>  
  
```csharp  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  <span data-ttu-id="8d42b-105">Další informace o where klauzule ve výrazu dotazu, najdete v části [kde klauzule](../../../csharp/language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="8d42b-105">For more information on the where clause in a query expression, see [where clause](../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
 <span data-ttu-id="8d42b-106">Kromě omezení rozhraní `where` klauzule může obsahovat omezení základní třídu, která uvádí, že typ musí mít zadaný třídy jako základní třída (nebo být třídy sám sebe) aby bylo možné použít jako argument typu pro obecného typu.</span><span class="sxs-lookup"><span data-stu-id="8d42b-106">In addition to interface constraints, a `where` clause can include a base class constraint, which states that a type must have the specified class as a base class (or be that class itself) in order to be used as a type argument for that generic type.</span></span> <span data-ttu-id="8d42b-107">Pokud se používá takové omezení, musí být před jiná omezení u tohoto typu parametru.</span><span class="sxs-lookup"><span data-stu-id="8d42b-107">If such a constraint is used, it must appear before any other constraints on that type parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 <span data-ttu-id="8d42b-108">`where` Klauzule může také zahrnovat omezení konstruktor.</span><span class="sxs-lookup"><span data-stu-id="8d42b-108">The `where` clause may also include a constructor constraint.</span></span> <span data-ttu-id="8d42b-109">Je možné vytvořit instanci typu parametr pomocí operátor new; ale, aby bylo možné učinit parametr typu musí být omezen omezením konstruktor `new()`.</span><span class="sxs-lookup"><span data-stu-id="8d42b-109">It is possible to create an instance of a type parameter using the new operator; however, in order to do so the type parameter must be constrained by the constructor constraint, `new()`.</span></span> <span data-ttu-id="8d42b-110">[New() omezení](../../../csharp/language-reference/keywords/new-constraint.md) umožňuje kompilátoru vědět, že musí mít přístupné některý typ argument zadaný bez parametrů--nebo--výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="8d42b-110">The [new() Constraint](../../../csharp/language-reference/keywords/new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="8d42b-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8d42b-111">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 <span data-ttu-id="8d42b-112">`new()` Omezení, zobrazí se v poslední `where` klauzule.</span><span class="sxs-lookup"><span data-stu-id="8d42b-112">The `new()` constraint appears last in the `where` clause.</span></span>  
  
 <span data-ttu-id="8d42b-113">S více typů parametrů, použijte jednu `where` klauzuli pro každý parametr typu, například:</span><span class="sxs-lookup"><span data-stu-id="8d42b-113">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 <span data-ttu-id="8d42b-114">Můžete také připojit omezení zadání parametrů Obecné metody takto:</span><span class="sxs-lookup"><span data-stu-id="8d42b-114">You can also attach constraints to type parameters of generic methods, like this:</span></span>  
  
```csharp  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 <span data-ttu-id="8d42b-115">Všimněte si, že syntaxe pro popis typu parametru omezení delegáti je stejná jako u metody:</span><span class="sxs-lookup"><span data-stu-id="8d42b-115">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>  
  
```csharp  
delegate T MyDelegate<T>() where T : new()  
```  
  
 <span data-ttu-id="8d42b-116">Informace pro obecné delegáty najdete v tématu [obecní delegáti](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="8d42b-116">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
 <span data-ttu-id="8d42b-117">Podrobnosti o syntaxi a použití omezení najdete v tématu [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8d42b-117">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="8d42b-118">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8d42b-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8d42b-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d42b-119">See Also</span></span>  
 [<span data-ttu-id="8d42b-120">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8d42b-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8d42b-121">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="8d42b-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8d42b-122">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="8d42b-122">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="8d42b-123">New – omezení</span><span class="sxs-lookup"><span data-stu-id="8d42b-123">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)  
 [<span data-ttu-id="8d42b-124">Omezení parametrů typů</span><span class="sxs-lookup"><span data-stu-id="8d42b-124">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
