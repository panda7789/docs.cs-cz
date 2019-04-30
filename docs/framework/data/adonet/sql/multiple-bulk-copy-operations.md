---
title: Vícečetné operace hromadného kopírování
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: 405a82c625853d242ca68088ffdf81b6bcd7c518
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922210"
---
# <a name="multiple-bulk-copy-operations"></a>Vícečetné operace hromadného kopírování
Můžete provádět vícečetné operace hromadného kopírování pomocí jednu instanci <xref:System.Data.SqlClient.SqlBulkCopy> třídy. Pokud se parametry operace změnit mezi kopie (například název cílové tabulky), je potřeba je aktualizovat před některý z následných volání **WriteToServer** metod, jak je ukázáno v následujícím příkladu. Pokud explicitně, všechny hodnoty vlastnosti zůstávají stejné, stejně jako v předchozí operaci hromadného kopírování pro danou instanci.  
  
> [!NOTE]
>  Vícečetné operace hromadného kopírování stejnou instanci pomocí provádí <xref:System.Data.SqlClient.SqlBulkCopy> obvykle je efektivnější než použití samostatné instance pro každou operaci.  
  
 Pokud provedete několik použití stejné operace hromadného kopírování <xref:System.Data.SqlClient.SqlBulkCopy> objektu, neexistují žádná omezení toho, jestli zdrojová nebo cílová informace stejné nebo různé v jednotlivých operacích. Ale musíte zajistit, že informací o přidružení typu sloupce správně nastavený pokaždé, když zapíšete do serveru.  
  
> [!IMPORTANT]
>  Tato ukázka se nespustí, pokud jste vytvořili pracovní tabulky, jak je popsáno v [příklad nastavení hromadného kopírování](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Tento kód je k dispozici k předvedení syntaxe pro používání **SqlBulkCopy** pouze. Pokud zdrojové a cílové tabulky jsou umístěny ve stejné instanci systému SQL Server, je jednodušší a rychlejší použití příkazů jazyka Transact-SQL `INSERT … SELECT` příkaz Kopírovat data.  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Operace hromadného kopírování na SQL Serveru](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
