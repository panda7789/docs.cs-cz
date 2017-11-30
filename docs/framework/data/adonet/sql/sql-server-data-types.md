---
title: Data serveru SQL typy a ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 16c675491a378d72d82a252d79a73379f494893c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-data-types-and-adonet"></a>Data serveru SQL typy a ADO.NET
SQL Server a rozhraní .NET Framework jsou založené na jiný typ systémy, které může mít za následek ztrátu dat. Chcete-li zachovat integritu dat, zprostředkovatel dat .NET Framework pro SQL Server (<xref:System.Data.SqlClient>) poskytuje typu přístupového objektu metody pro práci s daty na serveru SQL. Můžete použít výčtů ve <xref:System.Data.SqlDbType> třídy k určení <xref:System.Data.SqlClient.SqlParameter> datové typy.  
  
 Další informace a tabulky, které popisuje data zadáte mapování mezi datové typy rozhraní .NET Framework a SQL Server najdete v tématu [mapování datového typu SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).  
  
 SQL Server 2008 zavádí nové typy dat, které jsou navržené tak, abyste splnili obchodní požadavky pro práci s datum a čas, strukturovaná, částečně strukturovaná i nestrukturovaná data. Ty jsou popsány v SQL Server 2008 Books Online.  
  
 Datové typy systému SQL Server, které jsou k dispozici pro použití ve vaší aplikaci závisí na verzi systému SQL Server, který používáte. Další informace najdete v tématu příslušné verze SQL Server Books Online v následující tabulce.  
  
 **SQL Server Books Online**  
  
1.  [Datové typy (databázový stroj)](http://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [SqlTypes a datové sady](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 Popisuje typ podporu pro `SqlTypes` v `DataSet`.  
  
 [Zpracování hodnot Null](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 Ukazuje, jak pracovat s hodnotami null a s hodnotou tři logiku.  
  
 [Porovnáním různých GUID a hodnoty uniqueidentifier](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 Ukazuje, jak pracovat s hodnotami GUID a uniqueidentifier v systému SQL Server a rozhraní .NET Framework.  
  
 [Datum a čas dat](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 Popisuje postup použití nových typech dat Datum a čas byla zavedená v systému SQL Server 2008.  
  
 [Velké UDT](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 Ukazuje, jak k načtení dat z velké hodnoty UDT byla zavedená v systému SQL Server 2008.  
  
 [Data XML v systému SQL Server](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 Popisuje, jak pracovat s daty XML načíst ze serveru SQL.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Data.DataSet>  
 Popisuje `DataSet` třídy a všechny její členy.  
  
 <xref:System.Data.SqlTypes>  
 Popisuje `SqlTypes` obor názvů a všechny její členy.  
  
 <xref:System.Data.SqlDbType>  
 Popisuje `SqlDbType` výčet a všechny její členy.  
  
 <xref:System.Data.DbType>  
 Popisuje `DbType` výčet a všechny její členy.  
  
## <a name="see-also"></a>Viz také  
 [Mapování datového typu SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Konfigurace parametrů a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Parametry s hodnotou tabulky](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)  
 [Binární a velké hodnoty dat systému SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
