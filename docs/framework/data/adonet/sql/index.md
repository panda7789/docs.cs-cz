---
title: SQL Server a ADO.NET
description: Přečtěte si o funkcích a chování .NET Framework Zprostředkovatel dat pro SQL Server, které zapouzdřují protokoly pro konkrétní databáze.
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: eeb0ab69a68dfc2fc0faa1b4e833f80b307fffe5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286440"
---
# <a name="sql-server-and-adonet"></a>SQL Server a ADO.NET
Tato část popisuje funkce a chování, které jsou specifické pro .NET Framework Zprostředkovatel dat pro SQL Server ( <xref:System.Data.SqlClient> ).  
  
 <xref:System.Data.SqlClient>poskytuje přístup k verzím SQL Server, které zapouzdřují protokoly pro konkrétní databáze. Funkce poskytovatele dat je navržena tak, aby byla podobná poskytovateli .NET Framework dat pro OLE DB, ODBC a Oracle. <xref:System.Data.SqlClient>zahrnuje analyzátor TDS (Tabular data Stream), který komunikuje přímo s SQL Server.  
  
> [!NOTE]
> Chcete-li použít Zprostředkovatel dat .NET Framework pro SQL Server, aplikace musí odkazovat na <xref:System.Data.SqlClient> obor názvů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [SQL Server – zabezpečení](sql-server-security.md)  
 Poskytuje přehled SQL Serverch funkcí zabezpečení a scénářů aplikací pro vytváření zabezpečených aplikací ADO.NET, které cílí na SQL Server.  
  
 [Datové typy SQL Serveru a ADO.NET](sql-server-data-types.md)  
 Popisuje, jak pracovat s datovými typy SQL Server a jak komunikují s datovými typy .NET Framework.  
  
 [Binární a vysoké hodnoty na SQL Serveru](sql-server-binary-and-large-value-data.md)  
 Popisuje, jak pracovat s velkým množstvím dat v SQL Server.  
  
 [Operace dat na SQL Serveru v ADO.NET](sql-server-data-operations.md)  
 Popisuje, jak pracovat s daty v SQL Server. Obsahuje oddíly o operacích hromadného kopírování, MARS, asynchronních operací a parametrech s hodnotou tabulky.  
  
 [Funkce SQL Serveru a ADO.NET](sql-server-features-and-adonet.md)  
 Popisuje SQL Server funkce, které jsou užitečné pro vývojáře aplikací ADO.NET.  
  
 [Technologie LINQ to SQL](./linq/index.md)  
 V této části najdete popis základních stavebních bloků, procesů a technik potřebných pro vytváření aplikací LINQ to SQL.  
  
 Úplnou dokumentaci k databázovému stroji SQL Server najdete v tématu SQL Server Knihy online pro verzi SQL Server, kterou používáte.  
  
 [SQL Server Knihy online](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení aplikací ADO.NET](../securing-ado-net-applications.md)
- [Mapování datového typu v ADO.NET](../data-type-mappings-in-ado-net.md)
- [Datové sady, datové tabulky a datová zobrazení](../dataset-datatable-dataview/index.md)
- [Načítání a úpravy dat v ADO.NET](../retrieving-and-modifying-data.md)
- [Přehled ADO.NET](../ado-net-overview.md)
