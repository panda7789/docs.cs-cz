---
title: Obecné kolekce v rozhraní .NET
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
ms.openlocfilehash: 829ef35d2e26f67ea956a0838d93b9667ad58df4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="generic-collections-in-net"></a>Obecné kolekce v rozhraní .NET

 Poskytuje řadu obecné třídy kolekcí v knihovně tříd rozhraní .NET <xref:System.Collections.Generic> a <xref:System.Collections.ObjectModel> obory názvů. Další podrobné informace o těchto tříd naleznete v tématu [běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
### <a name="systemcollectionsgeneric"></a>System.Collections.Generic –  
 Mnoho typů obecnou kolekci je analogických neobecné typy. <xref:System.Collections.Generic.Dictionary%602> je obecná verze <xref:System.Collections.Hashtable>; používá obecná struktura <xref:System.Collections.Generic.KeyValuePair%602> pro výčet místo <xref:System.Collections.DictionaryEntry>.  
  
 <xref:System.Collections.Generic.List%601> je obecná verze <xref:System.Collections.ArrayList>. Existují obecné <xref:System.Collections.Generic.Queue%601> a <xref:System.Collections.Generic.Stack%601> třídy, které odpovídají neobecné verzi.  
  
 Obecné a neobecné verzích <xref:System.Collections.Generic.SortedList%602>. Obě verze jsou hybridních slovník a seznam. <xref:System.Collections.Generic.SortedDictionary%602> Obecná třída je čistě slovník a nemá žádný neobecný protějšek.  
  
 <xref:System.Collections.Generic.LinkedList%601> Obecná třída je true odkazovaného seznamu. Nemá žádné neobecné protějšky.  
  
### <a name="systemcollectionsobjectmodel"></a>System.Collections.ObjectModel  
 <xref:System.Collections.ObjectModel.Collection%601> Obecná třída poskytuje základní třídu pro odvození vlastních obecnou kolekci typů. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Třída poskytuje snadný způsob, jak vytvořit kolekci jen pro čtení z libovolného typu, který implementuje <xref:System.Collections.Generic.IList%601> obecné rozhraní. <xref:System.Collections.ObjectModel.KeyedCollection%602> Obecná třída poskytuje způsob, jak ukládat objekty, které obsahují vlastní klíče.  
  
## <a name="other-generic-types"></a>Další obecné typy  
 <xref:System.Nullable%601> Obecná struktura umožňuje používat typy hodnot, jako by mohla být přiřazena `null`. To může být užitečné při práci s dotazů databáze, kde může být chybějící pole, které obsahují typy hodnot. Parametr obecného typu mohou být jakéhokoli typu hodnotu.  
  
> [!NOTE]
>  V jazyce C# a Visual Basic, není nutné používat <xref:System.Nullable%601> explicitně, protože jazyk má syntaxi pro typy s možnou hodnotou Null. V tématu [typy s možnou hodnotou Null (C# programování průvodce)](../../csharp/programming-guide/nullable-types/index.md) a [typy s možnou hodnotou Null hodnot (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md). 
  
 <xref:System.ArraySegment%601> Obecná struktura poskytuje způsob, jak vymezení rozsahu elementů v rámci jednorozměrné, počítáno od nuly pole libovolného typu. Parametr obecného typu je typ elementy pole.  
  
 <xref:System.EventHandler%601> Obecný delegát se eliminuje potřeba deklarovat typ delegáta pro zpracování událostí, pokud událost následuje vzor zpracování událostí používané [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Předpokládejme například, že jste vytvořili `MyEventArgs` třídy, které jsou odvozené od <xref:System.EventArgs>, aby udržení data pro událost. Potom můžete událost deklarovat takto:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [Obecné typy](../../../docs/standard/generics/index.md)  
 [Obecné delegáty pro manipulaci s poli a seznamy](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [Obecná rozhraní](../../../docs/standard/generics/interfaces.md)
