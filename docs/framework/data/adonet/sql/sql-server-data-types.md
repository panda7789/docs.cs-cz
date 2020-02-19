---
title: Datové typy SQL Serveru a ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: f727c69b1dd5c23c6a89911005256de70255fd4c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452328"
---
# <a name="sql-server-data-types-and-adonet"></a>Datové typy SQL Serveru a ADO.NET
SQL Server a rozhraní .NET Framework jsou založeny na jiný typ systémy, které může způsobit ztrátu dat. Aby se zajistila integrita dat, .NET Framework Zprostředkovatel dat pro SQL Server (<xref:System.Data.SqlClient>) poskytují typové přístupové metody pro práci s SQL Server daty. Výčty v třídách <xref:System.Data.SqlDbType> lze použít k určení <xref:System.Data.SqlClient.SqlParameter> datových typů.  
  
 Další informace a tabulku, která popisuje mapování datových typů mezi SQL Server a .NET Framework datových typů naleznete v tématu [SQL Server mapování datových typů](../sql-server-data-type-mappings.md).  
  
 SQL Server 2008 zavádí nové datové typy, které jsou navržené tak, aby vyhovovaly obchodním potřebám pro práci s daty a časem, strukturovanými, částečně strukturovanými a nestrukturovanými daty. Ty jsou popsány v SQL Server 2008 Knihy online.  
  
 SQL Server datové typy, které jsou k dispozici pro použití ve vaší aplikaci, závisí na verzi SQL Server, kterou používáte. Další informace najdete v příslušné verzi SQL Server Knihy online v následující tabulce.  
  
 **Dokumentace SQL Serveru**  
  
1. [Datové typy (Transact-SQL)](/sql/t-sql/data-types/data-types-transact-sql)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [SqlTypes a datová sada](sqltypes-and-the-dataset.md)  
 Popisuje podporu typu pro `SqlTypes` v `DataSet`.  
  
 [Zpracování hodnot null](handling-null-values.md)  
 Ukazuje, jak pracovat s hodnotami null a s logikou se třemi hodnotami.  
  
 [Porovnání hodnoty GUID a uniqueidentifier](comparing-guid-and-uniqueidentifier-values.md)  
 Ukazuje, jak pracovat s hodnotami GUID a uniqueidentifier v SQL Server a .NET Framework.  
  
 [Kalendářní a časová data](date-and-time-data.md)  
 Popisuje způsob použití nových datových typů data a času zavedených v SQL Server 2008.  
  
 [Velké uživatelsky definované typy](large-udts.md)  
 Ukazuje, jak načíst data z velké hodnoty UDT představené v SQL Server 2008.  
  
 [Data XML na SQL Serveru](xml-data-in-sql-server.md)  
 Popisuje, jak pracovat s daty XML načtenými z SQL Server.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Data.DataSet>  
 Popisuje třídu `DataSet` a všechny její členy.  
  
 <xref:System.Data.SqlTypes>  
 Popisuje obor názvů `SqlTypes` a všechny jeho členy.  
  
 <xref:System.Data.SqlDbType>  
 Popisuje výčet `SqlDbType` a všechny jeho členy.  
  
 <xref:System.Data.DbType>  
 Popisuje výčet `DbType` a všechny jeho členy.  
  
## <a name="see-also"></a>Viz také

- [Mapování datových typů SQL Serveru](../sql-server-data-type-mappings.md)
- [Konfigurace parametrů a datové typy parametrů](../configuring-parameters-and-parameter-data-types.md)
- [Parametry s hodnotami v tabulkách](table-valued-parameters.md)
- [Binární a vysoké hodnoty na SQL Serveru](sql-server-binary-and-large-value-data.md)
- [Přehled ADO.NET](../ado-net-overview.md)
