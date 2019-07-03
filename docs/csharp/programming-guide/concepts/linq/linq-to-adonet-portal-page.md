---
title: LINQ to ADO.NET (stránka portálu)
ms.date: 07/20/2015
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
ms.openlocfilehash: 8c39582ee95619bfddc7b89380e0a86305eeac27
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539505"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (stránka portálu)
Technologie LINQ to ADO.NET umožňuje dotazování přes jakýkoli vyčíslitelný objekt v ADO.NET pomocí [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] programovací model.  
  
> [!NOTE]
>  LINQ to ADO.NET dokumentace ke službě se nachází v části ADO.NET SDK rozhraní .NET Framework: [LINQ a ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).  
  
 Existují tři samostatné ADO.NET [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] technologií: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]a LINQ to Entities. Technologie LINQ to DataSet poskytuje širší, optimalizované dotazování <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] umožňuje zadat dotaz přímo schémata databáze systému SQL Server a LINQ to Entities umožňuje dotazování Entity Data Model.  
  
## <a name="linq-to-dataset"></a>LINQ na DataSet  
 <xref:System.Data.DataSet> Je jedním z nejpoužívanějších komponenty technologie ADO.NET a je klíčovým prvkem odpojené programovací model, který vychází ADO.NET. Bez ohledu na tato úroveň, ale <xref:System.Data.DataSet> má omezené možnosti dotazu.  
  
 Technologie LINQ to DataSet umožňuje vytvoření bohatších možností dotazování <xref:System.Data.DataSet> pomocí stejné funkce dotazování, který je k dispozici pro mnoha dalším datovým zdrojům.  
  
 Další informace najdete v tématu [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] poskytuje infrastrukturu prostředí run-time pro správu relačních dat jako objektů. V [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], datový model relační databáze je namapován na objektový model vyjádřený v programovacím jazyce vývojáře. Při spuštění aplikace, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] integrovaný jazyk dotazů v objektovém modelu převádí na SQL a odesílá je do databáze pro spuštění. Když databázi vrátí výsledky, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] přeloží zpět do objektů, které můžete pracovat s.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zahrnuje podporu pro uložených procedur a uživatelem definovaných funkcí v databázi a dědičnosti v objektovém modelu.  
  
 Další informace najdete v tématu [technologie LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Prostřednictvím modelu Entity Data Model je přístupný relačních dat jako objektů v prostředí .NET. Tím je objekt vrstvy ideální cíl pro [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] podporu umožňující vývojářům formulovali dotazy na databázi z jazyk používaný k vytváření obchodní logiku. Tato schopnost je známá jako LINQ to Entities. Zobrazit [technologii LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) Další informace.  
  
## <a name="see-also"></a>Viz také:

- [LINQ a ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
