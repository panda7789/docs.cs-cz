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
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích
Existují třídy a členové <xref:System.Collections> obor názvů, který ve výchozím nastavení poskytují chování zohledňující jazykovou verzi. Výchozí konstruktory pro <xref:System.Collections.CaseInsensitiveComparer> a <xref:System.Collections.CaseInsensitiveHashCodeProvider> třídy inicializaci nové instance pomocí <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> vlastnost. Všechny přetížení <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> metoda vytvořit novou instanci třídy <xref:System.Collections.Hashtable> pomocí `Thread.CurrentCulture` vlastnost ve výchozím nastavení. Přetížení <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> metoda provést řazení zohledňující jazykovou verzi pomocí výchozí `Thread.CurrentCulture`. Řazení a vyhledávání v <xref:System.Collections.SortedList> může být ovlivněno `Thread.CurrentCulture` při použití řetězce jako klíče. Postupujte podle doporučení poskytnutých v této části získat nezávislé na jazykových výsledky z tyto třídy a metody v `Collections` oboru názvů.  
  
 **Poznámka:** předávání <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> k porovnání metoda provést porovnání na jazykové verzi. Však nevytváří-lingvistické porovnání, například cesty k souborům, klíčů registru a proměnných prostředí. Ani podporuje rozhodnutí o zabezpečení na základě výsledku porovnání. Lingvistické porovnání nebo podporu pro zabezpečení na základě výsledku rozhodnutí, by aplikace měla používat porovnání metodu, která přijímá <xref:System.StringComparison> hodnotu. Aplikace by pak předat <xref:System.StringComparison>.  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>Pomocí CaseInsensitiveComparer a CaseInsensitiveHashCodeProvider  
 Výchozí konstruktory pro `CaseInsensitiveHashCodeProvider` a `CaseInsensitiveComparer` inicializuje novou instanci třídy pomocí `Thread.CurrentCulture`, což chování zohledňující jazykovou verzi. Následující příklad kódu ukazuje konstruktor pro `Hashtable` , je zohledňující jazykovou verzi, protože používá výchozí konstruktory pro `CaseInsensitiveHashCodeProvider` a `CaseInsensitiveComparer`.  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 Pokud chcete vytvořit nezávislé na jazykových `Hashtable` pomocí `CaseInsensitiveComparer` a `CaseInsensitiveHashCodeProvider` třídy, inicializaci nové instance těchto tříd pomocí konstruktorů, které přijímají `culture` parametr. Pro `culture` parametr, zadejte <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Následující příklad kódu ukazuje konstruktor pro nezávislé na jazykových `Hashtable`.  
  
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
 `CollectionsUtil.CreateCaseInsensitiveHashTable` Metoda je užitečná zkratka pro vytvoření nové instance `Hashtable` třídu, která nerozlišuje malá a velká řetězce. Nicméně všechna přetížení `CollectionsUtil.CreateCaseInsensitiveHashTable` metoda jsou závislé na jazykové verzi, protože používají `Thread.CurrentCulture` vlastnost. Nelze vytvořit nezávislé na jazykových `Hashtable` pomocí této metody. Chcete-li vytvořit nezávislé na jazykových `Hashtable`, použijte `Hashtable` konstruktor, který přijímá `culture` parametr. Pro `culture` parametr, zadejte `CultureInfo.InvariantCulture`. Následující příklad kódu ukazuje konstruktor pro nezávislé na jazykových `Hashtable`.  
  
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
 A `SortedList` představuje kolekci párů klíč hodnota, které jsou seřazené podle klíče a je přístupný pomocí klíče a pro index. Při použití `SortedList` tam, kde jsou řetězce klíčů, řazení a vyhledávání můžou mít vliv `Thread.CurrentCulture` vlastnost. K získání nezávislé na jazykových chování z `SortedList`, vytvoření `SortedList` pomocí jedné z konstruktorů, které přijímají `comparer` parametr. `comparer` Parametr určuje <xref:System.Collections.IComparer> implementaci má být použita při porovnání klíčů. Pro parametr, zadejte vlastní porovnávací funkci třídu, která využívá `CultureInfo.InvariantCulture` k porovnání klíčů. Následující příklad ukazuje třídu vlastní porovnávací funkci na jazykové verzi, můžete zadat jako `comparer` parametru `SortedList` konstruktor.  
  
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
  
 Obecně platí, že pokud použijete `SortedList` řetězce bez zadání vlastní invariantní porovnávání ke změně `Thread.CurrentCulture` po naplnění seznamu, mohou zneplatnit seznamu.  
  
## <a name="using-the-arraylistsort-method"></a>Pomocí ArrayList.Sort – metoda  
 Přetížení `ArrayList.Sort` metoda provést řazení zohledňující jazykovou verzi pomocí výchozí `Thread.CurrentCulture` vlastnost. Výsledky se může lišit podle jazykové verze kvůli jiné pořadí řazení. Chcete-li vyloučit chování zohledňující jazykovou verzi, použijte přetížení této metody, které přijímají `IComparer` implementace. Pro `comparer` parametr, zadejte vlastní invariantní porovnávání třídu, která využívá `CultureInfo.InvariantCulture`. Příklad vlastní invariantní porovnávání třídy je součástí [použití třídy SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) tématu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.CaseInsensitiveComparer>  
 <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Collections.SortedList>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Collections.IComparer>  
 [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
