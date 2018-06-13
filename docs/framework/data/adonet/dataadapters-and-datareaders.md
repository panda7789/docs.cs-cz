---
title: DataAdapters a DataReaders
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 7fd7013478bbf30c2a7e915045e3dd192ca92540
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758097"
---
# <a name="dataadapters-and-datareaders"></a>DataAdapters a DataReaders
Můžete použít technologie ADO.NET **DataReader** načíst jen pro čtení, dopředné datový proud z databáze. Výsledky se vrátí jako dotazu se provede a jsou uložené ve vyrovnávací paměti sítě na straně klienta, dokud na žádost uživatele pomocí **čtení** metodu **DataReader –**. Pomocí **DataReader** může zvýšit výkon aplikace načtením dat, jakmile je k dispozici i (ve výchozím nastavení) ukládání pouze jeden řádek v daný okamžik v paměti a snižuje zátěž systému.  
  
 A <xref:System.Data.Common.DataAdapter> slouží k načtení dat ze zdroje dat a naplnění tabulky v rámci <xref:System.Data.DataSet>. `DataAdapter` Rovněž řeší změny provedené `DataSet` zpět do zdroje dat. `DataAdapter` Používá `Connection` objekt zprostředkovatel dat .NET Framework pro připojení ke zdroji dat a používá `Command` objekty, které chcete načíst data ze a odkazující na zdroj dat změny.  
  
 Má každý zprostředkovatel dat .NET Framework je součástí rozhraní .NET Framework <xref:System.Data.Common.DbDataReader> a <xref:System.Data.Common.DbDataAdapter> objektu: Zprostředkovatel dat .NET Framework pro OLE DB zahrnuje <xref:System.Data.OleDb.OleDbDataReader> a <xref:System.Data.OleDb.OleDbDataAdapter> objekt, zprostředkovatel dat .NET Framework pro SQL Server obsahuje <xref:System.Data.SqlClient.SqlDataReader> a <xref:System.Data.SqlClient.SqlDataAdapter> objektu, zahrnuje zprostředkovatel dat .NET Framework pro ODBC <xref:System.Data.Odbc.OdbcDataReader> a <xref:System.Data.Odbc.OdbcDataAdapter> objekt a zprostředkovatel dat .NET Framework pro Oracle zahrnuje <xref:System.Data.OracleClient.OracleDataReader> a <xref:System.Data.OracleClient.OracleDataAdapter> objektu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Načítání dat pomocí čtečky dat](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 Popisuje technologie ADO.NET **DataReader** objekt a způsobu jeho použití vrátit datový proud výsledků ze zdroje dat.  
  
 [Naplnění datové sady z adaptéru dat](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 Popisuje, jak k vyplnění `DataSet` tabulky, sloupce a řádky pomocí `DataAdapter`.  
  
 [Parametry adaptéru dat](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 Popisuje, jak používat parametry se příkaz Vlastnosti `DataAdapter` včetně postup mapování obsahu sloupce v `DataSet` pro parametr příkazu.  
  
 [Přidání existujících omezení do datové sady](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 Popisuje, jak přidat do existující omezení `DataSet`.  
  
 [Mapování adaptéru dat, datové tabulky a datového sloupce](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 Popisuje, jak nastavit `DataTableMappings` a `ColumnMappings` pro `DataAdapter`.  
  
 [Stránkování prostřednictvím výsledku dotazu](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 Poskytuje příklad zobrazení jako stránky s daty výsledků dotazu.  
  
 [Aktualizace zdrojů dat pomocí adaptérů dat](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 Popisuje způsob použití `DataAdapter` změny v řešení `DataSet` zpět do databáze.  
  
 [Zpracování událostí adaptéru dat](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 Popisuje `DataAdapter` událostí a jejich použití.  
  
 [Provádění dávkových operací pomocí adaptérů dat](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 Popisuje zlepšení výkonu aplikací, protože se sníží počet zpátečních cest k systému SQL Server při použití aktualizací z `DataSet`.  
  
## <a name="see-also"></a>Viz také  
 [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
