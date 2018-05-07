---
title: Operace hromadného kopírování v systému SQL Server
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 87373f55181742a243c60bc4b471334535d88ff7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="bulk-copy-operations-in-sql-server"></a>Operace hromadného kopírování v systému SQL Server
Microsoft SQL Server obsahuje oblíbených nástroj příkazového řádku s názvem **bcp** pro rychle hromadné kopírování velkých souborů do tabulky a zobrazení databáze systému SQL Server. <xref:System.Data.SqlClient.SqlBulkCopy> Třída umožňuje zapisovat řešení spravovaného kódu, které poskytují podobné funkce. Existují další způsoby, jak načíst data do tabulky SQL Server (například příkazech INSERT), ale <xref:System.Data.SqlClient.SqlBulkCopy> nabízí výhodu významně zvýšit výkon nad nimi.  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> Třída slouží k zápisu dat pouze na tabulky serveru SQL Server. Ale zdroj dat není omezený na SQL Server; lze použít libovolný zdroj dat, dokud k můžete načíst data <xref:System.Data.DataTable> instance nebo pro čtení s <xref:System.Data.IDataReader> instance.  
  
 Pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídu, můžete provést:  
  
-   Jeden hromadné operace kopírování  
  
-   Více operace hromadného kopírování  
  
-   Operace hromadného kopírování v rámci transakce.  
  
> [!NOTE]
>  Při použití rozhraní .NET Framework verze 1.1 nebo starší (který nepodporuje <xref:System.Data.SqlClient.SqlBulkCopy> třída), můžete spustit SQL Server Transact-SQL **BULK INSERT** příkaz pomocí <xref:System.Data.SqlClient.SqlCommand> objekt.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Příklad nastavení hromadného kopírování](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 Popisuje tabulky použité v ukázkách hromadné kopírování a poskytuje skripty SQL pro vytvoření tabulky v databázi AdventureWorks.  
  
 [Jednorázové operace hromadného kopírování](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 Popisuje, jak provést jedné hromadné kopírování dat do instance systému SQL Server pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy a jak provádět hromadné kopírování pomocí příkazů Transact-SQL a <xref:System.Data.SqlClient.SqlCommand> třídy.  
  
 [Vícečetné operace hromadného kopírování](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 Popisuje, jak provést několik operace hromadného kopírování dat do instance systému SQL Server pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy.  
  
 [Operace transakcí a hromadného kopírování](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 Popisuje, jak provádět operace hromadného kopírování v rámci transakce, včetně postup potvrzení nebo vrácení transakce.  
  
## <a name="see-also"></a>Viz také  
 [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
