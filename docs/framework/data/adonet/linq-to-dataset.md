---
title: LINQ na DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 8a16e3fe0cea04813be50a83f906170199e78e3e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764850"
---
# <a name="linq-to-dataset"></a>LINQ na DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] umožňuje snadnější a rychlejší dotazu přes data uložená v mezipaměti <xref:System.Data.DataSet> objektu. Konkrétně [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zjednodušuje dotazování tím, že umožňuje vývojářům psát dotazy z programovací jazyk, samostatně, místo pomocí samostatných dotazovací jazyk. To je zvlášť vhodné pro Visual Studio vývojáře, kteří teď můžete využít výhod kontrolu syntaxe kompilaci, statické zadáním a podporu technologie IntelliSense poskytované sady Visual Studio jejich dotazů.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Můžete také použít k dotazu přes data, která byla konsolidována z jednoho nebo více zdrojů dat. To umožňuje mnoho scénářů, které vyžadují flexibilitu při jak data jsou reprezentována a zpracovávají, jako je například dotazování místně agregovaná data a střední vrstvy ukládání do mezipaměti ve webových aplikací. Obecné sestavy, analýzu a aplikace pro business intelligence klást tato metoda manipulaci.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Funkce je zveřejněna primárně prostřednictvím metody rozšíření v <xref:System.Data.DataRowExtensions> a <xref:System.Data.DataTableExtensions> třídy. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] staví na a používá existující [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architekturu a není určena k nahrazení [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] v kódu aplikace. Existující kód ADO.NET 2.0 budou nadále fungovat v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aplikace. Vztah [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] k [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] a úložiště dat je znázorněno v následujícím diagramu.  
  
 ![LINQ na DataSet je založena na zprostředkovatele ADO.NET](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Začínáme](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Viz také  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ a ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)
