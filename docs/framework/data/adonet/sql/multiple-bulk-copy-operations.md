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
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="5e8eb-102">Vícečetné operace hromadného kopírování</span><span class="sxs-lookup"><span data-stu-id="5e8eb-102">Multiple Bulk Copy Operations</span></span>
<span data-ttu-id="5e8eb-103">Můžete provést více operací hromadného kopírování pomocí jediné instance <xref:System.Data.SqlClient.SqlBulkCopy> třídy.</span><span class="sxs-lookup"><span data-stu-id="5e8eb-103">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="5e8eb-104">Pokud se parametry operace mění mezi kopiemi (například názvem cílové tabulky), je nutné je aktualizovat před jakýmkoli následným voláním libovolné metody **WriteToServer** , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5e8eb-104">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="5e8eb-105">Pokud se explicitně nezmění, všechny hodnoty vlastností zůstanou stejné jako u předchozí operace hromadného kopírování pro danou instanci.</span><span class="sxs-lookup"><span data-stu-id="5e8eb-105">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e8eb-106">Provádění více operací hromadného kopírování pomocí stejné instance <xref:System.Data.SqlClient.SqlBulkCopy> je obvykle efektivnější než použití samostatné instance pro každou operaci.</span><span class="sxs-lookup"><span data-stu-id="5e8eb-106">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="5e8eb-107">Pokud provedete několik operací hromadného kopírování pomocí <xref:System.Data.SqlClient.SqlBulkCopy> stejného objektu, neexistují žádná omezení na to, zda jsou informace o zdroji nebo cíli v každé operaci stejné nebo jiné.</span><span class="sxs-lookup"><span data-stu-id="5e8eb-107">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="5e8eb-108">Je však nutné zajistit, aby informace o přidružení sloupce byly správně nastaveny při každém zápisu na server.</span><span class="sxs-lookup"><span data-stu-id="5e8eb-108">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5e8eb-109">Tato ukázka nebude spuštěna, pokud jste nevytvořili pracovní tabulky, jak je popsáno v tématu [hromadné kopírování – příklad nastavení](bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="5e8eb-109">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](bulk-copy-example-setup.md).</span></span> <span data-ttu-id="5e8eb-110">Tento kód je k dispozici k předvedení syntaxe pouze pro použití **SqlBulkCopy** .</span><span class="sxs-lookup"><span data-stu-id="5e8eb-110">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="5e8eb-111">Pokud se zdrojové a cílové tabulky nacházejí ve stejné instanci SQL Server, je snazší a rychlejší použít příkaz Transact-SQL `INSERT … SELECT` ke zkopírování dat.</span><span class="sxs-lookup"><span data-stu-id="5e8eb-111">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5e8eb-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e8eb-112">See also</span></span>

- [<span data-ttu-id="5e8eb-113">Operace hromadného kopírování na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="5e8eb-113">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="5e8eb-114">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5e8eb-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
