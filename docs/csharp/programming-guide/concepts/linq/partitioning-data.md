---
title: Dělení dat (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: d9330e9973b2f25903e1f81a7296362e2a7c756b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591590"
---
# <a name="partitioning-data-c"></a>Dělení dat (C#)
Dělení v jazyce LINQ odkazuje na operaci rozdělení vstupní sekvence do dvou oddílů bez přeuspořádání prvků a vrácení jedné z sekcí.  
  
 Následující ilustrace znázorňuje výsledky tří různých operací dělení na sekvenci znaků. První operace vrátí první tři prvky v sekvenci. Druhá operace přeskočí první tři prvky a vrátí zbývající prvky. Třetí operace přeskočí první dva prvky v sekvenci a vrátí další tři prvky.  
  
 ![Obrázek, který ukazuje tři operace dělení na oddíly LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 Standardní metody operátoru dotazu, které sekvence oddílů jsou uvedeny v následující části.  
  
## <a name="operators"></a>Operátory  
  
|Název operátoru|Popis|C#Syntaxe výrazu dotazu|Další informace|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Skip|Přeskočí prvky až do zadané pozice v sekvenci.|Není k dispozici.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile –|Přeskočí prvky založené na funkci predikátu, dokud element nesplní podmínku.|Není k dispozici.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Přebírá prvky až do zadané pozice v sekvenci.|Není k dispozici.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile –|Převezme prvky založené na funkci predikátu, dokud element nesplní podmínku.|Není k dispozici.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
