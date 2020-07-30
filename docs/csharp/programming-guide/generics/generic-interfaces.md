---
title: Obecná rozhraní – Průvodce programováním v C#
description: Seznamte se s používáním obecných rozhraní v jazyce C#. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 43817a236e95b3ab8fd0ba94da98457eeec2396c
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301889"
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="e1410-104">Obecná rozhraní (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e1410-104">Generic Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="e1410-105">Často je užitečné definovat rozhraní buď pro obecné třídy kolekce, nebo pro obecné třídy, které reprezentují položky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="e1410-105">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="e1410-106">Preference pro obecné třídy je použití obecných rozhraní, například <xref:System.IComparable%601> spíše než <xref:System.IComparable> , aby se zabránilo zabalení a rozbalení operací na typech hodnot.</span><span class="sxs-lookup"><span data-stu-id="e1410-106">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="e1410-107">Knihovna tříd .NET Framework definuje několik obecných rozhraní pro použití s třídami kolekce v <xref:System.Collections.Generic> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e1410-107">The .NET Framework class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="e1410-108">Když je rozhraní zadáno jako omezení parametru typu, lze použít pouze typy, které implementují rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e1410-108">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="e1410-109">Následující příklad kódu ukazuje `SortedList<T>` třídu, která je odvozena od `GenericList<T>` třídy.</span><span class="sxs-lookup"><span data-stu-id="e1410-109">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="e1410-110">Další informace najdete v tématu [Úvod do obecných typů](./index.md).</span><span class="sxs-lookup"><span data-stu-id="e1410-110">For more information, see [Introduction to Generics](./index.md).</span></span> <span data-ttu-id="e1410-111">`SortedList<T>`Přidá omezení `where T : IComparable<T>` .</span><span class="sxs-lookup"><span data-stu-id="e1410-111">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="e1410-112">To umožňuje, aby `BubbleSort` metoda v nástroji `SortedList<T>` používala obecnou <xref:System.IComparable%601.CompareTo%2A> metodu pro prvky seznamu.</span><span class="sxs-lookup"><span data-stu-id="e1410-112">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="e1410-113">V tomto příkladu jsou prvky seznamu jednoduchou třídou, `Person` , která implementuje `IComparable<Person>` .</span><span class="sxs-lookup"><span data-stu-id="e1410-113">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 <span data-ttu-id="e1410-114">Více rozhraní lze zadat jako omezení pro jeden typ následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e1410-114">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 <span data-ttu-id="e1410-115">Rozhraní může definovat více než jeden parametr typu, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e1410-115">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 <span data-ttu-id="e1410-116">Pravidla dědičnosti, která se vztahují na třídy, se vztahují také na rozhraní:</span><span class="sxs-lookup"><span data-stu-id="e1410-116">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 <span data-ttu-id="e1410-117">Obecná rozhraní mohou dědit z neobecných rozhraní, pokud je obecné rozhraní kontravariantní, což znamená, že používá pouze parametr typu jako návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e1410-117">Generic interfaces can inherit from non-generic interfaces if the generic interface is contravariant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="e1410-118">V knihovně tříd .NET Framework <xref:System.Collections.Generic.IEnumerable%601> dědí z, <xref:System.Collections.IEnumerable> protože <xref:System.Collections.Generic.IEnumerable%601> používá pouze `T` v návratové hodnotě <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> a v <xref:System.Collections.Generic.IEnumerator%601.Current%2A> getter vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e1410-118">In the .NET Framework class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="e1410-119">Konkrétní třídy mohou implementovat uzavřená vytvořená rozhraní, a to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e1410-119">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 <span data-ttu-id="e1410-120">Obecné třídy mohou implementovat Obecná rozhraní nebo uzavřená vytvořená rozhraní, pokud seznam parametrů třídy poskytuje všechny argumenty vyžadované rozhraním, a to takto:</span><span class="sxs-lookup"><span data-stu-id="e1410-120">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 <span data-ttu-id="e1410-121">Pravidla, která řídí přetížení metody, jsou stejná pro metody v obecných třídách, obecných strukturách nebo obecných rozhraních.</span><span class="sxs-lookup"><span data-stu-id="e1410-121">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="e1410-122">Další informace najdete v tématu [Obecné metody](./generic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="e1410-122">For more information, see [Generic Methods](./generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1410-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1410-123">See also</span></span>

- [<span data-ttu-id="e1410-124">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e1410-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e1410-125">Úvod do obecných typů</span><span class="sxs-lookup"><span data-stu-id="e1410-125">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="e1410-126">prostředí</span><span class="sxs-lookup"><span data-stu-id="e1410-126">interface</span></span>](../../language-reference/keywords/interface.md)
- [<span data-ttu-id="e1410-127">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="e1410-127">Generics</span></span>](../../../standard/generics/index.md)
