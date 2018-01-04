---
title: Architektura technologie ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2916321ff51f335b40a2cc4eef90cdccdfc25bda
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="adonet-architecture"></a>Architektura technologie ADO.NET
Zpracování dat má tradičně účinné především založeného na připojení, dvouvrstvá modelu. Jako zpracování dat stále používá vícevrstvé architektury, jsou programátory přepnutí do odpojeného přístup zajistit lepší škálovatelnost pro své aplikace.  
  
## <a name="adonet-components"></a>Komponenty technologie ADO.NET  
 Dvě hlavní součásti [!INCLUDE[ado_orcas_long](../../../../includes/ado-orcas-long-md.md)] pro přístup k informacím a manipulace s daty, jsou [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelé dat a <xref:System.Data.DataSet>.  
  
### <a name="net-framework-data-providers"></a>Zprostředkovatelé dat .NET framework  
 Zprostředkovatelé dat .NET Framework jsou komponenty, které byly explicitně určené pro manipulaci s daty a rychlé dopředné, jen pro čtení přístup k datům. `Connection` Objekt zajišťuje připojení ke zdroji dat. `Command` Objektu umožňuje přístup k příkazům databázi vrátit data, měnit data, spuštění uložené procedury a odeslání nebo načíst informace o parametrech. `DataReader` Poskytuje datový proud dat ze zdroje dat s vysokým výkonem. Nakonec `DataAdapter` poskytuje most mezi `DataSet` objekt a zdroj dat. `DataAdapter` Používá `Command` objekty, které chcete spustit příkaz SQL ve zdroji dat pro obě zatížení `DataSet` s daty a sloučit změny, které byly provedeny k datům ve `DataSet` zpět do zdroje dat. Další informace najdete v tématu [zprostředkovatelé dat .NET Framework](../../../../docs/framework/data/adonet/data-providers.md) a [načtení a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md).  
  
### <a name="the-dataset"></a>Datové sady  
 Technologie ADO.NET `DataSet` explicitně slouží pro přístup k datům nezávislé na libovolný zdroj dat. V důsledku toho dá použít s několika a různé datové zdroje, použít s daty XML nebo použít ke správě dat místní aplikace. `DataSet` Obsahuje kolekci jednoho nebo více <xref:System.Data.DataTable> objektů, který se skládá z řádků a sloupců dat a také primární klíč, cizí klíč, omezení a vztah informace o datech v `DataTable` objekty. Další informace najdete v tématu [datové sady, DataTables a DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Následující diagram znázorňuje vztah mezi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat a `DataSet`.  
  
 ![Obrázek ADO.Net](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
Architektura technologie ADO.NET  
  
### <a name="choosing-a-datareader-or-a-dataset"></a>Výběr DataReader nebo datové sady  
 Pokud se rozhodnete, jestli by aplikace měla použít `DataReader` (najdete v části [načítání dat pomocí DataReader –](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)) nebo `DataSet` (najdete v části [datové sady, DataTables a DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)), zvažte typ Funkce, které vaše aplikace vyžaduje. Použití `DataSet` proveďte následující:  
  
-   Data místně v aplikaci do mezipaměti, aby je můžete používat. Pokud potřebujete přečtěte si výsledky dotazu, `DataReader` je vhodnější.  
  
-   Vzdálená data mezi vrstvami nebo z webové služby XML.  
  
-   Práce s daty dynamicky například vytvoření vazby na ovládací prvek Windows Forms nebo kombinace a související data z více zdrojů.  
  
-   Proveďte rozsáhlé zpracování dat bez nutnosti otevřít připojení ke zdroji dat, což uvolní připojení k jiné klienti používat.  
  
 Pokud nechcete, aby funkce poskytované službou `DataSet`, může zvýšit výkon vaší aplikace pomocí `DataReader` vrátit data způsobem dopředné, jen pro čtení. I když `DataAdapter` používá `DataReader` k vyplnění obsah `DataSet` (najdete v části [naplňování datové sady z modul DataAdapter](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)), pomocí `DataReader`, může zvýšit výkon, protože ušetříte paměť by být využívány službou `DataSet`a vyhnout se zpracování, který je nutný k vytvoření a vyplnění obsah `DataSet`.  
  
## <a name="linq-to-dataset"></a>LINQ na DataSet  
 LINQ na DataSet poskytuje možnosti dotazu a kompilaci typ kontroly nad daty, které jsou uložené v mezipaměti v objektu datové sady. Umožňuje psát dotazy v jednom jazyce vývoj rozhraní .NET Framework, jako je například C# nebo Visual Basic. Další informace najdete v tématu [LINQ na DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>Technologie LINQ to SQL  
 Technologie LINQ to SQL podporuje dotazy pro objektový model, který je namapovaný na datové struktury relační databáze bez použití zprostředkující konceptuálního modelu. Každá tabulka představuje samostatnou třídu úzce spojovacích objektový model schématu relační databáze. Technologie LINQ to SQL překládá dotazy language-integrated ve model objektu do jazyka Transact-SQL a odešle je do databáze pro provedení. Při databáze vrátí výsledky, znamená, že technologie LINQ to SQL výsledky zpět do objektů. Další informace najdete v tématu [technologie LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 Je určen ADO.NET Entity Framework a umožňuje vývojářům vytvářet aplikace přístup dat programování s koncepční aplikační model místo programování přímo proti schématu relační úložiště. Cílem je snížit množství kód a údržby, které jsou potřeba pro aplikace orientované na data. Další informace najdete v tématu [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
## <a name="wcf-data-services"></a>WCF Data Services  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]slouží k nasazení služeb dat na webu nebo v intranetu. Strukturovaná data jako entity a vztahy podle specifikací modelu Entity Data Model. Data pro tento model nasazení je adresovat pomocí standardní protokol HTTP. Další informace najdete v tématu [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="xml-and-adonet"></a>Soubor XML a ADO.NET  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]využívá power XML zajistit odpojené přístup k datům. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]byl navrženou ruční-na skladě s třídami XML v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]; obě jsou součástí jednoho systému.  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]a třídy XML v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sloučit v `DataSet` objektu. `DataSet` Možné naplnit dat z XML zdroje, ať už je do souboru nebo datový proud XML. `DataSet` Lze zapsat jako kompatibilní XML World Wide Web Consortium (W3C), která bude obsahovat schématem schématu definition language (XSD) schématu XML, bez ohledu na zdroji dat v `DataSet`. Z důvodu formát nativní serializace `DataSet` formátu XML, je vynikající střední pro přesun dat mezi vrstvami, což `DataSet` na optimální volbu pro kontext dat a schématu vzdálené komunikace do a z webové služby XML. Další informace najdete v tématu [XML – dokumenty a Data](../../../../docs/standard/data/xml/index.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
