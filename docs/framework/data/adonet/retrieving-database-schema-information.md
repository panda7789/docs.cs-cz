---
title: Načítání informací o databázovém schématu
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 885d3c9ad61c9099c960ddb0c0f77fa8a98dbefa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133702"
---
# <a name="retrieving-database-schema-information"></a>Načítání informací o databázovém schématu
Získání informací o schématu z databáze se provádí v procesu zjišťování schématu. Zjišťování schématu umožňuje aplikacím vyžadovat, že spravovaného poskytovatele vyhledání a vrácení informací o schématu databáze, označované také jako *metadat*, dané databáze. Prvky schématu jinou databázi, jako například tabulky, sloupce a uložené procedury jsou přístupné prostřednictvím kolekce schémat. Každá kolekce schématu obsahuje širokou škálu informací o schématu specifické pro použitý zprostředkovatel.  
  
 Každá implementace spravovaného zprostředkovatele .NET Framework **GetSchema** metoda ve **připojení** třídy a informace o schématu, která je vrácena z **GetSchema**metoda je k dispozici ve formě <xref:System.Data.DataTable>. **GetSchema** je metoda přetížená metoda, která poskytuje volitelných parametrů pro určení kolekce schématu pro vrácení a omezit množství vrácených informací.  
  
 Zprostředkovatelé dat .NET Framework pro OLE DB, ODBC, Oracle a SqlClient poskytují **GetSchemaTable** metodu, která vrací objekt DataTable popisující sloupce metadat **DataReader**.  
  
 Zprostředkovatel dat .NET Framework pro OLE DB také poskytuje informace o schématu pomocí <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> metodu <xref:System.Data.OleDb.OleDbConnection> objektu. Jako argumenty **Metoda GetOleDbSchemaTable** přebírá <xref:System.Data.OleDb.OleDbSchemaGuid> , který identifikuje vrátí informace o schématu, a vrátí pole omezení toho, které sloupce. **Metoda GetOleDbSchemaTable** vrátí <xref:System.Data.DataTable> načtou informace požadované schéma.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Příkaz GetSchema a kolekce schémat](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 Popisuje **GetSchema** metoda a jak ho lze načíst a omezit informace o schématu z databáze.  
  
 Omezení schématu  
 Popisuje omezení schématu, které lze použít s **GetSchema**.  
  
 [Společné kolekce schémat](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 Popisuje všechny společné kolekce schémat všech zprostředkovatelů spravovaným rozhraním .NET Framework podporován.  
  
 [Kolekce schémat SQL Serveru](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 Popisuje kolekci schémat zprostředkovatelem rozhraní .NET Framework pro SQL Server podporována.  
  
 [Kolekce schémat Oracle](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 Popisuje kolekci schémat zprostředkovatelem rozhraní .NET Framework pro Oracle podporována.  
  
 [Kolekce schémat ODBC](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 Popisuje kolekce schémat pro ovladače ODBC.  
  
 [Kolekce schémat OLE DB](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 Popisuje kolekce schémat pro zprostředkovatele OLE DB.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 Popisuje **GetSchema** metodu <xref:System.Data.Common.DbConnection> třídy.  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 Popisuje **GetSchema** metodu <xref:System.Data.Odbc.OdbcConnection> třídy.  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 Popisuje **GetSchema** metodu <xref:System.Data.OleDb.OleDbConnection> třídy.  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 Popisuje **GetSchema** metodu <xref:System.Data.OracleClient.OracleConnection> třídy.  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 Popisuje **GetSchema** metodu <xref:System.Data.SqlClient.SqlConnection> třídy.  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 Popisuje **GetSchemaTable** metodu <xref:System.Data.Common.DbDataReader> třídy.  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 Popisuje **GetSchemaTable** metodu <xref:System.Data.Odbc.OdbcDataReader> třídy.  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 Popisuje **GetSchemaTable** metodu <xref:System.Data.OleDb.OleDbDataReader> třídy.  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 Popisuje **GetSchemaTable** metodu <xref:System.Data.OracleClient.OracleDataReader> třídy.  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 Popisuje **GetSchemaTable** metodu <xref:System.Data.SqlClient.SqlDataReader> třídy.  
  
## <a name="see-also"></a>Viz také:

- [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
