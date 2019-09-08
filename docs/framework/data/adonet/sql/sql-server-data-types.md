---
title: Datové typy SQL Serveru a ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 642fe0d541aca01d6ffb2d9279c4d0fa91eadb63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780849"
---
# <a name="sql-server-data-types-and-adonet"></a>Datové typy SQL Serveru a ADO.NET
SQL Server a rozhraní .NET Framework jsou založeny na jiný typ systémy, které může způsobit ztrátu dat. Aby se zajistila integrita dat, poskytuje .NET Framework Zprostředkovatel dat<xref:System.Data.SqlClient>pro SQL Server () typové přístupové metody pro práci s SQL Servermi daty. Můžete použít výčty ve <xref:System.Data.SqlDbType> třídách k určení <xref:System.Data.SqlClient.SqlParameter> datových typů.  
  
 Další informace a tabulku, která popisuje mapování datových typů mezi SQL Server a .NET Framework datových typů naleznete v tématu [SQL Server mapování datových typů](../sql-server-data-type-mappings.md).  
  
 SQL Server 2008 zavádí nové datové typy, které jsou navržené tak, aby vyhovovaly obchodním potřebám pro práci s daty a časem, strukturovanými, částečně strukturovanými a nestrukturovanými daty. Ty jsou popsány v SQL Server 2008 Knihy online.  
  
 SQL Server datové typy, které jsou k dispozici pro použití ve vaší aplikaci, závisí na verzi SQL Server, kterou používáte. Další informace najdete v příslušné verzi SQL Server Knihy online v následující tabulce.  
  
 **SQL Server Books Online**  
  
1. [Datové typy (databázový stroj)](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [SqlTypes a datová sada](sqltypes-and-the-dataset.md)  
 Popisuje podporu typu pro `SqlTypes` `DataSet`v.  
  
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
  
## <a name="reference"></a>Reference  
 <xref:System.Data.DataSet>  
 `DataSet` Popisuje třídu a všechny její členy.  
  
 <xref:System.Data.SqlTypes>  
 `SqlTypes` Popisuje obor názvů a všechny jeho členy.  
  
 <xref:System.Data.SqlDbType>  
 `SqlDbType` Popisuje výčet a všechny jeho členy.  
  
 <xref:System.Data.DbType>  
 `DbType` Popisuje výčet a všechny jeho členy.  
  
## <a name="see-also"></a>Viz také:

- [Mapování datových typů SQL Serveru](../sql-server-data-type-mappings.md)
- [Konfigurace parametrů a datové typy parametrů](../configuring-parameters-and-parameter-data-types.md)
- [Parametry s hodnotami v tabulkách](table-valued-parameters.md)
- [Binární a vysoké hodnoty na SQL Serveru](sql-server-binary-and-large-value-data.md)
- [Přehled ADO.NET](../ado-net-overview.md)
