---
title: Obecné kolekce na platformě .NET
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
ms.openlocfilehash: dce0e38b0198396ec0dbc3ced7f2f59c2b112b56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708407"
---
# <a name="generic-collections-in-net"></a>Obecné kolekce v rozhraní .NET

 Knihovna tříd .NET poskytuje řadu obecných <xref:System.Collections.Generic> <xref:System.Collections.ObjectModel> tříd kolekce v oborech názvů a. Podrobnější informace o těchto třídách naleznete [v tématu Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
## <a name="systemcollectionsgeneric"></a>System.Collections.Generic

 Mnoho typů obecné kolekce jsou přímé analogy neobecných typů. <xref:System.Collections.Generic.Dictionary%602>je obecná verze <xref:System.Collections.Hashtable>; používá obecnou strukturu <xref:System.Collections.Generic.KeyValuePair%602> pro výčet <xref:System.Collections.DictionaryEntry>namísto .  
  
 <xref:System.Collections.Generic.List%601>je obecná verze <xref:System.Collections.ArrayList>aplikace . Existují obecné <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Generic.Stack%601> a třídy, které odpovídají neobecné verze.  
  
 Existují obecné a neobecné <xref:System.Collections.Generic.SortedList%602>verze aplikace . Obě verze jsou hybridy slovníku a seznamu. Obecná <xref:System.Collections.Generic.SortedDictionary%602> třída je čistý slovník a nemá žádný neobecný protějšek.  
  
 Obecná <xref:System.Collections.Generic.LinkedList%601> třída je skutečně propojený seznam. Nemá žádný neobecný protějšek.  
  
## <a name="systemcollectionsobjectmodel"></a>System.collections.objectmodel

 Obecná <xref:System.Collections.ObjectModel.Collection%601> třída poskytuje základní třídu pro odvození vlastních typů obecných kolekcí. Třída <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> poskytuje snadný způsob, jak vytvořit kolekci jen pro <xref:System.Collections.Generic.IList%601> čtení z libovolného typu, který implementuje obecné rozhraní. Obecná <xref:System.Collections.ObjectModel.KeyedCollection%602> třída poskytuje způsob ukládání objektů, které obsahují vlastní klíče.  
  
## <a name="other-generic-types"></a>Jiné obecné typy

 Obecná <xref:System.Nullable%601> struktura umožňuje používat typy hodnot, jako `null`by mohly být přiřazeny . To může být užitečné při práci s databázovými dotazy, kde mohou chybět pole obsahující typy hodnot. Parametr obecného typu může být libovolný typ hodnoty.  
  
> [!NOTE]
> V jazyce C# a visual basicu není nutné explicitně používat, <xref:System.Nullable%601> protože jazyk má syntaxi pro typy s možnou hodnotou null. Viz [Nullable typy hodnot (C# odkaz)](../../csharp/language-reference/builtin-types/nullable-value-types.md) a [Nullable typy hodnot (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).
  
 Obecná <xref:System.ArraySegment%601> struktura poskytuje způsob, jak vymezovat rozsah prvků v rámci jednorozměrné pole s nulovým základem libovolného typu. Parametr obecného typu je typ prvků pole.  
  
 Obecný <xref:System.EventHandler%601> delegát eliminuje potřebu deklarovat typ delegáta pro zpracování událostí, pokud vaše událost následuje vzor zpracování událostí používaný rozhraním .NET Framework. Předpokládejme například, že `MyEventArgs` jste vytvořili <xref:System.EventArgs>třídu odvozenou z aplikace pro uložení dat pro událost. Poté můžete deklarovat událost takto:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Obecné typy](../../../docs/standard/generics/index.md)
- [Obecní delegáty pro manipulaci s poli a seznamy](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Obecná rozhraní](../../../docs/standard/generics/interfaces.md)
