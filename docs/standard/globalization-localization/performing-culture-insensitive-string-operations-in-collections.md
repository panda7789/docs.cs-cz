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
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích

V oboru <xref:System.Collections> názvů jsou třídy a členy, které ve výchozím nastavení poskytují chování citlivé na jazykovou verzi. Konstruktory bez parametrů <xref:System.Collections.CaseInsensitiveComparer> pro <xref:System.Collections.CaseInsensitiveHashCodeProvider> a třídy inicializovat novou instanci pomocí vlastnosti. <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> Všechna přetížení <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> metody vytvořit novou instanci <xref:System.Collections.Hashtable> třídy pomocí vlastnosti `Thread.CurrentCulture` ve výchozím nastavení. Přetížení <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> metody provádět jazykové verze citlivé řazení `Thread.CurrentCulture`ve výchozím nastavení pomocí . Řazení a vyhledávání v <xref:System.Collections.SortedList> a může `Thread.CurrentCulture` být ovlivněna při řetězce jsou používány jako klíče. Postupujte podle doporučení použití uvedených v této části získat výsledky necitlivé na jazykové verzi z těchto tříd a metod v oboru `Collections` názvů.

> [!NOTE]
> Předání <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> metody porovnání provést porovnání necitlivé na jazykovou verzi. Nezpůsobuje však nejazykové porovnání, například pro cesty k souborům, klíče registru a proměnné prostředí. Nepodporuje ani rozhodnutí o zabezpečení založená na výsledku porovnání. Pro nejazykové porovnání nebo podporu pro rozhodnutí o zabezpečení založené na výsledcích aplikace <xref:System.StringComparison> by měla použít metodu porovnání, která přijímá hodnotu. Aplikace by pak <xref:System.StringComparison>měla projít .

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>Použití tříd CaseInsensitiveComparer a CaseInsensitiveHashCodeProvider

Konstruktory bez parametrů `CaseInsensitiveHashCodeProvider` `CaseInsensitiveComparer` pro a inicializovat novou `Thread.CurrentCulture`instanci třídy pomocí , výsledkem chování citlivé na jazykovou verzi. Následující příklad kódu ukazuje konstruktor `Hashtable` pro, který je citlivý na jazykovou verzi, protože používá konstruktory bez parametrů pro `CaseInsensitiveHashCodeProvider` a `CaseInsensitiveComparer`.

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

Pokud chcete vytvořit jazykovou verzi `Hashtable` necitlivý pomocí `CaseInsensitiveComparer` třídy a, `CaseInsensitiveHashCodeProvider` inicializovat nové instance těchto `culture` tříd pomocí konstruktory, které přijímají parametr. Pro `culture` parametr zadejte <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Následující příklad kódu ukazuje konstruktor pro jazykovou `Hashtable`verzi necitlivý .

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

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a>Použití metody CollectionsUtil.CreateCaseInsensitiveHashTable

Metoda `CollectionsUtil.CreateCaseInsensitiveHashTable` je užitečným zástupcem pro vytvoření `Hashtable` nové instance třídy, která ignoruje případ řetězců. Všechna přetížení `CollectionsUtil.CreateCaseInsensitiveHashTable` metody jsou však citlivé na jazykovou verzi, protože používají `Thread.CurrentCulture` vlastnost. Pomocí této metody nelze `Hashtable` vytvořit necitlivý na jazykovou verzi. Chcete-li vytvořit jazykovou verzi necitlivý `Hashtable`, použijte `Hashtable` konstruktor, který přijímá `culture` parametr. Pro `culture` parametr zadejte `CultureInfo.InvariantCulture`. Následující příklad kódu ukazuje konstruktor pro jazykovou `Hashtable`verzi necitlivý .

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

## <a name="using-the-sortedlist-class"></a>Použití třídy SortedList

A `SortedList` představuje kolekci párů klíč a hodnota, které jsou seřazeny podle klíčů a jsou přístupné klíčem a indexem. Při použití `SortedList` kde řetězce jsou klíče, řazení a vyhledávání může být `Thread.CurrentCulture` ovlivněna vlastnost. Chcete-li získat chování necitlivé na jazykovou `SortedList`verzi z , vytvořte `SortedList` pomocí jednoho z konstruktorů, který přijímá `comparer` parametr. Parametr `comparer` určuje implementaci, která <xref:System.Collections.IComparer> se má použít při porovnávání klíčů. Pro parametr zadejte vlastní třídu `CultureInfo.InvariantCulture` porovnávače, která používá k porovnání klíčů. Následující příklad ilustruje vlastní třídu porovnávání necitlivou na `comparer` jazykovou `SortedList` verzi, kterou můžete zadat jako parametr konstruktoru.

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

Obecně platí, že `SortedList` pokud použijete řetězce on bez zadání vlastního invariantního porovnávání, změna po `Thread.CurrentCulture` naplnění seznamu může zrušit platnost seznamu.

## <a name="using-the-arraylistsort-method"></a>Použití metody ArrayList.Sort

Přetížení `ArrayList.Sort` metody provádět jazykové verze citlivé řazení `Thread.CurrentCulture` ve výchozím nastavení pomocí vlastnosti. Výsledky se mohou lišit podle jazykové verze v důsledku různých pořadí řazení. Chcete-li eliminovat chování citlivé na jazykovou verzi, `IComparer` použijte přetížení této metody, které přijímají implementaci. Pro `comparer` parametr zadejte vlastní invariantní třídu porovnávače, která používá `CultureInfo.InvariantCulture`. Příklad vlastní třídy invariantního porovnávání je uveden v [tématu Using the SortedList Class.](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1)

## <a name="see-also"></a>Viz také

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
