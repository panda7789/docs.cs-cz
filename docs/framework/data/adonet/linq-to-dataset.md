---
title: LINQ na DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 36335f90c7850fa00a15e7112b7473637250c656
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306236"
---
# <a name="linq-to-dataset"></a>LINQ na DataSet
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zajišťuje snadnější a rychlejší dotaz data uložená v mezipaměti <xref:System.Data.DataSet> objektu. Konkrétně [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zjednodušuje dotazování tím, že umožňuje vývojářům psát dotazy v programovacím jazyce, nikoli pomocí samostatné dotazovací jazyk. To je užitečné zejména pro Visual Studio získávají vývojáři, kteří můžou využívat kontrola syntaxe v době kompilace, psát statické, a podporu technologie IntelliSense poskytovaný sadou Visual Studio ve svých dotazech.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Můžete také použít k dotazu nad daty, který byl sloučen z jednoho nebo více zdrojů dat. To umožňuje mnoho scénářů, které potřebují flexibilně jak data jsou reprezentovány a zpracována, jako jsou například dotazování místně agregovaná data a střední vrstvy, ukládání do mezipaměti ve webových aplikacích. Tato metoda manipulaci s vyžadují zejména obecné vytváření sestav, analýzy a v aplikacích business intelligence.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Funkce se zveřejňuje prostřednictvím metody rozšíření v především <xref:System.Data.DataRowExtensions> a <xref:System.Data.DataTableExtensions> třídy. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] navazuje na a použije se stávající architekturou ADO.NET a není určena k nahrazení technologie ADO.NET v kódu aplikace. Stávající kód technologie ADO.NET bude i nadále fungovat v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] aplikace. Vztah mezi [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ADO.NET a data store je znázorněn v následujícím diagramu.  
  
 ![Diagram znázorňující, že LINQ to DataSet je založen na zprostředkovatele rozhraní ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Začínáme](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
  
 [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a>Viz také:

- [Language-Integrated Query (LINQ) –C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [Language-Integrated Query (LINQ) – Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ a ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
