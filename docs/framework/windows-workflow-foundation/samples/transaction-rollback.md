---
title: "Vrácení transakce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f377147-7529-4689-a588-608cee87fdf8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aaebbb7fa2e6e0420243c32cb70c64092ea86fa7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-rollback"></a><span data-ttu-id="8d965-102">Vrácení transakce</span><span class="sxs-lookup"><span data-stu-id="8d965-102">Transaction Rollback</span></span>
<span data-ttu-id="8d965-103">Tento příklad ukazuje, jak vytvořit vlastní <xref:System.Activities.NativeActivity> který přistupuje k vedlejším <xref:System.Activities.RuntimeTransactionHandle> získat vedlejším transakce a explicitně vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="8d965-103">This sample shows how to create a custom <xref:System.Activities.NativeActivity> that accesses the ambient <xref:System.Activities.RuntimeTransactionHandle> to get the ambient transaction and explicitly roll it back.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="8d965-104">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8d965-104">Sample Details</span></span>  
 <span data-ttu-id="8d965-105">V pracovním postupu, transakce je automaticky při dokončení krajních <xref:System.Activities.Statements.TransactionScope> nebo <xref:System.ServiceModel.Activities.TransactedReceiveScope> dokončení.</span><span class="sxs-lookup"><span data-stu-id="8d965-105">In workflow, a transaction is automatically completed when the outermost <xref:System.Activities.Statements.TransactionScope> or <xref:System.ServiceModel.Activities.TransactedReceiveScope> completes.</span></span>  <span data-ttu-id="8d965-106">Transakce implicitně zobrazí zpět v případě, že k neošetřené výjimce šíří přes hranice oboru.</span><span class="sxs-lookup"><span data-stu-id="8d965-106">A transaction implicitly rolls back when an unhandled exception propagates across the scope boundary.</span></span> <span data-ttu-id="8d965-107">Však může nastat situace, kdy má smysl explicitně bez nutnosti výjimku vrácení transakce.</span><span class="sxs-lookup"><span data-stu-id="8d965-107">However, there may be times when it makes sense to explicitly roll back a transaction without having to throw an exception.</span></span> <span data-ttu-id="8d965-108">V takovém případě můžete aktivity vlastní vrácení zpět jako jeden v této ukázce explicitně přerušení vedlejším transakce a zadejte z důvodu výjimky volitelné.</span><span class="sxs-lookup"><span data-stu-id="8d965-108">In this case, you can use the custom rollback activity like the one in this sample to explicitly abort the ambient transaction and provide an optional exception reason.</span></span>  
  
 <span data-ttu-id="8d965-109">`RollbackActivity` Je <xref:System.Activities.NativeActivity> jak to vyžaduje přístup k vlastnostem provádění získat vedlejším <xref:System.Activities.RuntimeTransactionHandle>.</span><span class="sxs-lookup"><span data-stu-id="8d965-109">The `RollbackActivity` is a <xref:System.Activities.NativeActivity> as it requires access to the execution properties to get the ambient <xref:System.Activities.RuntimeTransactionHandle>.</span></span> <span data-ttu-id="8d965-110">V `Execute` metoda, získá <xref:System.Activities.RuntimeTransactionHandle> a zkontroluje, zda je `null`, což naznačuje, že aktivita byl použit bez ambientní spuštění transakce.</span><span class="sxs-lookup"><span data-stu-id="8d965-110">In the `Execute` method, it obtains the <xref:System.Activities.RuntimeTransactionHandle> and checks whether it is `null`, which indicates that the activity was used without an ambient run-time transaction.</span></span> <span data-ttu-id="8d965-111">Poté získá transakce, znovu kontrola zda `null` je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8d965-111">It then obtains the transaction, again checking whether `null` is present.</span></span> <span data-ttu-id="8d965-112">Je možné, že vedlejším <xref:System.Activities.RuntimeTransactionHandle> bez někdy inicializace spuštění transakce.</span><span class="sxs-lookup"><span data-stu-id="8d965-112">It is possible to have an ambient <xref:System.Activities.RuntimeTransactionHandle> without ever initializing a run-time transaction.</span></span> <span data-ttu-id="8d965-113">Nakonec zruší transakce voláním <xref:System.Transactions.Transaction.Rollback%2A> a zadání výjimka zadaný uživatelem nebo obecná výjimka, která uvádí, že aktivita vrátila zpět transakci.</span><span class="sxs-lookup"><span data-stu-id="8d965-113">Finally it aborts the transaction by calling <xref:System.Transactions.Transaction.Rollback%2A> and specifying either a user-provided exception or a generic exception that states that the activity rolled back the transaction.</span></span>  
  
 <span data-ttu-id="8d965-114">Ukázkový pracovní postup se skládá z <xref:System.Activities.Statements.TransactionScope> jehož subjekt vytiskne stav transakce před a po `RollbackActivity` provede.</span><span class="sxs-lookup"><span data-stu-id="8d965-114">The demonstration workflow consists of a <xref:System.Activities.Statements.TransactionScope> whose body prints the transaction status before and after the `RollbackActivity` executes.</span></span> <span data-ttu-id="8d965-115">Všimněte si, že i když transakce byla vrácena zpět, <xref:System.Activities.Statements.TransactionScope> provede dokončen a není přerušení pracovního postupu, dokud se nedokončí text.</span><span class="sxs-lookup"><span data-stu-id="8d965-115">Note that even though the transaction has been rolled back, the <xref:System.Activities.Statements.TransactionScope> executes to completion and does not abort the workflow until the body completes.</span></span> <span data-ttu-id="8d965-116">Pracovní postup byl přerušen, protože <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> výchozí nastavení vlastnosti `true`.</span><span class="sxs-lookup"><span data-stu-id="8d965-116">The workflow is aborted because the <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> property defaults to `true`.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="8d965-117">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="8d965-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="8d965-118">Spouštění řešení TransactionRollback.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d965-118">Load the TransactionRollback.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="8d965-119">Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="8d965-119">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="8d965-120">Stisknutím kombinace kláves CTRL + F5 a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8d965-120">Press CTRL+F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8d965-121">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="8d965-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8d965-122">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8d965-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8d965-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8d965-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8d965-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8d965-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactionRollback`  
  
## <a name="see-also"></a><span data-ttu-id="8d965-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d965-125">See Also</span></span>  
 [<span data-ttu-id="8d965-126">Transakce</span><span class="sxs-lookup"><span data-stu-id="8d965-126">Transactions</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)
