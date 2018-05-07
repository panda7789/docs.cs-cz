---
title: Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: a8b347be33ea6acbdf8a78a7af45fd3d0c27f8fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)
Indexery jsou stejné jako vlastnosti. S výjimkou rozdíly uvedené v následující tabulce všechna pravidla, které jsou definovány pro vlastnost přístupových objektů týkají přístupové objekty indexer také.  
  
|Vlastnost|indexer|  
|--------------|-------------|  
|Umožňuje metody, která se má volat, jako kdyby byly členy veřejná data.|Umožňuje elementy vnitřní objekt nelze přistupovat pomocí notace pole na samotný objekt kolekce.|  
|Přistupovat prostřednictvím jednoduchý název.|Dostupné v indexu.|  
|Může být statické nebo instanci členu.|Musí být členem instance.|  
|A [získat](../../../csharp/language-reference/keywords/get.md) přistupujícího objektu vlastnosti nemá žádné parametry.|A `get` přístupových indexer obsahuje stejný seznam formální parametr jako indexeru.|  
|A [nastavit](../../../csharp/language-reference/keywords/set.md) přistupující objekt vlastnosti obsahuje implicitní `value` parametr.|A `set` přístupových indexer obsahuje stejný seznam formální parametr jako indexeru a také [hodnotu](../../../csharp/language-reference/keywords/value.md) parametr.|  
|Podporuje zkrácený syntax s [Auto-Implemented vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).|Nepodporuje zkrácenou syntaxi.|  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Indexery](../../../csharp/programming-guide/indexers/index.md)  
 [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
