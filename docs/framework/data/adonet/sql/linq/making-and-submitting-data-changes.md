---
title: Vytvoření a odeslání změn dat
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: 23dc45c990763e69b41608f6c3ec15a8db17bf23
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743005"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="e0cbb-102">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="e0cbb-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="e0cbb-103">Témata v této části popisují postup vytvoření a přenášejí změny na databázi a způsobu řešení konfliktů optimistického řízení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="e0cbb-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0cbb-104">Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`, a `Delete` databázové operace.</span><span class="sxs-lookup"><span data-stu-id="e0cbb-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="e0cbb-105">Další informace najdete v tématu [přizpůsobení Insert, Update a operace odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="e0cbb-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="e0cbb-106">Vývojáři, kteří používají Visual Studio můžete použít Návrháře relací objektů pro vývoj uložené procedury k tomuto účelu.</span><span class="sxs-lookup"><span data-stu-id="e0cbb-106">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e0cbb-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e0cbb-107">In This Section</span></span>  
 [<span data-ttu-id="e0cbb-108">Postupy: Vložení řádků do databáze</span><span class="sxs-lookup"><span data-stu-id="e0cbb-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="e0cbb-109">Popisuje, jak vložit řádky v databázi tak, že přidáte objekty objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="e0cbb-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="e0cbb-110">Postupy: Aktualizace řádků v databázi</span><span class="sxs-lookup"><span data-stu-id="e0cbb-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="e0cbb-111">Popisuje postup aktualizace řádků v databázi aktualizací objekty v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="e0cbb-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="e0cbb-112">Postupy: Odstranit řádky z databáze</span><span class="sxs-lookup"><span data-stu-id="e0cbb-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="e0cbb-113">Popisuje postup odstranění řádků v databázi tak, že odstraníte objekty v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="e0cbb-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="e0cbb-114">Postupy: Odešlete změny do databáze</span><span class="sxs-lookup"><span data-stu-id="e0cbb-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="e0cbb-115">Popisuje, jak odeslat objektový model změn v databázi.</span><span class="sxs-lookup"><span data-stu-id="e0cbb-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="e0cbb-116">Postupy: Závorky odeslání dat pomocí transakce</span><span class="sxs-lookup"><span data-stu-id="e0cbb-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="e0cbb-117">Popisuje, jak zahrnout operace v transakci.</span><span class="sxs-lookup"><span data-stu-id="e0cbb-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="e0cbb-118">Postupy: Dynamické vytvoření databáze</span><span class="sxs-lookup"><span data-stu-id="e0cbb-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="e0cbb-119">Popisuje, jak dynamicky generovat databází a některé typické scénáře pro tento přístup.</span><span class="sxs-lookup"><span data-stu-id="e0cbb-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="e0cbb-120">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="e0cbb-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="e0cbb-121">Popisuje postupy pro řešení problémů s optimistického řízení souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="e0cbb-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
