---
title: Adaptéry a čtečky dat
description: Přečtěte si o DataReader ADO.NET, který načte data z databáze a generuje data ze zdroje dat a naplní datovou sadu.
ms.date: 03/30/2017
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
ms.openlocfilehash: 17463d65266baa53521bed9603c8abd96923277b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286970"
---
# <a name="dataadapters-and-datareaders"></a>Adaptéry a čtečky dat
Pomocí objektu **DataReader** ADO.NET můžete načíst proud dat pouze pro čtení z databáze. Výsledky jsou vraceny při spuštění dotazu a jsou uloženy v síťové vyrovnávací paměti klienta, dokud je nepožadujete pomocí metody **Read** objektu **DataReader**. Použití objektu **DataReader** může zvýšit výkon aplikace načtením dat, jakmile jsou k dispozici, a (ve výchozím nastavení) ukládat pouze jeden řádek v čase paměti a snížit zatížení systému.  
  
 <xref:System.Data.Common.DataAdapter>Slouží k načtení dat ze zdroje dat a naplnění tabulek v rámci <xref:System.Data.DataSet> . `DataAdapter`Také řeší změny provedené v `DataSet` zpátky na zdroj dat. `DataAdapter`Používá `Connection` objekt poskytovatele .NET Framework dat pro připojení ke zdroji dat a používá `Command` objekty k načtení dat z a řešení změn ve zdroji dat.  
  
 Každý .NET Framework poskytovatel dat, který je součástí .NET Framework, má <xref:System.Data.Common.DbDataReader> a a <xref:System.Data.Common.DbDataAdapter> objekt: .NET Framework Zprostředkovatel dat pro OLE DB obsahuje <xref:System.Data.OleDb.OleDbDataReader> objekt a <xref:System.Data.OleDb.OleDbDataAdapter> , .NET Framework Zprostředkovatel dat pro SQL Server obsahuje <xref:System.Data.SqlClient.SqlDataReader> objekt a <xref:System.Data.SqlClient.SqlDataAdapter> , .NET Framework Zprostředkovatel dat pro rozhraní ODBC <xref:System.Data.Odbc.OdbcDataReader> <xref:System.Data.Odbc.OdbcDataAdapter> <xref:System.Data.OracleClient.OracleDataReader> <xref:System.Data.OracleClient.OracleDataAdapter> obsahuje objekt a a .NET Framework Zprostředkovatel dat pro Oracle obsahuje objekt a.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Načítání dat pomocí čtečky dat](retrieving-data-using-a-datareader.md)  
 Popisuje objekt **DataReader** ADO.NET a jeho použití k vrácení datového proudu výsledků ze zdroje dat.  
  
 [Naplnění datové sady z adaptéru dat](populating-a-dataset-from-a-dataadapter.md)  
 Popisuje, jak vyplnit `DataSet` tabulky, sloupce a řádky pomocí tabulek, sloupců a řádků `DataAdapter` .  
  
 [Parametry adaptéru dat](dataadapter-parameters.md)  
 Popisuje, jak použít parametry s vlastnostmi příkazu, `DataAdapter` včetně způsobu mapování obsahu sloupce v nástroji `DataSet` na parametr příkazu.  
  
 [Přidání existujících omezení do datové sady](adding-existing-constraints-to-a-dataset.md)  
 Popisuje, jak přidat existující omezení do `DataSet` .  
  
 [Mapování adaptéru dat, datové tabulky a datového sloupce](dataadapter-datatable-and-datacolumn-mappings.md)  
 Popisuje, jak nastavit `DataTableMappings` a `ColumnMappings` pro `DataAdapter` .  
  
 [Stránkování prostřednictvím výsledku dotazu](paging-through-a-query-result.md)  
 Poskytuje příklad zobrazení výsledků dotazu jako stránek dat.  
  
 [Aktualizace zdrojů dat pomocí adaptérů dat](updating-data-sources-with-dataadapters.md)  
 Popisuje, jak použít `DataAdapter` k vyřešení změn v `DataSet` databázi.  
  
 [Zpracování událostí adaptéru dat](handling-dataadapter-events.md)  
 Popisuje `DataAdapter` události a jejich použití.  
  
 [Provádění dávkových operací pomocí adaptérů dat](performing-batch-operations-using-dataadapters.md)  
 Popisuje zvýšení výkonu aplikace tím, že omezuje počet přenosů, které se SQL Server při aplikování aktualizací z `DataSet` .  
  
## <a name="see-also"></a>Viz také

- [Připojení ke zdroji dat](connecting-to-a-data-source.md)
- [Příkazy a parametry](commands-and-parameters.md)
- [Transakce a souběžnost](transactions-and-concurrency.md)
- [Datové sady, datové tabulky a datová zobrazení](./dataset-datatable-dataview/index.md)
- [Přehled ADO.NET](ado-net-overview.md)
