---
title: Obecná rozhraní – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 4cce23da7579e30ecff80b3afb92a5a58795c1bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712205"
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="90db0-102">Obecná rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="90db0-102">Generic Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="90db0-103">Je často užitečné definovat rozhraní pro obecné třídy kolekce nebo pro obecné třídy, které představují položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="90db0-103">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="90db0-104">Předvolbou pro obecné třídy je použití <xref:System.IComparable%601> obecných <xref:System.IComparable>rozhraní, například spíše než , aby se zabránilo zabalení a rozbalení operace na typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="90db0-104">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="90db0-105">Knihovna tříd rozhraní .NET Framework definuje několik obecných rozhraní <xref:System.Collections.Generic> pro použití s třídami kolekce v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="90db0-105">The .NET Framework class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="90db0-106">Pokud je rozhraní zadáno jako omezení parametru typu, lze použít pouze typy, které implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="90db0-106">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="90db0-107">Následující příklad kódu `SortedList<T>` ukazuje třídu, `GenericList<T>` která je odvozena od třídy.</span><span class="sxs-lookup"><span data-stu-id="90db0-107">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="90db0-108">Další informace naleznete [v tématu Úvod do obecných typů](./index.md).</span><span class="sxs-lookup"><span data-stu-id="90db0-108">For more information, see [Introduction to Generics](./index.md).</span></span> <span data-ttu-id="90db0-109">`SortedList<T>`přidá omezení `where T : IComparable<T>`.</span><span class="sxs-lookup"><span data-stu-id="90db0-109">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="90db0-110">To umožňuje `BubbleSort` metodu v `SortedList<T>` <xref:System.IComparable%601.CompareTo%2A> použití obecné metody na list prvky.</span><span class="sxs-lookup"><span data-stu-id="90db0-110">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="90db0-111">V tomto příkladu jsou prvky `Person`seznamu jednoduchou třídou , která implementuje `IComparable<Person>`.</span><span class="sxs-lookup"><span data-stu-id="90db0-111">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 <span data-ttu-id="90db0-112">Více rozhraní lze zadat jako omezení pro jeden typ, takto:</span><span class="sxs-lookup"><span data-stu-id="90db0-112">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 <span data-ttu-id="90db0-113">Rozhraní může definovat více než jeden parametr typu, a to následovně:</span><span class="sxs-lookup"><span data-stu-id="90db0-113">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 <span data-ttu-id="90db0-114">Pravidla dědičnosti, která platí pro třídy platí také pro rozhraní:</span><span class="sxs-lookup"><span data-stu-id="90db0-114">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 <span data-ttu-id="90db0-115">Obecná rozhraní mohou dědit z neobecných rozhraní, pokud je obecné rozhraní kontravariantní, což znamená, že používá pouze parametr typu jako vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90db0-115">Generic interfaces can inherit from non-generic interfaces if the generic interface is contravariant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="90db0-116">V knihovně tříd rozhraní <xref:System.Collections.Generic.IEnumerable%601> .NET <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> Framework `T` dědí z, <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> protože <xref:System.Collections.Generic.IEnumerator%601.Current%2A> používá pouze v návratové hodnotě a v vlastnosti getter.</span><span class="sxs-lookup"><span data-stu-id="90db0-116">In the .NET Framework class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="90db0-117">Konkrétní třídy mohou implementovat uzavřené konstruované rozhraní, a to následovně:</span><span class="sxs-lookup"><span data-stu-id="90db0-117">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 <span data-ttu-id="90db0-118">Obecné třídy mohou implementovat obecná rozhraní nebo uzavřená konstruovaná rozhraní, pokud seznam parametrů třídy poskytuje všechny argumenty vyžadované rozhraním, a to následovně:</span><span class="sxs-lookup"><span data-stu-id="90db0-118">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 <span data-ttu-id="90db0-119">Pravidla, která řídí přetížení metody jsou stejné pro metody v rámci obecných tříd, obecných struktur nebo obecných rozhraní.</span><span class="sxs-lookup"><span data-stu-id="90db0-119">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="90db0-120">Další informace naleznete [v tématu Obecné metody](./generic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="90db0-120">For more information, see [Generic Methods](./generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90db0-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="90db0-121">See also</span></span>

- [<span data-ttu-id="90db0-122">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="90db0-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="90db0-123">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="90db0-123">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="90db0-124">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="90db0-124">interface</span></span>](../../language-reference/keywords/interface.md)
- [<span data-ttu-id="90db0-125">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="90db0-125">Generics</span></span>](../../../standard/generics/index.md)
