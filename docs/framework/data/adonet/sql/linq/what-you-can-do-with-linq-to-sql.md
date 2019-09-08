---
title: Možnosti použití LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: 8baf361ba66ba33927121ae20edcc6c12964c21c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792095"
---
# <a name="what-you-can-do-with-linq-to-sql"></a><span data-ttu-id="92081-102">Možnosti použití LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="92081-102">What You Can Do With LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="92081-103">podporuje všechny klíčové funkce, které byste očekávali jako vývojář SQL.</span><span class="sxs-lookup"><span data-stu-id="92081-103">supports all the key capabilities you would expect as a SQL developer.</span></span> <span data-ttu-id="92081-104">Můžete zadávat dotazy na informace a vkládat, aktualizovat a odstraňovat informace z tabulek.</span><span class="sxs-lookup"><span data-stu-id="92081-104">You can query for information, and insert, update, and delete information from tables.</span></span>  
  
## <a name="selecting"></a><span data-ttu-id="92081-105">Výběr</span><span class="sxs-lookup"><span data-stu-id="92081-105">Selecting</span></span>  
 <span data-ttu-id="92081-106">Výběr (*projekce*) se dosahuje pouhým zápisem [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] dotazu ve vlastním programovacím jazyce a následným spuštěním tohoto dotazu, který načte výsledky.</span><span class="sxs-lookup"><span data-stu-id="92081-106">Selecting (*projection*) is achieved by just writing a [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] query in your own programming language, and then executing that query to retrieve the results.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="92081-107">sám sebe převede všechny nezbytné operace na nezbytné operace SQL, se kterými jste se seznámili.</span><span class="sxs-lookup"><span data-stu-id="92081-107">itself translates all the necessary operations into the necessary SQL operations that you are familiar with.</span></span> <span data-ttu-id="92081-108">Další informace najdete v tématu [LINQ to SQL](index.md).</span><span class="sxs-lookup"><span data-stu-id="92081-108">For more information, see [LINQ to SQL](index.md).</span></span>  
  
 <span data-ttu-id="92081-109">V následujícím příkladu se v okně konzoly načtou a zobrazují názvy společností zákazníků z Londýna.</span><span class="sxs-lookup"><span data-stu-id="92081-109">In the following example, the company names of customers from London are retrieved and displayed in the console window.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a><span data-ttu-id="92081-110">Vkládání</span><span class="sxs-lookup"><span data-stu-id="92081-110">Inserting</span></span>  
 <span data-ttu-id="92081-111">Chcete-li spustit `Insert`SQL, stačí přidat objekty do objektového modelu, který jste vytvořili, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> a zavolat <xref:System.Data.Linq.DataContext>na.</span><span class="sxs-lookup"><span data-stu-id="92081-111">To execute a SQL `Insert`, just add objects to the object model you have created, and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="92081-112">V následujícím příkladu je nový zákazník a informace o zákazníkovi přidány do `Customers` tabulky pomocí. <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A></span><span class="sxs-lookup"><span data-stu-id="92081-112">In the following example, a new customer and information about the customer is added to the `Customers` table by using <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a><span data-ttu-id="92081-113">Doplnění</span><span class="sxs-lookup"><span data-stu-id="92081-113">Updating</span></span>  
 <span data-ttu-id="92081-114">K `Update` položce databáze nejprve Načtěte položku a upravte ji přímo v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="92081-114">To `Update` a database entry, first retrieve the item and edit it directly in the object model.</span></span> <span data-ttu-id="92081-115">Po úpravě objektu zavolejte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> na, aby se aktualizovala databáze.</span><span class="sxs-lookup"><span data-stu-id="92081-115">After you have modified the object, call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to update the database.</span></span>  
  
 <span data-ttu-id="92081-116">V následujícím příkladu jsou načteni všichni zákazníci z Londýna.</span><span class="sxs-lookup"><span data-stu-id="92081-116">In the following example, all customers who are from London are retrieved.</span></span> <span data-ttu-id="92081-117">Pak se název města změní z "Londýn" na "Londýn-Metro".</span><span class="sxs-lookup"><span data-stu-id="92081-117">Then the name of the city is changed from "London" to "London - Metro".</span></span> <span data-ttu-id="92081-118"><xref:System.Data.Linq.DataContext.SubmitChanges%2A> Nakonec je volána k odeslání změn do databáze.</span><span class="sxs-lookup"><span data-stu-id="92081-118">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to send the changes to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a><span data-ttu-id="92081-119">Odstraňuje</span><span class="sxs-lookup"><span data-stu-id="92081-119">Deleting</span></span>  
 <span data-ttu-id="92081-120">Na `Delete` položku, odeberte položku z kolekce, do které patří, a potom zavolejte <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> na k potvrzení změny.</span><span class="sxs-lookup"><span data-stu-id="92081-120">To `Delete` an item, remove the item from the collection to which it belongs, and then call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to commit the change.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="92081-121">nerozpozná operace kaskádového odstranění.</span><span class="sxs-lookup"><span data-stu-id="92081-121">does not recognize cascade-delete operations.</span></span> <span data-ttu-id="92081-122">Pokud chcete odstranit řádek v tabulce s omezeními, přečtěte si téma [How to: Odstraní řádky z databáze](how-to-delete-rows-from-the-database.md).</span><span class="sxs-lookup"><span data-stu-id="92081-122">If you want to delete a row in a table that has constraints against it, see [How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="92081-123">V následujícím příkladu je zákazník, který `CustomerID` je z `98128` databáze načten.</span><span class="sxs-lookup"><span data-stu-id="92081-123">In the following example, the customer who has `CustomerID` of `98128` is retrieved from the database.</span></span> <span data-ttu-id="92081-124">Po potvrzení, že se řádek zákazníka načetl, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> se pak zavolá, aby se tento objekt odebral z kolekce.</span><span class="sxs-lookup"><span data-stu-id="92081-124">Then, after confirming that the customer row was retrieved, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> is called to remove that object from the collection.</span></span> <span data-ttu-id="92081-125">Nakonec se <xref:System.Data.Linq.DataContext.SubmitChanges%2A> volá, aby se odstranění předalo do databáze.</span><span class="sxs-lookup"><span data-stu-id="92081-125">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to forward the deletion to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="92081-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92081-126">See also</span></span>

- [<span data-ttu-id="92081-127">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="92081-127">Programming Guide</span></span>](programming-guide.md)
- [<span data-ttu-id="92081-128">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="92081-128">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="92081-129">Začínáme</span><span class="sxs-lookup"><span data-stu-id="92081-129">Getting Started</span></span>](getting-started.md)
