---
title: Obecné metody (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
ms.openlocfilehash: 0fb5267e6324d3dffd1ad5a72ef3718c8cdd08b8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552902"
---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="e6d1b-102">Obecné metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e6d1b-102">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="e6d1b-103">Obecná metoda je metoda, která je deklarována s parametry typu, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e6d1b-103">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]  
  
 <span data-ttu-id="e6d1b-104">Následující příklad kódu ukazuje jeden způsob, jak volat metodu pomocí `int` pro argument typu:</span><span class="sxs-lookup"><span data-stu-id="e6d1b-104">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]  
  
 <span data-ttu-id="e6d1b-105">Také můžete vynechat argument typu a kompilátor odvodí.</span><span class="sxs-lookup"><span data-stu-id="e6d1b-105">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="e6d1b-106">Následující volání `Swap` je ekvivalentem předchozího volání:</span><span class="sxs-lookup"><span data-stu-id="e6d1b-106">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]  
  
 <span data-ttu-id="e6d1b-107">Stejná pravidla pro odvození typu platí pro statické metody a metody instance.</span><span class="sxs-lookup"><span data-stu-id="e6d1b-107">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="e6d1b-108">Kompilátor může odvodit typ parametrů na základě argumentů metody, které můžete předat nelze jej odvodit jenom z omezení parametry typu nebo návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e6d1b-108">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="e6d1b-109">Odvození typu proměnné proto nefunguje s metodami, které mají žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="e6d1b-109">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="e6d1b-110">Odvození typu vyvolá v době kompilace předtím, než kompilátor pokusí přeložit podpisy přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="e6d1b-110">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="e6d1b-111">Kompilátor použije logiku odvození typu na všechny obecné metody, které mají stejný název.</span><span class="sxs-lookup"><span data-stu-id="e6d1b-111">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="e6d1b-112">V kroku rozlišení přetížení kompilátor obsahuje pouze tyto obecné metody, na které bylo úspěšné odvození typu proměnné.</span><span class="sxs-lookup"><span data-stu-id="e6d1b-112">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="e6d1b-113">V rámci obecné třídy neobecné metody mají přístup k úrovni třídy typové parametry, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e6d1b-113">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]  
  
 <span data-ttu-id="e6d1b-114">Při definování obecné metody, která má stejné parametry typu jako obsahující třídu, kompilátor vygeneruje upozornění CS0693, protože v rámci oboru metody argument zadaný pro vnitřní `T` skryje argument zadaný pro vnější `T`.</span><span class="sxs-lookup"><span data-stu-id="e6d1b-114">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning CS0693 because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="e6d1b-115">Pokud požadujete flexibilitu volání metody obecnou třídu s argumenty typů než ty, pokud byla vytvořena instance třídy, zvažte poskytnutí jiný identifikátor pro typ parametru metody, jak je znázorněno v `GenericList2<T>` následující Příklad.</span><span class="sxs-lookup"><span data-stu-id="e6d1b-115">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]  
  
 <span data-ttu-id="e6d1b-116">Umožňuje povolit více specializované operace u parametrů typu v metodách omezení.</span><span class="sxs-lookup"><span data-stu-id="e6d1b-116">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="e6d1b-117">Tato verze `Swap<T>`teď s názvem `SwapIfGreater<T>`, lze použít pouze s argumenty typů, které implementují <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="e6d1b-117">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]  
  
 <span data-ttu-id="e6d1b-118">Obecné metody lze přetížit na několik parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="e6d1b-118">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="e6d1b-119">Například následující metody můžete všechny nacházet ve stejné třídě:</span><span class="sxs-lookup"><span data-stu-id="e6d1b-119">For example, the following methods can all be located in the same class:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="e6d1b-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e6d1b-120">C# Language Specification</span></span>  
 <span data-ttu-id="e6d1b-121">Další informace najdete v tématu [Specifikace jazyka C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e6d1b-121">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d1b-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6d1b-122">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="e6d1b-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e6d1b-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e6d1b-124">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="e6d1b-124">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [<span data-ttu-id="e6d1b-125">Metody</span><span class="sxs-lookup"><span data-stu-id="e6d1b-125">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
