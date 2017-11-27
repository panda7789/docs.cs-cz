---
title: "Obecné metody (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 63252dbe4307889f57d35e23eb0575f84358d737
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="d2ca1-102">Obecné metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d2ca1-102">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="d2ca1-103">Obecná metoda je metoda, která je deklarovaný s parametry typu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d2ca1-103">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 <span data-ttu-id="d2ca1-104">Následující příklad kódu ukazuje jeden ze způsobů k volání metody pomocí `int` pro argument typu:</span><span class="sxs-lookup"><span data-stu-id="d2ca1-104">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 <span data-ttu-id="d2ca1-105">Argument typu můžete vypustit a kompilátor odvodí.</span><span class="sxs-lookup"><span data-stu-id="d2ca1-105">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="d2ca1-106">Následující volání do `Swap` je ekvivalentem předchozího volání:</span><span class="sxs-lookup"><span data-stu-id="d2ca1-106">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 <span data-ttu-id="d2ca1-107">Stejná pravidla pro odvození typu týkají statických metod a instance metody.</span><span class="sxs-lookup"><span data-stu-id="d2ca1-107">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="d2ca1-108">Kompilátor můžete infer – parametry typu podle argumenty metoda, kterou předáte v; nemůže infer – parametry typu jenom z omezení nebo vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d2ca1-108">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="d2ca1-109">Odvození typu proto nefunguje s metodami, které mají žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="d2ca1-109">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="d2ca1-110">Odvození typu nastane při kompilaci než kompilátor pokusí přeložit přetížené metody podpisy.</span><span class="sxs-lookup"><span data-stu-id="d2ca1-110">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="d2ca1-111">Kompilátor logiku odvození typu platí pro všechny obecné metody, které sdílejí stejný název.</span><span class="sxs-lookup"><span data-stu-id="d2ca1-111">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="d2ca1-112">V kroku rozlišení přetížení kompilátor obsahuje pouze obecné metody ve kterých byla úspěšná odvození typu.</span><span class="sxs-lookup"><span data-stu-id="d2ca1-112">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="d2ca1-113">V rámci obecné třídy neobecnou metody přístup parametry typu na úrovni třídy následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d2ca1-113">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 <span data-ttu-id="d2ca1-114">Pokud definujete obecné metody, která přijímá stejnými parametry typu jako obsahující třídy, kompilátor vygeneruje upozornění CS0693, protože v rámci oboru metody argument zadaný pro vnitřní `T` skryje argument zadaný pro vnější `T`.</span><span class="sxs-lookup"><span data-stu-id="d2ca1-114">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning CS0693 because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="d2ca1-115">Pokud budete potřebovat flexibilitu voláním metody – obecná třída s argumenty typu než ty, které jsou zadané, když byla vytvořena instance třídy, zvažte zadat jiný identifikátor pro typ parametru metody, jak je znázorněno v `GenericList2<T>` v následujícím Příklad.</span><span class="sxs-lookup"><span data-stu-id="d2ca1-115">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 <span data-ttu-id="d2ca1-116">Pomocí omezení pro povolení více specializované operací parametrů typů v metodách.</span><span class="sxs-lookup"><span data-stu-id="d2ca1-116">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="d2ca1-117">Tato verze `Swap<T>`nyní s názvem `SwapIfGreater<T>`, lze použít pouze s argumenty typu, které implementují <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="d2ca1-117">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 <span data-ttu-id="d2ca1-118">Obecné metody mohou být přetíženy na několik parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="d2ca1-118">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="d2ca1-119">Například následující metody můžete všechny nacházet ve stejné třídě:</span><span class="sxs-lookup"><span data-stu-id="d2ca1-119">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="d2ca1-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d2ca1-120">C# Language Specification</span></span>  
 <span data-ttu-id="d2ca1-121">Další informace najdete v tématu [Specifikace jazyka C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d2ca1-121">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ca1-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2ca1-122">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="d2ca1-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="d2ca1-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d2ca1-124">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="d2ca1-124">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="d2ca1-125">Metody</span><span class="sxs-lookup"><span data-stu-id="d2ca1-125">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
