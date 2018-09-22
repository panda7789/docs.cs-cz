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
ms.openlocfilehash: 0e458f45fea8e2207ced930daebf10e653901fa7
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584276"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích
Existují třídy a členy v <xref:System.Collections> obor názvů, který poskytuje ve výchozím nastavení chování závislé na jazykové verzi. Výchozí konstruktory pro <xref:System.Collections.CaseInsensitiveComparer> a <xref:System.Collections.CaseInsensitiveHashCodeProvider> třídy inicializuje novou instanci používat <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> vlastnost. Všechna přetížení <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> metoda vytvořit novou instanci třídy <xref:System.Collections.Hashtable> pomocí `Thread.CurrentCulture` vlastnosti ve výchozím nastavení. Přetížení <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> metoda provedení řazení zohledňující jazykovou verzi pomocí výchozí `Thread.CurrentCulture`. Řazení a vyhledávání v <xref:System.Collections.SortedList> může být ovlivněna `Thread.CurrentCulture` při použití řetězců jako klíče. Použití doporučení k dispozici v této části získání výsledků nezávislých na jazykové verzi z těchto tříd a metod v `Collections` oboru názvů.  
  
 **Poznámka:** předávání <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> k porovnání metoda provést porovnání nezávislá na jazykové verzi. Ale to nezpůsobí nejazykové porovnání, například cesty k souborům, klíče registru a proměnných prostředí. Ani nepodporuje rozhodnutí o zabezpečení založeno na výsledku porovnání. Nejazykové porovnání nebo podporu pro rozhodnutí o zabezpečení na základě výsledku, aplikace by měla použít metodu porovnání, která přijímá <xref:System.StringComparison> hodnotu. Aplikace by měla předat <xref:System.StringComparison>.  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>CaseInsensitiveComparer – a CaseInsensitiveHashCodeProvider – třídy  
 Výchozí konstruktory pro `CaseInsensitiveHashCodeProvider` a `CaseInsensitiveComparer` inicializuje novou instanci třídy pomocí `Thread.CurrentCulture`výsledkem chování závislé na jazykové verzi. Následující příklad kódu ukazuje konstruktor `Hashtable` , který je zohledňující jazykovou verzi, protože používá výchozí konstruktory pro `CaseInsensitiveHashCodeProvider` a `CaseInsensitiveComparer`.  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 Pokud chcete vytvořit nezávislých na jazykové verzi `Hashtable` pomocí `CaseInsensitiveComparer` a `CaseInsensitiveHashCodeProvider` tříd, inicializuje nové instance těchto tříd pomocí konstruktorů, které přijímají `culture` parametru. Pro `culture` parametr, zadejte <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Následující příklad kódu ukazuje konstruktor pro nezávislých na jazykové verzi `Hashtable`.  
  
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
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a>Pomocí CollectionsUtil.CreateCaseInsensitiveHashTable – metoda  
 `CollectionsUtil.CreateCaseInsensitiveHashTable` Metoda je užitečná zkratka pro vytvoření nové instance položky `Hashtable` třídu, která se ignoruje velikost písmen řetězců. Nicméně všechna přetížení `CollectionsUtil.CreateCaseInsensitiveHashTable` metody jsou závislé na jazykové verzi, protože používají `Thread.CurrentCulture` vlastnost. Nelze vytvořit nezávislých na jazykové verzi `Hashtable` pomocí této metody. Chcete-li vytvořit nezávislých na jazykové verzi `Hashtable`, použijte `Hashtable` konstruktor, který přijímá `culture` parametr. Pro `culture` parametr, zadejte `CultureInfo.InvariantCulture`. Následující příklad kódu ukazuje konstruktor pro nezávislých na jazykové verzi `Hashtable`.  
  
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
## <a name="using-the-sortedlist-class"></a>Pomocí SortedList – třída  
 A `SortedList` představuje kolekci párů klíč hodnota, které jsou seřazeny podle klíče a jsou přístupné pomocí klíče a podle indexu. Při použití `SortedList` tam, kde jsou řetězce klíčů, řazení a vyhledávání může být ovlivněna `Thread.CurrentCulture` vlastnost. Získat nezávislých na jazykové verzi chování `SortedList`, vytvořit `SortedList` pomocí jednoho z konstruktorů, které přijímají `comparer` parametr. `comparer` Parametr určuje, <xref:System.Collections.IComparer> implementace pro použití při porovnávání klíče. Pro parametr, zadejte vlastní porovnávací metody třídu, která používá `CultureInfo.InvariantCulture` k porovnání klíčů. Následující příklad ukazuje třídu vlastní porovnávací metody nezávislých na jazykové verzi, můžete zadat jako `comparer` parametr `SortedList` konstruktoru.  
  
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
  
 Obecně platí, že pokud použijete `SortedList` na řetězce bez zadání vlastní výchozí porovnávací metody, změnu `Thread.CurrentCulture` po naplnění seznamu, mohou zneplatnit seznamu.  
  
## <a name="using-the-arraylistsort-method"></a>Pomocí ArrayList.Sort – metoda  
 Přetížení `ArrayList.Sort` provedení řazení zohledňující jazykovou verzi pomocí výchozí metody `Thread.CurrentCulture` vlastnost. Výsledky můžou lišit podle jazykové verze kvůli jiné pořadí řazení. Chcete-li vyloučit chování závislé na jazykové verzi, použijte přetížení této metody, které přijímají `IComparer` implementace. Pro `comparer` parametr, zadejte vlastní výchozí porovnávací metody třídu, která používá `CultureInfo.InvariantCulture`. Příklad vlastní výchozí porovnávací metody třídy je k dispozici v [horizontálních oddílů pomocí třídy SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) tématu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.CaseInsensitiveComparer>  
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
- <xref:System.Collections.SortedList>  
- <xref:System.Collections.Hashtable>  
- <xref:System.Collections.IComparer>  
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
