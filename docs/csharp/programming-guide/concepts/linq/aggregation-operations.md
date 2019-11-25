---
title: Agregační operace (C#)
ms.date: 07/20/2015
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
ms.openlocfilehash: aebefcad8a741a97a51e73bfade9d4a16d343100
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141541"
---
# <a name="aggregation-operations-c"></a>Agregační operace (C#)
Agregační operace vypočítá jednu hodnotu z kolekce hodnot. Ukázka operace agregace počítá průměrnou denní teplotu z hodnoty denních teplot v měsíci.  
  
 Následující ilustrace znázorňuje výsledky dvou různých agregačních operací na sekvenci čísel. První operace Sečte čísla. Druhá operace vrátí maximální hodnotu v sekvenci.  
  
 ![Ilustrace znázorňující agregační operace LINQ](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 Standardní metody operátoru dotazu, které provádějí operace agregace, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|C#Syntaxe výrazu dotazu|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Aggregate|Provede vlastní agregační operaci na hodnotách kolekce.|Nelze použít.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Vypočítat|Vypočítá průměrnou hodnotu kolekce hodnot.|Nelze použít.|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Výpočtu|Spočítá prvky v kolekci, volitelně pouze ty prvky, které odpovídají funkci predikátu.|Nelze použít.|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Spočítá prvky ve velké kolekci, volitelně pouze ty prvky, které odpovídají funkci predikátu.|Nelze použít.|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Počet|Určuje maximální hodnotu v kolekci.|Nelze použít.|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Dlouhé|Určuje minimální hodnotu v kolekci.|Nelze použít.|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Zapůjčen|Vypočítá součet hodnot v kolekci.|Nelze použít.|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
- [Jak vypočítat hodnoty sloupce v textovém souboru CSV (LINQ) (C#)](./how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Postupy: dotaz na největší soubor nebo soubory ve stromu adresářů (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
- [Postupy: dotazování na celkový počet bajtů v sadě složek (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)
