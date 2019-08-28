---
title: 'Postupy: Aktualizace řádků v databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: bf4c50bba4b4bc2bf6b7b1c2b79426566c874dd4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043565"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="78071-102">Postupy: Aktualizace řádků v databázi</span><span class="sxs-lookup"><span data-stu-id="78071-102">How to: Update Rows in the Database</span></span>

<span data-ttu-id="78071-103">Řádky v databázi lze aktualizovat úpravou hodnot členů objektů přidružených [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> ke kolekci a odesláním změn do databáze.</span><span class="sxs-lookup"><span data-stu-id="78071-103">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="78071-104">Převede změny do příslušných příkazů SQL `UPDATE` .</span><span class="sxs-lookup"><span data-stu-id="78071-104">translates your changes into the appropriate SQL `UPDATE` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="78071-105">Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`a `Delete` databázové operace.</span><span class="sxs-lookup"><span data-stu-id="78071-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="78071-106">Další informace najdete v tématu [přizpůsobení operací vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="78071-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="78071-107">Vývojáři, kteří používají Visual Studio, mohou použít Návrhář relací objektů k vývoji uložených procedur pro stejný účel.</span><span class="sxs-lookup"><span data-stu-id="78071-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="78071-108">Následující postup předpokládá, že <xref:System.Data.Linq.DataContext> se připojíte k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="78071-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="78071-109">Další informace najdete v tématu [jak: Připojení k databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="78071-109">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>

### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="78071-110">Aktualizace řádku v databázi</span><span class="sxs-lookup"><span data-stu-id="78071-110">To update a row in the database</span></span>

1. <span data-ttu-id="78071-111">Dotaz na databázi pro řádek, který se má aktualizovat</span><span class="sxs-lookup"><span data-stu-id="78071-111">Query the database for the row to be updated.</span></span>

2. <span data-ttu-id="78071-112">Proveďte požadované změny hodnot členů ve výsledném [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektu.</span><span class="sxs-lookup"><span data-stu-id="78071-112">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>

3. <span data-ttu-id="78071-113">Odešlete změny do databáze.</span><span class="sxs-lookup"><span data-stu-id="78071-113">Submit the changes to the database.</span></span>

## <a name="example"></a><span data-ttu-id="78071-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="78071-114">Example</span></span>

<span data-ttu-id="78071-115">Následující příklad dotazuje databázi pro pořadí #11000 a poté změní hodnoty `ShipName` a `ShipVia` ve výsledném `Order` objektu.</span><span class="sxs-lookup"><span data-stu-id="78071-115">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="78071-116">Nakonec se změny těchto hodnot členů odesílají do databáze jako změny ve `ShipName` sloupcích a. `ShipVia`</span><span class="sxs-lookup"><span data-stu-id="78071-116">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="78071-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78071-117">See also</span></span>

- [<span data-ttu-id="78071-118">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="78071-118">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="78071-119">Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="78071-119">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="78071-120">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="78071-120">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
