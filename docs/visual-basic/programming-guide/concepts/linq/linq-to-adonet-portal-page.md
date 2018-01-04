---
title: "LINQ to ADO.NET (stránka portálu)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e2a78340e358fa0e0739e10f7b8da3cbc25b9541
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (stránka portálu)
[!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)]Umožňuje zadat dotaz na libovolný vyčíslitelný objekt v [!INCLUDE[vstecado](~/includes/vstecado-md.md)] pomocí [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] programovací model.  
  
> [!NOTE]
>  [!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] Dokumentace se nacházejí v části ADO.NET sady SDK rozhraní .NET Framework: [LINQ a ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec).  
  
 Existují tři samostatné ADO.NET [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] technologie: [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], a [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]poskytuje bohatší, optimalizované dotazování přes <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] umožňuje prohledávat přímo [!INCLUDE[ssNoVersion](~/includes/ssnoversion-md.md)] databáze schémata a [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] umožňuje dotazování [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)].  
  
## <a name="linq-to-dataset"></a>LINQ na DataSet  
 <xref:System.Data.DataSet> Je jednou z nejčastěji používané komponenty [!INCLUDE[vstecado](~/includes/vstecado-md.md)], a je klíčovým prvkem odpojené programování modelu, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] je založený na. I přes tato úroveň, ale <xref:System.Data.DataSet> má omezené možnosti dotazu.  
  
 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]Umožňuje vytvořit bohatší možnosti dotazu do <xref:System.Data.DataSet> pomocí stejné funkce dotazu, která je k dispozici pro mnoho další datové zdroje.  
  
 Další informace najdete v tématu [LINQ na DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]poskytuje infrastruktuře runtime pro správu relačních dat jako objekty. V [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], datový model relační databáze je namapována na objektový model vyjádřené v programovací jazyk vývojář. Při spuštění aplikace, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] překládá dotazy language-integrated ve model objektu do SQL a odesílá je do databáze pro provedení. Když databáze vrátí výsledky, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] překládá je zpět do objekty, které můžete upravit.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]zahrnuje podporu pro uložené procedury a uživatelem definované funkce v databázi a dědičnost v objektovém modelu.  
  
 Další informace najdete v tématu [technologie LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Prostřednictvím [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)], relačních dat je k dispozici jako objekty v prostředí .NET. Díky tomu objekt vrstvy ideální cíl pro [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] podpory, což vývojářům formulovali dotazy na databázi z jazyk používaný k vytvoření obchodní logiku. Tato funkce se označuje jako [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. V tématu [technologie LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) Další informace.  
  
## <a name="see-also"></a>Viz také  
 [LINQ a ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
