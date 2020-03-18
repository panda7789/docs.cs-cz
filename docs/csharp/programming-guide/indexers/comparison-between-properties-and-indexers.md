---
title: Porovnání vlastností a indexerů – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 330d222083ce599719698c023803196dfe88da84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712127"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)
Indexery jsou jako vlastnosti. S výjimkou rozdílů uvedených v následující tabulce platí všechna pravidla, která jsou definována pro přístupové objekty vlastností také pro přístupové objekty indexeru.  
  
|Vlastnost|Indexer|  
|--------------|-------------|  
|Umožňuje metody, které mají být volány, jako by byly členy veřejných dat.|Umožňuje prvky vnitřní kolekce objektu, které mají být přístupné pomocí zápisu pole na samotný objekt.|  
|Přístup prostřednictvím jednoduchého názvu.|Přístup prostřednictvím indexu.|  
|Může být statický nebo člen instance.|Musí být členem instance.|  
|Přístupový [objekt get](../../language-reference/keywords/get.md) vlastnosti nemá žádné parametry.|Přistupující `get` objekt indexeru má stejný seznam formálních parametrů jako indexer.|  
|Set [set](../../language-reference/keywords/set.md) přistupující objekt vlastnosti obsahuje implicitní `value` parametr.|Přistupující `set` objekt indexeru má stejný seznam formálních parametrů jako indexer a také parametr [hodnoty.](../../language-reference/keywords/value.md)|  
|Podporuje zkrácenou syntaxi s [automaticky implementovanými vlastnostmi](../classes-and-structs/auto-implemented-properties.md).|Podporuje výraz tělesně členy pro získat pouze indexery.|  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Indexery](./index.md)
- [Vlastnosti](../classes-and-structs/properties.md)
