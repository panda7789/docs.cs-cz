---
title: Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CaseInsensitiveComparer class, using
- CollectionsUtil.CreateCaseInsensitiveHashtable method
- culture-insensitive string operations, collections
- collections [.NET Framework], culture-insensitive string operations
- CaseInsensitiveHashCodeProvider class, using
- ArrayList.Sort method
- SortedList class, culture-insensitive string operations
- culture parameter
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
ms.openlocfilehash: 13a9f4896a37be4297f2a1a11435b85ade381c66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353676"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="d284c-102">Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích</span><span class="sxs-lookup"><span data-stu-id="d284c-102">Performing Culture-Insensitive String Operations in Collections</span></span>

<span data-ttu-id="d284c-103">V oboru <xref:System.Collections> názvů jsou třídy a členy, které ve výchozím nastavení poskytují chování citlivé na jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="d284c-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="d284c-104">Konstruktory bez parametrů <xref:System.Collections.CaseInsensitiveComparer> pro <xref:System.Collections.CaseInsensitiveHashCodeProvider> a třídy inicializovat novou instanci pomocí vlastnosti. <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d284c-104">The parameterless constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="d284c-105">Všechna přetížení <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> metody vytvořit novou instanci <xref:System.Collections.Hashtable> třídy pomocí vlastnosti `Thread.CurrentCulture` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="d284c-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="d284c-106">Přetížení <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> metody provádět jazykové verze citlivé řazení `Thread.CurrentCulture`ve výchozím nastavení pomocí .</span><span class="sxs-lookup"><span data-stu-id="d284c-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="d284c-107">Řazení a vyhledávání v <xref:System.Collections.SortedList> a může `Thread.CurrentCulture` být ovlivněna při řetězce jsou používány jako klíče.</span><span class="sxs-lookup"><span data-stu-id="d284c-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="d284c-108">Postupujte podle doporučení použití uvedených v této části získat výsledky necitlivé na jazykové verzi z těchto tříd a metod v oboru `Collections` názvů.</span><span class="sxs-lookup"><span data-stu-id="d284c-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>

> [!NOTE]
> <span data-ttu-id="d284c-109">Předání <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> metody porovnání provést porovnání necitlivé na jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="d284c-109">Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="d284c-110">Nezpůsobuje však nejazykové porovnání, například pro cesty k souborům, klíče registru a proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="d284c-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="d284c-111">Nepodporuje ani rozhodnutí o zabezpečení založená na výsledku porovnání.</span><span class="sxs-lookup"><span data-stu-id="d284c-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="d284c-112">Pro nejazykové porovnání nebo podporu pro rozhodnutí o zabezpečení založené na výsledcích aplikace <xref:System.StringComparison> by měla použít metodu porovnání, která přijímá hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d284c-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="d284c-113">Aplikace by pak <xref:System.StringComparison>měla projít .</span><span class="sxs-lookup"><span data-stu-id="d284c-113">The application should then pass <xref:System.StringComparison>.</span></span>

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="d284c-114">Použití tříd CaseInsensitiveComparer a CaseInsensitiveHashCodeProvider</span><span class="sxs-lookup"><span data-stu-id="d284c-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>

<span data-ttu-id="d284c-115">Konstruktory bez parametrů `CaseInsensitiveHashCodeProvider` `CaseInsensitiveComparer` pro a inicializovat novou `Thread.CurrentCulture`instanci třídy pomocí , výsledkem chování citlivé na jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="d284c-115">The parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="d284c-116">Následující příklad kódu ukazuje konstruktor `Hashtable` pro, který je citlivý na jazykovou verzi, protože používá konstruktory bez parametrů pro `CaseInsensitiveHashCodeProvider` a `CaseInsensitiveComparer`.</span><span class="sxs-lookup"><span data-stu-id="d284c-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the parameterless constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

<span data-ttu-id="d284c-117">Pokud chcete vytvořit jazykovou verzi `Hashtable` necitlivý pomocí `CaseInsensitiveComparer` třídy a, `CaseInsensitiveHashCodeProvider` inicializovat nové instance těchto `culture` tříd pomocí konstruktory, které přijímají parametr.</span><span class="sxs-lookup"><span data-stu-id="d284c-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="d284c-118">Pro `culture` parametr zadejte <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d284c-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d284c-119">Následující příklad kódu ukazuje konstruktor pro jazykovou `Hashtable`verzi necitlivý .</span><span class="sxs-lookup"><span data-stu-id="d284c-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

```vb
internalHashtable = New Hashtable(New
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))
```

```csharp
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider
    (CultureInfo.InvariantCulture),
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));
```

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="d284c-120">Použití metody CollectionsUtil.CreateCaseInsensitiveHashTable</span><span class="sxs-lookup"><span data-stu-id="d284c-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>

<span data-ttu-id="d284c-121">Metoda `CollectionsUtil.CreateCaseInsensitiveHashTable` je užitečným zástupcem pro vytvoření `Hashtable` nové instance třídy, která ignoruje případ řetězců.</span><span class="sxs-lookup"><span data-stu-id="d284c-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="d284c-122">Všechna přetížení `CollectionsUtil.CreateCaseInsensitiveHashTable` metody jsou však citlivé na jazykovou verzi, protože používají `Thread.CurrentCulture` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d284c-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="d284c-123">Pomocí této metody nelze `Hashtable` vytvořit necitlivý na jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="d284c-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="d284c-124">Chcete-li vytvořit jazykovou verzi necitlivý `Hashtable`, použijte `Hashtable` konstruktor, který přijímá `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="d284c-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="d284c-125">Pro `culture` parametr zadejte `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="d284c-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="d284c-126">Následující příklad kódu ukazuje konstruktor pro jazykovou `Hashtable`verzi necitlivý .</span><span class="sxs-lookup"><span data-stu-id="d284c-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>

```vb
internalHashtable = New Hashtable(New
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))
```

```csharp
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider
    (CultureInfo.InvariantCulture),
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));
```

<a name="cpconperformingculture-insensitivestringoperationsincollectionsanchor1"></a>

## <a name="using-the-sortedlist-class"></a><span data-ttu-id="d284c-127">Použití třídy SortedList</span><span class="sxs-lookup"><span data-stu-id="d284c-127">Using the SortedList Class</span></span>

<span data-ttu-id="d284c-128">A `SortedList` představuje kolekci párů klíč a hodnota, které jsou seřazeny podle klíčů a jsou přístupné klíčem a indexem.</span><span class="sxs-lookup"><span data-stu-id="d284c-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="d284c-129">Při použití `SortedList` kde řetězce jsou klíče, řazení a vyhledávání může být `Thread.CurrentCulture` ovlivněna vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d284c-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="d284c-130">Chcete-li získat chování necitlivé na jazykovou `SortedList`verzi z , vytvořte `SortedList` pomocí jednoho z konstruktorů, který přijímá `comparer` parametr.</span><span class="sxs-lookup"><span data-stu-id="d284c-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="d284c-131">Parametr `comparer` určuje implementaci, která <xref:System.Collections.IComparer> se má použít při porovnávání klíčů.</span><span class="sxs-lookup"><span data-stu-id="d284c-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="d284c-132">Pro parametr zadejte vlastní třídu `CultureInfo.InvariantCulture` porovnávače, která používá k porovnání klíčů.</span><span class="sxs-lookup"><span data-stu-id="d284c-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="d284c-133">Následující příklad ilustruje vlastní třídu porovnávání necitlivou na `comparer` jazykovou `SortedList` verzi, kterou můžete zadat jako parametr konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d284c-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>

```vb
Imports System.Collections
Imports System.Globalization

Friend Class InvariantComparer
    Implements IComparer
    Private m_compareInfo As CompareInfo
    Friend Shared [Default] As New InvariantComparer()

    Friend Sub New()
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo
    End Sub

    Public Function Compare(a As Object, b As Object) As Integer _
            Implements IComparer.Compare
        Dim sa As String = CType(a, String)
        Dim sb As String = CType(b, String)
        If Not (sa Is Nothing) And Not (sb Is Nothing) Then
            Return m_compareInfo.Compare(sa, sb)
        Else
            Return Comparer.Default.Compare(a, b)
        End If
    End Function
End Class
```

```csharp
using System;
using System.Collections;
using System.Globalization;

internal class InvariantComparer : IComparer
{
    private CompareInfo m_compareInfo;
    internal static readonly InvariantComparer Default = new
        InvariantComparer();

    internal InvariantComparer()
    {
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo;
    }

    public int Compare(Object a, Object b)
    {
        String sa = a as String;
        String sb = b as String;
        if (sa != null && sb != null)
            return m_compareInfo.Compare(sa, sb);
        else
            return Comparer.Default.Compare(a,b);
    }
}
```

<span data-ttu-id="d284c-134">Obecně platí, že `SortedList` pokud použijete řetězce on bez zadání vlastního invariantního porovnávání, změna po `Thread.CurrentCulture` naplnění seznamu může zrušit platnost seznamu.</span><span class="sxs-lookup"><span data-stu-id="d284c-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>

## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="d284c-135">Použití metody ArrayList.Sort</span><span class="sxs-lookup"><span data-stu-id="d284c-135">Using the ArrayList.Sort Method</span></span>

<span data-ttu-id="d284c-136">Přetížení `ArrayList.Sort` metody provádět jazykové verze citlivé řazení `Thread.CurrentCulture` ve výchozím nastavení pomocí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d284c-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="d284c-137">Výsledky se mohou lišit podle jazykové verze v důsledku různých pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="d284c-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="d284c-138">Chcete-li eliminovat chování citlivé na jazykovou verzi, `IComparer` použijte přetížení této metody, které přijímají implementaci.</span><span class="sxs-lookup"><span data-stu-id="d284c-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="d284c-139">Pro `comparer` parametr zadejte vlastní invariantní třídu porovnávače, která používá `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="d284c-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="d284c-140">Příklad vlastní třídy invariantního porovnávání je uveden v [tématu Using the SortedList Class.](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1)</span><span class="sxs-lookup"><span data-stu-id="d284c-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="d284c-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="d284c-141">See also</span></span>

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [<span data-ttu-id="d284c-142">Provádění řetězcových operací nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="d284c-142">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
