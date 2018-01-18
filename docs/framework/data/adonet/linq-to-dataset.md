---
title: LINQ na DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cdd3f21d8b02c24db24d2efd08487ef1a290e022
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="linq-to-dataset"></a>LINQ na DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]umožňuje snadnější a rychlejší dotazu přes data uložená v mezipaměti <xref:System.Data.DataSet> objektu. Konkrétně [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zjednodušuje dotazování tím, že umožňuje vývojářům psát dotazy z programovací jazyk, samostatně, místo pomocí samostatných dotazovací jazyk. To je užitečné zejména pro [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] vývojáři, kteří teď můžete využít výhod kontrolu syntaxe kompilaci, zadáním statické, a poskytuje podporu technologie IntelliSense [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] jejich dotazů.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]Můžete také použít k dotazu přes data, která byla konsolidována z jednoho nebo více zdrojů dat. To umožňuje mnoho scénářů, které vyžadují flexibilitu při jak data jsou reprezentována a zpracovávají, jako je například dotazování místně agregovaná data a střední vrstvy ukládání do mezipaměti ve webových aplikací. Obecné sestavy, analýzu a aplikace pro business intelligence klást tato metoda manipulaci.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Funkce je zveřejněna primárně prostřednictvím metody rozšíření v <xref:System.Data.DataRowExtensions> a <xref:System.Data.DataTableExtensions> třídy. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]staví na a používá existující [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] architekturu a není určena k nahrazení [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] v kódu aplikace. Existující kód ADO.NET 2.0 budou nadále fungovat v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aplikace. Vztah [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] k [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] a úložiště dat je znázorněno v následujícím diagramu.  
  
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
