---
title: Přehled LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: dc20a8fb-03f6-4b68-9c2b-7f7299e3070b
ms.openlocfilehash: 20d9be052ba2567c16718b4b1c1019427c9b5df1
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634817"
---
# <a name="linq-to-dataset-overview"></a>Přehled LINQ to DataSet
<xref:System.Data.DataSet> je jednou z široce používaných komponent ADO.NET. Je klíčovým prvkem odpojeného programovacího modelu, na kterém je ADO.NET založen, a umožňuje explicitně ukládat data z různých zdrojů dat do mezipaměti. Pro prezentační vrstvu je <xref:System.Data.DataSet> úzce integrovaný s ovládacími prvky GUI pro datovou vazbu. V případě střední vrstvy poskytuje mezipaměť, která zachovává relační tvar dat, a zahrnuje rychlé jednoduché navigační služby dotazů a hierarchií. Běžnou technikou pro snížení počtu požadavků na databázi je použití <xref:System.Data.DataSet> pro ukládání do mezipaměti v prostřední vrstvě. Zvažte například webovou aplikaci ASP.NET řízená daty. Často se podstatná část dat aplikace nemění často a je společná napříč relacemi nebo uživateli. Tato data je možné uchovávat v paměti na webovém serveru, což snižuje počet požadavků na databázi a urychluje interakce uživatele. Dalším užitečným aspektem <xref:System.Data.DataSet> je to, že aplikace umožňuje přenést podmnožiny dat z jednoho nebo více zdrojů dat do prostoru aplikace. Aplikace pak může manipulovat s daty v paměti a přitom zachovat relační tvar.  
  
 <xref:System.Data.DataSet> má bez ohledu na své význačnost možnosti dotazů. Metodu <xref:System.Data.DataTable.Select%2A> lze použít pro filtrování a řazení a metody <xref:System.Data.DataRow.GetChildRows%2A> a <xref:System.Data.DataRow.GetParentRow%2A> lze použít pro navigaci v hierarchii. Pro něco složitějšího, ale vývojář musí napsat vlastní dotaz. To může mít za následek nedostatečně náročné aplikace a jejich údržbu.  
  
 LINQ to DataSet usnadňuje a urychlují dotaz na data uložená v mezipaměti v objektu <xref:System.Data.DataSet>. Tyto dotazy jsou vyjádřeny v samotném programovacím jazyce, nikoli jako řetězcové literály vložené v kódu aplikace. To znamená, že vývojáři se nemusí učit o samostatném dotazovacímu jazyku. Kromě toho LINQ to DataSet umožňuje vývojářům sady Visual Studio pracovat častěji, protože integrované vývojové prostředí (IDE) sady Visual Studio poskytuje kontrolu syntaxe v době kompilace, statické typování a podporu technologie IntelliSense pro LINQ. LINQ to DataSet lze také použít k dotazování na data, která byla konsolidována z jednoho nebo více zdrojů dat. Díky tomu je možné mnoha scénářů, které vyžadují flexibilitu při reprezentaci a zpracování dat. Tato metoda manipulace vyžaduje zejména obecné vytváření sestav, analýzy a business intelligence aplikace.  
  
## <a name="querying-datasets-using-linq-to-dataset"></a>Dotazování na datové sady pomocí LINQ to DataSet  
 Než začnete s dotazem na objekt <xref:System.Data.DataSet> pomocí LINQ to DataSet, je nutné naplnit <xref:System.Data.DataSet>. Existuje několik způsobů, jak načíst data do <xref:System.Data.DataSet>, jako je například použití třídy <xref:System.Data.Common.DataAdapter> nebo [LINQ to SQL](./sql/linq/index.md). Po načtení dat do objektu <xref:System.Data.DataSet> můžete začít dotazovat. Formulace dotazů pomocí LINQ to DataSet je podobná použití LINQ (Language-Integrated Query) pro jiné zdroje dat s podporou LINQ. Dotazy LINQ lze provádět v rámci jednoduchých tabulek v <xref:System.Data.DataSet> nebo proti více než jedné tabulce pomocí standardních operátorů dotazu <xref:System.Linq.Enumerable.Join%2A> a <xref:System.Linq.Enumerable.GroupJoin%2A>.  
  
 Dotazy LINQ jsou podporovány proti typovým i netypovým <xref:System.Data.DataSet>m objektům. Pokud je schéma <xref:System.Data.DataSet> známo v době návrhu aplikace, je doporučena typová <xref:System.Data.DataSet>. V zadaném <xref:System.Data.DataSet>tabulky a řádky zadávané členy pro každý sloupec, což usnadňuje čtení dotazů a jejich snadnější čitelnost.  
  
 Kromě standardních operátorů dotazu implementovaných v System. Core. dll LINQ to DataSet přidává několik rozšíření specifických pro <xref:System.Data.DataSet>, které usnadňuje dotazování nad sadou objektů <xref:System.Data.DataRow>. Tato rozšíření specifická pro <xref:System.Data.DataSet>zahrnují operátory pro porovnávání sekvencí řádků a také metody, které poskytují přístup k hodnotám sloupců <xref:System.Data.DataRow>.  
  
## <a name="n-tier-applications-and-linq-to-dataset"></a>N-vrstvé aplikace a LINQ to DataSet  
 N-vrstvé datové aplikace jsou aplikace zaměřené na data, které jsou rozdělené do několika logických vrstev (nebo vrstev). Typická N-vrstvá aplikace zahrnuje prezentační vrstvu, střední vrstvu a datovou vrstvu. Rozdělení komponent aplikace do oddělených vrstev zvyšuje udržovatelnost a škálovatelnost aplikace. Další informace o N-vrstvých datových aplikacích naleznete v tématu [práce s datovými sadami v n-vrstvých aplikacích](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).  
  
 V N-vrstvých aplikacích se <xref:System.Data.DataSet> často používá k ukládání informací do mezipaměti pro webovou aplikaci v prostřední vrstvě. LINQ to DataSet funkce dotazování je implementována prostřednictvím rozšiřujících metod a rozšiřuje stávající <xref:System.Data.DataSet>ADO.NET 2,0.  
  
## <a name="see-also"></a>Viz také:

- [Dotazy na datové sady](querying-datasets-linq-to-dataset.md)
- [LINQ (Language-Integrated Query) –C#](../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (Language-Integrated Query) – Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ to SQL](./sql/linq/index.md)
