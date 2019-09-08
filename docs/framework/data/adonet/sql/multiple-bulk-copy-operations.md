---
title: Vícečetné operace hromadného kopírování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: 838f56311f165c99c71cc734576bbdb53a946b7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792063"
---
# <a name="multiple-bulk-copy-operations"></a>Vícečetné operace hromadného kopírování
Můžete provést více operací hromadného kopírování pomocí jediné instance <xref:System.Data.SqlClient.SqlBulkCopy> třídy. Pokud se parametry operace mění mezi kopiemi (například názvem cílové tabulky), je nutné je aktualizovat před jakýmkoli následným voláním libovolné metody **WriteToServer** , jak je znázorněno v následujícím příkladu. Pokud se explicitně nezmění, všechny hodnoty vlastností zůstanou stejné jako u předchozí operace hromadného kopírování pro danou instanci.  
  
> [!NOTE]
> Provádění více operací hromadného kopírování pomocí stejné instance <xref:System.Data.SqlClient.SqlBulkCopy> je obvykle efektivnější než použití samostatné instance pro každou operaci.  
  
 Pokud provedete několik operací hromadného kopírování pomocí <xref:System.Data.SqlClient.SqlBulkCopy> stejného objektu, neexistují žádná omezení na to, zda jsou informace o zdroji nebo cíli v každé operaci stejné nebo jiné. Je však nutné zajistit, aby informace o přidružení sloupce byly správně nastaveny při každém zápisu na server.  
  
> [!IMPORTANT]
> Tato ukázka nebude spuštěna, pokud jste nevytvořili pracovní tabulky, jak je popsáno v tématu [hromadné kopírování – příklad nastavení](bulk-copy-example-setup.md). Tento kód je k dispozici k předvedení syntaxe pouze pro použití **SqlBulkCopy** . Pokud se zdrojové a cílové tabulky nacházejí ve stejné instanci SQL Server, je snazší a rychlejší použít příkaz Transact-SQL `INSERT … SELECT` ke zkopírování dat.  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Operace hromadného kopírování na SQL Serveru](bulk-copy-operations-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
