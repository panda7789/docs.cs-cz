---
title: Typy řazených kolekcí
ms.date: 04/30/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET Framework], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
ms.openlocfilehash: 2d9d3744859eea1a09923980b3b4c57eca6bba97
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287936"
---
# <a name="sorted-collection-types"></a>Typy řazených kolekcí

<xref:System.Collections.SortedList?displayProperty=nameWithType>Třída, <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> Obecná třída a <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> Obecná třída jsou podobné jako <xref:System.Collections.Hashtable> Třída a <xref:System.Collections.Generic.Dictionary%602> obecnou třídu v tom, že implementují <xref:System.Collections.IDictionary> rozhraní, ale udržují své prvky v pořadí řazení podle klíče a nemají pro vkládání a čtení vlastností zatřiďovacích tabulek. Tři třídy mají několik běžných funkcí:

- Všechny tři třídy implementují <xref:System.Collections.IDictionary?displayProperty=nameWithType> rozhraní. Tyto dvě obecné třídy také implementují <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> Obecné rozhraní.

- Každý prvek je dvojice klíč/hodnota pro účely výčtu.

   > [!NOTE]
   > Neobecná <xref:System.Collections.SortedList> třída vrací <xref:System.Collections.DictionaryEntry> objekty při výčtu, i když dva obecné typy vracejí <xref:System.Collections.Generic.KeyValuePair%602> objekty.

- Prvky jsou seřazeny podle <xref:System.Collections.IComparer?displayProperty=nameWithType> implementace (pro neobecné <xref:System.Collections.SortedList> ) nebo <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementace (pro dvě obecné třídy).

- Každá třída poskytuje vlastnosti, které vracejí kolekce obsahující pouze klíče, nebo pouze hodnoty.

V následující tabulce je uveden seznam rozdílů mezi dvěma seřazenými třídami seznamu a <xref:System.Collections.Generic.SortedDictionary%602> třídou.

| <xref:System.Collections.SortedList>neobecná třída a <xref:System.Collections.Generic.SortedList%602> Obecná třída | <xref:System.Collections.Generic.SortedDictionary%602>Obecná třída |
|--|--|
| Vlastnosti, které vracejí klíče a hodnoty jsou indexované, což umožňuje efektivní indexované načítání. | Žádné indexované načtení. |
| Načítání je O (protokol `n` ). | Načítání je O (protokol `n` ). |
| Vložení a odebrání jsou obecně O ( `n` ). vložení však je o (log `n` ) pro data, která jsou již v pořadí řazení, aby byl každý prvek přidán na konec seznamu. (Předpokládá se, že změna velikosti není nutná.) | Vkládání a odebírání se používá v (protokol `n` ). |
| Používá méně paměti než <xref:System.Collections.Generic.SortedDictionary%602> . | Používá více paměti než <xref:System.Collections.SortedList> neobecnou třídu a <xref:System.Collections.Generic.SortedList%602> obecnou třídu. |

Pro seřazené seznamy nebo slovníky, které musí být přístupné souběžně z více vláken, můžete přidat logiku řazení ke třídě, která je odvozena z <xref:System.Collections.Concurrent.ConcurrentDictionary%602> . Při zvažování neměnnosti následující odpovídající neměnné typy následují podobné sémantiky řazení: <xref:System.Collections.Immutable.ImmutableSortedSet%601> a <xref:System.Collections.Immutable.ImmutableSortedDictionary%602> .

> [!NOTE]
> Pro hodnoty, které obsahují vlastní klíče (například záznamy zaměstnanců obsahující identifikační číslo zaměstnance), můžete vytvořit kolekci s klíčem, která obsahuje některé charakteristiky seznamu a některé charakteristiky slovníku odvozenou z <xref:System.Collections.ObjectModel.KeyedCollection%602> Obecné třídy.

Počínaje .NET Framework 4 <xref:System.Collections.Generic.SortedSet%601> poskytuje třída samostatně vyvážení stromu, který uchovává data v seřazeném pořadí po vložení, odstranění a hledání. Tato třída a <xref:System.Collections.Generic.HashSet%601> Třída implementuje <xref:System.Collections.Generic.ISet%601> rozhraní.

## <a name="see-also"></a>Viz také

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [Běžně používané typy kolekcí](commonly-used-collection-types.md)
