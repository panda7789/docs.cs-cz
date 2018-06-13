---
title: 'Postupy: vložení řádků do databáze'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 4f46e38642d42e3a2e4d5f05e23cc76cf431119b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361731"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="282a1-102">Postupy: vložení řádků do databáze</span><span class="sxs-lookup"><span data-stu-id="282a1-102">How to: Insert Rows Into the Database</span></span>
<span data-ttu-id="282a1-103">Vložení řádků do databáze přidáním objektů do přidruženého [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekce a potom odeslání změn do databáze.</span><span class="sxs-lookup"><span data-stu-id="282a1-103">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="282a1-104"> Přeloží změny do příslušné SQL `INSERT` příkazy.</span><span class="sxs-lookup"><span data-stu-id="282a1-104"> translates your changes into the appropriate SQL `INSERT` commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="282a1-105">Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`, a `Delete` databáze operace.</span><span class="sxs-lookup"><span data-stu-id="282a1-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="282a1-106">Další informace najdete v tématu [přizpůsobení vložit, aktualizovat a odstranit operace](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="282a1-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="282a1-107">Vývojáři pomocí sady Visual Studio můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] vyvíjet uložené procedury k tomuto účelu.</span><span class="sxs-lookup"><span data-stu-id="282a1-107">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="282a1-108">Následující postup předpokládá, že platný <xref:System.Data.Linq.DataContext> naváže připojení k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="282a1-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="282a1-109">Další informace najdete v tématu [postupy: připojení k databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="282a1-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="282a1-110">O vložení řádku do databáze</span><span class="sxs-lookup"><span data-stu-id="282a1-110">To insert a row into the database</span></span>  
  
1.  <span data-ttu-id="282a1-111">Vytvořte nový objekt, který obsahuje data ve sloupci na odeslání.</span><span class="sxs-lookup"><span data-stu-id="282a1-111">Create a new object that includes the column data to be submitted.</span></span>  
  
2.  <span data-ttu-id="282a1-112">Přidat nový objekt, který má [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` kolekci spojenou s cílovou tabulkou v databázi.</span><span class="sxs-lookup"><span data-stu-id="282a1-112">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>  
  
3.  <span data-ttu-id="282a1-113">Odeslání změn do databáze.</span><span class="sxs-lookup"><span data-stu-id="282a1-113">Submit the change to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="282a1-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="282a1-114">Example</span></span>  
 <span data-ttu-id="282a1-115">Následující příklad kódu vytvoří nový objekt typu `Order` a naplní s příslušnými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="282a1-115">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="282a1-116">Potom přidá nový objekt, který má `Order` kolekce.</span><span class="sxs-lookup"><span data-stu-id="282a1-116">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="282a1-117">Nakonec dojde k odeslání změn do databáze jako nový řádek `Orders` tabulky.</span><span class="sxs-lookup"><span data-stu-id="282a1-117">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="282a1-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="282a1-118">See Also</span></span>  
 [<span data-ttu-id="282a1-119">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="282a1-119">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="282a1-120">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="282a1-120">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [<span data-ttu-id="282a1-121">Postupy: přiřazení uložené procedury k provedení aktualizací, vložení a odstranění (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="282a1-121">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [<span data-ttu-id="282a1-122">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="282a1-122">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
