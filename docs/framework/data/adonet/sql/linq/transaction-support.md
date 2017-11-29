---
title: "Podpora transakcí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7c1d438a83f090795a158ade1dfdbb7d2b2df863
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="transaction-support"></a><span data-ttu-id="b778e-102">Podpora transakcí</span><span class="sxs-lookup"><span data-stu-id="b778e-102">Transaction Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b778e-103">podporuje tři modely odlišné transakcí.</span><span class="sxs-lookup"><span data-stu-id="b778e-103"> supports three distinct transaction models.</span></span> <span data-ttu-id="b778e-104">Následující seznam obsahuje tyto modely v pořadí provést kontroly.</span><span class="sxs-lookup"><span data-stu-id="b778e-104">The following lists these models in the order of checks performed.</span></span>  
  
## <a name="explicit-local-transaction"></a><span data-ttu-id="b778e-105">Explicitní místní transakce</span><span class="sxs-lookup"><span data-stu-id="b778e-105">Explicit Local Transaction</span></span>  
 <span data-ttu-id="b778e-106">Když <xref:System.Data.Linq.DataContext.SubmitChanges%2A> je volána, pokud <xref:System.Data.Linq.DataContext.Transaction%2A> je nastavena na (`IDbTransaction`) transakce, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> volání je provést v rámci stejné transakci.</span><span class="sxs-lookup"><span data-stu-id="b778e-106">When <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called, if the <xref:System.Data.Linq.DataContext.Transaction%2A> property is set to a (`IDbTransaction`) transaction, the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> call is executed in the context of the same transaction.</span></span>  
  
 <span data-ttu-id="b778e-107">Je vaší povinností potvrzení nebo vrácení změn transakce po úspěšné provedení transakce.</span><span class="sxs-lookup"><span data-stu-id="b778e-107">It is your responsibility to commit or rollback the transaction after successful execution of the transaction.</span></span> <span data-ttu-id="b778e-108">Připojení odpovídající transakce musí odpovídat připojení používané pro tvorbu <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="b778e-108">The connection corresponding to the transaction must match the connection used for constructing the <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="b778e-109">Pokud se používá jiné připojení, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="b778e-109">An exception is thrown if a different connection is used.</span></span>  
  
## <a name="explicit-distributable-transaction"></a><span data-ttu-id="b778e-110">Explicitní distribuovatelného transakce</span><span class="sxs-lookup"><span data-stu-id="b778e-110">Explicit Distributable Transaction</span></span>  
 <span data-ttu-id="b778e-111">Můžete volat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozhraní API (mimo jiné včetně <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) v rámci oboru aktivní <xref:System.Transactions.Transaction>.</span><span class="sxs-lookup"><span data-stu-id="b778e-111">You can call [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] APIs (including but not limited to <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) in the scope of an active <xref:System.Transactions.Transaction>.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b778e-112">zjistí, že volání je v oboru transakce a nevytvoří nové transakce.</span><span class="sxs-lookup"><span data-stu-id="b778e-112"> detects that the call is in the scope of a transaction and does not create a new transaction.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b778e-113">také je zabráněno v tomto případě Probíhá ukončování připojení.</span><span class="sxs-lookup"><span data-stu-id="b778e-113"> also avoids closing the connection in this case.</span></span> <span data-ttu-id="b778e-114">Můžete provést dotaz a <xref:System.Data.Linq.DataContext.SubmitChanges%2A> spuštěních v kontextu tuto transakci.</span><span class="sxs-lookup"><span data-stu-id="b778e-114">You can perform query and <xref:System.Data.Linq.DataContext.SubmitChanges%2A> executions in the context of such a transaction.</span></span>  
  
## <a name="implicit-transaction"></a><span data-ttu-id="b778e-115">Implicitní transakce</span><span class="sxs-lookup"><span data-stu-id="b778e-115">Implicit Transaction</span></span>  
 <span data-ttu-id="b778e-116">Při volání <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kontroluje, zda volání je v oboru <xref:System.Transactions.Transaction> nebo, pokud `Transaction` vlastnost (`IDbTransaction`) je nastaven na spuštění uživatele místní transakce.</span><span class="sxs-lookup"><span data-stu-id="b778e-116">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] checks to see whether the call is in the scope of a <xref:System.Transactions.Transaction> or if the `Transaction` property (`IDbTransaction`) is set to a user-started local transaction.</span></span> <span data-ttu-id="b778e-117">Pokud najde ani transakce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spustí místní transakce (`IDbTransaction`) a používá je generovaný příkazy SQL.</span><span class="sxs-lookup"><span data-stu-id="b778e-117">If it finds neither transaction, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a local transaction (`IDbTransaction`) and uses it to execute the generated SQL commands.</span></span> <span data-ttu-id="b778e-118">Po úspěšném dokončení všechny příkazy SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] potvrdí místní transakci a vrátí.</span><span class="sxs-lookup"><span data-stu-id="b778e-118">When all SQL commands have been successfully completed, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] commits the local transaction and returns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b778e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b778e-119">See Also</span></span>  
 [<span data-ttu-id="b778e-120">Základní informace</span><span class="sxs-lookup"><span data-stu-id="b778e-120">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="b778e-121">Postupy: závorka odesílání dat pomocí transakce</span><span class="sxs-lookup"><span data-stu-id="b778e-121">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
