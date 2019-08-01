---
title: Porovnání mezi vlastnostmi a indexery – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 31e6b4b10a6ffec031a2e41a2bd16c843f802fb7
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671681"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)
Indexery jsou jako vlastnosti. S výjimkou rozdílů uvedených v následující tabulce se všechna pravidla, která jsou definována pro přistupující objekty vlastnosti, vztahují také na přistupující objekty indexeru.  
  
|Vlastnost|Indexer|  
|--------------|-------------|  
|Povoluje volání metod, jako by šlo o veřejné datové členy.|Povoluje prvky interní kolekce objektu, které jsou k dispozici pomocí zápisu pole u objektu samotného.|  
|Je k dispozici prostřednictvím jednoduchého názvu.|Je k dispozici prostřednictvím indexu.|  
|Může být statický nebo členem instance.|Musí být členem instance.|  
|Přístupový objekt [Get](../../../csharp/language-reference/keywords/get.md) vlastnosti nemá žádné parametry.|`get` Přistupující objekt indexeru má stejný seznam formálních parametrů jako indexer.|  
|Přístupový objekt [set](../../../csharp/language-reference/keywords/set.md) vlastnosti obsahuje implicitní `value` parametr.|Přistupující objekt indexeru má stejný formální seznam parametrů jako indexer a také parametr [Value.](../../../csharp/language-reference/keywords/value.md) `set`|  
|Podporuje zkrácenou syntaxi s [automaticky implementovanými vlastnostmi](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).|Podporuje členy Expression těle pro získání pouze indexerů.|  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Indexery](../../../csharp/programming-guide/indexers/index.md)
- [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
