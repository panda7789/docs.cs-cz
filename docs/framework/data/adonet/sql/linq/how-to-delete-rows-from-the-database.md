---
title: 'Postupy: Odstranění řádků z databáze'
description: Naučte se odstraňovat řádky v databázi odebráním LINQ to SQL objektů z kolekce související s tabulkami. LINQ to SQL překládá odstranění příkazů SQL DELETE.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: d08621e834961e1db9312cac36bd2e69133142b5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286388"
---
# <a name="how-to-delete-rows-from-the-database"></a><span data-ttu-id="d6f4a-104">Postupy: Odstranění řádků z databáze</span><span class="sxs-lookup"><span data-stu-id="d6f4a-104">How to: Delete Rows From the Database</span></span>

<span data-ttu-id="d6f4a-105">Řádky v databázi můžete odstranit odebráním odpovídajících [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objektů z jejich kolekce související s tabulkami.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-105">You can delete rows in a database by removing the corresponding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objects from their table-related collection.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="d6f4a-106">Převede změny na příslušné `DELETE` příkazy SQL.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-106">translates your changes to the appropriate SQL `DELETE` commands.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="d6f4a-107">nepodporuje ani nerozeznává operace kaskádového odstranění.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-107">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="d6f4a-108">Pokud chcete odstranit řádek v tabulce, která má omezení proti němu, je nutné provést jednu z následujících úloh:</span><span class="sxs-lookup"><span data-stu-id="d6f4a-108">If you want to delete a row in a table that has constraints against it, you must complete either of the following tasks:</span></span>

- <span data-ttu-id="d6f4a-109">Nastavte `ON DELETE CASCADE` pravidlo v omezení cizího klíče v databázi.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-109">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>

- <span data-ttu-id="d6f4a-110">Použijte vlastní kód pro první odstranění podřízených objektů, které brání odstranění nadřazeného objektu.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-110">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>

 <span data-ttu-id="d6f4a-111">V opačném případě je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-111">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="d6f4a-112">Viz druhý příklad kódu dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-112">See the second code example later in this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="d6f4a-113">Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert` , `Update` a `Delete` databázové operace.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-113">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="d6f4a-114">Další informace najdete v tématu [přizpůsobení operací vložení, aktualizace a odstranění](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d6f4a-114">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="d6f4a-115">Vývojáři, kteří používají Visual Studio, mohou použít Návrhář relací objektů k vývoji uložených procedur pro stejný účel.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-115">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="d6f4a-116">Následující postup předpokládá, že se <xref:System.Data.Linq.DataContext> připojíte k databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-116">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="d6f4a-117">Další informace najdete v tématu [Postup: připojení k databázi](how-to-connect-to-a-database.md).</span><span class="sxs-lookup"><span data-stu-id="d6f4a-117">For more information, see [How to: Connect to a Database](how-to-connect-to-a-database.md).</span></span>

### <a name="to-delete-a-row-in-the-database"></a><span data-ttu-id="d6f4a-118">Odstranění řádku v databázi</span><span class="sxs-lookup"><span data-stu-id="d6f4a-118">To delete a row in the database</span></span>

1. <span data-ttu-id="d6f4a-119">Dotaz na databázi pro řádek, který se má odstranit</span><span class="sxs-lookup"><span data-stu-id="d6f4a-119">Query the database for the row to be deleted.</span></span>

2. <span data-ttu-id="d6f4a-120">Zavolejte <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-120">Call the <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> method.</span></span>

3. <span data-ttu-id="d6f4a-121">Odeslat změnu do databáze.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-121">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="d6f4a-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6f4a-122">Example</span></span>

<span data-ttu-id="d6f4a-123">Tento první příklad kódu se dotazuje databáze na Podrobnosti objednávky, které patří k objednávce #11000, označí tyto podrobnosti objednávky k odstranění a odešle tyto změny do databáze.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-123">This first code example queries the database for order details that belong to Order #11000, marks these order details for deletion, and submits these changes to the database.</span></span>

[!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
[!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="d6f4a-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6f4a-124">Example</span></span>

<span data-ttu-id="d6f4a-125">V tomto druhém příkladu je cílem odebrat objednávku (#10250).</span><span class="sxs-lookup"><span data-stu-id="d6f4a-125">In this second example, the objective is to remove an order (#10250).</span></span> <span data-ttu-id="d6f4a-126">Kód nejprve prohledá `OrderDetails` tabulku, aby bylo možné zjistit, zda je v pořadí, ve kterém má být odebráno podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-126">The code first examines the `OrderDetails` table to see whether the order to be removed has children there.</span></span> <span data-ttu-id="d6f4a-127">Má-li objednávka podřízené položky, nejprve podřízené položky a pořadí jsou označeny pro odebrání.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-127">If the order has children, first the children and then the order are marked for removal.</span></span> <span data-ttu-id="d6f4a-128">Vrátí <xref:System.Data.Linq.DataContext> skutečné odstranění ve správném pořadí, aby se příkazy DELETE odesílané do databáze dodržovaly omezeními databáze.</span><span class="sxs-lookup"><span data-stu-id="d6f4a-128">The <xref:System.Data.Linq.DataContext> puts the actual deletes in correct order so that delete commands sent to the database abide by the database constraints.</span></span>

[!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
[!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="d6f4a-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6f4a-129">See also</span></span>

- [<span data-ttu-id="d6f4a-130">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="d6f4a-130">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="d6f4a-131">Postupy: Přiřazení uložených procedur za účelem aktualizací, vkládání a odstraňování (Návrhář relací objektů)</span><span class="sxs-lookup"><span data-stu-id="d6f4a-131">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="d6f4a-132">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="d6f4a-132">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
