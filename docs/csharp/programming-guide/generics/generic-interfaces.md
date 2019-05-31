---
title: Obecná rozhraní - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 7fc79874c8e1ff24c38d288d3f6708e2851419e3
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423470"
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="ac997-102">Obecná rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ac997-102">Generic Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="ac997-103">Často je užitečné k definování rozhraní pro obecné kolekce tříd nebo pro obecné třídy, které představují položek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="ac997-103">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="ac997-104">Předvolby pro obecné třídy, je pomocí obecných rozhraní, jako <xref:System.IComparable%601> spíše než <xref:System.IComparable>, aby se zabránilo operace zabalení a rozbalení u typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="ac997-104">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="ac997-105">Definuje několik obecných rozhraní pro použití s kolekcí tříd v knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ac997-105">The .NET Framework class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="ac997-106">Pokud je zadána jako omezení pro parametr typu, je možné pouze typy, které implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ac997-106">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="ac997-107">Následující příklad kódu ukazuje `SortedList<T>` třídu odvozenou od `GenericList<T>` třídy.</span><span class="sxs-lookup"><span data-stu-id="ac997-107">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="ac997-108">Další informace najdete v tématu [Úvod do obecných typů](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="ac997-108">For more information, see [Introduction to Generics](../../../csharp/programming-guide/generics/index.md).</span></span> <span data-ttu-id="ac997-109">`SortedList<T>` Přidá omezení `where T : IComparable<T>`.</span><span class="sxs-lookup"><span data-stu-id="ac997-109">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="ac997-110">Díky tomu `BubbleSort` metoda `SortedList<T>` museli používat obecná <xref:System.IComparable%601.CompareTo%2A> metodu na seznamu elementů.</span><span class="sxs-lookup"><span data-stu-id="ac997-110">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="ac997-111">V tomto příkladu, prvky seznamu jsou jednoduchá třída `Person`, který implementuje `IComparable<Person>`.</span><span class="sxs-lookup"><span data-stu-id="ac997-111">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 <span data-ttu-id="ac997-112">Několik rozhraní se dá nastavit jako omezení u jednoho typu, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ac997-112">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 <span data-ttu-id="ac997-113">Rozhraní může definovat více než jeden parametr typu, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ac997-113">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 <span data-ttu-id="ac997-114">Pravidla dědičnosti, které se vztahují na třídy platí také pro rozhraní:</span><span class="sxs-lookup"><span data-stu-id="ac997-114">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 <span data-ttu-id="ac997-115">Obecná rozhraní může dědit z rozhraní Obecné, pokud obecného rozhraní je kontravariantní, což znamená, že pouze jako návratová hodnota používá jeho typu parametru.</span><span class="sxs-lookup"><span data-stu-id="ac997-115">Generic interfaces can inherit from non-generic interfaces if the generic interface is contravariant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="ac997-116">V knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic.IEnumerable%601> dědí z <xref:System.Collections.IEnumerable> protože <xref:System.Collections.Generic.IEnumerable%601> využívat jenom takové `T` v návratové hodnotě <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> a <xref:System.Collections.Generic.IEnumerator%601.Current%2A> metoda getter vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ac997-116">In the .NET Framework class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="ac997-117">Konkrétní třídy mohou implementovat rozhraní uzavřený konstruovaný, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ac997-117">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 <span data-ttu-id="ac997-118">Obecné třídy můžete implementovat obecné rozhraní nebo uzavřený konstruovaný rozhraní za předpokladu, seznam parametrů třídy poskytuje všechny argumenty, které vyžadují rozhraní, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ac997-118">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 <span data-ttu-id="ac997-119">Pravidla, která řídí přetížení metody jsou stejné pro metody v rámci obecných tříd, obecné struktury nebo obecná rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ac997-119">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="ac997-120">Další informace najdete v tématu [obecné metody](../../../csharp/programming-guide/generics/generic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="ac997-120">For more information, see [Generic Methods](../../../csharp/programming-guide/generics/generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac997-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac997-121">See also</span></span>

- [<span data-ttu-id="ac997-122">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ac997-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ac997-123">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="ac997-123">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="ac997-124">interface</span><span class="sxs-lookup"><span data-stu-id="ac997-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)
- [<span data-ttu-id="ac997-125">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="ac997-125">Generics</span></span>](~/docs/standard/generics/index.md)
