---
title: Operace hromadného kopírování na SQL Serveru
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 086b3b997cf0915be7cfa603a651eb412d52e985
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194796"
---
# <a name="bulk-copy-operations-in-sql-server"></a>Operace hromadného kopírování na SQL Serveru
Microsoft SQL Server obsahuje oblíbené nástroje příkazového řádku s názvem **bcp** pro rychle hromadné kopírování velkých souborů do tabulky a zobrazení v databázích systému SQL Server. <xref:System.Data.SqlClient.SqlBulkCopy> Třída umožňuje zapisovat spravovaného kódu řešení, která poskytuje podobné funkce. Existují jiné způsoby, jak načíst data do tabulky SQL serveru (například příkazy INSERT), ale <xref:System.Data.SqlClient.SqlBulkCopy> nabízí výhody výkonu nad nimi.  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> Třídy lze použít k zápisu dat jenom do tabulek systému SQL Server. Ale není omezena pouze na serveru SQL Server; zdroj dat můžete použít libovolný zdroj dat, za předpokladu, data je možné načíst do <xref:System.Data.DataTable> instance nebo si přečtěte s <xref:System.Data.IDataReader> instance.  
  
 Použití <xref:System.Data.SqlClient.SqlBulkCopy> třídy, můžete provést:  
  
-   Jeden hromadného kopírování  
  
-   Vícečetné operace hromadného kopírování  
  
-   Operaci hromadného kopírování v rámci transakce  
  
> [!NOTE]
>  Při použití rozhraní .NET Framework verze 1.1 nebo starší (což není podporováno <xref:System.Data.SqlClient.SqlBulkCopy> třídy), můžete spustit SQL Server Transact-SQL **BULK INSERT** pomocí příkazu <xref:System.Data.SqlClient.SqlCommand> objektu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Příklad nastavení hromadného kopírování](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 Popisuje tabulky používané v příkladech hromadného kopírování a obsahuje skripty SQL pro vytváření tabulek v databázi AdventureWorks.  
  
 [Jednorázové operace hromadného kopírování](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 Popisuje, jak provést jedné hromadné kopírování dat do instance SQL serveru pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy a jak provádět operaci hromadného kopírování pomocí příkazů jazyka Transact-SQL a <xref:System.Data.SqlClient.SqlCommand> třídy.  
  
 [Vícečetné operace hromadného kopírování](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 Popisuje, jak provést vícečetné operace hromadného kopírování dat do instance SQL serveru pomocí <xref:System.Data.SqlClient.SqlBulkCopy> třídy.  
  
 [Operace transakcí a hromadného kopírování](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 Popisuje, jak provést operaci hromadného kopírování v rámci transakce, včetně jak potvrzení nebo vrácení transakce.  
  
## <a name="see-also"></a>Viz také:

- [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
