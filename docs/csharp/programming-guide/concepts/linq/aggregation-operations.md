---
title: Agregační operace (C#)
ms.date: 07/20/2015
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
ms.openlocfilehash: 0ce45948b94a04b506fefe65d3b1b7bb01110bbb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509188"
---
# <a name="aggregation-operations-c"></a>Agregační operace (C#)
Operace agregace vypočítá jedinou hodnotu z kolekce hodnot. Příklad operace agregace je výpočet denní teplota z za měsíc denní teplotní hodnoty.  
  
 Následující obrázek ukazuje výsledky dvou různých agregační operace na sekvenci čísel. První operace sečte čísla. Druhou operaci vrátí maximální hodnotu v pořadí.  
  
 ![Agregační operace LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")  
  
 Standardní metody operátoru dotazu, které provádějí operace agregace jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu jazyka C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Aggregate|Provede vlastní agregační operace na hodnotách kolekce.|Nelze použít.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Průměr|Vypočítá průměrnou hodnotu kolekci hodnot.|Nelze použít.|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Počet|Vrátí počet prvků v kolekci, volitelně pouze elementy, které splňují funkce predikátu.|Nelze použít.|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Vrátí počet prvků v velkou kolekci volitelně pouze elementy, které splňují funkce predikátu.|Nelze použít.|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|maximální počet|Určuje maximální hodnotu v kolekci.|Nelze použít.|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|min|Určuje minimální hodnota v kolekci.|Nelze použít.|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Součet|Vypočítá součet hodnot v kolekci.|Nelze použít.|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>  
- [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [Postupy: výpočet hodnot sloupce v textovém souboru CSV (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)  
- [Postupy: dotazování na největší soubor či soubory v adresářovém stromu (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)  
- [Postupy: dotaz pro celkový počet bajtů v sadě složek (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)
