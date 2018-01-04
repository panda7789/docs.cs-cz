---
title: "Generování kolekcí v architektuře .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], collections
- generic collections [.NET Framework]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d7e7d11446c14cffbef1e5cade5f082874187636
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="generic-collections-in-the-net-framework"></a><span data-ttu-id="0189c-102">Generování kolekcí v architektuře .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0189c-102">Generic Collections in the .NET Framework</span></span>
<span data-ttu-id="0189c-103">Toto téma obsahuje přehled obecné třídy kolekcí a jiné obecné typy v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0189c-103">This topic provides an overview of the generic collection classes and other generic types in the .NET Framework.</span></span>  
  
## <a name="generic-collections-in-the-net-framework"></a><span data-ttu-id="0189c-104">Generování kolekcí v architektuře .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0189c-104">Generic Collections in the .NET Framework</span></span>  
 <span data-ttu-id="0189c-105">Poskytuje řadu obecné třídy kolekcí v knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic> a <xref:System.Collections.ObjectModel> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="0189c-105">The .NET Framework class library provides a number of generic collection classes in the <xref:System.Collections.Generic> and <xref:System.Collections.ObjectModel> namespaces.</span></span> <span data-ttu-id="0189c-106">Další informace o těchto tříd naleznete v tématu [běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="0189c-106">For more information about these classes, see [Commonly Used Collection Types](../../../docs/standard/collections/commonly-used-collection-types.md).</span></span>  
  
### <a name="systemcollectionsgeneric"></a><span data-ttu-id="0189c-107">System.Collections.Generic –</span><span class="sxs-lookup"><span data-stu-id="0189c-107">System.Collections.Generic</span></span>  
 <span data-ttu-id="0189c-108">Mnoho typů obecnou kolekci je analogických neobecné typy.</span><span class="sxs-lookup"><span data-stu-id="0189c-108">Many of the generic collection types are direct analogs of nongeneric types.</span></span> <span data-ttu-id="0189c-109"><xref:System.Collections.Generic.Dictionary%602>je obecná verze <xref:System.Collections.Hashtable>; používá obecná struktura <xref:System.Collections.Generic.KeyValuePair%602> pro výčet místo <xref:System.Collections.DictionaryEntry>.</span><span class="sxs-lookup"><span data-stu-id="0189c-109"><xref:System.Collections.Generic.Dictionary%602> is a generic version of <xref:System.Collections.Hashtable>; it uses the generic structure <xref:System.Collections.Generic.KeyValuePair%602> for enumeration instead of <xref:System.Collections.DictionaryEntry>.</span></span>  
  
 <span data-ttu-id="0189c-110"><xref:System.Collections.Generic.List%601>je obecná verze <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="0189c-110"><xref:System.Collections.Generic.List%601> is a generic version of <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="0189c-111">Existují obecné <xref:System.Collections.Generic.Queue%601> a <xref:System.Collections.Generic.Stack%601> třídy, které odpovídají neobecné verzi.</span><span class="sxs-lookup"><span data-stu-id="0189c-111">There are generic <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601> classes that correspond to the nongeneric versions.</span></span>  
  
 <span data-ttu-id="0189c-112">Obecné a neobecné verzích <xref:System.Collections.Generic.SortedList%602>.</span><span class="sxs-lookup"><span data-stu-id="0189c-112">There are generic and nongeneric versions of <xref:System.Collections.Generic.SortedList%602>.</span></span> <span data-ttu-id="0189c-113">Obě verze jsou hybridních slovník a seznam.</span><span class="sxs-lookup"><span data-stu-id="0189c-113">Both versions are hybrids of a dictionary and a list.</span></span> <span data-ttu-id="0189c-114"><xref:System.Collections.Generic.SortedDictionary%602> Obecná třída je čistě slovník a nemá žádný neobecný protějšek.</span><span class="sxs-lookup"><span data-stu-id="0189c-114">The <xref:System.Collections.Generic.SortedDictionary%602> generic class is a pure dictionary and has no nongeneric counterpart.</span></span>  
  
 <span data-ttu-id="0189c-115"><xref:System.Collections.Generic.LinkedList%601> Obecná třída je true odkazovaného seznamu.</span><span class="sxs-lookup"><span data-stu-id="0189c-115">The <xref:System.Collections.Generic.LinkedList%601> generic class is a true linked list.</span></span> <span data-ttu-id="0189c-116">Nemá žádné neobecné protějšky.</span><span class="sxs-lookup"><span data-stu-id="0189c-116">It has no nongeneric counterpart.</span></span>  
  
### <a name="systemcollectionsobjectmodel"></a><span data-ttu-id="0189c-117">System.Collections.ObjectModel</span><span class="sxs-lookup"><span data-stu-id="0189c-117">System.Collections.ObjectModel</span></span>  
 <span data-ttu-id="0189c-118"><xref:System.Collections.ObjectModel.Collection%601> Obecná třída poskytuje základní třídu pro odvození vlastních obecnou kolekci typů.</span><span class="sxs-lookup"><span data-stu-id="0189c-118">The <xref:System.Collections.ObjectModel.Collection%601> generic class provides a base class for deriving your own generic collection types.</span></span> <span data-ttu-id="0189c-119"><xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Třída poskytuje snadný způsob, jak vytvořit kolekci jen pro čtení z libovolného typu, který implementuje <xref:System.Collections.Generic.IList%601> obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0189c-119">The <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> class provides an easy way to produce a read-only collection from any type that implements the <xref:System.Collections.Generic.IList%601> generic interface.</span></span> <span data-ttu-id="0189c-120"><xref:System.Collections.ObjectModel.KeyedCollection%602> Obecná třída poskytuje způsob, jak ukládat objekty, které obsahují vlastní klíče.</span><span class="sxs-lookup"><span data-stu-id="0189c-120">The <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class provides a way to store objects that contain their own keys.</span></span>  
  
## <a name="other-generic-types"></a><span data-ttu-id="0189c-121">Další obecné typy</span><span class="sxs-lookup"><span data-stu-id="0189c-121">Other Generic Types</span></span>  
 <span data-ttu-id="0189c-122"><xref:System.Nullable%601> Obecná struktura umožňuje používat typy hodnot, jako by mohla být přiřazena `null`.</span><span class="sxs-lookup"><span data-stu-id="0189c-122">The <xref:System.Nullable%601> generic structure allows you to use value types as if they could be assigned `null`.</span></span> <span data-ttu-id="0189c-123">To může být užitečné při práci s dotazů databáze, kde může být chybějící pole, které obsahují typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="0189c-123">This can be useful when working with database queries, where fields that contain value types can be missing.</span></span> <span data-ttu-id="0189c-124">Parametr obecného typu mohou být jakéhokoli typu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0189c-124">The generic type parameter can be any value type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0189c-125">V jazyce C# není nutné používat <xref:System.Nullable%601> explicitně, protože jazyk má syntaxi pro typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="0189c-125">In C# it is not necessary to use <xref:System.Nullable%601> explicitly because the language has syntax for nullable types.</span></span>  
  
 <span data-ttu-id="0189c-126"><xref:System.ArraySegment%601> Obecná struktura poskytuje způsob, jak vymezení rozsahu elementů v rámci jednorozměrné, počítáno od nuly pole libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="0189c-126">The <xref:System.ArraySegment%601> generic structure provides a way to delimit a range of elements within a one-dimensional, zero-based array of any type.</span></span> <span data-ttu-id="0189c-127">Parametr obecného typu je typ elementy pole.</span><span class="sxs-lookup"><span data-stu-id="0189c-127">The generic type parameter is the type of the array's elements.</span></span>  
  
 <span data-ttu-id="0189c-128"><xref:System.EventHandler%601> Obecný delegát se eliminuje potřeba deklarovat typ delegáta pro zpracování událostí, pokud událost následuje vzor zpracování událostí používané [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0189c-128">The <xref:System.EventHandler%601> generic delegate eliminates the need to declare a delegate type to handle events, if your event follows the event-handling pattern used by the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="0189c-129">Předpokládejme například, že jste vytvořili `MyEventArgs` třídy, které jsou odvozené od <xref:System.EventArgs>, aby udržení data pro událost.</span><span class="sxs-lookup"><span data-stu-id="0189c-129">For example, suppose you have created a `MyEventArgs` class, derived from <xref:System.EventArgs>, to hold the data for your event.</span></span> <span data-ttu-id="0189c-130">Potom můžete událost deklarovat takto:</span><span class="sxs-lookup"><span data-stu-id="0189c-130">You can then declare the event as follows:</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="0189c-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="0189c-131">See Also</span></span>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [<span data-ttu-id="0189c-132">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="0189c-132">Generics</span></span>](../../../docs/standard/generics/index.md)  
 [<span data-ttu-id="0189c-133">Obecné delegáty pro manipulaci s poli a seznamy</span><span class="sxs-lookup"><span data-stu-id="0189c-133">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [<span data-ttu-id="0189c-134">Obecná rozhraní</span><span class="sxs-lookup"><span data-stu-id="0189c-134">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)
