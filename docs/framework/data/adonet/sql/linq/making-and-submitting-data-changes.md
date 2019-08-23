---
title: Vytvoření a odeslání změn dat
ms.date: 03/30/2017
ms.assetid: d68c2dc3-99b3-49ab-b547-2ca5b386429a
ms.openlocfilehash: dd0a8288ca924cb17bdacdeeb94f81c3d27d3e4e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915777"
---
# <a name="making-and-submitting-data-changes"></a><span data-ttu-id="2c768-102">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="2c768-102">Making and Submitting Data Changes</span></span>
<span data-ttu-id="2c768-103">Témata v této části popisují, jak provádět a přenášet změny v databázi a jak zvládnout konflikty optimistické souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="2c768-103">The topics in this section describe how to make and transmit changes to the database and how to handle optimistic concurrency conflicts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c768-104">Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`a `Delete` databázové operace.</span><span class="sxs-lookup"><span data-stu-id="2c768-104">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="2c768-105">Další informace najdete v tématu [přizpůsobení operací vložení, aktualizace a odstranění](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="2c768-105">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
>   
>  <span data-ttu-id="2c768-106">Vývojáři, kteří používají Visual Studio, mohou použít Návrhář relací objektů k vývoji uložených procedur pro stejný účel.</span><span class="sxs-lookup"><span data-stu-id="2c768-106">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c768-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2c768-107">In This Section</span></span>  
 [<span data-ttu-id="2c768-108">Postupy: Vložit řádky do databáze</span><span class="sxs-lookup"><span data-stu-id="2c768-108">How to: Insert Rows Into the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-insert-rows-into-the-database.md)  
 <span data-ttu-id="2c768-109">Popisuje, jak vložit řádky do databáze přidáním objektů do objektového modelu.</span><span class="sxs-lookup"><span data-stu-id="2c768-109">Describes how to insert rows in the database by adding objects to the object model.</span></span>  
  
 [<span data-ttu-id="2c768-110">Postupy: Aktualizovat řádky v databázi</span><span class="sxs-lookup"><span data-stu-id="2c768-110">How to: Update Rows in the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-update-rows-in-the-database.md)  
 <span data-ttu-id="2c768-111">Popisuje, jak aktualizovat řádky v databázi aktualizací objektů v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="2c768-111">Describes how to update rows in the database by updating objects in the object model.</span></span>  
  
 [<span data-ttu-id="2c768-112">Postupy: Odstraní řádky z databáze.</span><span class="sxs-lookup"><span data-stu-id="2c768-112">How to: Delete Rows From the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)  
 <span data-ttu-id="2c768-113">Popisuje, jak odstranit řádky v databázi odstraněním objektů v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="2c768-113">Describes how to delete rows in the database by deleting objects in the object model.</span></span>  
  
 [<span data-ttu-id="2c768-114">Postupy: Odeslat změny do databáze</span><span class="sxs-lookup"><span data-stu-id="2c768-114">How to: Submit Changes to the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-submit-changes-to-the-database.md)  
 <span data-ttu-id="2c768-115">Popisuje, jak odeslat změny modelu objektu do databáze.</span><span class="sxs-lookup"><span data-stu-id="2c768-115">Describes how to send object-model changes to the database.</span></span>  
  
 [<span data-ttu-id="2c768-116">Postupy: Odesílání dat v závorkách pomocí transakcí</span><span class="sxs-lookup"><span data-stu-id="2c768-116">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)  
 <span data-ttu-id="2c768-117">Popisuje, jak zahrnout operace do transakce.</span><span class="sxs-lookup"><span data-stu-id="2c768-117">Describes how to include operations in a transaction.</span></span>  
  
 [<span data-ttu-id="2c768-118">Postupy: Dynamické vytvoření databáze</span><span class="sxs-lookup"><span data-stu-id="2c768-118">How to: Dynamically Create a Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)  
 <span data-ttu-id="2c768-119">Popisuje, jak dynamicky generovat databáze a typické scénáře tohoto přístupu.</span><span class="sxs-lookup"><span data-stu-id="2c768-119">Describes how to generate databases dynamically, and typical scenarios for this approach.</span></span>  
  
 [<span data-ttu-id="2c768-120">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="2c768-120">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 <span data-ttu-id="2c768-121">Popisuje techniky pro řešení problémů s optimistické souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="2c768-121">Describes techniques for addressing optimistic concurrency issues.</span></span>
