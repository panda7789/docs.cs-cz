---
title: "Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích"
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
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b84f25aa2470104be98b9f3858091c44f40ba6a7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="0064d-102">Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích</span><span class="sxs-lookup"><span data-stu-id="0064d-102">Performing Culture-Insensitive String Operations in Collections</span></span>
<span data-ttu-id="0064d-103">Existují třídy a členové <xref:System.Collections> obor názvů, který ve výchozím nastavení poskytují chování zohledňující jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="0064d-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="0064d-104">Výchozí konstruktory pro <xref:System.Collections.CaseInsensitiveComparer> a <xref:System.Collections.CaseInsensitiveHashCodeProvider> třídy inicializaci nové instance pomocí <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0064d-104">The default constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="0064d-105">Všechny přetížení <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> metoda vytvořit novou instanci třídy <xref:System.Collections.Hashtable> pomocí `Thread.CurrentCulture` vlastnost ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="0064d-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="0064d-106">Přetížení <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> metoda provést řazení zohledňující jazykovou verzi pomocí výchozí `Thread.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="0064d-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="0064d-107">Řazení a vyhledávání v <xref:System.Collections.SortedList> může být ovlivněno `Thread.CurrentCulture` při použití řetězce jako klíče.</span><span class="sxs-lookup"><span data-stu-id="0064d-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="0064d-108">Postupujte podle doporučení poskytnutých v této části získat nezávislé na jazykových výsledky z tyto třídy a metody v `Collections` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0064d-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>  
  
 <span data-ttu-id="0064d-109">**Poznámka:** předávání <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> k porovnání metoda provést porovnání na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="0064d-109">**Note** Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="0064d-110">Však nevytváří-lingvistické porovnání, například cesty k souborům, klíčů registru a proměnných prostředí.</span><span class="sxs-lookup"><span data-stu-id="0064d-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="0064d-111">Ani podporuje rozhodnutí o zabezpečení na základě výsledku porovnání.</span><span class="sxs-lookup"><span data-stu-id="0064d-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="0064d-112">Lingvistické porovnání nebo podporu pro zabezpečení na základě výsledku rozhodnutí, by aplikace měla používat porovnání metodu, která přijímá <xref:System.StringComparison> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0064d-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="0064d-113">Aplikace by pak předat <xref:System.StringComparison>.</span><span class="sxs-lookup"><span data-stu-id="0064d-113">The application should then pass <xref:System.StringComparison>.</span></span>  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="0064d-114">Pomocí CaseInsensitiveComparer a CaseInsensitiveHashCodeProvider</span><span class="sxs-lookup"><span data-stu-id="0064d-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>  
 <span data-ttu-id="0064d-115">Výchozí konstruktory pro `CaseInsensitiveHashCodeProvider` a `CaseInsensitiveComparer` inicializuje novou instanci třídy pomocí `Thread.CurrentCulture`, což chování zohledňující jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="0064d-115">The default constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="0064d-116">Následující příklad kódu ukazuje konstruktor pro `Hashtable` , je zohledňující jazykovou verzi, protože používá výchozí konstruktory pro `CaseInsensitiveHashCodeProvider` a `CaseInsensitiveComparer`.</span><span class="sxs-lookup"><span data-stu-id="0064d-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the default constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 <span data-ttu-id="0064d-117">Pokud chcete vytvořit nezávislé na jazykových `Hashtable` pomocí `CaseInsensitiveComparer` a `CaseInsensitiveHashCodeProvider` třídy, inicializaci nové instance těchto tříd pomocí konstruktorů, které přijímají `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="0064d-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="0064d-118">Pro `culture` parametr, zadejte <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0064d-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0064d-119">Následující příklad kódu ukazuje konstruktor pro nezávislé na jazykových `Hashtable`.</span><span class="sxs-lookup"><span data-stu-id="0064d-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>  
  
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
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="0064d-120">Pomocí CollectionsUtil.CreateCaseInsensitiveHashTable – metoda</span><span class="sxs-lookup"><span data-stu-id="0064d-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>  
 <span data-ttu-id="0064d-121">`CollectionsUtil.CreateCaseInsensitiveHashTable` Metoda je užitečná zkratka pro vytvoření nové instance `Hashtable` třídu, která nerozlišuje malá a velká řetězce.</span><span class="sxs-lookup"><span data-stu-id="0064d-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="0064d-122">Nicméně všechna přetížení `CollectionsUtil.CreateCaseInsensitiveHashTable` metoda jsou závislé na jazykové verzi, protože používají `Thread.CurrentCulture` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0064d-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="0064d-123">Nelze vytvořit nezávislé na jazykových `Hashtable` pomocí této metody.</span><span class="sxs-lookup"><span data-stu-id="0064d-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="0064d-124">Chcete-li vytvořit nezávislé na jazykových `Hashtable`, použijte `Hashtable` konstruktor, který přijímá `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="0064d-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="0064d-125">Pro `culture` parametr, zadejte `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="0064d-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="0064d-126">Následující příklad kódu ukazuje konstruktor pro nezávislé na jazykových `Hashtable`.</span><span class="sxs-lookup"><span data-stu-id="0064d-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>  
  
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
## <a name="using-the-sortedlist-class"></a><span data-ttu-id="0064d-127">Pomocí SortedList – třída</span><span class="sxs-lookup"><span data-stu-id="0064d-127">Using the SortedList Class</span></span>  
 <span data-ttu-id="0064d-128">A `SortedList` představuje kolekci párů klíč hodnota, které jsou seřazené podle klíče a je přístupný pomocí klíče a pro index.</span><span class="sxs-lookup"><span data-stu-id="0064d-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="0064d-129">Při použití `SortedList` tam, kde jsou řetězce klíčů, řazení a vyhledávání můžou mít vliv `Thread.CurrentCulture` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0064d-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="0064d-130">K získání nezávislé na jazykových chování z `SortedList`, vytvoření `SortedList` pomocí jedné z konstruktorů, které přijímají `comparer` parametr.</span><span class="sxs-lookup"><span data-stu-id="0064d-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="0064d-131">`comparer` Parametr určuje <xref:System.Collections.IComparer> implementaci má být použita při porovnání klíčů.</span><span class="sxs-lookup"><span data-stu-id="0064d-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="0064d-132">Pro parametr, zadejte vlastní porovnávací funkci třídu, která využívá `CultureInfo.InvariantCulture` k porovnání klíčů.</span><span class="sxs-lookup"><span data-stu-id="0064d-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="0064d-133">Následující příklad ukazuje třídu vlastní porovnávací funkci na jazykové verzi, můžete zadat jako `comparer` parametru `SortedList` konstruktor.</span><span class="sxs-lookup"><span data-stu-id="0064d-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>  
  
```vb  
Imports System  
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
  
 <span data-ttu-id="0064d-134">Obecně platí, že pokud použijete `SortedList` řetězce bez zadání vlastní invariantní porovnávání ke změně `Thread.CurrentCulture` po naplnění seznamu, mohou zneplatnit seznamu.</span><span class="sxs-lookup"><span data-stu-id="0064d-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>  
  
## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="0064d-135">Pomocí ArrayList.Sort – metoda</span><span class="sxs-lookup"><span data-stu-id="0064d-135">Using the ArrayList.Sort Method</span></span>  
 <span data-ttu-id="0064d-136">Přetížení `ArrayList.Sort` metoda provést řazení zohledňující jazykovou verzi pomocí výchozí `Thread.CurrentCulture` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0064d-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="0064d-137">Výsledky se může lišit podle jazykové verze kvůli jiné pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="0064d-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="0064d-138">Chcete-li vyloučit chování zohledňující jazykovou verzi, použijte přetížení této metody, které přijímají `IComparer` implementace.</span><span class="sxs-lookup"><span data-stu-id="0064d-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="0064d-139">Pro `comparer` parametr, zadejte vlastní invariantní porovnávání třídu, která využívá `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="0064d-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="0064d-140">Příklad vlastní invariantní porovnávání třídy je součástí [použití třídy SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) tématu.</span><span class="sxs-lookup"><span data-stu-id="0064d-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0064d-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="0064d-141">See Also</span></span>  
 <xref:System.Collections.CaseInsensitiveComparer>  
 <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Collections.SortedList>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Collections.IComparer>  
 [<span data-ttu-id="0064d-142">Provádění řetězcových operací nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="0064d-142">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
