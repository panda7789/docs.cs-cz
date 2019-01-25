---
title: Adaptéry a čtečky dat
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: f4588187aad910d0b50b0c804e6de20a477b567b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583506"
---
# <a name="dataadapters-and-datareaders"></a>Adaptéry a čtečky dat
Můžete použít ADO.NET **DataReader** načíst jen pro čtení, dopředné datový proud s daty z databáze. Výsledky se vrátí jako dotaz spustí a jsou uloženy v síti vyrovnávací paměti na straně klienta, dokud si je vyžádat použití **čtení** metodu **DataReader**. Použití **DataReader** může zvýšit výkon aplikace, tak načítání dat, jako je k dispozici i (ve výchozím nastavení) ukládání pouze jeden řádek v daný okamžik v paměti a snížení režie systému.  
  
 A <xref:System.Data.Common.DataAdapter> slouží k načtení dat ze zdroje dat a naplnění tabulky v rámci <xref:System.Data.DataSet>. `DataAdapter` Také řeší změny provedené `DataSet` zpět do zdroje dat. `DataAdapter` Používá `Connection` objekt zprostředkovatele dat .NET Framework pro připojení ke zdroji dat a používá `Command` objekty k načtení dat z a řešení změn ke zdroji dat.  
  
 Má každý zprostředkovatele dat .NET Framework je součástí rozhraní .NET Framework <xref:System.Data.Common.DbDataReader> a <xref:System.Data.Common.DbDataAdapter> objektu: obsahuje zprostředkovatele dat .NET Framework pro OLE DB <xref:System.Data.OleDb.OleDbDataReader> a <xref:System.Data.OleDb.OleDbDataAdapter> objektu zprostředkovatele dat .NET Framework pro SQL Server obsahuje <xref:System.Data.SqlClient.SqlDataReader> a <xref:System.Data.SqlClient.SqlDataAdapter> objektu zprostředkovatele dat .NET Framework pro ODBC zahrnuje <xref:System.Data.Odbc.OdbcDataReader> a <xref:System.Data.Odbc.OdbcDataAdapter> objektu a zprostředkovatele dat .NET Framework pro Oracle zahrnuje <xref:System.Data.OracleClient.OracleDataReader> a <xref:System.Data.OracleClient.OracleDataAdapter> objektu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Načítání dat pomocí čtečky dat](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 Popisuje ADO.NET **DataReader** objekt a jak ji používat k vrátit datový proud výsledků ze zdroje dat.  
  
 [Naplnění datové sady z adaptéru dat](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 Popisuje, jak vyplnit `DataSet` s tabulkami, sloupci a řádky pomocí `DataAdapter`.  
  
 [Parametry adaptéru dat](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 Popisuje způsob použití parametrů pro příkaz Vlastnosti `DataAdapter` včetně postup mapování obsahu sloupce v `DataSet` parametru příkazu.  
  
 [Přidání existujících omezení do datové sady](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 Popisuje postup přidání existujících omezení `DataSet`.  
  
 [Mapování adaptéru dat, datové tabulky a datového sloupce](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 Popisuje, jak nastavit `DataTableMappings` a `ColumnMappings` pro `DataAdapter`.  
  
 [Stránkování prostřednictvím výsledku dotazu](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 Poskytuje příklad zobrazení výsledků dotazu jako stránky s daty.  
  
 [Aktualizace zdrojů dat pomocí adaptérů dat](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 Popisuje způsob použití `DataAdapter` změny v řešení `DataSet` zpět do databáze.  
  
 [Zpracování událostí adaptéru dat](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 Popisuje `DataAdapter` události a jejich použití.  
  
 [Provádění dávkových operací pomocí adaptérů dat](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 Popisuje zlepšení výkonu aplikací snížením počet zpátečních cest k serveru SQL Server, při použití aktualizací od `DataSet`.  
  
## <a name="see-also"></a>Viz také:
- [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [Datové sady, datové tabulky a datová zobrazení](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
