---
title: Dotazy na datové sady (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 5ecf85a73cd38fc1fa575bd591618e5273b390e0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422439"
---
# <a name="querying-datasets-linq-to-dataset"></a>Dotazy na datové sady (LINQ to DataSet)
Po <xref:System.Data.DataSet> objekt naplněné daty, můžete začít ho dotazování. Formulování dotazů s [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] podobá se to používání [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] proti jiné [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]– povolené zdroje. Nezapomeňte však, že při použití [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazuje přes <xref:System.Data.DataSet> objekt dotazujete výčet <xref:System.Data.DataRow> objekty namísto výčet vlastního typu. To znamená, že můžete použít některý z členů <xref:System.Data.DataRow> tříd ve vaší [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazy. Umožňuje vytvořit bohatě vybaveným a komplexní dotazy.  
  
 Stejně jako v jiných implementacích [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], můžete vytvořit [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazy ve dvou různých formách: výraz syntaxe využívající dotazy a syntaxe dotazů založených na volání metody. Další informace o těchto dvou formách, naleznete v tématu [Začínáme s dotazy LINQ](https://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9). Můžete použít syntaxe výrazu dotazu nebo syntaxe dotazů založených na volání metody k provedení dotazů na jedné tabulky v <xref:System.Data.DataSet>, proti více tabulek v <xref:System.Data.DataSet>, nebo na tabulky v typovaného <xref:System.Data.DataSet>.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Dotazy na jednu tabulku](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 Popisuje, jak provádět dotazy na jednu tabulku.  
  
 [Dotazy na křížovou tabulku](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 Popisuje, jak provádět dotazy na křížovou tabulku.  
  
 [Dotazy na typové datové sady](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 Popisuje, jak provádět dotazy zadali <xref:System.Data.DataSet> objekty.  
  
## <a name="see-also"></a>Viz také  
 [Příklady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Načtení dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
