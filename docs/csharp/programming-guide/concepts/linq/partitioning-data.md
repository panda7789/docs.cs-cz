---
title: Dělení dat (C#)
description: Naučte se, jak rozdělit data v LINQ. Podívejte se na Obrázek znázorňující výsledky operací dělení.
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 3c85eaec2dc01b683234a27714750354982be440
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302604"
---
# <a name="partitioning-data-c"></a>Dělení dat (C#)
Dělení v jazyce LINQ odkazuje na operaci rozdělení vstupní sekvence do dvou oddílů bez přeuspořádání prvků a vrácení jedné z sekcí.  
  
 Následující ilustrace znázorňuje výsledky tří různých operací dělení na sekvenci znaků. První operace vrátí první tři prvky v sekvenci. Druhá operace přeskočí první tři prvky a vrátí zbývající prvky. Třetí operace přeskočí první dva prvky v sekvenci a vrátí další tři prvky.  
  
 ![Obrázek, který ukazuje tři operace dělení na oddíly LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 Standardní metody operátoru dotazu, které sekvence oddílů jsou uvedeny v následující části.  
  
## <a name="operators"></a>Operátory  
  
|Název operátoru|Popis|Syntaxe výrazu dotazu v jazyce C#|Další informace|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Přeskočit|Přeskočí prvky až do zadané pozice v sekvenci.|Neužívá se.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile –|Přeskočí prvky založené na funkci predikátu, dokud element nesplní podmínku.|Neužívá se.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Přebírá prvky až do zadané pozice v sekvenci.|Neužívá se.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile –|Převezme prvky založené na funkci predikátu, dokud element nesplní podmínku.|Neužívá se.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (C#)](./standard-query-operators-overview.md)
