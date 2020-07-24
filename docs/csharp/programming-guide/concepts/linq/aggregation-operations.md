---
title: Agregační operace (C#)
description: Další informace o metodách pro provádění agregační operace. Agregační operace vypočítá jednu hodnotu z kolekce hodnot.
ms.date: 07/20/2015
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
ms.openlocfilehash: 3d5a52249520478571db2fcfd7aa5d10fb013565
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104309"
---
# <a name="aggregation-operations-c"></a>Agregační operace (C#)
Agregační operace vypočítá jednu hodnotu z kolekce hodnot. Ukázka operace agregace počítá průměrnou denní teplotu z hodnoty denních teplot v měsíci.  
  
 Následující ilustrace znázorňuje výsledky dvou různých agregačních operací na sekvenci čísel. První operace Sečte čísla. Druhá operace vrátí maximální hodnotu v sekvenci.  
  
 ![Ilustrace znázorňující agregační operace LINQ](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 Standardní metody operátoru dotazu, které provádějí operace agregace, jsou uvedeny v následující části.  
  
## <a name="methods"></a>Metody  
  
|Název metody|Popis|Syntaxe výrazu dotazu v jazyce C#|Další informace|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Agregace|Provede vlastní agregační operaci na hodnotách kolekce.|Neužívá se.|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|Průměr|Vypočítá průměrnou hodnotu kolekce hodnot.|Neužívá se.|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|Count|Spočítá prvky v kolekci, volitelně pouze ty prvky, které odpovídají funkci predikátu.|Neužívá se.|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|LongCount|Spočítá prvky ve velké kolekci, volitelně pouze ty prvky, které odpovídají funkci predikátu.|Neužívá se.|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|Maximum|Určuje maximální hodnotu v kolekci.|Neužívá se.|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|Minimum|Určuje minimální hodnotu v kolekci.|Neužívá se.|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|Sčítání|Vypočítá součet hodnot v kolekci.|Neužívá se.|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq>
- [Přehled standardních operátorů dotazů (C#)](./standard-query-operators-overview.md)
- [Jak vypočítat hodnoty sloupce v textovém souboru CSV (LINQ) (C#)](./how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [Dotazování na největší soubor nebo soubory ve stromu adresářů (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
- [Postup dotazování na celkový počet bajtů v sadě složek (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)
