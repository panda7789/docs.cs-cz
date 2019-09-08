---
title: Adaptéry a čtečky dat
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 20c6d514e70d2e4db451e0fff02e72688bf7d0ba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786647"
---
# <a name="dataadapters-and-datareaders"></a>Adaptéry a čtečky dat
Pomocí objektu **DataReader** ADO.NET můžete načíst proud dat pouze pro čtení z databáze. Výsledky jsou vraceny při spuštění dotazu a jsou uloženy v síťové vyrovnávací paměti klienta, dokud je nepožadujete pomocí metody **Read** objektu **DataReader**. Použití objektu **DataReader** může zvýšit výkon aplikace načtením dat, jakmile jsou k dispozici, a (ve výchozím nastavení) ukládat pouze jeden řádek v čase paměti a snížit zatížení systému.  
  
 Slouží k načtení dat ze zdroje dat a naplnění tabulek <xref:System.Data.DataSet>v rámci. <xref:System.Data.Common.DataAdapter> Také řeší změny provedené v `DataSet` zpátky na zdroj dat. `DataAdapter` Používá objekt poskytovatele .NET Framework dat pro připojení ke zdroji dat a používá `Command` objekty k načtení dat z a řešení změn ve zdroji dat. `Connection` `DataAdapter`  
  
 Každý .NET Framework poskytovatel dat, který je součástí .NET Framework, <xref:System.Data.Common.DbDataReader> má <xref:System.Data.Common.DbDataAdapter> a a objekt: .NET Framework <xref:System.Data.OleDb.OleDbDataReader> zprostředkovatel dat pro <xref:System.Data.OleDb.OleDbDataAdapter> OLE DB obsahuje objekt a, .NET Framework Zprostředkovatel dat pro SQL. Server obsahuje <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlDataAdapter> objekt a a .NET Framework <xref:System.Data.Odbc.OdbcDataReader> zprostředkovatel dat pro <xref:System.Data.Odbc.OdbcDataAdapter> rozhraní ODBC obsahuje objekt a a .NET Framework Zprostředkovatel dat pro Oracle zahrnuje <xref:System.Data.OracleClient.OracleDataReader> a. <xref:System.Data.OracleClient.OracleDataAdapter> objekt.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Načítání dat pomocí čtečky dat](retrieving-data-using-a-datareader.md)  
 Popisuje objekt **DataReader** ADO.NET a jeho použití k vrácení datového proudu výsledků ze zdroje dat.  
  
 [Naplnění datové sady z adaptéru dat](populating-a-dataset-from-a-dataadapter.md)  
 Popisuje, jak vyplnit `DataSet` tabulky, sloupce a řádky pomocí tabulek, sloupců a řádků. `DataAdapter`  
  
 [Parametry adaptéru dat](dataadapter-parameters.md)  
 Popisuje, jak použít parametry s vlastnostmi `DataAdapter` příkazu, včetně způsobu mapování obsahu sloupce `DataSet` v nástroji na parametr příkazu.  
  
 [Přidání existujících omezení do datové sady](adding-existing-constraints-to-a-dataset.md)  
 Popisuje, jak přidat existující omezení do `DataSet`.  
  
 [Mapování adaptéru dat, datové tabulky a datového sloupce](dataadapter-datatable-and-datacolumn-mappings.md)  
 Popisuje, jak nastavit `DataTableMappings` a `ColumnMappings` pro `DataAdapter`.  
  
 [Stránkování prostřednictvím výsledku dotazu](paging-through-a-query-result.md)  
 Poskytuje příklad zobrazení výsledků dotazu jako stránek dat.  
  
 [Aktualizace zdrojů dat pomocí adaptérů dat](updating-data-sources-with-dataadapters.md)  
 Popisuje, jak použít `DataAdapter` k vyřešení změn `DataSet` v databázi.  
  
 [Zpracování událostí adaptéru dat](handling-dataadapter-events.md)  
 Popisuje `DataAdapter` události a jejich použití.  
  
 [Provádění dávkových operací pomocí adaptérů dat](performing-batch-operations-using-dataadapters.md)  
 Popisuje zvýšení výkonu aplikace tím, že omezuje počet přenosů, které se SQL Server při aplikování `DataSet`aktualizací z.  
  
## <a name="see-also"></a>Viz také:

- [Připojení ke zdroji dat](connecting-to-a-data-source.md)
- [Příkazy a parametry](commands-and-parameters.md)
- [Transakce a souběžnost](transactions-and-concurrency.md)
- [Datové sady, datové tabulky a datová zobrazení](./dataset-datatable-dataview/index.md)
- [Přehled ADO.NET](ado-net-overview.md)
