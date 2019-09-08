---
title: Operace hromadného kopírování na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: ae97bcdd6776d573cf9e523133c2c00a42c273bb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782524"
---
# <a name="bulk-copy-operations-in-sql-server"></a>Operace hromadného kopírování na SQL Serveru
Microsoft SQL Server obsahuje oblíbený nástroj příkazového řádku s názvem **BCP** pro rychlé hromadné kopírování velkých souborů do tabulek nebo zobrazení v databázích SQL Server. <xref:System.Data.SqlClient.SqlBulkCopy> Třída umožňuje psát řešení spravovaného kódu, která poskytují podobné funkce. Existují i další způsoby, jak načíst data do SQL Server tabulky (například příkazy INSERT), ale <xref:System.Data.SqlClient.SqlBulkCopy> v nich nabízí významné výhody výkonu.  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> Třídu lze použít k zápisu dat pouze do SQL Server tabulek. Ale zdroj dat není omezen na SQL Server; můžete použít jakýkoliv zdroj dat, pokud data lze načíst do <xref:System.Data.DataTable> instance nebo číst <xref:System.Data.IDataReader> s instancí.  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> Pomocí třídy můžete provádět následující akce:  
  
- Jedna operace hromadného kopírování  
  
- Více operací hromadného kopírování  
  
- Operace hromadného kopírování v rámci transakce  
  
> [!NOTE]
> Při použití .NET Framework verze 1,1 nebo starší (která <xref:System.Data.SqlClient.SqlBulkCopy> třídu nepodporuje) můžete spustit příkaz SQL Server Transact-SQL **Bulk INSERT** pomocí <xref:System.Data.SqlClient.SqlCommand> objektu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Příklad nastavení hromadného kopírování](bulk-copy-example-setup.md)  
 Popisuje tabulky používané v ukázkách hromadného kopírování a poskytuje skripty SQL pro vytváření tabulek v databázi AdventureWorks.  
  
 [Jednorázové operace hromadného kopírování](single-bulk-copy-operations.md)  
 Popisuje, jak provést jednu hromadnou kopii dat do instance SQL Server pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy a jak provést operaci hromadného kopírování s použitím příkazů jazyka Transact-SQL <xref:System.Data.SqlClient.SqlCommand> a třídy.  
  
 [Vícečetné operace hromadného kopírování](multiple-bulk-copy-operations.md)  
 Popisuje, jak provést více operací hromadného kopírování dat do instance SQL Server pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy.  
  
 [Operace transakcí a hromadného kopírování](transaction-and-bulk-copy-operations.md)  
 Popisuje, jak provést operaci hromadného kopírování v rámci transakce, včetně toho, jak transakci potvrdit nebo vrátit zpět.  
  
## <a name="see-also"></a>Viz také:

- [SQL Server a ADO.NET](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
