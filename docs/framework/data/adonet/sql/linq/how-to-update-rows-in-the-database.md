---
title: 'Postupy: Aktualizace řádků v databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: c2055e1dd988352b50a439531ab5533f34a4965e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793131"
---
# <a name="how-to-update-rows-in-the-database"></a><span data-ttu-id="d8bb6-102">Postupy: Aktualizace řádků v databázi</span><span class="sxs-lookup"><span data-stu-id="d8bb6-102">How to: Update Rows in the Database</span></span>

<span data-ttu-id="d8bb6-103">Řádky v databázi lze aktualizovat úpravou hodnot členů objektů přidružených [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> ke kolekci a odesláním změn do databáze.</span><span class="sxs-lookup"><span data-stu-id="d8bb6-103">You can update rows in a database by modifying member values of the objects associated with the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="d8bb6-104">Převede změny do příslušných příkazů SQL `UPDATE` .</span><span class="sxs-lookup"><span data-stu-id="d8bb6-104">translates your changes into the appropriate SQL `UPDATE` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="d8bb6-105">Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`a `Delete` databázové operace.</span><span class="sxs-lookup"><span data-stu-id="d8bb6-105">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="d8bb6-106">Další informace najdete v tématu [přizpůsobení operací vložení, aktualizace a odstranění](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d8bb6-106">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="d8bb6-107">Vývojáři, kteří používají Visual Studio, mohou použít Návrhář relací objektů k vývoji uložených procedur pro stejný účel.</span><span class="sxs-lookup"><span data-stu-id="d8bb6-107">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="d8bb6-108">Následující postup předpokládá, že <xref:System.Data.Linq.DataContext> se připojíte k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="d8bb6-108">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="d8bb6-109">Další informace najdete v tématu [jak: Připojení k databázi](how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="d8bb6-109">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-update-a-row-in-the-database"></a><span data-ttu-id="d8bb6-110">Aktualizace řádku v databázi</span><span class="sxs-lookup"><span data-stu-id="d8bb6-110">To update a row in the database</span></span>

1. <span data-ttu-id="d8bb6-111">Dotaz na databázi pro řádek, který se má aktualizovat</span><span class="sxs-lookup"><span data-stu-id="d8bb6-111">Query the database for the row to be updated.</span></span>

2. <span data-ttu-id="d8bb6-112">Proveďte požadované změny hodnot členů ve výsledném [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektu.</span><span class="sxs-lookup"><span data-stu-id="d8bb6-112">Make desired changes to member values in the resulting [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object.</span></span>

3. <span data-ttu-id="d8bb6-113">Odešlete změny do databáze.</span><span class="sxs-lookup"><span data-stu-id="d8bb6-113">Submit the changes to the database.</span></span>

## <a name="example"></a><span data-ttu-id="d8bb6-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="d8bb6-114">Example</span></span>

<span data-ttu-id="d8bb6-115">Následující příklad dotazuje databázi pro pořadí #11000 a poté změní hodnoty `ShipName` a `ShipVia` ve výsledném `Order` objektu.</span><span class="sxs-lookup"><span data-stu-id="d8bb6-115">The following example queries the database for order #11000, and then changes the values of `ShipName` and `ShipVia` in the resulting `Order` object.</span></span> <span data-ttu-id="d8bb6-116">Nakonec se změny těchto hodnot členů odesílají do databáze jako změny ve `ShipName` sloupcích a. `ShipVia`</span><span class="sxs-lookup"><span data-stu-id="d8bb6-116">Finally, the changes to these member values are submitted to the database as changes in the `ShipName` and `ShipVia` columns.</span></span>

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="d8bb6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8bb6-117">See also</span></span>

- [<span data-ttu-id="d8bb6-118">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="d8bb6-118">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="d8bb6-119">Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="d8bb6-119">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="d8bb6-120">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="d8bb6-120">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
