---
title: "LINQ na DataSet přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8b853eac26f41a3537438bd1f9b0263ae06b6e77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-dataset-overview"></a>LINQ na DataSet přehled
<xref:System.Data.DataSet> Je jedním z více často používaný součástí [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Je důležitou součástí odpojeném programování modelu, který [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] vychází z, a umožňuje explicitně ukládat data do mezipaměti z různých zdrojů. Pro prezentační vrstvy <xref:System.Data.DataSet> je úzce integrovaná s grafickým uživatelským rozhraním ovládací prvky pro datovou vazbu. Pro střední vrstvě poskytuje mezipaměti, který zachovává relační tvaru dat a zahrnuje rychle jednoduchý dotaz a hierarchii navigační služby. Běžné metoda používaná k snížit počet požadavků na databázi, které se má používat <xref:System.Data.DataSet> pro ukládání do mezipaměti ve střední vrstvě. Zvažte například řízené daty [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové aplikace. Podstatnou část dat aplikací často nemění příliš často a je společná pro relací nebo uživatele. Tato data je možné mít v paměti na webovém serveru, která omezuje počet požadavků v databázi a urychluje interakce uživatele. Další užitečné aspekt <xref:System.Data.DataSet> je, že umožňuje aplikaci tím podmnožiny dat z jedné nebo více zdroje dat do prostoru aplikace. Aplikace pak můžete upravit na data v paměti, při zachování jejich relačního modelu.  
  
 Bez ohledu na jeho úroveň <xref:System.Data.DataSet> má omezené možnosti dotazu. <xref:System.Data.DataTable.Select%2A> Metodu můžete použít pro filtrování a řazení a <xref:System.Data.DataRow.GetChildRows%2A> a <xref:System.Data.DataRow.GetParentRow%2A> metody lze použít pro navigační hierarchie. Pro jakýkoli složitější ale, musí vývojář napsat vlastní dotaz. Výsledkem může být aplikace, které nízký výkon a jsou poměrně složitá.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]umožňuje snadnější a rychlejší dotazu přes data uložená v mezipaměti <xref:System.Data.DataSet> objektu. Tyto dotazy jsou vyjádřeny v programovacím jazyce sám sebe, nikoli jako textové literály vložených v kódu aplikace. To znamená, že vývojáři nemají další samostatné dotazovací jazyk. Kromě toho [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] umožňuje [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] vývojářům zvýšit produktivitu, fungovat, protože [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] IDE poskytuje kontrolu syntaxe kompilaci, statické zadáním a podporu technologie IntelliSense pro [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]Můžete také použít k dotazu přes data, která byla konsolidována z jednoho nebo více zdrojů dat. To umožňuje mnoho scénářů, které vyžadují flexibilitu při fungování reprezentované a zpracovat data. Obecné sestavy, analýzu a aplikace pro business intelligence klást tato metoda manipulaci.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>Dotazování datové sady pomocí LINQ na DataSet  
 Před zahájením dotazování <xref:System.Data.DataSet> pomocí [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], musí naplnit <xref:System.Data.DataSet>. Načtení dat do několika způsoby <xref:System.Data.DataSet>, například pomocí <xref:System.Data.Common.DataAdapter> třídy nebo [technologie LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md). Jakmile jsou data načtená do <xref:System.Data.DataSet> objekt, můžete začít se dotaz. Formulování dotazy s [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] je podobný používání [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] proti dalších [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-povolené datové zdroje. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]v jedné tabulky je adresovat dotazy <xref:System.Data.DataSet> nebo před více než jedné tabulky pomocí <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A> standardní operátory dotazu.  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]dotazy jsou podporovaná u zadali i netypová <xref:System.Data.DataSet> objekty. Pokud schéma <xref:System.Data.DataSet> je známý v době návrhu aplikace, zadaný <xref:System.Data.DataSet> se doporučuje. V zadaný <xref:System.Data.DataSet>, tabulky a řádky zadali členy pro jednotlivé sloupce, které usnadňuje dotazy jednodušší a srozumitelnější.  
  
 Kromě standardní operátory dotazu implementované v System.Core.dll [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] přidá několik <xref:System.Data.DataSet>-konkrétní rozšíření, které usnadňují dotazu přes sadu <xref:System.Data.DataRow> objekty. Tyto <xref:System.Data.DataSet>-konkrétní rozšíření zahrnují operátory pro porovnání pořadí řádků, jakož i metody, které poskytují přístup k hodnotám sloupce <xref:System.Data.DataRow>.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>Vícevrstvé aplikace a LINQ na DataSet  
 Vícevrstvé datové aplikace jsou zaměřené na data aplikací, které jsou rozdělené do několika logické vrstvy (nebo úrovně). Typická vícevrstvé aplikace obsahuje prezentační vrstvy, střední vrstvy a datové vrstvy. Rozdělení komponent aplikace do oddělených vrstev zvyšuje udržovatelnost a škálovatelnost aplikace. Další informace o vícevrstvých datových aplikací najdete v tématu [pracovat s datovými sadami ve vícevrstvých aplikacích](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).  
  
 Ve vícevrstvé aplikace <xref:System.Data.DataSet> se často používá ve střední vrstvě pro informace o mezipaměti pro webovou aplikaci. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Funkcích pro dotazování se implementuje pomocí metod rozšíření a rozšiřuje stávající 2.0 ADO.NET <xref:System.Data.DataSet>.  
  
## <a name="see-also"></a>Viz také  
 [Dotazování datové sady](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [Technologie LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
