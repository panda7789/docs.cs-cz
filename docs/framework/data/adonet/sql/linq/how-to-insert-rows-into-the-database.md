---
title: 'Postupy: Vložení řádků do databáze'
description: Naučte se vkládat řádky do databáze přidáním LINQ to SQL objektů do kolekce související s tabulkami. LINQ to SQL překládá přidávání do příkazů SQL INSERT.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 39eee6edf59d2adb7de41efd88899050fbe69fd8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286349"
---
# <a name="how-to-insert-rows-into-the-database"></a><span data-ttu-id="5ba1a-104">Postupy: Vložení řádků do databáze</span><span class="sxs-lookup"><span data-stu-id="5ba1a-104">How to: Insert Rows Into the Database</span></span>

<span data-ttu-id="5ba1a-105">Řádky do databáze vložíte přidáním objektů do přidružené [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekce a následným odesláním změn do databáze.</span><span class="sxs-lookup"><span data-stu-id="5ba1a-105">You insert rows into a database by adding objects to the associated [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection and then submitting the changes to the database.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="5ba1a-106">Převede změny do příslušných `INSERT` příkazů SQL.</span><span class="sxs-lookup"><span data-stu-id="5ba1a-106">translates your changes into the appropriate SQL `INSERT` commands.</span></span>

> [!NOTE]
> <span data-ttu-id="5ba1a-107">Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert` , `Update` a `Delete` databázové operace.</span><span class="sxs-lookup"><span data-stu-id="5ba1a-107">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="5ba1a-108">Další informace najdete v tématu [přizpůsobení operací vložení, aktualizace a odstranění](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="5ba1a-108">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="5ba1a-109">Vývojáři, kteří používají Visual Studio, mohou použít Návrhář relací objektů k vývoji uložených procedur pro stejný účel.</span><span class="sxs-lookup"><span data-stu-id="5ba1a-109">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="5ba1a-110">Následující postup předpokládá, že se <xref:System.Data.Linq.DataContext> připojíte k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="5ba1a-110">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="5ba1a-111">Další informace najdete v tématu [Postup: připojení k databázi](how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="5ba1a-111">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-insert-a-row-into-the-database"></a><span data-ttu-id="5ba1a-112">Vložení řádku do databáze</span><span class="sxs-lookup"><span data-stu-id="5ba1a-112">To insert a row into the database</span></span>

1. <span data-ttu-id="5ba1a-113">Vytvoří nový objekt, který obsahuje data sloupce, která se mají odeslat.</span><span class="sxs-lookup"><span data-stu-id="5ba1a-113">Create a new object that includes the column data to be submitted.</span></span>

2. <span data-ttu-id="5ba1a-114">Přidejte nový objekt do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` kolekce přidružené k cílové tabulce v databázi.</span><span class="sxs-lookup"><span data-stu-id="5ba1a-114">Add the new object to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associated with the target table in the database.</span></span>

3. <span data-ttu-id="5ba1a-115">Odeslat změnu do databáze.</span><span class="sxs-lookup"><span data-stu-id="5ba1a-115">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="5ba1a-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ba1a-116">Example</span></span>

<span data-ttu-id="5ba1a-117">Následující příklad kódu vytvoří nový objekt typu `Order` a naplní ho příslušnými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="5ba1a-117">The following code example creates a new object of type `Order` and populates it with appropriate values.</span></span> <span data-ttu-id="5ba1a-118">Následně přidá nový objekt do `Order` kolekce.</span><span class="sxs-lookup"><span data-stu-id="5ba1a-118">It then adds the new object to the `Order` collection.</span></span> <span data-ttu-id="5ba1a-119">Nakonec odešle změnu do databáze jako nový řádek v `Orders` tabulce.</span><span class="sxs-lookup"><span data-stu-id="5ba1a-119">Finally, it submits the change to the database as a new row in the `Orders` table.</span></span>

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="5ba1a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ba1a-120">See also</span></span>

- [<span data-ttu-id="5ba1a-121">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="5ba1a-121">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="5ba1a-122">Metody DataContext (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="5ba1a-122">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [<span data-ttu-id="5ba1a-123">Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="5ba1a-123">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="5ba1a-124">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="5ba1a-124">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
