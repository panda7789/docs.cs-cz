---
title: Agregační operace (C#)
ms.date: 07/20/2015
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
ms.openlocfilehash: 04415c430059057cef26b3750faa03b925cfa994
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594980"
---
# <a name="aggregation-operations-c"></a>Agregační operace (C#)
Agregační operace vypočítá jednu hodnotu z kolekce hodnot. Ukázka operace agregace počítá průměrnou denní teplotu z hodnoty denních teplot v měsíci.  
  
 Následující ilustrace znázorňuje výsledky dvou různých agregačních operací na sekvenci čísel. První operace Sečte čísla. Druhá operace vrátí maximální hodnotu v sekvenci.  
  
 ![Ilustrace znázorňující agregační operace LINQ](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 Standardní metody operátoru dotazu, které provádějí operace agregace, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|C#Syntaxe výrazu dotazu|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Aggregate|Provede vlastní agregační operaci na hodnotách kolekce.|Není k dispozici.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Average|Vypočítá průměrnou hodnotu kolekce hodnot.|Není k dispozici.|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Count|Spočítá prvky v kolekci, volitelně pouze ty prvky, které odpovídají funkci predikátu.|Není k dispozici.|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Spočítá prvky ve velké kolekci, volitelně pouze ty prvky, které odpovídají funkci predikátu.|Není k dispozici.|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Maximum|Určuje maximální hodnotu v kolekci.|Není k dispozici.|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Minimum|Určuje minimální hodnotu v kolekci.|Není k dispozici.|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Součet|Vypočítá součet hodnot v kolekci.|Není k dispozici.|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Linq>
- [Přehled standardních operátorů dotazůC#()](./standard-query-operators-overview.md)
- [Postupy: Hodnoty výpočetních sloupců v textovém souboru CSV (LINQ) (C#)](./how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Postupy: Dotaz na největší soubor nebo soubory v adresářovém stromu (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
- [Postupy: Dotaz na celkový počet bajtů v sadě složek (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)
