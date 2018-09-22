---
title: Generování kolekcí v .NET
ms.date: 02/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET], collections
- generic collections [.NET]
- generic types [.NET]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cdead5a54c6e8dbe6fd61f82fc3985913bd7d381
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584354"
---
# <a name="generic-collections-in-net"></a>Generování kolekcí v .NET

 Nabízí celou řadu obecné kolekce tříd v knihovně tříd rozhraní .NET <xref:System.Collections.Generic> a <xref:System.Collections.ObjectModel> obory názvů. Podrobné informace o těchto tříd, naleznete v tématu [běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
### <a name="systemcollectionsgeneric"></a>System.Collections.Generic  
 Mnoho typů obecných kolekcí jsou analogických neobecné typy. <xref:System.Collections.Generic.Dictionary%602> je obecný verze <xref:System.Collections.Hashtable>; používá obecná struktura <xref:System.Collections.Generic.KeyValuePair%602> pro výčet místo <xref:System.Collections.DictionaryEntry>.  
  
 <xref:System.Collections.Generic.List%601> je obecný verze <xref:System.Collections.ArrayList>. Jsou Obecné <xref:System.Collections.Generic.Queue%601> a <xref:System.Collections.Generic.Stack%601> třídy, které odpovídají neobecné verze.  
  
 Existují verze obecných a neobecných <xref:System.Collections.Generic.SortedList%602>. Obě verze jsou hybridních slovník a seznam. <xref:System.Collections.Generic.SortedDictionary%602> Obecné třídy je čistě slovníku a nemá neobecný protějšek.  
  
 <xref:System.Collections.Generic.LinkedList%601> Obecná třída je true propojeného seznamu. Nemá žádný neobecný protějšek.  
  
### <a name="systemcollectionsobjectmodel"></a>System.Collections.ObjectModel  
 <xref:System.Collections.ObjectModel.Collection%601> Obecná třída poskytuje základní třídu pro odvození typů obecných kolekcí. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Třída poskytuje snadný způsob, jak vytvořit kolekci určenou jen pro čtení z libovolného typu, který implementuje <xref:System.Collections.Generic.IList%601> obecného rozhraní. <xref:System.Collections.ObjectModel.KeyedCollection%602> Obecná třída poskytuje způsob, jak ukládat objekty, které obsahují vlastní klíče.  
  
## <a name="other-generic-types"></a>Další obecné typy  
 <xref:System.Nullable%601> Obecná struktura umožňuje používat typy hodnot, jako by mohla být přiřazena `null`. To může být užitečné při práci s dotazy na databázi, kde může být chybějící pole, které obsahují typy hodnot. Parametr obecného typu může být libovolný typ hodnoty.  
  
> [!NOTE]
>  V jazyce C# a Visual Basic, není nutné používat <xref:System.Nullable%601> explicitně, protože jazyk má syntaxi pro typy připouštějící hodnotu Null. Zobrazit [typy s možnou hodnotou Null (C# Programming Guide)](../../csharp/programming-guide/nullable-types/index.md) a [typy s možnou hodnotou Null (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md). 
  
 <xref:System.ArraySegment%601> Obecná struktura poskytuje způsob, jak omezíte rozsah prvků v rámci založený na nule, jednorozměrné pole libovolného typu. Parametr obecného typu je typ prvků pole.  
  
 <xref:System.EventHandler%601> Obecného delegáta se eliminuje potřeba deklarovat typ delegáta pro zpracování událostí, pokud událost následuje vzor zpracování událostí používané [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Předpokládejme například, že jste vytvořili `MyEventArgs` třídu odvozenou z <xref:System.EventArgs>, pro uchovávání dat pro událost. Událost je pak může deklarovat následujícím způsobem:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic?displayProperty=nameWithType>  
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
- [Obecné typy](../../../docs/standard/generics/index.md)  
- [Obecné delegáty pro manipulaci s poli a seznamy](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
- [Obecná rozhraní](../../../docs/standard/generics/interfaces.md)
