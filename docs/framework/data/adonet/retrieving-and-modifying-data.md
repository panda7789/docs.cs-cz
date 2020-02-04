---
title: Načítání a úpravy dat
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: 65c373ecff004e219527754bf2e9cc56837dc305
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980051"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Načítání a úpravy dat v ADO.NET
Primární funkce libovolné databázové aplikace se připojuje ke zdroji dat a načítá data, která obsahuje. Poskytovatelé dat .NET Framework ADO.NET slouží jako most mezi aplikací a zdrojem dat, což umožňuje provádět příkazy a také načítat data pomocí datového typu **DataReader** nebo **DataAdapter**. Klíčovou funkcí libovolné databázové aplikace je možnost aktualizovat data uložená v databázi. Aktualizace dat v ADO.NET zahrnuje použití příkazů **DataAdapter** a <xref:System.Data.DataSet>a objektů **příkazu** ; a může také zahrnovat použití transakcí.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Připojení ke zdroji dat](connecting-to-a-data-source.md)  
 Popisuje, jak navázat připojení ke zdroji dat a jak pracovat s událostmi připojení.  
  
 [Připojovací řetězce](connection-strings.md)  
 Obsahuje témata popisující různé aspekty použití připojovacích řetězců, včetně klíčových slov připojovacích řetězců, bezpečnostních údajů a jejich ukládání a načítání.  
  
 [Sdružování připojení](connection-pooling.md)  
 Popisuje sdružování připojení pro poskytovatele .NET Framework dat.  
  
 [Příkazy a parametry](commands-and-parameters.md)  
 Obsahuje témata popisující, jak vytvořit příkazy a tvůrci příkazů, nakonfigurovat parametry a spustit příkazy pro načtení a úpravu dat.  
  
 [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)  
 Obsahuje témata popisující datačtecí a dataadaptéry, parametry, zpracování událostí DataAdapter a provádění operací Batch.  
  
 [Transakce a souběžnost](transactions-and-concurrency.md)  
 Obsahuje témata popisující, jak provádět místní transakce, distribuované transakce a pracovat s optimistické souběžnosti.  
  
 [Načítání hodnot identity nebo automatického číslování](retrieving-identity-or-autonumber-values.md)  
 Poskytuje příklad mapování hodnot generovaných pro sloupec **identity** v SQL Server tabulce nebo pro pole **AutoNumber** v tabulce Microsoft Access, do sloupce vloženého řádku v tabulce. Popisuje sloučení hodnot identity v `DataTable`.  
  
 [Načítání binárních dat](retrieving-binary-data.md)  
 Popisuje, jak načíst binární data nebo velké datové struktury pomocí `CommandBehavior`.`SequentialAccess` Chcete-li změnit výchozí chování `DataReader`.  
  
 [Úpravy dat pomocí uložených procedur](modifying-data-with-stored-procedures.md)  
 Popisuje způsob použití vstupních parametrů a výstupních parametrů uložených procedur pro vložení řádku do databáze a vrácení nové hodnoty identity.  
  
 [Načítání informací o databázovém schématu](retrieving-database-schema-information.md)  
 Popisuje, jak získat dostupné databáze nebo katalogy, tabulky a zobrazení v databázi, omezeních, která existují pro tabulky, a další informace o schématu ze zdroje dat.  
  
 [DbProviderFactories](dbproviderfactories.md)  
 Popisuje model továrny poskytovatele a ukazuje, jak používat základní třídy v oboru názvů `System.Data.Common`.  
  
 [Trasování data v ADO.NET](data-tracing.md)  
 Popisuje, jak ADO.NET poskytuje integrovanou funkci pro trasování dat.  
  
 [Čítače výkonu](performance-counters.md)  
 Popisuje čítače výkonu dostupné pro `SqlClient` a `OracleClient`.  
  
 [Asynchronní programování](asynchronous-programming.md)  
 Popisuje podporu ADO.NET pro asynchronní programování.  
  
 [Podpora streamování SqlClient](sqlclient-streaming-support.md)  
 Popisuje, jak psát aplikace, které streamují data z SQL Server bez toho, aby byla plně načtena v paměti.  
  
## <a name="see-also"></a>Viz také:

- [Mapování datového typu v ADO.NET](data-type-mappings-in-ado-net.md)
- [Datové sady, datové tabulky a datová zobrazení](./dataset-datatable-dataview/index.md)
- [Zabezpečení aplikací ADO.NET](securing-ado-net-applications.md)
- [SQL Server a ADO.NET](./sql/index.md)
- [Přehled ADO.NET](ado-net-overview.md)
