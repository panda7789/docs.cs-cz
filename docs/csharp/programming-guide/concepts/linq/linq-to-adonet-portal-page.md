---
title: LINQ to ADO.NET (stránka portálu)
ms.date: 07/20/2015
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
ms.openlocfilehash: aa8a5922ab33bf571f96d7b2dc3ea7d5877464cb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526229"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (stránka portálu)
[!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] umožňuje dotazování přes jakýkoli vyčíslitelný objekt v [!INCLUDE[vstecado](~/includes/vstecado-md.md)] pomocí [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] programovací model.  
  
> [!NOTE]
>  [!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] Dokumentace se nacházejí v části ADO.NET SDK rozhraní .NET Framework: [LINQ a ADO.NET](https://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec).  
  
 Existují tři samostatné ADO.NET [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] technologie: [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], a [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)] poskytuje širší, optimalizované dotazování <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] umožňuje přímo dotazovat schémata databáze systému SQL Server, a [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] umožňuje dotazování [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)].  
  
## <a name="linq-to-dataset"></a>LINQ na DataSet  
 <xref:System.Data.DataSet> Je jedním z nejpoužívanějších součástí [!INCLUDE[vstecado](~/includes/vstecado-md.md)], a je klíčovým prvkem odpojené programovací model, který [!INCLUDE[vstecado](~/includes/vstecado-md.md)] je postavená na. Bez ohledu na tato úroveň, ale <xref:System.Data.DataSet> má omezené možnosti dotazu.  
  
 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)] Umožňuje vytvoření bohatších možností dotazování <xref:System.Data.DataSet> pomocí stejné funkce dotazování, který je k dispozici pro mnoha dalším datovým zdrojům.  
  
 Další informace najdete v tématu [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] poskytuje infrastrukturu prostředí run-time pro správu relačních dat jako objektů. V [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], datový model relační databáze je namapován na objektový model vyjádřený v programovacím jazyce vývojáře. Při spuštění aplikace, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] integrovaný jazyk dotazů v objektovém modelu převádí na SQL a odesílá je do databáze pro spuštění. Když databázi vrátí výsledky, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] přeloží zpět do objektů, které můžete pracovat s.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zahrnuje podporu pro uložených procedur a uživatelem definovaných funkcí v databázi a dědičnosti v objektovém modelu.  
  
 Další informace najdete v tématu [technologie LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Až [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)], je přístupný relačních dat jako objektů v prostředí .NET. Tím je objekt vrstvy ideální cíl pro [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] podporu umožňující vývojářům formulovali dotazy na databázi z jazyk používaný k vytváření obchodní logiku. Tato schopnost je známá jako [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. Zobrazit [technologii LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) Další informace.  
  
## <a name="see-also"></a>Viz také

- [LINQ a ADO.NET](https://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)  
- [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
