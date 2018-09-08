---
title: Přehled LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: 43c3aa081bd934202bd3a7831741054115d7a6d5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44138809"
---
# <a name="linq-to-dataset-overview"></a>Přehled LINQ to DataSet
<xref:System.Data.DataSet> Je jedním z více široce používané komponenty [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Je klíčovým prvkem odpojeném programovací model, který [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] vychází z, a umožňuje explicitně mezipaměti dat z různých datových zdrojů. Pro prezentační vrstvy <xref:System.Data.DataSet> je úzce integrovaná s ovládacími prvky grafického uživatelského rozhraní pro datovou vazbu. Poskytuje mezipaměť, která zachová tvar relační data a zahrnuje rychle jednoduchý dotaz a služby navigační hierarchie pro střední vrstvy. Běžná technika umožňuje snížit počet požadavků na databázi, které se má používat <xref:System.Data.DataSet> pro ukládání do mezipaměti ve střední vrstvě. Představte si třeba řízené daty [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webovou aplikaci. Podstatnou část dat aplikace často nemění příliš často a je společná pro relace nebo uživatelů. Tato data může být uložený v paměti na webovém serveru, která omezuje počet požadavků na databázi a zrychluje interakcí uživatele. Dalším užitečným aspektem <xref:System.Data.DataSet> patří povolení aplikace tak, aby podmnožiny dat z jednoho nebo více zdroje dat do prostoru aplikace. Aplikace pak můžete pracovat s na data v paměti, a přitom zachovat jeho tvar relační.  
  
 Bez ohledu na jeho význačnost <xref:System.Data.DataSet> má omezené možnosti dotazu. <xref:System.Data.DataTable.Select%2A> Metodu můžete použít pro filtrování a řazení a <xref:System.Data.DataRow.GetChildRows%2A> a <xref:System.Data.DataRow.GetParentRow%2A> metody lze použít pro navigační hierarchie. Pro všechno, co složitější ale vývojář musí napsat vlastní dotaz. Výsledkem může být aplikace, které jejich zpracování zhoršilo a je obtížné udržovat.  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zajišťuje snadnější a rychlejší dotaz data uložená v mezipaměti <xref:System.Data.DataSet> objektu. Tyto dotazy jsou vyjádřeny v programovacím jazyce, nikoli jako řetězce literálů vložené do kódu aplikace. To znamená, že vývojáři nemají další samostatné dotazovací jazyk. Kromě toho [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] umožňuje vývojářům sady Visual Studio více produktivně pracovat, protože rozhraní IDE sady Visual Studio poskytuje kontrola syntaxe v době kompilace, statické psát a podporu technologie IntelliSense pro [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Můžete také použít k dotazu nad daty, který byl sloučen z jednoho nebo více zdrojů dat. To umožňuje mnoho scénářů, které potřebují flexibilně fungování reprezentované a zpracovat data. Tato metoda manipulaci s vyžadují zejména obecné vytváření sestav, analýzy a v aplikacích business intelligence.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>Dotazy na datové sady pomocí LINQ to DataSet  
 Před zahájením dotazování <xref:System.Data.DataSet> pomocí [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], musíte vyplnit <xref:System.Data.DataSet>. Existuje několik způsobů, jak načíst data do <xref:System.Data.DataSet>, jako je třeba použití <xref:System.Data.Common.DataAdapter> třídy nebo [technologie LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md). Po načtení dat do <xref:System.Data.DataSet> objektu, můžete začít dotazovat ji. Formulování dotazy s [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] podobá se to používání [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] proti jiné [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]– povolené zdroje. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazy lze provést na jedné tabulky v <xref:System.Data.DataSet> nebo před více než jednu tabulku s použitím <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A> standardních operátorů pro dotazování.  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazy jsou podporovány vůči typu a netypová <xref:System.Data.DataSet> objekty. Pokud schéma <xref:System.Data.DataSet> je znám v době návrhu aplikace, typovaného <xref:System.Data.DataSet> se doporučuje. V typovaného <xref:System.Data.DataSet>, tabulek a řádků zadali členy pro jednotlivé sloupce, které provádí dotazy, jednodušší a lépe čitelný.  
  
 Kromě standardních dotazovacích operátorů, implementovat v System.Core.dll [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] přidá několik <xref:System.Data.DataSet>-konkrétní rozšíření, které usnadňují dotazu přes sadu <xref:System.Data.DataRow> objekty. Tyto <xref:System.Data.DataSet>-konkrétní rozšíření zahrnují operátory pro porovnání sekvence řádků, stejně jako metody, které poskytují přístup k hodnoty sloupce <xref:System.Data.DataRow>.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>N-vrstvé aplikace a LINQ to DataSet  
 Vícevrstvé datové aplikace jsou datově orientovaných aplikací, které jsou rozdělené do několika logické vrstvy (nebo úrovní). Typická N-vrstvá aplikace obsahuje prezentační vrstvu, střední vrstvu a datovou vrstvu. Rozdělení komponent aplikace do oddělených vrstev zvyšuje udržovatelnost a škálovatelnost aplikace. Další informace o vícevrstvých datových aplikací najdete v tématu [práce s datovými sadami ve vícevrstvých aplikacích](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
 V N-vrstvé aplikace <xref:System.Data.DataSet> se často používá ve střední vrstvě pro informace o mezipaměti pro webové aplikace. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Funkcích pro dotazování se implementuje pomocí metod rozšíření a rozšiřuje stávající 2.0 ADO.NET <xref:System.Data.DataSet>.  
  
## <a name="see-also"></a>Viz také  
 [Dotazy na datové sady](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
