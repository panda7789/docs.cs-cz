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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353676"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích

V oboru názvů <xref:System.Collections> existují třídy a členy, které ve výchozím nastavení poskytují chování zohledňující jazykovou verzi. Konstruktory bez parametrů pro <xref:System.Collections.CaseInsensitiveComparer> a <xref:System.Collections.CaseInsensitiveHashCodeProvider> třídy inicializují novou instanci pomocí vlastnosti <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>. Všechna přetížení metody <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> ve výchozím nastavení vytvoří novou instanci třídy <xref:System.Collections.Hashtable> pomocí vlastnosti `Thread.CurrentCulture`. Přetížení metody <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> provádějí řazení zohledňující jazykovou verzi ve výchozím nastavení pomocí `Thread.CurrentCulture`. Řazení a vyhledávání v <xref:System.Collections.SortedList> může být ovlivněno `Thread.CurrentCulture` při použití řetězců jako klíčů. Použijte doporučení k používání uvedená v této části k získání výsledků nezávislých na jazykové verzi z těchto tříd a metod v oboru názvů `Collections`.

> [!NOTE]
> Předání <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> k metodě porovnání provádí porovnání nezávislé na jazykové verzi. Nezpůsobuje ale nelingvistické porovnání, například pro cesty k souboru, klíče registru a proměnné prostředí. Ani to nepodporuje rozhodnutí o zabezpečení na základě výsledku porovnání. Pro nelingvistické porovnání nebo podporu pro rozhodování o zabezpečení na základě výsledků by aplikace měla používat metodu porovnání, která přijímá <xref:System.StringComparison>ou hodnotu. Aplikace by pak měla předat <xref:System.StringComparison>.

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>Použití tříd CaseInsensitiveComparer a CaseInsensitiveHashCodeProvider

Konstruktory bez parametrů pro `CaseInsensitiveHashCodeProvider` a `CaseInsensitiveComparer` Inicializuje novou instanci třídy pomocí `Thread.CurrentCulture`, což vede k chování zohledňující jazykovou verzi. Následující příklad kódu ukazuje konstruktor pro `Hashtable`, který je závislý na jazykové verzi, protože používá konstruktory bez parametrů pro `CaseInsensitiveHashCodeProvider` a `CaseInsensitiveComparer`.

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

Pokud chcete vytvořit `Hashtable` nezávisle na jazykové verzi pomocí tříd `CaseInsensitiveComparer` a `CaseInsensitiveHashCodeProvider`, inicializujte nové instance těchto tříd pomocí konstruktorů, které přijímají parametr `culture`. Pro parametr `culture` zadejte <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Následující příklad kódu ukazuje konstruktor pro `Hashtable`nezávislá na jazykové verzi.

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

Metoda `CollectionsUtil.CreateCaseInsensitiveHashTable` je užitečnou zkratkou pro vytvoření nové instance `Hashtable` třídy, která ignoruje velikost písmen řetězců. Nicméně všechna přetížení metody `CollectionsUtil.CreateCaseInsensitiveHashTable` jsou závislá na jazykové verzi, protože používají vlastnost `Thread.CurrentCulture`. Pomocí této metody nelze vytvořit `Hashtable` nezávislá na jazykové verzi. Chcete-li vytvořit `Hashtable`nezávislá na jazykové verzi, použijte konstruktor `Hashtable`, který přijímá parametr `culture`. Pro parametr `culture` zadejte `CultureInfo.InvariantCulture`. Následující příklad kódu ukazuje konstruktor pro `Hashtable`nezávislá na jazykové verzi.

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

`SortedList` představuje kolekci párů klíč-hodnota, které jsou seřazené podle klíčů a jsou přístupné pomocí klíče a indexu. Když použijete `SortedList`, kde jsou řetězce klíče, řazení a vyhledávání může být ovlivněno vlastností `Thread.CurrentCulture`. Chcete-li získat chování nezávislé na jazykové verzi z `SortedList`, vytvořte `SortedList` pomocí jednoho konstruktoru, který přijímá parametr `comparer`. Parametr `comparer` určuje implementaci <xref:System.Collections.IComparer>, která se má použít při porovnávání klíčů. Pro parametr zadejte vlastní třídu porovnávače, která používá `CultureInfo.InvariantCulture` k porovnání klíčů. Následující příklad ukazuje vlastní třídu pro porovnávání bez rozlišení jazykové verze, kterou lze zadat jako parametr `comparer` do konstruktoru `SortedList`.

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

Obecně platí, že pokud použijete `SortedList` v řetězcích bez určení vlastní invariantní porovnávání, změna `Thread.CurrentCulture` po naplnění seznamu může seznam neověřit.

## <a name="using-the-arraylistsort-method"></a>Použití metody ArrayList. Sort

Přetížení metody `ArrayList.Sort` provádějí řazení zohledňující jazykovou verzi ve výchozím nastavení pomocí vlastnosti `Thread.CurrentCulture`. Výsledky se mohou lišit podle jazykové verze z důvodu různých pořadí řazení. Chcete-li eliminovat chování zohledňující jazykovou verzi, použijte přetížení této metody, které přijímají implementaci `IComparer`. Pro parametr `comparer` zadejte vlastní třídu pro invariantní porovnávání, která používá `CultureInfo.InvariantCulture`. Příklad vlastní třídy invariantní porovnávání je k dispozici v tématu [použití třídy SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) .

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
