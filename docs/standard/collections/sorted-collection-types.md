---
title: "Typy řazených kolekcí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET Framework], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7efe53d472e1789d49acc3973acdf190c8ff6662
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="sorted-collection-types"></a><span data-ttu-id="3b7e6-102">Typy řazených kolekcí</span><span class="sxs-lookup"><span data-stu-id="3b7e6-102">Sorted Collection Types</span></span>
<span data-ttu-id="3b7e6-103"><xref:System.Collections.SortedList?displayProperty=nameWithType> Třídy, <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> – obecná třída a <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> obecné třídy jsou podobné <xref:System.Collections.Hashtable> – třída a <xref:System.Collections.Generic.Dictionary%602> obecné třídy v tom, že implementují <xref:System.Collections.IDictionary> rozhraní, ale zachovávají jejich elementy v řazení pořadí pomocí klíče a nemají o(1), která vložení a načtení charakteristik zatřiďovacích tabulkách.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-103">The <xref:System.Collections.SortedList?displayProperty=nameWithType> class, the <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> generic class, and the <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> generic class are similar to the <xref:System.Collections.Hashtable> class and the <xref:System.Collections.Generic.Dictionary%602> generic class in that they implement the <xref:System.Collections.IDictionary> interface, but they maintain their elements in sort order by key, and they do not have the O(1) insertion and retrieval characteristic of hash tables.</span></span> <span data-ttu-id="3b7e6-104">Tři třídy mají společnou několik funkcí:</span><span class="sxs-lookup"><span data-stu-id="3b7e6-104">The three classes have several features in common:</span></span>  
  
-   <span data-ttu-id="3b7e6-105">Všechny tři třídy implementují <xref:System.Collections.IDictionary?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-105">All three classes implement the <xref:System.Collections.IDictionary?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="3b7e6-106">Dvě obecné třídy také implementovat <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> obecné rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-106">The two generic classes also implement the <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> generic interface.</span></span>  
  
-   <span data-ttu-id="3b7e6-107">Každý prvek je dvojice klíč/hodnota pro účely výčtu.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-107">Each element is a key/value pair for enumeration purposes.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3b7e6-108">Neobecná <xref:System.Collections.SortedList> vrací <xref:System.Collections.DictionaryEntry> objekty při výčtu, i když dva obecné typy vracejí <xref:System.Collections.Generic.KeyValuePair%602> objekty.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-108">The nongeneric <xref:System.Collections.SortedList> class returns <xref:System.Collections.DictionaryEntry> objects when enumerated, although the two generic types return <xref:System.Collections.Generic.KeyValuePair%602> objects.</span></span>  
  
-   <span data-ttu-id="3b7e6-109">Elementy jsou seřazené podle <xref:System.Collections.IComparer?displayProperty=nameWithType> implementace (pro neobecný <xref:System.Collections.SortedList>) nebo <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementace (pro dvě obecné třídy).</span><span class="sxs-lookup"><span data-stu-id="3b7e6-109">Elements are sorted according to a <xref:System.Collections.IComparer?displayProperty=nameWithType> implementation (for nongeneric <xref:System.Collections.SortedList>) or a <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation (for the two generic classes).</span></span>  
  
-   <span data-ttu-id="3b7e6-110">Každá třída poskytuje vlastnosti, které vracejí kolekce obsahující pouze klíče nebo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-110">Each class provides properties that return collections containing only the keys or only the values.</span></span>  
  
 <span data-ttu-id="3b7e6-111">Následující tabulka uvádí některé rozdíly mezi dvěma třídami seřazený seznam a <xref:System.Collections.Generic.SortedDictionary%602> třídy.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-111">The following table lists some of the differences between the two sorted list classes and the <xref:System.Collections.Generic.SortedDictionary%602> class.</span></span>  
  
|<span data-ttu-id="3b7e6-112"><xref:System.Collections.SortedList>Neobecná třída a <xref:System.Collections.Generic.SortedList%602> – obecná třída</span><span class="sxs-lookup"><span data-stu-id="3b7e6-112"><xref:System.Collections.SortedList> nongeneric class and <xref:System.Collections.Generic.SortedList%602> generic class</span></span>|<span data-ttu-id="3b7e6-113"><xref:System.Collections.Generic.SortedDictionary%602>– Obecná třída</span><span class="sxs-lookup"><span data-stu-id="3b7e6-113"><xref:System.Collections.Generic.SortedDictionary%602> generic class</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="3b7e6-114">Jsou indexované vlastnosti, které vracejí klíče a hodnoty, umožňuje efektivní indexované načtení.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-114">The properties that return keys and values are indexed, allowing efficient indexed retrieval.</span></span>|<span data-ttu-id="3b7e6-115">Neindexované načítání.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-115">No indexed retrieval.</span></span>|  
|<span data-ttu-id="3b7e6-116">Načítání je O (protokolu `n`).</span><span class="sxs-lookup"><span data-stu-id="3b7e6-116">Retrieval is O(log `n`).</span></span>|<span data-ttu-id="3b7e6-117">Načítání je O (protokolu `n`).</span><span class="sxs-lookup"><span data-stu-id="3b7e6-117">Retrieval is O(log `n`).</span></span>|  
|<span data-ttu-id="3b7e6-118">Vložení a odebrání jsou obecně O (`n`), nicméně vložení je O (protokolu `n`) pro data, která jsou již v pořadí, řazení, aby každý prvek přidán na konec seznamu.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-118">Insertion and removal are generally O(`n`); however, insertion is O(log `n`) for data that are already in sort order, so that each element is added to the end of the list.</span></span> <span data-ttu-id="3b7e6-119">(Předpokladem je, že není požadována změna velikosti.)</span><span class="sxs-lookup"><span data-stu-id="3b7e6-119">(This assumes that a resize is not required.)</span></span>|<span data-ttu-id="3b7e6-120">Vložení a odebrání jsou O (protokolu `n`).</span><span class="sxs-lookup"><span data-stu-id="3b7e6-120">Insertion and removal are O(log `n`).</span></span>|  
|<span data-ttu-id="3b7e6-121">Vyžaduje méně paměti než <xref:System.Collections.Generic.SortedDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-121">Uses less memory than a <xref:System.Collections.Generic.SortedDictionary%602>.</span></span>|<span data-ttu-id="3b7e6-122">Větší spotřebu paměti než <xref:System.Collections.SortedList> neobecné třídy a <xref:System.Collections.Generic.SortedList%602> – obecná třída.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-122">Uses more memory than the <xref:System.Collections.SortedList> nongeneric class and the <xref:System.Collections.Generic.SortedList%602> generic class.</span></span>|  
  
 <span data-ttu-id="3b7e6-123">Seřazené seznamy nebo slovníky, které musí být přístupné z více vláken současně, můžete přidat logiku řazení na třídu, která je odvozena z <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-123">For sorted lists or dictionaries that must be accessible concurrently from multiple threads, you can add sorting logic to a class that derives from <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b7e6-124">Hodnoty, které obsahují vlastní klíče (například záznamy zaměstnanců, které obsahují identifikační číslo zaměstnance), můžete vytvořit kolekci s klíčem, která má některé vlastnosti seznamu a některé vlastnosti slovníku odvozené z <xref:System.Collections.ObjectModel.KeyedCollection%602> obecné Třída.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-124">For values that contain their own keys (for example, employee records that contain an employee ID number), you can create a keyed collection that has some characteristics of a list and some characteristics of a dictionary by deriving from the <xref:System.Collections.ObjectModel.KeyedCollection%602> generic class.</span></span>  
  
 <span data-ttu-id="3b7e6-125">Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], <xref:System.Collections.Generic.SortedSet%601> třída poskytuje samoobslužné vyrovnávání stromové struktury, která udržuje data seřazená po vložení, odstranění a vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-125">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the <xref:System.Collections.Generic.SortedSet%601> class provides a self-balancing tree that maintains data in sorted order after insertions, deletions, and searches.</span></span> <span data-ttu-id="3b7e6-126">Tato třída a <xref:System.Collections.Generic.HashSet%601> implementaci třídy <xref:System.Collections.Generic.ISet%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3b7e6-126">This class and the <xref:System.Collections.Generic.HashSet%601> class implement the <xref:System.Collections.Generic.ISet%601> interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b7e6-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b7e6-127">See Also</span></span>  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>  
 [<span data-ttu-id="3b7e6-128">Běžně používané typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="3b7e6-128">Commonly Used Collection Types</span></span>](../../../docs/standard/collections/commonly-used-collection-types.md)
