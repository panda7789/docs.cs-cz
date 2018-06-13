---
title: Obecné kolekce v rozhraní .NET
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET], collections
- generic collections [.NET]
- generic types [.NET]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 829ef35d2e26f67ea956a0838d93b9667ad58df4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576617"
---
# <a name="generic-collections-in-net"></a><span data-ttu-id="b3b00-102">Obecné kolekce v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="b3b00-102">Generic Collections in .NET</span></span>

 <span data-ttu-id="b3b00-103">Poskytuje řadu obecné třídy kolekcí v knihovně tříd rozhraní .NET <xref:System.Collections.Generic> a <xref:System.Collections.ObjectModel> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="b3b00-103">The .NET class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="b3b00-104">Další podrobné informace o těchto tříd naleznete v tématu [běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="b3b00-104">For more detailed information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
### <a name="systemcollectionsgeneric"></a><span data-ttu-id="b3b00-105">System.Collections.Generic –</span><span class="sxs-lookup"><span data-stu-id="b3b00-105">System.Collections.Generic</span></span>  
 <span data-ttu-id="b3b00-106">Mnoho typů obecnou kolekci je analogických neobecné typy.</span><span class="sxs-lookup"><span data-stu-id="b3b00-106">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="b3b00-107"><xref:System.Collections.Generic.Dictionary%602> je obecná verze <xref:System.Collections.Hashtable>; používá obecná struktura <xref:System.Collections.Generic.KeyValuePair%602> pro výčet místo <xref:System.Collections.DictionaryEntry>.</span><span class="sxs-lookup"><span data-stu-id="b3b00-107"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="b3b00-108"><xref:System.Collections.Generic.List%601> je obecná verze <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="b3b00-108"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="b3b00-109">Existují obecné <xref:System.Collections.Generic.Queue%601> a <xref:System.Collections.Generic.Stack%601> třídy, které odpovídají neobecné verzi.</span><span class="sxs-lookup"><span data-stu-id="b3b00-109">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="b3b00-110">Obecné a neobecné verzích <xref:System.Collections.Generic.SortedList%602>.</span><span class="sxs-lookup"><span data-stu-id="b3b00-110">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="b3b00-111">Obě verze jsou hybridních slovník a seznam.</span><span class="sxs-lookup"><span data-stu-id="b3b00-111">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="b3b00-112"><xref:System.Collections.Generic.SortedDictionary%602> Obecná třída je čistě slovník a nemá žádný neobecný protějšek.</span><span class="sxs-lookup"><span data-stu-id="b3b00-112">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="b3b00-113"><xref:System.Collections.Generic.LinkedList%601> Obecná třída je true odkazovaného seznamu.</span><span class="sxs-lookup"><span data-stu-id="b3b00-113">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="b3b00-114">Nemá žádné neobecné protějšky.</span><span class="sxs-lookup"><span data-stu-id="b3b00-114">It has no nongeneric counterpart.</span></span>  
  
### <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="b3b00-115">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="b3b00-115">System.Collections.ObjectModel</span></span>  
 <span data-ttu-id="b3b00-116"><xref:System.Collections.ObjectModel.Collection%601> Obecná třída poskytuje základní třídu pro odvození vlastních obecnou kolekci typů.</span><span class="sxs-lookup"><span data-stu-id="b3b00-116">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="b3b00-117"><xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Třída poskytuje snadný způsob, jak vytvořit kolekci jen pro čtení z libovolného typu, který implementuje <xref:System.Collections.Generic.IList%601> obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b3b00-117">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="b3b00-118"><xref:System.Collections.ObjectModel.KeyedCollection%602> Obecná třída poskytuje způsob, jak ukládat objekty, které obsahují vlastní klíče.</span><span class="sxs-lookup"><span data-stu-id="b3b00-118">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="b3b00-119">Další obecné typy</span><span class="sxs-lookup"><span data-stu-id="b3b00-119">Other Generic Types</span></span>  
 <span data-ttu-id="b3b00-120"><xref:System.Nullable%601> Obecná struktura umožňuje používat typy hodnot, jako by mohla být přiřazena `null`.</span><span class="sxs-lookup"><span data-stu-id="b3b00-120">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="b3b00-121">To může být užitečné při práci s dotazů databáze, kde může být chybějící pole, které obsahují typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="b3b00-121">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="b3b00-122">Parametr obecného typu mohou být jakéhokoli typu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b3b00-122">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3b00-123">V jazyce C# a Visual Basic, není nutné používat <xref:System.Nullable%601> explicitně, protože jazyk má syntaxi pro typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="b3b00-123">In C# and Visual Basic, it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span> <span data-ttu-id="b3b00-124">V tématu [typy s možnou hodnotou Null (C# programování průvodce)](../../csharp/programming-guide/nullable-types/index.md) a [typy s možnou hodnotou Null hodnot (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="b3b00-124">See [Nullable types (C# Programming Guide)](../../csharp/programming-guide/nullable-types/index.md) and [Nullable value types (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).</span></span> 
  
 <span data-ttu-id="b3b00-125"><xref:System.ArraySegment%601> Obecná struktura poskytuje způsob, jak vymezení rozsahu elementů v rámci jednorozměrné, počítáno od nuly pole libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="b3b00-125">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="b3b00-126">Parametr obecného typu je typ elementy pole.</span><span class="sxs-lookup"><span data-stu-id="b3b00-126">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="b3b00-127"><xref:System.EventHandler%601> Obecný delegát se eliminuje potřeba deklarovat typ delegáta pro zpracování událostí, pokud událost následuje vzor zpracování událostí používané [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b3b00-127">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="b3b00-128">Předpokládejme například, že jste vytvořili `MyEventArgs` třídy, které jsou odvozené od <xref:System.EventArgs>, aby udržení data pro událost.</span><span class="sxs-lookup"><span data-stu-id="b3b00-128">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="b3b00-129">Potom můžete událost deklarovat takto:</span><span class="sxs-lookup"><span data-stu-id="b3b00-129">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="b3b00-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3b00-130">See Also</span></span>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [<span data-ttu-id="b3b00-131">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="b3b00-131">Generics</span></span>](../../../docs/standard/generics/index.md)  
 [<span data-ttu-id="b3b00-132">Obecné delegáty pro manipulaci s poli a seznamy</span><span class="sxs-lookup"><span data-stu-id="b3b00-132">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [<span data-ttu-id="b3b00-133">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3b00-133">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
