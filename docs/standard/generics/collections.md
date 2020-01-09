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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708407"
---
# <a name="generic-collections-in-net"></a>Obecné kolekce v .NET

 Knihovna tříd .NET poskytuje řadu obecných tříd kolekcí v oborech názvů <xref:System.Collections.Generic> a <xref:System.Collections.ObjectModel>. Podrobnější informace o těchto třídách naleznete v tématu [běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
## <a name="systemcollectionsgeneric"></a>System.Collections.Generic

 Mnohé z obecných typů kolekcí jsou přímé analogické pro neobecné typy. <xref:System.Collections.Generic.Dictionary%602> je obecná verze <xref:System.Collections.Hashtable>; místo <xref:System.Collections.DictionaryEntry>používá obecnou strukturu <xref:System.Collections.Generic.KeyValuePair%602> pro výčet.  
  
 <xref:System.Collections.Generic.List%601> je obecná verze <xref:System.Collections.ArrayList>. Existují obecné třídy <xref:System.Collections.Generic.Queue%601> a <xref:System.Collections.Generic.Stack%601>, které odpovídají neobecným verzím.  
  
 Existují obecné a neobecné verze <xref:System.Collections.Generic.SortedList%602>. Obě verze jsou hybridy slovníku a seznamu. <xref:System.Collections.Generic.SortedDictionary%602> obecná třída je čistě slovník a nemá žádné neobecné protějšky.  
  
 <xref:System.Collections.Generic.LinkedList%601> obecná třída je skutečný propojený seznam. Nemá žádný obecný protějšek.  
  
## <a name="systemcollectionsobjectmodel"></a>System.Collections.ObjectModel

 Obecná třída <xref:System.Collections.ObjectModel.Collection%601> poskytuje základní třídu pro odvození vlastních typů obecných kolekcí. Třída <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> poskytuje snadný způsob, jak vytvořit kolekci jen pro čtení z libovolného typu, který implementuje <xref:System.Collections.Generic.IList%601> obecné rozhraní. <xref:System.Collections.ObjectModel.KeyedCollection%602> obecná třída poskytuje způsob, jak ukládat objekty, které obsahují vlastní klíče.  
  
## <a name="other-generic-types"></a>Jiné obecné typy

 <xref:System.Nullable%601> Obecná struktura umožňuje používat typy hodnot, jako by mohly být přiřazeny `null`. To může být užitečné při práci s databázovými dotazy, kde mohou chybět pole, která obsahují hodnotové typy. Parametr obecného typu může být libovolný typ hodnoty.  
  
> [!NOTE]
> V C# a Visual Basic není nutné <xref:System.Nullable%601> explicitně používat, protože jazyk obsahuje syntaxi pro typy s možnou hodnotou null. Viz typy [hodnot s možnou hodnotouC# null (referenční)](../../csharp/language-reference/builtin-types/nullable-value-types.md) a typy s [možnou hodnotou null (Visual Basic)](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).
  
 <xref:System.ArraySegment%601> Obecná struktura poskytuje způsob, jak omezit rozsah prvků v rámci jednorozměrného pole libovolného typu, který je založený na nule. Parametr obecného typu je typ prvků pole.  
  
 <xref:System.EventHandler%601> obecný delegát eliminuje nutnost deklarovat typ delegáta pro zpracování událostí, pokud událost následuje vzor zpracování událostí, který používá .NET Framework. Předpokládejme například, že jste vytvořili třídu `MyEventArgs` odvozenou z <xref:System.EventArgs>a chcete uchovávat data pro vaši událost. Následně můžete deklarovat událost následujícím způsobem:  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Obecné typy](../../../docs/standard/generics/index.md)
- [Obecné delegáty pro manipulaci s poli a seznamy](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)
- [Obecná rozhraní](../../../docs/standard/generics/interfaces.md)
