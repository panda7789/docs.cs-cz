---
title: SQL Server Data typy a ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 878bbe41f259f1e50cd0a41669c7a352e78bc0f1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44221581"
---
# <a name="sql-server-data-types-and-adonet"></a>SQL Server Data typy a ADO.NET
SQL Server a rozhraní .NET Framework jsou založeny na jiný typ systémy, které může způsobit ztrátu dat. K zachování integrity dat, zprostředkovatele dat .NET Framework pro SQL Server (<xref:System.Data.SqlClient>) poskytuje typy přístupové metody pro práci s daty formátu SQL Server. Výčty v můžete použít <xref:System.Data.SqlDbType> třídy k určení <xref:System.Data.SqlClient.SqlParameter> datové typy.  
  
 Další informace a tabulky, které popisuje data zadejte mapování mezi SQL serverem a datové typy rozhraní .NET Framework najdete v tématu [mapování datového typu SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).  
  
 SQL Server 2008 zavádí nové datové typy, které jsou určeny k uspokojení potřeb pro práci s datem a časem, strukturovaná, částečně strukturovaná a Nestrukturovaná data. Ty jsou popsány v SQL Server 2008 Books Online.  
  
 Datové typy serveru SQL Server, které jsou k dispozici pro použití ve vaší aplikaci, závisí na verzi systému SQL Server, který používáte. Další informace najdete v příslušné verzi SQL Server Books Online v následující tabulce.  
  
 **SQL Server Books Online**  
  
1.  [Datové typy (databázový stroj)](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [SqlTypes a datová sada](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 Popisuje podporu typu `SqlTypes` v `DataSet`.  
  
 [Zpracování hodnot null](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 Ukazuje, jak pracovat s hodnotami null a s hodnotou tři logiku.  
  
 [Porovnání hodnoty GUID a uniqueidentifier](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 Ukazuje, jak pracovat s identifikátorem GUID a uniqueidentifier hodnotami v systému SQL Server a rozhraní .NET Framework.  
  
 [Kalendářní a časová data](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 Popisuje, jak použít nové typy dat data a času zavedena v systému SQL Server 2008.  
  
 [Velké uživatelsky definované typy](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 Ukazuje, jak načíst data z velké hodnoty uživatelsky definované typy zavedena v systému SQL Server 2008.  
  
 [Data XML na SQL Serveru](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 Popisuje, jak pracovat s XML dat načtených z SQL serveru.  
  
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
 [Mapování datových typů SQL Serveru](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Konfigurace parametrů a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Parametry s hodnotami v tabulkách](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)  
 [Binární a vysoké hodnoty na SQL Serveru](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
