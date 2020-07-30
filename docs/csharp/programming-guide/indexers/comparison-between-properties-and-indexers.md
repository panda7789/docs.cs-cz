---
title: Porovnání mezi vlastnostmi a indexery – Průvodce programováním v C#
description: Porovnejte, jak Indexery v jazyce C# jsou jako vlastnosti. S výjimkou některých rozdílů se pravidla definovaná pro přistupující objekty vlastnosti vztahují na přistupující objekty indexeru.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: b83ce3db3d4b53fb7bcc5f3b3cd603a375d5d473
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299172"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)
Indexery jsou jako vlastnosti. S výjimkou rozdílů uvedených v následující tabulce se všechna pravidla, která jsou definována pro přistupující objekty vlastnosti, vztahují také na přistupující objekty indexeru.  
  
|Vlastnost|Indexer|  
|--------------|-------------|  
|Povoluje volání metod, jako by šlo o veřejné datové členy.|Povoluje prvky interní kolekce objektu, které jsou k dispozici pomocí zápisu pole u objektu samotného.|  
|Je k dispozici prostřednictvím jednoduchého názvu.|Je k dispozici prostřednictvím indexu.|  
|Může být statický nebo členem instance.|Musí být členem instance.|  
|Přístupový objekt [Get](../../language-reference/keywords/get.md) vlastnosti nemá žádné parametry.|`get`Přistupující objekt indexeru má stejný seznam formálních parametrů jako indexer.|  
|Přístupový objekt [set](../../language-reference/keywords/set.md) vlastnosti obsahuje implicitní `value` parametr.|`set`Přistupující objekt indexeru má stejný formální seznam parametrů jako indexer a také parametr [Value](../../language-reference/keywords/value.md) .|  
|Podporuje zkrácenou syntaxi s [automaticky implementovanými vlastnostmi](../classes-and-structs/auto-implemented-properties.md).|Podporuje členy Expression těle pro získání pouze indexerů.|  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Indexery](./index.md)
- [Vlastnosti](../classes-and-structs/properties.md)
