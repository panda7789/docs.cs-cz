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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159257"
---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="8b2a0-102">Porovnávání a řazení v kolekcích</span><span class="sxs-lookup"><span data-stu-id="8b2a0-102">Comparisons and Sorts Within Collections</span></span>
<span data-ttu-id="8b2a0-103">Třídy <xref:System.Collections> provádějí porovnání téměř všemi procesy zapojenými do správy kolekcí, bez ohledu na to, zda se má element vyhledat, nebo vrátit hodnotu páru klíč-hodnota.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-103">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>  
  
 <span data-ttu-id="8b2a0-104">Kolekce obvykle využívají porovnávání rovnosti a/nebo porovnávací řazení.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-104">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="8b2a0-105">Pro porovnání se používají dva konstrukce.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-105">Two constructs are used for comparisons.</span></span>  
  
<a name="BKMK_Checkingforequality"></a>
## <a name="checking-for-equality"></a><span data-ttu-id="8b2a0-106">Kontroluje se rovnost.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-106">Checking for equality</span></span>  
 <span data-ttu-id="8b2a0-107">Metody jako `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>a `Remove` používají pro prvky kolekce porovnávání rovnosti.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-107">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="8b2a0-108">Pokud je kolekce obecná, než jsou položky porovnány podle následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="8b2a0-108">If the collection is generic, than items are compared for equality according to the following guidelines:</span></span>  
  
- <span data-ttu-id="8b2a0-109">Pokud typ T implementuje obecné rozhraní <xref:System.IEquatable%601>, pak je porovnávání rovnosti metodou <xref:System.IEquatable%601.Equals%2A> tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-109">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>  
  
- <span data-ttu-id="8b2a0-110">Pokud typ T neimplementuje <xref:System.IEquatable%601>, použije se <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-110">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> is used.</span></span>  
  
 <span data-ttu-id="8b2a0-111">Kromě toho některé přetížení konstruktoru pro kolekce slovníku přijímají implementaci <xref:System.Collections.Generic.IEqualityComparer%601>, která se používá k porovnání klíčů pro rovnost.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-111">In addition, some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="8b2a0-112">Příklad naleznete v <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-112">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> constructor.</span></span>  
  
<a name="BKMK_Determiningsortorder"></a>
## <a name="determining-sort-order"></a><span data-ttu-id="8b2a0-113">Určování pořadí řazení</span><span class="sxs-lookup"><span data-stu-id="8b2a0-113">Determining sort order</span></span>  
 <span data-ttu-id="8b2a0-114">Metody jako `BinarySearch` a `Sort` používají pro prvky kolekce porovnávací řazení.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-114">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="8b2a0-115">Porovnání mohou být mezi prvky kolekce nebo mezi prvkem a zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-115">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="8b2a0-116">Pro porovnávání objektů existuje pojem `default comparer` a `explicit comparer`.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-116">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>  
  
 <span data-ttu-id="8b2a0-117">Výchozí porovnávání spoléhá alespoň na jeden objekt, který je porovnán pro implementaci rozhraní **IComparable** .</span><span class="sxs-lookup"><span data-stu-id="8b2a0-117">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="8b2a0-118">Je vhodné implementovat **IComparable** u všech tříd, které se používají jako hodnoty v kolekci seznamu nebo jako klíče v kolekci slovníku.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-118">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="8b2a0-119">Pro obecnou kolekci je porovnání rovnosti určeno podle následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="8b2a0-119">For a generic collection, equality comparison is determined according to the following:</span></span>  
  
- <span data-ttu-id="8b2a0-120">Pokud typ T implementuje obecné rozhraní <xref:System.IComparable%601?displayProperty=nameWithType>, pak je výchozí porovnávací metodou <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-120">If type T implements the <xref:System.IComparable%601?displayProperty=nameWithType> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> method of that interface</span></span>  
  
- <span data-ttu-id="8b2a0-121">Pokud typ T implementuje jiné než obecné <xref:System.IComparable?displayProperty=nameWithType> rozhraní, pak je výchozí porovnávací metoda <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-121">If type T implements the non-generic <xref:System.IComparable?displayProperty=nameWithType> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> method of that interface.</span></span>  
  
- <span data-ttu-id="8b2a0-122">Pokud typ T neimplementuje rozhraní, pak neexistuje žádná výchozí porovnávací hodnota a explicitní porovnávací nebo relační delegát musí být poskytnut explicitně.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-122">If type T doesn’t implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>  
  
 <span data-ttu-id="8b2a0-123">Aby bylo možné poskytnout explicitní porovnání, některé metody přijímají implementaci **IComparer** jako parametr.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-123">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="8b2a0-124">Například metoda <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> přijímá <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementaci.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-124">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation.</span></span>  
  
 <span data-ttu-id="8b2a0-125">Aktuální nastavení jazykové verze systému může ovlivnit porovnání a seřazení v rámci kolekce.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-125">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="8b2a0-126">Ve výchozím nastavení porovnání a řazení v **kolekcích** tříd jsou závislé na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-126">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="8b2a0-127">Chcete-li ignorovat nastavení jazykové verze, a proto získat konzistentní porovnání a řazení výsledků, použijte <xref:System.Globalization.CultureInfo.InvariantCulture%2A> s přetíženími členů, která přijímají <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-127">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="8b2a0-128">Další informace naleznete v tématu [provádění řetězcových operací nezávislých na jazykové verzi v kolekcích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) a [provádění řetězcových operací nezávislých na jazykové verzi v polích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="8b2a0-128">For more information, see [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>  
  
<a name="BKMK_Equalityandsortexample"></a>
## <a name="equality-and-sort-example"></a><span data-ttu-id="8b2a0-129">Příklad rovnosti a řazení</span><span class="sxs-lookup"><span data-stu-id="8b2a0-129">Equality and sort example</span></span>  
 <span data-ttu-id="8b2a0-130">Následující kód ukazuje implementaci <xref:System.IEquatable%601> a <xref:System.IComparable%601> v jednoduchém obchodním objektu.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-130">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="8b2a0-131">Kromě toho, když je objekt uložen v seznamu a seřazen, se zobrazí, že volání metody <xref:System.Collections.Generic.List%601.Sort> má za následek použití výchozí porovnávací metody pro `Part` typ a metoda <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> implementovaná pomocí anonymní metody.</span><span class="sxs-lookup"><span data-stu-id="8b2a0-131">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8b2a0-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b2a0-132">See also</span></span>

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
