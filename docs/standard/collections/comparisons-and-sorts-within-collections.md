---
title: Porovnávání a řazení v kolekcích
description: Porovnávání & seřadí pomocí tříd System. Collections v rozhraní .NET, které vám pomůžou najít prvek pro odebrání nebo vrácení hodnoty páru klíč-hodnota.
ms.date: 04/30/2020
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
ms.openlocfilehash: aa001e8469947a532d77059bd52024c6b47b508e
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769194"
---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="bfdda-103">Porovnávání a řazení v kolekcích</span><span class="sxs-lookup"><span data-stu-id="bfdda-103">Comparisons and sorts within collections</span></span>

<span data-ttu-id="bfdda-104"><xref:System.Collections>Třídy provádějí porovnávání téměř všemi procesy zapojenými do správy kolekcí, bez ohledu na to, zda je element vyhledá nebo nevrátí hodnotu dvojice klíč-hodnota.</span><span class="sxs-lookup"><span data-stu-id="bfdda-104">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>

<span data-ttu-id="bfdda-105">Kolekce obvykle využívají porovnávání rovnosti a/nebo porovnávací řazení.</span><span class="sxs-lookup"><span data-stu-id="bfdda-105">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="bfdda-106">Pro porovnání se používají dva konstrukce.</span><span class="sxs-lookup"><span data-stu-id="bfdda-106">Two constructs are used for comparisons.</span></span>

<a name="BKMK_Checkingforequality"></a>
## <a name="check-for-equality"></a><span data-ttu-id="bfdda-107">Kontrolovat rovnost</span><span class="sxs-lookup"><span data-stu-id="bfdda-107">Check for equality</span></span>

<span data-ttu-id="bfdda-108">Metody jako `Contains` ,, <xref:System.Collections.IList.IndexOf%2A> <xref:System.Collections.Generic.List%601.LastIndexOf%2A> a `Remove` používají pro prvky kolekce porovnávání rovnosti.</span><span class="sxs-lookup"><span data-stu-id="bfdda-108">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="bfdda-109">Pokud je kolekce obecná, pak jsou položky porovnány s rovností podle následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="bfdda-109">If the collection is generic, then items are compared for equality according to the following guidelines:</span></span>

- <span data-ttu-id="bfdda-110">Pokud typ T implementuje <xref:System.IEquatable%601> Obecné rozhraní, pak je porovnávání rovnosti metodou tohoto <xref:System.IEquatable%601.Equals%2A> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bfdda-110">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>

- <span data-ttu-id="bfdda-111">Pokud typ T neimplementuje <xref:System.IEquatable%601> , <xref:System.Object.Equals%2A?displayProperty=nameWithType> je použit.</span><span class="sxs-lookup"><span data-stu-id="bfdda-111">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> is used.</span></span>

<span data-ttu-id="bfdda-112">Kromě toho některé přetížení konstruktoru pro kolekce slovníku přijímají <xref:System.Collections.Generic.IEqualityComparer%601> implementaci, která se používá k porovnání klíčů pro rovnost.</span><span class="sxs-lookup"><span data-stu-id="bfdda-112">In addition, some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="bfdda-113">Příklad naleznete v <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="bfdda-113">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A> constructor.</span></span>

<a name="BKMK_Determiningsortorder"></a>
## <a name="determine-sort-order"></a><span data-ttu-id="bfdda-114">Určit pořadí řazení</span><span class="sxs-lookup"><span data-stu-id="bfdda-114">Determine sort order</span></span>

<span data-ttu-id="bfdda-115">Metody jako `BinarySearch` a `Sort` používají porovnávací řazení pro prvky kolekce.</span><span class="sxs-lookup"><span data-stu-id="bfdda-115">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="bfdda-116">Porovnání mohou být mezi prvky kolekce nebo mezi prvkem a zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="bfdda-116">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="bfdda-117">Pro porovnávání objektů existuje koncept `default comparer` a `explicit comparer` .</span><span class="sxs-lookup"><span data-stu-id="bfdda-117">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>

<span data-ttu-id="bfdda-118">Výchozí porovnávání spoléhá alespoň na jeden objekt, který je porovnán pro implementaci rozhraní **IComparable** .</span><span class="sxs-lookup"><span data-stu-id="bfdda-118">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="bfdda-119">Je vhodné implementovat **IComparable** u všech tříd, které se používají jako hodnoty v kolekci seznamu nebo jako klíče v kolekci slovníku.</span><span class="sxs-lookup"><span data-stu-id="bfdda-119">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="bfdda-120">Pro obecnou kolekci je porovnání rovnosti určeno podle následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="bfdda-120">For a generic collection, equality comparison is determined according to the following:</span></span>

- <span data-ttu-id="bfdda-121">Pokud typ T implementuje <xref:System.IComparable%601?displayProperty=nameWithType> Obecné rozhraní, pak je výchozí porovnávací metodou tohoto <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bfdda-121">If type T implements the <xref:System.IComparable%601?displayProperty=nameWithType> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> method of that interface</span></span>

- <span data-ttu-id="bfdda-122">Pokud typ T implementuje jiné než obecné <xref:System.IComparable?displayProperty=nameWithType> rozhraní, pak je výchozí porovnávací metodou tohoto <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bfdda-122">If type T implements the non-generic <xref:System.IComparable?displayProperty=nameWithType> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> method of that interface.</span></span>

- <span data-ttu-id="bfdda-123">Pokud typ T neimplementuje rozhraní, pak neexistuje žádná výchozí porovnávací hodnota a explicitní porovnávací nebo relační delegát musí být poskytnut explicitně.</span><span class="sxs-lookup"><span data-stu-id="bfdda-123">If type T doesn't implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>

<span data-ttu-id="bfdda-124">Aby bylo možné poskytnout explicitní porovnání, některé metody přijímají implementaci **IComparer** jako parametr.</span><span class="sxs-lookup"><span data-stu-id="bfdda-124">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="bfdda-125">Například <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> Metoda přijímá <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementaci.</span><span class="sxs-lookup"><span data-stu-id="bfdda-125">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation.</span></span>

<span data-ttu-id="bfdda-126">Aktuální nastavení jazykové verze systému může ovlivnit porovnání a seřazení v rámci kolekce.</span><span class="sxs-lookup"><span data-stu-id="bfdda-126">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="bfdda-127">Ve výchozím nastavení porovnání a řazení v **kolekcích** tříd jsou závislé na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="bfdda-127">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="bfdda-128">Chcete-li ignorovat nastavení jazykové verze, a proto získat konzistentní porovnání a řazení výsledků, použijte <xref:System.Globalization.CultureInfo.InvariantCulture%2A> s přetíženími členů, které přijímají <xref:System.Globalization.CultureInfo> .</span><span class="sxs-lookup"><span data-stu-id="bfdda-128">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="bfdda-129">Další informace naleznete v tématu [provádění řetězcových operací nezávislých na jazykové verzi v kolekcích](../globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) a [provádění řetězcových operací nezávislých na jazykové verzi v polích](../globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="bfdda-129">For more information, see [Performing Culture-Insensitive String Operations in Collections](../globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>

<a name="BKMK_Equalityandsortexample"></a>
## <a name="equality-and-sort-example"></a><span data-ttu-id="bfdda-130">Příklad rovnosti a řazení</span><span class="sxs-lookup"><span data-stu-id="bfdda-130">Equality and sort example</span></span>

<span data-ttu-id="bfdda-131">Následující kód ukazuje implementaci <xref:System.IEquatable%601> a <xref:System.IComparable%601> v jednoduchém obchodním objektu.</span><span class="sxs-lookup"><span data-stu-id="bfdda-131">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="bfdda-132">Kromě toho, když je objekt uložen v seznamu a seřazen, uvidíte, že volání <xref:System.Collections.Generic.List%601.Sort> metody je výsledkem použití výchozí porovnávací metody pro `Part` typ a <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> Metoda implementovaná pomocí anonymní metody.</span><span class="sxs-lookup"><span data-stu-id="bfdda-132">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>

[!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
[!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="bfdda-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfdda-133">See also</span></span>

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
