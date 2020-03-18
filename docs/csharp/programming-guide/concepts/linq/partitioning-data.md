---
title: Dělení dat (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: d9330e9973b2f25903e1f81a7296362e2a7c756b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591590"
---
# <a name="partitioning-data-c"></a>Dělení dat (C#)
Dělení v LINQ odkazuje na operaci rozdělení vstupní sekvence do dvou částí, bez změny uspořádání prvků a potom vrácení jednoho z oddílů.  
  
 Následující obrázek znázorňuje výsledky tří různých operací dělení na posloupnost znaků. První operace vrátí první tři prvky v pořadí. Druhá operace přeskočí první tři prvky a vrátí zbývající prvky. Třetí operace přeskočí první dva prvky v sekvenci a vrátí další tři prvky.  
  
 ![Obrázek, který znázorňuje tři operace dělení LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 Standardní metody operátoru dotazu, které jsou oddílsekvence jsou uvedeny v následující části.  
  
## <a name="operators"></a>Operátory  
  
|Název operátoru|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Skip|Přeskočí prvky až do zadané pozice v sekvenci.|Neužívá se.|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|Skipwhile|Přeskočí prvky založené na funkci predikátu, dokud prvek nesplňuje podmínku.|Neužívá se.|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Trvá prvky až do zadané pozice v sekvenci.|Neužívá se.|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|Takewhile|Bere prvky založené na funkci predikátu, dokud prvek nesplňuje podmínku.|Neužívá se.|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Standardní operátory dotazů – přehled (C#)](./standard-query-operators-overview.md)
