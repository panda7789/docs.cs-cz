---
title: Obecná rozhraní (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 72f48aa1d70e6cf81b20adc547e2d418c4497256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323635"
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="7a576-102">Obecná rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="7a576-102">Generic Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="7a576-103">Je často užitečné k definování rozhraní pro obecné kolekce třídy, nebo pro obecné třídy, které představují položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="7a576-103">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="7a576-104">Předvolby pro obecné třídy je pomocí obecných rozhraní, jako například <xref:System.IComparable%601> místo <xref:System.IComparable>, aby se zabránilo operace zabalení a rozbalení u typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="7a576-104">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="7a576-105">Definuje několik obecných rozhraní pro použití s třídy kolekce v knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7a576-105">The .NET Framework class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="7a576-106">Pokud je zadána jako parametr typu omezení, lze použít pouze typy, které implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7a576-106">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="7a576-107">Následující příklad kódu ukazuje `SortedList<T>` třídu odvozenou od `GenericList<T>` třídy.</span><span class="sxs-lookup"><span data-stu-id="7a576-107">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="7a576-108">Další informace najdete v tématu [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="7a576-108">For more information, see [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span></span> <span data-ttu-id="7a576-109">`SortedList<T>` Přidá omezení `where T : IComparable<T>`.</span><span class="sxs-lookup"><span data-stu-id="7a576-109">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="7a576-110">Díky tomu `BubbleSort` metoda v `SortedList<T>` používat obecná <xref:System.IComparable%601.CompareTo%2A> metoda v seznamu elementů.</span><span class="sxs-lookup"><span data-stu-id="7a576-110">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="7a576-111">V tomto příkladu jsou seznamu elementů třídu jednoduché `Person`, která implementuje `IComparable<Person>`.</span><span class="sxs-lookup"><span data-stu-id="7a576-111">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]  
  
 <span data-ttu-id="7a576-112">Více rozhraní lze zadat jako omezení typu, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7a576-112">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]  
  
 <span data-ttu-id="7a576-113">Rozhraní můžete definovat více než jeden parametr typu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7a576-113">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]  
  
 <span data-ttu-id="7a576-114">Pravidla dědičnosti, které se vztahují na třídy platí i pro rozhraní:</span><span class="sxs-lookup"><span data-stu-id="7a576-114">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]  
  
 <span data-ttu-id="7a576-115">Obecná rozhraní může dědit vlastnosti z rozhraní neobecnou, pokud obecné rozhraní opravné položky ke variant, což znamená, že její parametr typu se použije pouze jako návratová hodnota.</span><span class="sxs-lookup"><span data-stu-id="7a576-115">Generic interfaces can inherit from non-generic interfaces if the generic interface is contra-variant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="7a576-116">V knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic.IEnumerable%601> dědí z <xref:System.Collections.IEnumerable> protože <xref:System.Collections.Generic.IEnumerable%601> používá jenom `T` v návratové hodnotě <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> a v <xref:System.Collections.Generic.IEnumerator%601.Current%2A> metoda getter vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7a576-116">In the .NET Framework class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="7a576-117">Konkrétní třídy můžete implementovat uzavřené sestavené rozhraní, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7a576-117">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]  
  
 <span data-ttu-id="7a576-118">Obecné třídy můžete implementovat obecné rozhraní nebo uzavřených sestavené rozhraní také seznam parametrů třída poskytuje všechny argumenty, které vyžadují rozhraní, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7a576-118">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]  
  
 <span data-ttu-id="7a576-119">Pravidla, která řídí přetěžování metody jsou stejné pro metody v obecné třídy, struktury obecné nebo obecná rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7a576-119">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="7a576-120">Další informace najdete v tématu [obecné metody](../../../csharp/programming-guide/generics/generic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="7a576-120">For more information, see [Generic Methods](../../../csharp/programming-guide/generics/generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a576-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a576-121">See Also</span></span>  
 [<span data-ttu-id="7a576-122">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7a576-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7a576-123">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="7a576-123">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="7a576-124">interface</span><span class="sxs-lookup"><span data-stu-id="7a576-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
 [<span data-ttu-id="7a576-125">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="7a576-125">Generics</span></span>](~/docs/standard/generics/index.md)
