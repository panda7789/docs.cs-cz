---
title: "Načítání a upravovat Data v technologii ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 4ea157cd52bf92dace924baaa40f5b1bba6f13a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Načítání a upravovat Data v technologii ADO.NET
Primární funkce jakékoli aplikace, databáze je připojení ke zdroji dat a načítání dat, který ji obsahuje. Zprostředkovatele dat .NET Framework technologie ADO.NET sloužit jako most mezi aplikace a zdroj dat, což umožňuje provést příkazy také o načtení dat pomocí **DataReader –** nebo **DataAdapter** . Klíčové funkce jakékoli aplikace, databáze, je schopnost aktualizovat data, která je uložená v databázi. V technologii ADO.NET, aktualizace dat zahrnuje použití **DataAdapter** a <xref:System.Data.DataSet>, a **příkaz** objekty; a může zahrnovat také pomocí transakce.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 Popisuje, jak vytvořit připojení ke zdroji dat a jak pracovat s události připojení.  
  
 [Připojovací řetězce](../../../../docs/framework/data/adonet/connection-strings.md)  
 Obsahuje témata s popisem různé aspekty použití řetězců připojení, včetně klíčová slova řetězec připojení, bezpečnostní údaje a ukládání a načítání je.  
  
 [Sdružování připojení](../../../../docs/framework/data/adonet/connection-pooling.md)  
 Popisuje sdružování připojení pro poskytovatele dat .NET Framework.  
  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 Obsahuje témata s popisem vytváření příkazů a příkaz počítačů, nakonfigurujte parametry a postup provedení příkazu k načtení a upravovat data.  
  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 Obsahuje témata s popisem DataReaders, DataAdapters, parametry, zpracování událostí DataAdapter a provádění dávkových operací.  
  
 [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 Obsahuje témata popisující, jak provádět místní transakce, distribuovaných transakcí a pracovat s optimistickou metodu souběžného.  
  
 [Načítání hodnot identity nebo automatického číslování](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 Poskytuje příklad mapování hodnoty vygenerované **identity** sloupec v [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] tabulky, nebo **automatické číslování** pole v tabulce Microsoft Access ke sloupci vloženého řádku v tabulce. Popisuje slučovat hodnoty identity v `DataTable`.  
  
 [Načítání binárních dat](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 Popisuje, jak získat binární data nebo velkého množství dat struktur pomocí `CommandBehavior`.`SequentialAccess` Chcete-li změnit výchozí chování `DataReader`.  
  
 [Úpravy dat pomocí uložených procedur](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 Popisuje způsob používání vstupních parametrů uložené procedury a výstupní parametry vložit řádek v databázi, vrátí novou hodnotu identity.  
  
 [Načítání informací o databázovém schématu](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 Popisuje, jak získat dostupné databáze nebo katalogů, tabulky a zobrazení v databázi, omezení, která platí pro tabulky a další informace o schématu ze zdroje dat.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Popisuje model objektu pro vytváření zprostředkovatele a ukazuje, jak používat základní třídy v `System.Data.Common` oboru názvů.  
  
 [Trasování data v ADO.NET](../../../../docs/framework/data/adonet/data-tracing.md)  
 Popisuje, jak technologie ADO.NET poskytuje funkce integrované data trasování.  
  
 [Čítače výkonu](../../../../docs/framework/data/adonet/performance-counters.md)  
 Popisuje čítače výkonu, které jsou k dispozici pro `SqlClient` a `OracleClient`.  
  
 [Asynchronní programování](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 Popisuje [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] podporu pro asynchronní programování.  
  
 [Podpora streamování SqlClient](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 Popisuje, jak psát aplikace, které data z datového proudu [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] bez nutnosti, je plně načten do paměti.  
  
## <a name="see-also"></a>Viz také  
 [Mapování datového typu v ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server a ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
