---
title: Možnosti použití LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: efb7b86c3add99e596e6798c8267c09689899d56
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231575"
---
# <a name="what-you-can-do-with-linq-to-sql"></a><span data-ttu-id="6e946-102">Možnosti použití LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6e946-102">What You Can Do With LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="6e946-103">podporuje všechny klíčové funkce, které očekáváte jako vývojář SQL.</span><span class="sxs-lookup"><span data-stu-id="6e946-103">supports all the key capabilities you would expect as a SQL developer.</span></span> <span data-ttu-id="6e946-104">Můžete dotazovat na informace a vložit, aktualizovat a odstranit informace z tabulky.</span><span class="sxs-lookup"><span data-stu-id="6e946-104">You can query for information, and insert, update, and delete information from tables.</span></span>  
  
## <a name="selecting"></a><span data-ttu-id="6e946-105">Výběr</span><span class="sxs-lookup"><span data-stu-id="6e946-105">Selecting</span></span>  
 <span data-ttu-id="6e946-106">Výběr (*projekce*) můžete vytvořit jenom zápis [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazování v programovacím jazyce a pak spouštějící tento dotaz k načtení výsledků.</span><span class="sxs-lookup"><span data-stu-id="6e946-106">Selecting (*projection*) is achieved by just writing a [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] query in your own programming language, and then executing that query to retrieve the results.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="6e946-107">samotný přeloží všechny potřebné operace do nezbytné úkony SQL, které znáte.</span><span class="sxs-lookup"><span data-stu-id="6e946-107">itself translates all the necessary operations into the necessary SQL operations that you are familiar with.</span></span> <span data-ttu-id="6e946-108">Další informace najdete v tématu [technologie LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="6e946-108">For more information, see [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="6e946-109">V následujícím příkladu se názvy společností zákazníků z Londýna načte a zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="6e946-109">In the following example, the company names of customers from London are retrieved and displayed in the console window.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a><span data-ttu-id="6e946-110">Vložení</span><span class="sxs-lookup"><span data-stu-id="6e946-110">Inserting</span></span>  
 <span data-ttu-id="6e946-111">K provedení SQL `Insert`, stačí přidat objekty do modelu objektu, který jste vytvořili a volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="6e946-111">To execute a SQL `Insert`, just add objects to the object model you have created, and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="6e946-112">V následujícím příkladu nového zákazníka a informace o zákazníkovi, přidá se do `Customers` tabulky s použitím <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span><span class="sxs-lookup"><span data-stu-id="6e946-112">In the following example, a new customer and information about the customer is added to the `Customers` table by using <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a><span data-ttu-id="6e946-113">Aktualizace</span><span class="sxs-lookup"><span data-stu-id="6e946-113">Updating</span></span>  
 <span data-ttu-id="6e946-114">K `Update` položky databáze, nejdřív načíst položku a upravte jej přímo v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="6e946-114">To `Update` a database entry, first retrieve the item and edit it directly in the object model.</span></span> <span data-ttu-id="6e946-115">Poté, co jste změnili objektu, volejte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext> aktualizaci databáze.</span><span class="sxs-lookup"><span data-stu-id="6e946-115">After you have modified the object, call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to update the database.</span></span>  
  
 <span data-ttu-id="6e946-116">V následujícím příkladu jsou načteny všechny zákazníky, kteří jsou z Londýna.</span><span class="sxs-lookup"><span data-stu-id="6e946-116">In the following example, all customers who are from London are retrieved.</span></span> <span data-ttu-id="6e946-117">Potom název města, se změní z "Londýn" na "Londýn – Metro".</span><span class="sxs-lookup"><span data-stu-id="6e946-117">Then the name of the city is changed from "London" to "London - Metro".</span></span> <span data-ttu-id="6e946-118">Nakonec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána k odeslání změn do databáze.</span><span class="sxs-lookup"><span data-stu-id="6e946-118">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to send the changes to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a><span data-ttu-id="6e946-119">Odstraňuje se</span><span class="sxs-lookup"><span data-stu-id="6e946-119">Deleting</span></span>  
 <span data-ttu-id="6e946-120">K `Delete` některou položku, odeberte položku z kolekce, do které patří a poté zavolejte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext> potvrzení změn.</span><span class="sxs-lookup"><span data-stu-id="6e946-120">To `Delete` an item, remove the item from the collection to which it belongs, and then call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to commit the change.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="6e946-121">operace kaskádové odstranění nebyl rozpoznán.</span><span class="sxs-lookup"><span data-stu-id="6e946-121">does not recognize cascade-delete operations.</span></span> <span data-ttu-id="6e946-122">Pokud chcete odstranit řádek v tabulce, která má omezení pro to, najdete v článku [jak: Odstranit řádky z databáze](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span><span class="sxs-lookup"><span data-stu-id="6e946-122">If you want to delete a row in a table that has constraints against it, see [How to: Delete Rows From the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="6e946-123">V následujícím příkladu zákazníka, který má `CustomerID` z `98128` je načtena z databáze.</span><span class="sxs-lookup"><span data-stu-id="6e946-123">In the following example, the customer who has `CustomerID` of `98128` is retrieved from the database.</span></span> <span data-ttu-id="6e946-124">Po potvrzení, že se načetla řádku zákazníka, pak <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> je volána k odebrání objektu z kolekce.</span><span class="sxs-lookup"><span data-stu-id="6e946-124">Then, after confirming that the customer row was retrieved, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> is called to remove that object from the collection.</span></span> <span data-ttu-id="6e946-125">Nakonec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána k předávání odstranění do databáze.</span><span class="sxs-lookup"><span data-stu-id="6e946-125">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to forward the deletion to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="6e946-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e946-126">See also</span></span>

- [<span data-ttu-id="6e946-127">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="6e946-127">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [<span data-ttu-id="6e946-128">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6e946-128">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="6e946-129">Začínáme</span><span class="sxs-lookup"><span data-stu-id="6e946-129">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
