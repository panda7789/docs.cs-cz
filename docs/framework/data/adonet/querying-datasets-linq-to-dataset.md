---
title: Dotazování na datové sady (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: bb64abcffdbbcd46dfb11b2564619c565e461436
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634778"
---
# <a name="querying-datasets-linq-to-dataset"></a>Dotazování na datové sady (LINQ to DataSet)
Po naplnění <xref:System.Data.DataSet> objektu daty můžete začít dotazovat se na něj. Formulace dotazů pomocí LINQ to DataSet je podobná použití LINQ (Language-Integrated Query) pro jiné zdroje dat s podporou LINQ. Nezapomeňte však, že pokud používáte dotazy LINQ přes objekt <xref:System.Data.DataSet>, dotazuje se na výčet objektů <xref:System.Data.DataRow> namísto výčtu vlastního typu. To znamená, že můžete použít kterýkoli z členů třídy <xref:System.Data.DataRow> ve svých dotazech LINQ. To vám umožní vytvářet bohatě komplexní dotazy.  
  
 Stejně jako u jiných implementací technologie LINQ můžete vytvářet LINQ to DataSet dotazy ve dvou různých formulářích: Syntaxe výrazů dotazů a syntaxe dotazů založených na metodách. Pomocí syntaxe výrazu dotazu nebo syntaxe dotazu založeného na metodách můžete provádět dotazy na jednotlivé tabulky v <xref:System.Data.DataSet>, proti několika tabulkám v <xref:System.Data.DataSet>nebo k tabulkám ve typované <xref:System.Data.DataSet>.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Dotazy na jednu tabulku](single-table-queries-linq-to-dataset.md)  
 Popisuje, jak provádět dotazy na jednu tabulku.  
  
 [Dotazy na křížovou tabulku](cross-table-queries-linq-to-dataset.md)  
 Popisuje postup provádění dotazů mezi tabulkami.  
  
 [Dotazy na typové datové sady](querying-typed-datasets.md)  
 Popisuje způsob dotazování typu <xref:System.Data.DataSet> objektů.  
  
## <a name="see-also"></a>Viz také:

- [Příklady LINQ to DataSet](linq-to-dataset-examples.md)
- [Načtení dat do datové sady](loading-data-into-a-dataset.md)
