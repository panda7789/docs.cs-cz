---
title: "Více operace hromadného kopírování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8a753357719f451ce7acc2d7f42c0493ca2357ab
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="multiple-bulk-copy-operations"></a>Více operace hromadného kopírování
Můžete provést několik operace hromadného kopírování pomocí jednu instanci <xref:System.Data.SqlClient.SqlBulkCopy> třídy. Pokud se parametry operace změnit mezi kopie (například název cílové tabulky), je nutné je aktualizovat před žádné z následných volání **WriteToServer** metod, jak je ukázáno v následujícím příkladu. Pokud není výslovně změnili, všechny hodnoty vlastností zůstávají stejné, stejně jako v předchozí operace hromadného kopírování pro danou instanci.  
  
> [!NOTE]
>  Provádění více operace hromadného kopírování pomocí stejné instanci <xref:System.Data.SqlClient.SqlBulkCopy> obvykle je efektivnější než při použití samostatnou instanci pro každou operaci.  
  
 Pokud je třeba provést několik operace hromadného kopírování používající stejný <xref:System.Data.SqlClient.SqlBulkCopy> objektu, neexistují žádná omezení toho, jestli zdroje nebo cíle informace stejné nebo jiné v jednotlivých operacích. Ale musíte zajistit, že informací o přidružení typu sloupce je správně nastaveno při každém zápisu serveru.  
  
> [!IMPORTANT]
>  Tato ukázka se nespustí, pokud jste vytvořili pracovní tabulky, jak je popsáno v [hromadné kopírování příklad instalace](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Tento kód je určen k předvedení syntaxe pro používání **SqlBulkCopy** pouze. Pokud zdrojové a cílové tabulky jsou umístěny ve stejné instanci systému SQL Server, je snadnější a rychlejší pomocí jazyka Transact-SQL `INSERT … SELECT` příkaz Kopírovat data.  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Operace hromadného kopírování na SQL Serveru](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
