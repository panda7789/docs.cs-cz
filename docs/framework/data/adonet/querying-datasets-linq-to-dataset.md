---
title: Dotazování na datové sady (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 79a9b320fbdbfecc3f7d531d992b1529873871a5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783045"
---
# <a name="querying-datasets-linq-to-dataset"></a>Dotazování na datové sady (LINQ to DataSet)
Po naplnění <xref:System.Data.DataSet> objektu daty můžete začít dotazovat se na něj. Formulace dotazů pomocí LINQ to DataSet je podobná [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] použití s [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]jinými zdroji dat s podporou. Nezapomeňte však, že pokud používáte [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazy <xref:System.Data.DataSet> přes objekt, který se <xref:System.Data.DataRow> dotazuje na výčet objektů, místo výčtu vlastního typu. To znamená, že můžete použít libovolný ze členů <xref:System.Data.DataRow> třídy [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] v dotazech. To vám umožní vytvářet bohatě komplexní dotazy.  
  
 Stejně jako u jiných implementací [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]nástroje můžete vytvářet LINQ to DataSet dotazy ve dvou různých formulářích: Syntaxe výrazů dotazů a syntaxe dotazů založených na metodách. Pomocí syntaxe výrazu dotazu nebo syntaxe dotazu založeného na metodách můžete provádět dotazy na jednotlivé tabulky v <xref:System.Data.DataSet>, proti několika tabulkám <xref:System.Data.DataSet>v nebo v tabulkách v <xref:System.Data.DataSet>typu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Dotazy na jednu tabulku](single-table-queries-linq-to-dataset.md)  
 Popisuje, jak provádět dotazy na jednu tabulku.  
  
 [Dotazy na křížovou tabulku](cross-table-queries-linq-to-dataset.md)  
 Popisuje postup provádění dotazů mezi tabulkami.  
  
 [Dotazy na typové datové sady](querying-typed-datasets.md)  
 Popisuje, jak zadávat dotazy <xref:System.Data.DataSet> na typové objekty.  
  
## <a name="see-also"></a>Viz také:

- [Příklady LINQ to DataSet](linq-to-dataset-examples.md)
- [Načtení dat do datové sady](loading-data-into-a-dataset.md)
