---
title: LINQ na DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 5e1644af7e07ad3395a30e56df52b7f85cefa77c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45972894"
---
# <a name="linq-to-dataset"></a>LINQ na DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zajišťuje snadnější a rychlejší dotaz data uložená v mezipaměti <xref:System.Data.DataSet> objektu. Konkrétně [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zjednodušuje dotazování tím, že umožňuje vývojářům psát dotazy v programovacím jazyce, nikoli pomocí samostatné dotazovací jazyk. To je užitečné zejména pro Visual Studio získávají vývojáři, kteří můžou využívat kontrola syntaxe v době kompilace, psát statické, a podporu technologie IntelliSense poskytovaný sadou Visual Studio ve svých dotazech.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Můžete také použít k dotazu nad daty, který byl sloučen z jednoho nebo více zdrojů dat. To umožňuje mnoho scénářů, které potřebují flexibilně jak data jsou reprezentovány a zpracována, jako jsou například dotazování místně agregovaná data a střední vrstvy, ukládání do mezipaměti ve webových aplikacích. Tato metoda manipulaci s vyžadují zejména obecné vytváření sestav, analýzy a v aplikacích business intelligence.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Funkce se zveřejňuje prostřednictvím metody rozšíření v především <xref:System.Data.DataRowExtensions> a <xref:System.Data.DataTableExtensions> třídy. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] navazuje na a použije existující [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architektury a není určena k nahrazení [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] v kódu aplikace. Stávající kód technologie ADO.NET 2.0 bude i nadále fungovat v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aplikace. Vztah mezi [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] k [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] a úložiště dat je znázorněn v následujícím diagramu.  
  
 ![Technologie LINQ to DataSet je založená na zprostředkovateli ADO.NET](../../../../docs/framework/data/adonet/media/linqtodataset.gif "LINQtoDataSet")  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Začínáme](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Viz také  
 [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ a ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)
