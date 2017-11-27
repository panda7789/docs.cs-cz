---
title: "Postupy: aktualizace řádků v databázi"
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
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0ba7d6369b534edf5e8c61605b09823a36143a00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="a6df1-102">Postupy: aktualizace řádků v databázi</span><span class="sxs-lookup"><span data-stu-id="a6df1-102">How to: Update Rows in the Database</span></span>
<span data-ttu-id="a6df1-103">Řádky v databázi můžete aktualizovat změnou hodnoty členů objektů přidružených [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekce a potom odeslání změn do databáze.</span><span class="sxs-lookup"><span data-stu-id="a6df1-103">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="a6df1-104">Přeloží změny do příslušné SQL `UPDATE` příkazy.</span><span class="sxs-lookup"><span data-stu-id="a6df1-104"> translates your changes into the appropriate SQL `UPDATE` commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6df1-105">Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`, a `Delete` databáze operace.</span><span class="sxs-lookup"><span data-stu-id="a6df1-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="a6df1-106">Další informace najdete v tématu [přizpůsobení vložit, aktualizovat a odstranit operace](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a6df1-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="a6df1-107">Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] vyvíjet uložené procedury k tomuto účelu.</span><span class="sxs-lookup"><span data-stu-id="a6df1-107">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="a6df1-108">Následující postup předpokládá, že platný <xref:System.Data.Linq.DataContext> naváže připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="a6df1-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="a6df1-109">Další informace najdete v tématu [postupy: připojení k databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="a6df1-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="a6df1-110">O aktualizaci řádku v databázi</span><span class="sxs-lookup"><span data-stu-id="a6df1-110">To update a row in the database</span></span>  
  
1.  <span data-ttu-id="a6df1-111">Dotaz na databázi pro aktualizaci řádku.</span><span class="sxs-lookup"><span data-stu-id="a6df1-111">Query the database for the row to be updated.</span></span>  
  
2.  <span data-ttu-id="a6df1-112">Provést požadované změny hodnoty členů v výsledná [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektu.</span><span class="sxs-lookup"><span data-stu-id="a6df1-112">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>  
  
3.  <span data-ttu-id="a6df1-113">Odešlete změny do databáze.</span><span class="sxs-lookup"><span data-stu-id="a6df1-113">Submit the changes to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6df1-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6df1-114">Example</span></span>  
 <span data-ttu-id="a6df1-115">Následující příklad dotazu na databázi pro pořadí #11000 a poté změní hodnoty `ShipName` a `ShipVia` v výsledná `Order` objektu.</span><span class="sxs-lookup"><span data-stu-id="a6df1-115">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="a6df1-116">Nakonec změny na tyto hodnoty členů se odešlou do databáze jako změny v `ShipName` a `ShipVia` sloupce.</span><span class="sxs-lookup"><span data-stu-id="a6df1-116">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a6df1-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6df1-117">See Also</span></span>  
 [<span data-ttu-id="a6df1-118">Postupy: Správa je v konfliktu změn</span><span class="sxs-lookup"><span data-stu-id="a6df1-118">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="a6df1-119">Postupy: přiřazení uložené procedury k provedení aktualizací, vložení a odstranění (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="a6df1-119">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [<span data-ttu-id="a6df1-120">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="a6df1-120">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
