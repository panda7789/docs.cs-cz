---
title: "Načítání informací o schématu databáze"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 71493eb91415b5f4695e771c7a549244629bb654
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-database-schema-information"></a>Načítání informací o schématu databáze
Získání informací o schématu z databáze se provádí v procesu zjišťování schématu. Schéma zjišťování umožňuje aplikacím požádá spravovaného zprostředkovatele najít a vrátí informace o schématu databáze, také známé jako *metadata*, dané databáze. Prvky schématu jiné databázi, například tabulky, sloupce a uložených procedur se zveřejňují přes kolekcemi schémat. Každá kolekce schéma obsahuje celou řadu specifické pro použitý zprostředkovatel informace o schématu.  
  
 Každý z implementace spravovaných zprostředkovatelé rozhraní .NET Framework **GetSchema** metoda v **připojení** třídy a informace o schématu, která je vrácena z **GetSchema**metoda obsahuje ve formě <xref:System.Data.DataTable>. **GetSchema** metoda je přetížené metody, která poskytuje volitelné parametry pro zadání kolekce schémat vrátit a omezení množství vrácených informací.  
  
 Zadejte zprostředkovatele dat .NET Framework pro OLE DB, rozhraní ODBC, Oracle a SqlClient **GetSchemaTable** metodu, která vrátí DataTable popisující sloupce metadata **DataReader –**.  
  
 Zprostředkovatel dat .NET Framework pro OLE DB také zveřejňuje informace o schématu pomocí <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> metodu <xref:System.Data.OleDb.OleDbConnection> objektu. Jako argumenty **Metoda GetOleDbSchemaTable** trvá <xref:System.Data.OleDb.OleDbSchemaGuid> identifikující informace o schématu vrátit, a pole omezení pro ty vrácení sloupce. **Metoda GetOleDbSchemaTable** vrátí <xref:System.Data.DataTable> naplněn informacemi požadovaný schématu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [GetSchema a kolekcemi schémat](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 Popisuje **GetSchema** metoda a jak může sloužit k načtení a omezit informace o schématu z databáze.  
  
 Omezení schématu  
 Popisuje schéma omezení, které lze použít s **GetSchema**.  
  
 [Společné schéma kolekce](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 Popisuje všechny společné schéma kolekce nepodporuje všech zprostředkovatelů spravované rozhraní .NET Framework.  
  
 [Kolekcemi schémat serveru SQL](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 Popisuje kolekci schémat podporována zprostředkovatelem rozhraní .NET Framework pro SQL Server.  
  
 [Kolekce schématu Oracle](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 Popisuje kolekci schémat podporována zprostředkovatelem rozhraní .NET Framework pro Oracle.  
  
 [Kolekce schématu rozhraní ODBC](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 Popisuje kolekcemi schémat ovladačů ODBC.  
  
 [Kolekcemi schémat OLE DB](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 Popisuje kolekcemi schémat pro zprostředkovatele OLE DB.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Načítání a upravovat Data v technologii ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
