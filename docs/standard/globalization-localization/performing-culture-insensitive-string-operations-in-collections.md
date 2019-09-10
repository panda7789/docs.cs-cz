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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 222376e220bf74274082dfc6b76dc861d4f8ddc5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855981"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích

V <xref:System.Collections> oboru názvů existují třídy a členy, které ve výchozím nastavení poskytují chování zohledňující jazykovou verzi. Konstruktory bez parametrů pro <xref:System.Collections.CaseInsensitiveComparer> třídy a <xref:System.Collections.CaseInsensitiveHashCodeProvider> inicializují novou instanci pomocí <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> vlastnosti. Všechna přetížení <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> metody vytvoří novou instanci <xref:System.Collections.Hashtable> třídy pomocí `Thread.CurrentCulture` vlastnosti ve výchozím nastavení. Přetížení <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> metody provádějí řazení zohledňující jazykovou verzi ve výchozím nastavení pomocí `Thread.CurrentCulture`. Řazení a vyhledávání v <xref:System.Collections.SortedList> může být `Thread.CurrentCulture` ovlivněno při použití řetězců jako klíčů. Použijte doporučení k používání uvedená v této části k získání výsledků nezávislých na jazykové verzi z těchto tříd a metod v `Collections` oboru názvů.

> [!NOTE]
> Předání <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> do metody porovnání provede porovnání nezávislé na jazykové verzi. Nezpůsobuje ale nelingvistické porovnání, například pro cesty k souboru, klíče registru a proměnné prostředí. Ani to nepodporuje rozhodnutí o zabezpečení na základě výsledku porovnání. Pro nelingvistické porovnání nebo podporu pro rozhodování o zabezpečení na základě výsledků by aplikace měla používat metodu porovnání, která přijímá <xref:System.StringComparison> hodnotu. Aplikace by se měla předat <xref:System.StringComparison>.

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>Použití tříd CaseInsensitiveComparer a CaseInsensitiveHashCodeProvider

Konstruktory bez parametrů pro `CaseInsensitiveHashCodeProvider` a `CaseInsensitiveComparer` inicializují novou instanci třídy pomocí `Thread.CurrentCulture`, což vede k chování zohledňující jazykovou verzi. Následující příklad kódu ukazuje konstruktor pro `Hashtable` , který je závislý na jazykové verzi, protože používá konstruktory bez parametrů pro `CaseInsensitiveHashCodeProvider` a `CaseInsensitiveComparer`.

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

Pokud `Hashtable` chcete vytvořit nezávisle na jazykové verzi `CaseInsensitiveComparer` pomocí tříd a `CaseInsensitiveHashCodeProvider` , inicializujte nové instance těchto `culture` tříd pomocí konstruktorů, které přijímají parametr. Pro parametr zadejte <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. `culture` Následující příklad kódu ukazuje konstruktor pro nezávislou `Hashtable`jazykovou verzi.

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

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a>Použití metody CollectionsUtil. CreateCaseInsensitiveHashTable

Metoda je užitečnou zkratkou pro vytvoření nové instance `Hashtable` třídy, která ignoruje velikost písmen řetězců. `CollectionsUtil.CreateCaseInsensitiveHashTable` Nicméně všechna přetížení `CollectionsUtil.CreateCaseInsensitiveHashTable` metody jsou závislá na jazykové verzi, protože `Thread.CurrentCulture` používají vlastnost. Pomocí této metody nelze vytvořit nezávislou `Hashtable` jazykovou verzi. Chcete-li vytvořit nezávislou `Hashtable`jazykovou verzi `Hashtable` , použijte konstruktor, `culture` který přijímá parametr. Pro parametr zadejte `CultureInfo.InvariantCulture`. `culture` Následující příklad kódu ukazuje konstruktor pro nezávislou `Hashtable`jazykovou verzi.

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

`SortedList` Představuje kolekci párů klíč-hodnota, které jsou seřazené podle klíčů a jsou přístupné pomocí klíče a indexu. Když použijete `SortedList` řetězce, kde jsou klíče, může být řazení a vyhledávání ovlivněno `Thread.CurrentCulture` vlastností. Chcete-li získat chování nezávislé na jazykové verzi `SortedList`z a, `SortedList` vytvořte pomocí jednoho z `comparer` konstruktorů, které přijmou parametr. `comparer` Parametr<xref:System.Collections.IComparer> určuje implementaci, která se má použít při porovnávání klíčů. Pro parametr zadejte vlastní třídu porovnávače, která používá `CultureInfo.InvariantCulture` k porovnání klíčů. Následující příklad znázorňuje vlastní třídu porovnávání bez rozlišení jazykové verze, kterou lze zadat jako `comparer` parametr `SortedList` do konstruktoru.

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

Obecně platí, že pokud použijete `SortedList` pro řetězce bez určení vlastní invariantní porovnávání, může být Změna `Thread.CurrentCulture` na po naplnění seznamu neověřena v seznamu.

## <a name="using-the-arraylistsort-method"></a>Použití metody ArrayList. Sort

Přetížení `ArrayList.Sort` metody provádějí řazení zohledňující jazykovou verzi ve výchozím nastavení `Thread.CurrentCulture` pomocí vlastnosti. Výsledky se mohou lišit podle jazykové verze z důvodu různých pořadí řazení. Chcete-li eliminovat chování zohledňující jazykovou verzi, použijte přetížení této metody, které `IComparer` přijímají implementaci. Pro parametr zadejte vlastní třídu pro invariantní porovnávání, která používá `CultureInfo.InvariantCulture`. `comparer` Příklad vlastní třídy invariantní porovnávání je k dispozici v tématu [použití třídy SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) .

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
