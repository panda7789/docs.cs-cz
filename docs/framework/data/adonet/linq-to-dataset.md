---
title: LINQ na DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: c4069ef760877935c4ce194144d131d0dc58b4d3
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504365"
---
# <a name="linq-to-dataset"></a>LINQ na DataSet
Technologie LINQ to DataSet umožňuje jednodušší a rychlejší dotaz na data uložená v mezipaměti <xref:System.Data.DataSet> objektu. Konkrétně LINQ to DataSet zjednodušuje dotazování tím, že umožňuje vývojářům psát dotazy v programovacím jazyce, nikoli pomocí samostatné dotazovací jazyk. To je užitečné zejména pro Visual Studio získávají vývojáři, kteří můžou využívat kontrola syntaxe v době kompilace, psát statické, a podporu technologie IntelliSense poskytovaný sadou Visual Studio ve svých dotazech.  
  
 Technologie LINQ to DataSet lze také použít k dotazu nad daty, který byl sloučen z jednoho nebo více zdrojů dat. To umožňuje mnoho scénářů, které potřebují flexibilně jak data jsou reprezentovány a zpracována, jako jsou například dotazování místně agregovaná data a střední vrstvy, ukládání do mezipaměti ve webových aplikacích. Tato metoda manipulaci s vyžadují zejména obecné vytváření sestav, analýzy a v aplikacích business intelligence.  
  
 LINQ to DataSet funkce je k dispozici primárně prostřednictvím metody rozšíření v <xref:System.Data.DataRowExtensions> a <xref:System.Data.DataTableExtensions> třídy. Technologie LINQ to DataSet vychází a používá existující architekturu ADO.NET a není určena k nahrazení technologie ADO.NET v kódu aplikace. Stávající kód technologie ADO.NET bude nadále fungovat v technologii LINQ to DataSet aplikace. Vztah mezi LINQ to DataSet technologie ADO.NET a úložiště dat je znázorněn v následujícím diagramu.  
  
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
