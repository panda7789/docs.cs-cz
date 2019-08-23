---
title: LINQ to ADO.NET (stránka portálu)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 25ec71086d501e6ac9be22871563b0fb4e3cfb8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957579"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (stránka portálu)
LINQ to ADO.NET umožňuje dotazování na jakýkoliv vyčíslitelné objekt v ADO.NET pomocí [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] programovacího modelu.  
  
> [!NOTE]
> Dokumentace k LINQ to ADO.NET najdete v části ADO.NET sady .NET Framework SDK: [LINQ a ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).
  
 Existují tři samostatné technologie ADO.NET [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] : LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]a LINQ to Entities. LINQ to DataSet poskytuje bohatší a optimalizované dotazy přes <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] umožňuje přímo dotazovat se na SQL Server schémat databáze a LINQ to Entities umožňuje dotazovat se na model EDM (Entity Data Model).  
  
## <a name="linq-to-dataset"></a>LINQ na DataSet  
 <xref:System.Data.DataSet> Je jednou z nejčastěji používaných komponent v ADO.NET a je klíčovým prvkem odpojeného programovacího modelu, na kterém je ADO.NET sestaven. Navzdory tomuto význačnost však <xref:System.Data.DataSet> má aplikace omezené možnosti dotazování.  
  
 LINQ to DataSet umožňuje sestavovat bohatší možnosti <xref:System.Data.DataSet> dotazování pomocí stejných funkcí dotazů, které jsou k dispozici pro mnoho dalších zdrojů dat.  
  
 Další informace najdete v tématu [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]poskytuje infrastrukturu run-time pro správu relačních dat jako objektů. V [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]systému je datový model relační databáze mapován na objektový model vyjádřený v programovacím jazyce vývojáře. Při spuštění aplikace [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] přeloží dotazy integrované v jazyce v objektovém modelu do SQL a odešle je do databáze pro provedení. Když databáze vrátí výsledky, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] převede je zpátky na objekty, které můžete manipulovat.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]zahrnuje podporu pro uložené procedury a uživatelsky definované funkce v databázi a pro dědění v objektovém modelu.  
  
 Další informace najdete v tématu [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Prostřednictvím model EDM (Entity Data Model) jsou relační data vystavena jako objekty v prostředí .NET. Tím se objekt nastaví jako ideální cíl pro [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] podporu a umožňuje vývojářům formulovat dotazy z databáze z jazyka používaného k sestavení obchodní logiky. Tato funkce se označuje jako LINQ to Entities. Další informace najdete v tématu [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) .  
  
## <a name="see-also"></a>Viz také:

- [LINQ a ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [LINQ (Language-Integrated Query) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
