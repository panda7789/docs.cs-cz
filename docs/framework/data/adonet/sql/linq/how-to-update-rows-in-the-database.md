---
title: 'Postupy: Aktualizace řádků v databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: 30654a10382c8cc1bf99af320e3a6a493982219b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743130"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="cf6b4-102">Postupy: Aktualizace řádků v databázi</span><span class="sxs-lookup"><span data-stu-id="cf6b4-102">How to: Update Rows in the Database</span></span>
<span data-ttu-id="cf6b4-103">Řádky v databázi můžete aktualizovat změnou hodnoty členů objektů přidružených [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekce a potom odešlete změny do databáze.</span><span class="sxs-lookup"><span data-stu-id="cf6b4-103">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="cf6b4-104">Přeloží provedené změny do příslušné SQL `UPDATE` příkazy.</span><span class="sxs-lookup"><span data-stu-id="cf6b4-104">translates your changes into the appropriate SQL `UPDATE` commands.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf6b4-105">Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`, a `Delete` databázové operace.</span><span class="sxs-lookup"><span data-stu-id="cf6b4-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="cf6b4-106">Další informace najdete v tématu [přizpůsobení Insert, Update a operace odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="cf6b4-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="cf6b4-107">Vývojáři, kteří používají Visual Studio můžete použít Návrháře relací objektů pro vývoj uložené procedury k tomuto účelu.</span><span class="sxs-lookup"><span data-stu-id="cf6b4-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>  
  
 <span data-ttu-id="cf6b4-108">Následující postup předpokládá, že platný <xref:System.Data.Linq.DataContext> vás připojí k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="cf6b4-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="cf6b4-109">Další informace najdete v tématu [jak: Připojení k databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="cf6b4-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>  
  
### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="cf6b4-110">Aktualizujte řádek v databázi</span><span class="sxs-lookup"><span data-stu-id="cf6b4-110">To update a row in the database</span></span>  
  
1. <span data-ttu-id="cf6b4-111">Dotaz na databázi pro aktualizaci řádku.</span><span class="sxs-lookup"><span data-stu-id="cf6b4-111">Query the database for the row to be updated.</span></span>  
  
2. <span data-ttu-id="cf6b4-112">Proveďte požadované změny hodnoty členů ve výsledné [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektu.</span><span class="sxs-lookup"><span data-stu-id="cf6b4-112">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>  
  
3. <span data-ttu-id="cf6b4-113">Odešlete změny do databáze.</span><span class="sxs-lookup"><span data-stu-id="cf6b4-113">Submit the changes to the database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf6b4-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="cf6b4-114">Example</span></span>  
 <span data-ttu-id="cf6b4-115">V následujícím příkladu dotazuje databázi pro objednávku #11000 a poté změní hodnoty `ShipName` a `ShipVia` ve výsledné `Order` objektu.</span><span class="sxs-lookup"><span data-stu-id="cf6b4-115">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="cf6b4-116">Nakonec změny na tyto hodnoty členů se odešlou do databáze jako změny `ShipName` a `ShipVia` sloupce.</span><span class="sxs-lookup"><span data-stu-id="cf6b4-116">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="cf6b4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf6b4-117">See also</span></span>

- [<span data-ttu-id="cf6b4-118">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="cf6b4-118">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="cf6b4-119">Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="cf6b4-119">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="cf6b4-120">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="cf6b4-120">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
