---
title: Porovnání mezi vlastnostmi a indexery – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 330d222083ce599719698c023803196dfe88da84
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712127"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)
Indexery jsou jako vlastnosti. S výjimkou rozdílů uvedených v následující tabulce se všechna pravidla, která jsou definována pro přistupující objekty vlastnosti, vztahují také na přistupující objekty indexeru.  
  
|Vlastnost|Indexer|  
|--------------|-------------|  
|Povoluje volání metod, jako by šlo o veřejné datové členy.|Povoluje prvky interní kolekce objektu, které jsou k dispozici pomocí zápisu pole u objektu samotného.|  
|Je k dispozici prostřednictvím jednoduchého názvu.|Je k dispozici prostřednictvím indexu.|  
|Může být statický nebo členem instance.|Musí být členem instance.|  
|Přístupový objekt [Get](../../language-reference/keywords/get.md) vlastnosti nemá žádné parametry.|Přístupový objekt `get` indexeru má stejný seznam formálních parametrů jako indexer.|  
|Přístupový objekt [set](../../language-reference/keywords/set.md) vlastnosti obsahuje implicitní parametr `value`.|Přístupový objekt `set` indexeru má stejný formální seznam parametrů jako indexer a také parametr [Value](../../language-reference/keywords/value.md) .|  
|Podporuje zkrácenou syntaxi s [automaticky implementovanými vlastnostmi](../classes-and-structs/auto-implemented-properties.md).|Podporuje členy Expression těle pro získání pouze indexerů.|  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Indexery](./index.md)
- [Vlastnosti](../classes-and-structs/properties.md)
