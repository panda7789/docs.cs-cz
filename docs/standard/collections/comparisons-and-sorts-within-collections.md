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
ms.openlocfilehash: 3360652f22ed39ccfd99f9863052fe584b78562f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159257"
---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="c95be-102">Porovnávání a řazení v kolekcích</span><span class="sxs-lookup"><span data-stu-id="c95be-102">Comparisons and Sorts Within Collections</span></span>
<span data-ttu-id="c95be-103">Třídy <xref:System.Collections> provádět porovnání v téměř všechny procesy, které se podílejí na správě kolekcí, zda hledání prvku odebrat nebo vrácení hodnoty páru klíč a hodnota.</span><span class="sxs-lookup"><span data-stu-id="c95be-103">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>  
  
 <span data-ttu-id="c95be-104">Kolekce obvykle využívají porovnání rovnosti a/nebo porovnávání pořadí.</span><span class="sxs-lookup"><span data-stu-id="c95be-104">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="c95be-105">Pro porovnání se používají dvě konstrukce.</span><span class="sxs-lookup"><span data-stu-id="c95be-105">Two constructs are used for comparisons.</span></span>  
  
<a name="BKMK_Checkingforequality"></a>
## <a name="checking-for-equality"></a><span data-ttu-id="c95be-106">Kontrola rovnosti</span><span class="sxs-lookup"><span data-stu-id="c95be-106">Checking for equality</span></span>  
 <span data-ttu-id="c95be-107">Metody, `Contains`jako <xref:System.Collections.IList.IndexOf%2A> <xref:System.Collections.Generic.List%601.LastIndexOf%2A>je `Remove` například , , a použít porovnávání rovnosti pro prvky kolekce.</span><span class="sxs-lookup"><span data-stu-id="c95be-107">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="c95be-108">Pokud kolekce je obecný, než položky jsou porovnány pro rovnost podle následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="c95be-108">If the collection is generic, than items are compared for equality according to the following guidelines:</span></span>  
  
- <span data-ttu-id="c95be-109">Pokud typ T <xref:System.IEquatable%601> implementuje obecné rozhraní, pak <xref:System.IEquatable%601.Equals%2A> porovnávání rovnosti je metoda tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c95be-109">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>  
  
- <span data-ttu-id="c95be-110">Pokud typ T <xref:System.IEquatable%601>neimplementuje , <xref:System.Object.Equals%2A?displayProperty=nameWithType> se používá.</span><span class="sxs-lookup"><span data-stu-id="c95be-110">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> is used.</span></span>  
  
 <span data-ttu-id="c95be-111">Kromě toho některé přetížení konstruktoru pro kolekce <xref:System.Collections.Generic.IEqualityComparer%601> slovníku přijmout implementaci, která se používá k porovnání klíčů pro rovnost.</span><span class="sxs-lookup"><span data-stu-id="c95be-111">In addition, some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="c95be-112">Například viz <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> konstruktor.</span><span class="sxs-lookup"><span data-stu-id="c95be-112">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> constructor.</span></span>  
  
<a name="BKMK_Determiningsortorder"></a>
## <a name="determining-sort-order"></a><span data-ttu-id="c95be-113">Určení pořadí řazení</span><span class="sxs-lookup"><span data-stu-id="c95be-113">Determining sort order</span></span>  
 <span data-ttu-id="c95be-114">Metody, `BinarySearch` jako `Sort` je například a použít porovnání pořadí pro prvky kolekce.</span><span class="sxs-lookup"><span data-stu-id="c95be-114">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="c95be-115">Porovnání může být mezi prvky kolekce nebo mezi elementem a zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="c95be-115">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="c95be-116">Pro porovnání objektů je koncept a `default comparer` a `explicit comparer`.</span><span class="sxs-lookup"><span data-stu-id="c95be-116">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>  
  
 <span data-ttu-id="c95be-117">Výchozí porovnávání spoléhá alespoň na jeden z objektů, které jsou porovnány s implementací rozhraní **IComparable.**</span><span class="sxs-lookup"><span data-stu-id="c95be-117">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="c95be-118">Je vhodné implementovat **IComparable** na všechny třídy se používají jako hodnoty v seznamu kolekce nebo jako klíče v kolekci slovníku.</span><span class="sxs-lookup"><span data-stu-id="c95be-118">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="c95be-119">Pro obecnou kolekci porovnání rovnosti je určena podle následujících:</span><span class="sxs-lookup"><span data-stu-id="c95be-119">For a generic collection, equality comparison is determined according to the following:</span></span>  
  
- <span data-ttu-id="c95be-120">Pokud typ T <xref:System.IComparable%601?displayProperty=nameWithType> implementuje obecné rozhraní, pak <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> výchozí porovnávání je metoda tohoto rozhraní</span><span class="sxs-lookup"><span data-stu-id="c95be-120">If type T implements the <xref:System.IComparable%601?displayProperty=nameWithType> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> method of that interface</span></span>  
  
- <span data-ttu-id="c95be-121">Pokud typ T implementuje <xref:System.IComparable?displayProperty=nameWithType> neobecné rozhraní, pak <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> výchozí porovnávání je metoda tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c95be-121">If type T implements the non-generic <xref:System.IComparable?displayProperty=nameWithType> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> method of that interface.</span></span>  
  
- <span data-ttu-id="c95be-122">Pokud typ T neimplementuje žádné rozhraní, pak neexistuje žádný výchozí porovnávání a porovnávání nebo porovnání delegát musí být poskytnuty explicitně.</span><span class="sxs-lookup"><span data-stu-id="c95be-122">If type T doesn’t implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>  
  
 <span data-ttu-id="c95be-123">Chcete-li poskytnout explicitní porovnání, některé metody přijmout **IComparer** implementace jako parametr.</span><span class="sxs-lookup"><span data-stu-id="c95be-123">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="c95be-124">Metoda například <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> přijímá <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementaci.</span><span class="sxs-lookup"><span data-stu-id="c95be-124">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation.</span></span>  
  
 <span data-ttu-id="c95be-125">Aktuální nastavení jazykové verze systému může ovlivnit porovnání a řazení v rámci kolekce.</span><span class="sxs-lookup"><span data-stu-id="c95be-125">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="c95be-126">Ve výchozím nastavení porovnání a řazení ve **třídách Kolekce** jsou citlivé na jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="c95be-126">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="c95be-127">Chcete-li ignorovat nastavení jazykové verze a proto získat <xref:System.Globalization.CultureInfo.InvariantCulture%2A> konzistentní porovnání a <xref:System.Globalization.CultureInfo>řazení výsledků, použijte s přetížení majestátu, které přijímají .</span><span class="sxs-lookup"><span data-stu-id="c95be-127">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="c95be-128">Další informace naleznete [v tématu Provádění řetězcových operací necitlivých na jazykovou verzi v kolekcích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) a [provádění řetězcových operací necitlivých na jazykovou verzi v polích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="c95be-128">For more information, see [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>  
  
<a name="BKMK_Equalityandsortexample"></a>
## <a name="equality-and-sort-example"></a><span data-ttu-id="c95be-129">Příklad rovnosti a řazení</span><span class="sxs-lookup"><span data-stu-id="c95be-129">Equality and sort example</span></span>  
 <span data-ttu-id="c95be-130">Následující kód ukazuje implementaci <xref:System.IEquatable%601> a <xref:System.IComparable%601> na jednoduchý obchodní objekt.</span><span class="sxs-lookup"><span data-stu-id="c95be-130">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="c95be-131">Kromě toho, když je objekt uložen v seznamu a seřazeny, uvidíte, že <xref:System.Collections.Generic.List%601.Sort> volání `Part` metody má <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> za následek použití výchozího porovnávání pro typ a metodu implementovanou pomocí anonymní metody.</span><span class="sxs-lookup"><span data-stu-id="c95be-131">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c95be-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="c95be-132">See also</span></span>

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
