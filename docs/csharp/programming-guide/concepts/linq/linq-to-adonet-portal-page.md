---
title: LINQ to ADO.NET (stránka portálu)
description: LINQ to ADO.NET vám umožní dotazovat se na jakýkoliv vyčíslitelné objekt v ADO.NET pomocí programovacího modelu LINQ. Seznamte se se třemi ADO.NET technologie LINQ.
ms.date: 07/20/2015
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
ms.openlocfilehash: 0b09e678d29d27de5758cf5a5fcacd7391342792
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165758"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (stránka portálu)
LINQ to ADO.NET vám umožní dotazovat se na jakýkoliv vyčíslitelné objekt v ADO.NET pomocí programovacího modelu LINQ (Language-Integrated Query).  
  
> [!NOTE]
> Dokumentace LINQ to ADO.NET se nachází v části ADO.NET sady .NET Framework SDK: [LINQ a ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).  
  
 Existují tři samostatné technologie LINQ (ADO.NET Language-Integrated Query): LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] a LINQ to Entities. LINQ to DataSet poskytuje bohatší a optimalizované dotazy přes <xref:System.Data.DataSet> , [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] umožňuje přímo dotazovat se na SQL Server schémat databáze a LINQ to Entities umožňuje dotazovat se na model EDM (Entity Data Model).  
  
## <a name="linq-to-dataset"></a>LINQ na DataSet  
 <xref:System.Data.DataSet>Je jednou z nejčastěji používaných komponent v ADO.NET a je klíčovým prvkem odpojeného programovacího modelu, na kterém je ADO.NET sestaven. Navzdory tomuto význačnost však <xref:System.Data.DataSet> má aplikace omezené možnosti dotazování.  
  
 LINQ to DataSet umožňuje sestavovat bohatší možnosti dotazování <xref:System.Data.DataSet> pomocí stejných funkcí dotazů, které jsou k dispozici pro mnoho dalších zdrojů dat.  
  
 Další informace najdete v tématu [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]poskytuje infrastrukturu run-time pro správu relačních dat jako objektů. V systému [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] je datový model relační databáze mapován na objektový model vyjádřený v programovacím jazyce vývojáře. Při spuštění aplikace [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] přeloží dotazy integrované v jazyce v objektovém modelu do SQL a odešle je do databáze pro provedení. Když databáze vrátí výsledky, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] převede je zpátky na objekty, které můžete manipulovat.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]zahrnuje podporu pro uložené procedury a uživatelsky definované funkce v databázi a pro dědění v objektovém modelu.  
  
 Další informace najdete v tématu [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Prostřednictvím model EDM (Entity Data Model) jsou relační data vystavena jako objekty v prostředí .NET. Díky tomu je vrstva objektu ideálním cílem pro podporu LINQ, což vývojářům umožňuje formulovat dotazy z databáze z jazyka používaného k sestavení obchodní logiky. Tato funkce se označuje jako LINQ to Entities. Další informace najdete v tématu [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) .  
  
## <a name="see-also"></a>Viz také

- [LINQ a ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [LINQ (Language-Integrated Query) (C#)](./index.md)
