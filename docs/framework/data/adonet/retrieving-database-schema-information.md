---
title: Načítání informací o databázovém schématu
ms.date: 03/30/2017
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
ms.openlocfilehash: 26b234e35a0d0849914d87b61f4e8c8a87599448
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782739"
---
# <a name="retrieving-database-schema-information"></a>Načítání informací o databázovém schématu
Získání informací o schématu z databáze je provedeno procesem zjišťování schématu. Zjišťování schématu umožňuje aplikacím požádat, aby se spravované zprostředkovatele vyhledali a vraceli informace o schématu databáze, označované také jako *metadata*dané databáze. Různé prvky schématu databáze, jako jsou tabulky, sloupce a uložené procedury, se zveřejňují prostřednictvím kolekcí schémat. Každá kolekce schémat obsahuje nejrůznější informace o schématu specifické pro používaného poskytovatele.  
  
 Každé z .NET Framework spravovaných zprostředkovatelů implementuje ve třídě **Connection** metodu **GetSchema** a informace o schématu vrácené z metody **GetSchema** jsou <xref:System.Data.DataTable>v podobě. Metoda **GetSchema** je přetížená metoda, která poskytuje volitelné parametry pro určení kolekce schématu, která se má vrátit, a omezení množství vrácených informací.  
  
 Poskytovatelé dat .NET Framework pro OLE DB, ODBC, Oracle a SqlClient poskytují metodu **GetSchema** , která vrací objekt DataTable popisující metadata sloupce **DataReader**.  
  
 Zprostředkovatel dat .NET Framework pro OLE DB také zpřístupňuje informace o schématu pomocí <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> metody <xref:System.Data.OleDb.OleDbConnection> objektu. Jako argumenty **GetOleDbSchemaTable** přebírá <xref:System.Data.OleDb.OleDbSchemaGuid> , který identifikuje informace o schématu, které se mají vrátit, a pole omezení u těchto vrácených sloupců. **GetOleDbSchemaTable** vrátí hodnotu <xref:System.Data.DataTable> , která je vyplněna požadovanými informacemi o schématu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Příkaz GetSchema a kolekce schémat](getschema-and-schema-collections.md)  
 Popisuje metodu **GetSchema** a způsob, jak ji lze použít k načtení a omezení informací o schématu z databáze.  
  
 Omezení schématu  
 Popisuje omezení schématu, která lze použít s **GetSchema**.  
  
 [Společné kolekce schémat](common-schema-collections.md)  
 Popisuje všechny společné kolekce schémat podporované všemi .NET Framework spravovanými zprostředkovateli.  
  
 [Kolekce schémat SQL Serveru](sql-server-schema-collections.md)  
 Popisuje kolekci schémat podporovanou poskytovatelem .NET Framework pro SQL Server.  
  
 [Kolekce schémat Oracle](oracle-schema-collections.md)  
 Popisuje kolekci schémat podporovanou poskytovatelem .NET Framework pro Oracle.  
  
 [Kolekce schémat ODBC](odbc-schema-collections.md)  
 Popisuje kolekce schémat pro ovladače rozhraní ODBC.  
  
 [Kolekce schémat OLE DB](ole-db-schema-collections.md)  
 Popisuje kolekce schémat pro poskytovatele OLE DB.  
  
## <a name="reference"></a>Reference  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 Popisuje <xref:System.Data.Common.DbConnection> metodu **GetSchema** třídy.  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 Popisuje <xref:System.Data.Odbc.OdbcConnection> metodu **GetSchema** třídy.  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 Popisuje <xref:System.Data.OleDb.OleDbConnection> metodu **GetSchema** třídy.  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 Popisuje <xref:System.Data.OracleClient.OracleConnection> metodu **GetSchema** třídy.  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 Popisuje <xref:System.Data.SqlClient.SqlConnection> metodu **GetSchema** třídy.  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 Popisuje <xref:System.Data.Common.DbDataReader> metodu **GetSchema** třídy třídy.  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 Popisuje <xref:System.Data.Odbc.OdbcDataReader> metodu **GetSchema** třídy třídy.  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 Popisuje <xref:System.Data.OleDb.OleDbDataReader> metodu **GetSchema** třídy třídy.  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 Popisuje <xref:System.Data.OracleClient.OracleDataReader> metodu **GetSchema** třídy třídy.  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 Popisuje <xref:System.Data.SqlClient.SqlDataReader> metodu **GetSchema** třídy třídy.  
  
## <a name="see-also"></a>Viz také:

- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)
- [Přehled ADO.NET](ado-net-overview.md)
