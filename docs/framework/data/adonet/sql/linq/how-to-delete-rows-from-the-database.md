---
title: 'Postupy: odstranění řádků z databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: 179656fbecdc8efbef323c1882d756dea564c152
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360449"
---
# <a name="how-to-delete-rows-from-the-database"></a><span data-ttu-id="175db-102">Postupy: odstranění řádků z databáze</span><span class="sxs-lookup"><span data-stu-id="175db-102">How to: Delete Rows From the Database</span></span>
<span data-ttu-id="175db-103">Odstraněním řádků v databázi odebráním odpovídající [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objekty z kolekce jejich související tabulky.</span><span class="sxs-lookup"><span data-stu-id="175db-103">You can delete rows in a database by removing the corresponding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objects from their table-related collection.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="175db-104"> přeloží všechny změny příslušné SQL `DELETE` příkazy.</span><span class="sxs-lookup"><span data-stu-id="175db-104"> translates your changes to the appropriate SQL `DELETE` commands.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="175db-105"> nepodporuje nebo rozpoznat kaskádové odstranění operace.</span><span class="sxs-lookup"><span data-stu-id="175db-105"> does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="175db-106">Pokud chcete odstranit řádek v tabulce, která má omezení u ní, musíte provést některý z následujících úloh:</span><span class="sxs-lookup"><span data-stu-id="175db-106">If you want to delete a row in a table that has constraints against it, you must complete either of the following tasks:</span></span>  
  
-   <span data-ttu-id="175db-107">Nastavte `ON DELETE CASCADE` pravidlo v omezení cizího klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="175db-107">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>  
  
-   <span data-ttu-id="175db-108">Pomocí vlastního kódu nejprve odstranit podřízené objekty, které zabránit odstranění nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="175db-108">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>  
  
 <span data-ttu-id="175db-109">V opačném případě je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="175db-109">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="175db-110">Najdete v druhém příkladu dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="175db-110">See the second code example later in this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="175db-111">Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`, a `Delete` databáze operace.</span><span class="sxs-lookup"><span data-stu-id="175db-111">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="175db-112">Další informace najdete v tématu [přizpůsobení vložit, aktualizovat a odstranit operace](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="175db-112">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="175db-113">Vývojáři pomocí sady Visual Studio můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] vyvíjet uložené procedury k tomuto účelu.</span><span class="sxs-lookup"><span data-stu-id="175db-113">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="175db-114">Následující postup předpokládá, že platný <xref:System.Data.Linq.DataContext> naváže připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="175db-114">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="175db-115">Další informace najdete v tématu [postupy: připojení k databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="175db-115">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-delete-a-row-in-the-database"></a><span data-ttu-id="175db-116">Chcete-li odstranit řádek v databázi</span><span class="sxs-lookup"><span data-stu-id="175db-116">To delete a row in the database</span></span>  
  
1.  <span data-ttu-id="175db-117">Dotaz na databázi pro řádku, který má být odstraněna.</span><span class="sxs-lookup"><span data-stu-id="175db-117">Query the database for the row to be deleted.</span></span>  
  
2.  <span data-ttu-id="175db-118">Volání <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="175db-118">Call the <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> method.</span></span>  
  
3.  <span data-ttu-id="175db-119">Odeslání změn do databáze.</span><span class="sxs-lookup"><span data-stu-id="175db-119">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="175db-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="175db-120">Example</span></span>  
 <span data-ttu-id="175db-121">Tento první příklad kódu se dotazuje databáze podrobnosti pořadí, které patří do 11000 # pořadí, označí tyto podrobnosti pořadí k odstranění a odešle tyto změny do databáze.</span><span class="sxs-lookup"><span data-stu-id="175db-121">This first code example queries the database for order details that belong to Order #11000, marks these order details for deletion, and submits these changes to the database.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="175db-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="175db-122">Example</span></span>  
 <span data-ttu-id="175db-123">V tomto příkladu druhý cílem je odebrat pořadí (#10250).</span><span class="sxs-lookup"><span data-stu-id="175db-123">In this second example, the objective is to remove an order (#10250).</span></span> <span data-ttu-id="175db-124">Kód nejprve hledá `OrderDetails` tabulky, zda má pořadí, které se odeberou existuje podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="175db-124">The code first examines the `OrderDetails` table to see whether the order to be removed has children there.</span></span> <span data-ttu-id="175db-125">Pokud pořadí obsahuje podřízené položky, první podřízené objekty a pak pořadí jsou označeny pro odebrání.</span><span class="sxs-lookup"><span data-stu-id="175db-125">If the order has children, first the children and then the order are marked for removal.</span></span> <span data-ttu-id="175db-126"><xref:System.Data.Linq.DataContext> Vloží skutečného odstranění ve správném pořadí tak, aby odeslal do databáze příkazy odstranění dodržováním omezení databáze.</span><span class="sxs-lookup"><span data-stu-id="175db-126">The <xref:System.Data.Linq.DataContext> puts the actual deletes in correct order so that delete commands sent to the database abide by the database constraints.</span></span>  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="175db-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="175db-127">See Also</span></span>  
 [<span data-ttu-id="175db-128">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="175db-128">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="175db-129">Postupy: přiřazení uložené procedury k provedení aktualizací, vložení a odstranění (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="175db-129">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [<span data-ttu-id="175db-130">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="175db-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
