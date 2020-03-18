---
title: LINQ to ADO.NET (stránka portálu)
ms.date: 07/20/2015
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
ms.openlocfilehash: 84412e43a9d6b1e256e4ac8306a94126a3eaaaf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635545"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (stránka portálu)
LINQ ADO.NET umožňuje dotaz přes libovolný znakný objekt v ADO.NET pomocí programovacího modelu LINQ (Language-Integrated Query).  
  
> [!NOTE]
> Dokumentace linq ADO.NET je umístěna v ADO.NET části sady .NET Framework SDK: [LINQ a ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).  
  
 Existují tři samostatné technologie ADO.NET jazykově integrovaný dotaz (LINQ): [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]LINQ to DataSet a LINQ na entity. LINQ to DataSet poskytuje bohatší, optimalizované dotazování přes <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] umožňuje přímý dotaz sql server schémata databáze a LINQ entity umožňuje dotaz entity datový model.  
  
## <a name="linq-to-dataset"></a>LINQ na DataSet  
 Je <xref:System.Data.DataSet> jednou z nejpoužívanějších součástí v ADO.NET a je klíčovým prvkem odpojeného programovacího modelu, na kterých je ADO.NET postaven. Navzdory tomuto významu <xref:System.Data.DataSet> má však omezené možnosti dotazu.  
  
 LINQ to DataSet umožňuje vytvářet <xref:System.Data.DataSet> bohatší možnosti dotazu do pomocí stejné funkce dotazu, který je k dispozici pro mnoho jiných zdrojů dat.  
  
 Další informace naleznete v tématu [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]poskytuje run-time infrastrukturu pro správu relačních dat jako objektů. V [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]aplikaci je datový model relační databáze mapován na objektový model vyjádřený v programovacím jazyce vývojáře. Při spuštění aplikace [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] překládá dotazy integrované jazykem v objektovém modelu do SQL a odešle je do databáze pro spuštění. Když databáze vrátí výsledky, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] převede je zpět do objektů, se kterými můžete manipulovat.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]zahrnuje podporu pro uložené procedury a uživatelem definované funkce v databázi a dědičnost v objektovém modelu.  
  
 Další informace naleznete v tématu [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Prostřednictvím datového modelu entity jsou relační data vystavena jako objekty v prostředí .NET. Díky vrstvě objektu je ideální cíl pro podporu LINQ, což vývojářům umožňuje formulovat dotazy proti databázi z jazyka použitého k vytvoření obchodní logiky. Tato funkce se označuje jako LINQ entity. Další informace naleznete v tématu [LINQ to Entities.](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)  
  
## <a name="see-also"></a>Viz také

- [LINQ a ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Dotaz integrovaný jazykem (LINQ) (C#)](./index.md)
