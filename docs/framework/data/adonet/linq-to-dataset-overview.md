---
title: Přehled LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: de49febdc81eaf4f487423c5804d1e5cc897cdce
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794961"
---
# <a name="linq-to-dataset-overview"></a>Přehled LINQ to DataSet
<xref:System.Data.DataSet> Je jednou z široce používaných komponent ADO.NET. Je klíčovým prvkem odpojeného programovacího modelu, na kterém je ADO.NET založen, a umožňuje explicitně ukládat data z různých zdrojů dat do mezipaměti. Pro prezentační vrstvu <xref:System.Data.DataSet> je pro datovou vazbu úzce integrovaná s ovládacími prvky grafického uživatelského rozhraní. V případě střední vrstvy poskytuje mezipaměť, která zachovává relační tvar dat, a zahrnuje rychlé jednoduché navigační služby dotazů a hierarchií. Běžnou technikou pro snížení počtu požadavků na databázi je použití <xref:System.Data.DataSet> pro ukládání do mezipaměti v prostřední vrstvě. Zvažte například webovou aplikaci ASP.NET řízená daty. Často se podstatná část dat aplikace nemění často a je společná napříč relacemi nebo uživateli. Tato data je možné uchovávat v paměti na webovém serveru, což snižuje počet požadavků na databázi a urychluje interakce uživatele. Dalším užitečným aspektem <xref:System.Data.DataSet> je, že aplikace umožňuje přenést podmnožiny dat z jednoho nebo více zdrojů dat do prostoru aplikace. Aplikace pak může manipulovat s daty v paměti a přitom zachovat relační tvar.  
  
 Bez ohledu na <xref:System.Data.DataSet> jeho význačnost má aplikace omezené možnosti dotazování. Metodu lze použít pro filtrování a řazení <xref:System.Data.DataRow.GetChildRows%2A> a metody a <xref:System.Data.DataRow.GetParentRow%2A> lze použít pro navigaci v hierarchii. <xref:System.Data.DataTable.Select%2A> Pro něco složitějšího, ale vývojář musí napsat vlastní dotaz. To může mít za následek nedostatečně náročné aplikace a jejich údržbu.  
  
 LINQ to DataSet usnadňuje a urychlují dotazování na data uložená v <xref:System.Data.DataSet> objektu. Tyto dotazy jsou vyjádřeny v samotném programovacím jazyce, nikoli jako řetězcové literály vložené v kódu aplikace. To znamená, že vývojáři se nemusí učit o samostatném dotazovacímu jazyku. Kromě toho LINQ to DataSet umožňuje vývojářům sady Visual Studio pracovat častěji, protože integrované vývojové prostředí (IDE) sady Visual Studio poskytuje kontrolu syntaxe v době kompilace, statické typování a [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]podporu technologie IntelliSense pro. LINQ to DataSet lze také použít k dotazování na data, která byla konsolidována z jednoho nebo více zdrojů dat. Díky tomu je možné mnoha scénářů, které vyžadují flexibilitu při reprezentaci a zpracování dat. Tato metoda manipulace vyžaduje zejména obecné vytváření sestav, analýzy a business intelligence aplikace.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>Dotazování na datové sady pomocí LINQ to DataSet  
 Předtím, než můžete začít s dotazem na <xref:System.Data.DataSet> objekt pomocí LINQ to DataSet, je nutné <xref:System.Data.DataSet>vyplnit. Existuje několik způsobů <xref:System.Data.DataSet>, jak načíst data do, jako je například <xref:System.Data.Common.DataAdapter> použití třídy nebo [LINQ to SQL](./sql/linq/index.md). Po načtení dat do <xref:System.Data.DataSet> objektu je můžete začít dotazovat. Formulace dotazů pomocí LINQ to DataSet je podobná [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] použití s [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]jinými zdroji dat s podporou. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]dotazy mohou být provedeny pro jednotlivé tabulky v <xref:System.Data.DataSet> nebo proti více než jedné tabulce <xref:System.Linq.Enumerable.Join%2A> pomocí operátorů dotazů standard <xref:System.Linq.Enumerable.GroupJoin%2A> a.  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]dotazy jsou podporovány pro typové i netypové <xref:System.Data.DataSet> objekty. Pokud <xref:System.Data.DataSet> je schéma systému známo v době návrhu aplikace, je doporučeno zadat <xref:System.Data.DataSet> typ. V zadaném <xref:System.Data.DataSet>typu tabulky a řádky obsahují členy pro každý ze sloupců, které zjednodušují a čitelnější dotazy.  
  
 Kromě standardních operátorů dotazu implementovaných v System. Core. dll LINQ to DataSet přidává několik <xref:System.Data.DataSet>specifických rozšíření, která usnadňují dotazování nad <xref:System.Data.DataRow> sadou objektů. Tato <xref:System.Data.DataSet>rozšíření zahrnují operátory pro porovnávání sekvencí řádků a také metody, které poskytují přístup k hodnotám <xref:System.Data.DataRow>sloupců v.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>N-vrstvé aplikace a LINQ to DataSet  
 N-vrstvé datové aplikace jsou aplikace zaměřené na data, které jsou rozdělené do několika logických vrstev (nebo vrstev). Typická N-vrstvá aplikace zahrnuje prezentační vrstvu, střední vrstvu a datovou vrstvu. Rozdělení komponent aplikace do oddělených vrstev zvyšuje udržovatelnost a škálovatelnost aplikace. Další informace o N-vrstvých datových aplikacích naleznete v tématu [práce s datovými sadami v n-vrstvých aplikacích](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
 V N-vrstvých aplikacích <xref:System.Data.DataSet> se často používá v prostřední vrstvě k ukládání informací do mezipaměti pro webovou aplikaci. LINQ to DataSet funkce dotazování je implementována prostřednictvím rozšiřujících metod a rozšiřuje stávající ADO.NET 2,0 <xref:System.Data.DataSet>.  
  
## <a name="see-also"></a>Viz také:

- [Dotazy na datové sady](querying-datasets-linq-to-dataset.md)
- [LINQ (Language-Integrated Query) –C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (Language-Integrated Query) – Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](./sql/linq/index.md)
