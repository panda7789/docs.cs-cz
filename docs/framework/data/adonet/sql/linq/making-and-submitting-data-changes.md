---
title: "Vytvoření a odeslání změn dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d2b121bdadcc231d2ea3a2c1d2ebdab40306c5ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="9319d-102">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="9319d-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="9319d-103">Témata v této části popisují postup vytvoření a přenést změny v databázi a způsobu řešení konfliktů optimistickou metodu souběžného.</span><span class="sxs-lookup"><span data-stu-id="9319d-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9319d-104">Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`, a `Delete` databáze operace.</span><span class="sxs-lookup"><span data-stu-id="9319d-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="9319d-105">Další informace najdete v tématu [přizpůsobení vložit, aktualizovat a odstranit operace](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9319d-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="9319d-106">Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] vyvíjet uložené procedury k tomuto účelu.</span><span class="sxs-lookup"><span data-stu-id="9319d-106">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9319d-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9319d-107">In This Section</span></span>  
 [<span data-ttu-id="9319d-108">Postupy: Vložení řádků do databáze</span><span class="sxs-lookup"><span data-stu-id="9319d-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="9319d-109">Popisuje postup přidání objektů do objektový model vložte řádků v databázi.</span><span class="sxs-lookup"><span data-stu-id="9319d-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="9319d-110">Postupy: Aktualizace řádků v databázi</span><span class="sxs-lookup"><span data-stu-id="9319d-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="9319d-111">Popisuje postup aktualizace řádků v databázi aktualizací objekty v modelu objektu.</span><span class="sxs-lookup"><span data-stu-id="9319d-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="9319d-112">Postupy: Odstranění řádků z databáze</span><span class="sxs-lookup"><span data-stu-id="9319d-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="9319d-113">Popisuje postup odstranění řádků v databázi odstraněním objekty v modelu objektu.</span><span class="sxs-lookup"><span data-stu-id="9319d-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="9319d-114">Postupy: Odeslání změn do databáze</span><span class="sxs-lookup"><span data-stu-id="9319d-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="9319d-115">Popisuje, jak odeslat objektový model změn v databázi.</span><span class="sxs-lookup"><span data-stu-id="9319d-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="9319d-116">Postupy: Vytvoření transakčních sad pro odesílání dat</span><span class="sxs-lookup"><span data-stu-id="9319d-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="9319d-117">Popisuje, jak mají být zahrnuty operace transakce.</span><span class="sxs-lookup"><span data-stu-id="9319d-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="9319d-118">Postupy: Dynamické vytvoření databáze</span><span class="sxs-lookup"><span data-stu-id="9319d-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="9319d-119">Popisuje postup dynamicky generovat databází a typické scénáře pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="9319d-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="9319d-120">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="9319d-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="9319d-121">Popisuje techniky pro adresování optimistickou metodu souběžného problémy.</span><span class="sxs-lookup"><span data-stu-id="9319d-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
