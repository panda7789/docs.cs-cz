---
title: Porovnávání a řazení v kolekcích
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11393f4013a1b5ed9dc90154f289466432102a38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573117"
---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="007e3-102">Porovnávání a řazení v kolekcích</span><span class="sxs-lookup"><span data-stu-id="007e3-102">Comparisons and Sorts Within Collections</span></span>
<span data-ttu-id="007e3-103"><xref:System.Collections> Třídy provádění porovnávání v téměř všechny procesy související Správa kolekcí, zda hledání elementu, který chcete odebrat nebo vrací hodnotu z dvojice klíč hodnota.</span><span class="sxs-lookup"><span data-stu-id="007e3-103">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>  
  
 <span data-ttu-id="007e3-104">Kolekce obvykle využívají procedury rovnosti a řazení porovnávací funkce.</span><span class="sxs-lookup"><span data-stu-id="007e3-104">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="007e3-105">Pro porovnání se používají dva konstruktory.</span><span class="sxs-lookup"><span data-stu-id="007e3-105">Two constructs are used for comparisons.</span></span>  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a><span data-ttu-id="007e3-106">Kontrola rovnosti</span><span class="sxs-lookup"><span data-stu-id="007e3-106">Checking for equality</span></span>  
 <span data-ttu-id="007e3-107">Metody, jako `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, a `Remove` použít procedury rovnosti pro elementy z kolekce.</span><span class="sxs-lookup"><span data-stu-id="007e3-107">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="007e3-108">Pokud je kolekce Obecné, než položky jsou porovnána shoda podle následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="007e3-108">If the collection is generic, than items are compared for equality according to the following guidelines:</span></span>  
  
-   <span data-ttu-id="007e3-109">Pokud se implementuje typu t. <xref:System.IEquatable%601> obecné rozhraní a pak procedury rovnosti je <xref:System.IEquatable%601.Equals%2A> metody tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="007e3-109">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>  
  
-   <span data-ttu-id="007e3-110">Pokud typ T neimplementuje <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> se používá.</span><span class="sxs-lookup"><span data-stu-id="007e3-110">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> is used.</span></span>  
  
 <span data-ttu-id="007e3-111">Kromě toho některé přetěžování konstruktoru pro kolekce slovníku přijímá <xref:System.Collections.Generic.IEqualityComparer%601> implementace, která se používá k porovnání rovnosti klíče.</span><span class="sxs-lookup"><span data-stu-id="007e3-111">In addition, Some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="007e3-112">Příklad, naleznete v části <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="007e3-112">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> constructor.</span></span>  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a><span data-ttu-id="007e3-113">Určení pořadí řazení</span><span class="sxs-lookup"><span data-stu-id="007e3-113">Determining sort order</span></span>  
 <span data-ttu-id="007e3-114">Metody, jako `BinarySearch` a `Sort` použít řazení porovnávače pro elementy z kolekce.</span><span class="sxs-lookup"><span data-stu-id="007e3-114">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="007e3-115">Porovnávání může být mezi elementy kolekce nebo mezi elementem a zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="007e3-115">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="007e3-116">Pro porovnání objektů, je koncept `default comparer` a `explicit comparer`.</span><span class="sxs-lookup"><span data-stu-id="007e3-116">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>  
  
 <span data-ttu-id="007e3-117">Výchozí porovnávače spoléhá na alespoň jeden z objektů porovnávané implementovat **IComparable** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="007e3-117">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="007e3-118">Je vhodné implementovat **IComparable** na všechny třídy se používají jako hodnoty v seznamu kolekce nebo jako klíče v kolekci slovníku.</span><span class="sxs-lookup"><span data-stu-id="007e3-118">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="007e3-119">Pro obecnou kolekci je určen porovnání rovnosti podle následující:</span><span class="sxs-lookup"><span data-stu-id="007e3-119">For a generic collection, equality comparison is determined according to the following:</span></span>  
  
-   <span data-ttu-id="007e3-120">Pokud typ T implementuje <xref:System.IComparable%601?displayProperty=nameWithType> obecné rozhraní, činí výchozí porovnávače <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> metody tohoto rozhraní</span><span class="sxs-lookup"><span data-stu-id="007e3-120">If type T implements the <xref:System.IComparable%601?displayProperty=nameWithType> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> method of that interface</span></span>  
  
-   <span data-ttu-id="007e3-121">Pokud typ T implementuje neobecnou <xref:System.IComparable?displayProperty=nameWithType> rozhraní, pak je výchozí porovnávače <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> metody tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="007e3-121">If type T implements the non-generic <xref:System.IComparable?displayProperty=nameWithType> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> method of that interface.</span></span>  
  
-   <span data-ttu-id="007e3-122">Pokud typ T neimplementuje buď rozhraní, nejsou k dispozici žádné výchozí porovnávače a je třeba explicitně zadat delegáta porovnávače nebo porovnání.</span><span class="sxs-lookup"><span data-stu-id="007e3-122">If type T doesn’t implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>  
  
 <span data-ttu-id="007e3-123">Pokud chcete zadat explicitní porovnání, některé metody přijmout **IComparer** implementace jako parametr.</span><span class="sxs-lookup"><span data-stu-id="007e3-123">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="007e3-124">Například <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metoda přijímá <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementace.</span><span class="sxs-lookup"><span data-stu-id="007e3-124">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation.</span></span>  
  
 <span data-ttu-id="007e3-125">Aktuální nastavení jazykové verze systému může ovlivnit porovnávání a řazení v rámci kolekce.</span><span class="sxs-lookup"><span data-stu-id="007e3-125">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="007e3-126">Ve výchozím nastavení, porovnávání a řazení v **kolekce** třídy jsou závislé na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="007e3-126">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="007e3-127">Chcete-li ignorovat nastavení jazykové verze a proto získat konzistentní porovnání a řazení výsledků, použijte <xref:System.Globalization.CultureInfo.InvariantCulture%2A> se členy přetížení, které přijímají <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="007e3-127">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="007e3-128">Další informace najdete v tématu [provádění řetězcových operací nezávislých na jazykové verzi v kolekcích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) a [provádění řetězcových operací nezávislých na jazykové verzi v polích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="007e3-128">For more information, see [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a><span data-ttu-id="007e3-129">Příklad porovnávání a řazení</span><span class="sxs-lookup"><span data-stu-id="007e3-129">Equality and sort example</span></span>  
 <span data-ttu-id="007e3-130">Následující kód ukazuje implementaci nástroje <xref:System.IEquatable%601> a <xref:System.IComparable%601> na objekt jednoduché firmy.</span><span class="sxs-lookup"><span data-stu-id="007e3-130">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="007e3-131">Kromě toho, pokud je objekt uložený v seznamu a seřadit, zobrazí se tohoto volání <xref:System.Collections.Generic.List%601.Sort> metoda výsledkem použití výchozí porovnávače pro `Part` typ a <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> metoda implementována pomocí anonymní metody.</span><span class="sxs-lookup"><span data-stu-id="007e3-131">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="007e3-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="007e3-132">See Also</span></span>  
 <xref:System.Collections.IComparer>  
 <xref:System.IEquatable%601>  
 <xref:System.Collections.Generic.IComparer%601>  
 <xref:System.IComparable>  
 <xref:System.IComparable%601>
