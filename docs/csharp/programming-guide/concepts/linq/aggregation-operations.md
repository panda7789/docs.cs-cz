---
title: Operace agregace (C#)
ms.date: 07/20/2015
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
ms.openlocfilehash: ea32becbb7ad0d3944eaea7b1b5448342ed438a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347550"
---
# <a name="aggregation-operations-c"></a>Operace agregace (C#)
Operace agregace vypočítá jednu hodnotu z kolekce hodnot. Příkladem agregační operace je výpočet průměrné denní teploty z hodnot denní teploty za měsíc.  
  
 Následující obrázek znázorňuje výsledky dvou různých operací agregace na posloupnost čísel. První operace sečte čísla. Druhá operace vrátí maximální hodnotu v pořadí.  
  
 ![Obrázek, který znázorňuje operace agregace LINQ.](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 Standardní metody operátoru dotazu, které provádějí operace agregace jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Agregace|Provádí vlastní agregaci operace na hodnoty kolekce.|Neužívá se.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Průměr|Vypočítá průměrnou hodnotu kolekce hodnot.|Neužívá se.|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Počet|Počítá prvky v kolekci, volitelně pouze ty prvky, které splňují predikát funkce.|Neužívá se.|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|Dlouhý počet|Počítá prvky ve velké kolekci, volitelně pouze ty prvky, které splňují funkci predikátu.|Neužívá se.|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Maximum|Určuje maximální hodnotu v kolekci.|Neužívá se.|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Minimum|Určuje minimální hodnotu v kolekci.|Neužívá se.|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Součet|Vypočítá součet hodnot v kolekci.|Neužívá se.|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Standardní operátory dotazů – přehled (C#)](./standard-query-operators-overview.md)
- [Jak vypočítat hodnoty sloupců v textovém souboru CSV (LINQ) (C#)](./how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Jak dotazovat na největší soubor nebo soubory ve stromu adresářů (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
- [Jak dotazovat na celkový počet bajtů v sadě složek (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)
