---
title: INSERT, Update a operace odstranění
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: fcfb858dbc4bed1109c31c24b29731e74afd6ce1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="insert-update-and-delete-operations"></a><span data-ttu-id="372e0-102">INSERT, Update a operace odstranění</span><span class="sxs-lookup"><span data-stu-id="372e0-102">Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="372e0-103">Můžete provést `Insert`, `Update`, a `Delete` operace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] přidání, změně a odebírání objektů v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="372e0-103">You perform `Insert`, `Update`, and `Delete` operations in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] by adding, changing, and removing objects in your object model.</span></span> <span data-ttu-id="372e0-104">Ve výchozím nastavení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] znamená, že je vaše akce jazyka SQL a odešle změny do databáze.</span><span class="sxs-lookup"><span data-stu-id="372e0-104">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your actions to SQL and submits the changes to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="372e0-105"> nabízí větší manipulace a zachování změn, které jste provedli k objektům.</span><span class="sxs-lookup"><span data-stu-id="372e0-105"> offers maximum flexibility in manipulating and persisting changes that you made to your objects.</span></span> <span data-ttu-id="372e0-106">Jakmile objekty entity jsou k dispozici (buď je pomocí dotazu načítání nebo vytváření je znovu), můžete je změnit jako typický objekty ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="372e0-106">As soon as entity objects are available (either by retrieving them through a query or by constructing them anew), you can change them as typical objects in your application.</span></span> <span data-ttu-id="372e0-107">To znamená můžete změnit jejich hodnoty, můžete je přidat do kolekce a můžete je odebrat z kolekce.</span><span class="sxs-lookup"><span data-stu-id="372e0-107">That is, you can change their values, you can add them to your collections, and you can remove them from your collections.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="372e0-108"> sleduje změny a je připravený k přenosu zpět do databáze při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span><span class="sxs-lookup"><span data-stu-id="372e0-108"> tracks your changes and is ready to transmit them back to the database when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="372e0-109"> nepodporuje nebo rozpoznat kaskádové odstranění operace.</span><span class="sxs-lookup"><span data-stu-id="372e0-109"> does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="372e0-110">Pokud chcete odstranit řádek v tabulce, která má omezení u ní, musíte buď sadu `ON DELETE CASCADE` pravidlo v omezení cizího klíče v databázi, nebo pomocí vlastní kód nejprve odstranit podřízené objekty, které zabránit odstranění nadřazený objekt.</span><span class="sxs-lookup"><span data-stu-id="372e0-110">If you want to delete a row in a table that has constraints against it, you must either set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database, or use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span> <span data-ttu-id="372e0-111">V opačném případě je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="372e0-111">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="372e0-112">Další informace najdete v tématu [postupy: odstranění řádků z databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span><span class="sxs-lookup"><span data-stu-id="372e0-112">For more information, see [How to: Delete Rows From the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="372e0-113">Následující úryvky použití `Customer` a `Order` třídy z ukázková databáze Northwind.</span><span class="sxs-lookup"><span data-stu-id="372e0-113">The following excerpts use the `Customer` and `Order` classes from the Northwind sample database.</span></span> <span data-ttu-id="372e0-114">Definice tříd nejsou zobrazeny jako stručný výtah.</span><span class="sxs-lookup"><span data-stu-id="372e0-114">Class definitions are not shown for brevity.</span></span>  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 <span data-ttu-id="372e0-115">Při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automaticky generuje a spouští příkazy SQL, které musí mít přenést vaše změny zpět do databáze.</span><span class="sxs-lookup"><span data-stu-id="372e0-115">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatically generates and executes the SQL commands that it must have to transmit your changes back to the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="372e0-116">Toto chování můžete přepsat pomocí vlastní vlastní logiky, obvykle prostřednictvím uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="372e0-116">You can override this behavior by using your own custom logic, typically by way of a stored procedure.</span></span> <span data-ttu-id="372e0-117">Další informace najdete v tématu [odpovědnosti vývojáře v přepsání výchozí chování](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="372e0-117">For more information, see [Responsibilities of the Developer In Overriding Default Behavior](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).</span></span>  
>   
>  <span data-ttu-id="372e0-118">Vývojáři pomocí sady Visual Studio můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k vývoji uložené procedury pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="372e0-118">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for this purpose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="372e0-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="372e0-119">See Also</span></span>  
 [<span data-ttu-id="372e0-120">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="372e0-120">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="372e0-121">Přizpůsobení operací vložení, aktualizace a odstranění</span><span class="sxs-lookup"><span data-stu-id="372e0-121">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
