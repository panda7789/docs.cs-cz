---
title: "Pracovní postup provést v imperativní TransactionScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd0e8686-c1d0-4400-a541-da94ed03afc7
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 26117e7b089e85e8953912745ebc74baad8bfa29
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a><span data-ttu-id="a1de6-102">Pracovní postup provést v imperativní TransactionScope</span><span class="sxs-lookup"><span data-stu-id="a1de6-102">Execute a Workflow in an Imperative TransactionScope</span></span>
<span data-ttu-id="a1de6-103">Tento příklad ukazuje postup spuštění pracovního postupu pomocí <xref:System.Activities.WorkflowInvoker> pod <xref:System.Transactions.Transaction> z imperativní kód C#.</span><span class="sxs-lookup"><span data-stu-id="a1de6-103">This sample shows how to execute a workflow using <xref:System.Activities.WorkflowInvoker> under a <xref:System.Transactions.Transaction> from imperative C# code.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="a1de6-104">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a1de6-104">Sample Details</span></span>  
 <span data-ttu-id="a1de6-105">V imperativní C# kódu <xref:System.Transactions.TransactionScope> se používá k zapouzdření sadu práci, kterou provádí ve stejné transakci.</span><span class="sxs-lookup"><span data-stu-id="a1de6-105">In imperative C# code, the <xref:System.Transactions.TransactionScope> is used to encapsulate a set of work that executes under the same transaction.</span></span> <span data-ttu-id="a1de6-106"><xref:System.Transactions.TransactionScope> Funguje tak, že vytváření vedlejším transakce a inicializace <xref:System.Transactions.Transaction.Current%2A> vlastnosti, která lze přistupovat pomocí veškerou práci vykonáván v daném vláknu.</span><span class="sxs-lookup"><span data-stu-id="a1de6-106">The <xref:System.Transactions.TransactionScope> works by creating an ambient transaction and initializing the <xref:System.Transactions.Transaction.Current%2A> property, which can then be accessed by any work being executed on that thread.</span></span>  
  
 <span data-ttu-id="a1de6-107">Ekvivalentní chování pracovního postupu získáte musí provést další práci při inicializaci modulu runtime <xref:System.Transactions.Transaction.Current%2A> před provedením každou aktivitu, protože pracovní postup nespravuje spřažení podprocesu mezi aktivitami.</span><span class="sxs-lookup"><span data-stu-id="a1de6-107">To get equivalent behavior in workflow, the runtime has to do the extra work of initializing <xref:System.Transactions.Transaction.Current%2A> before executing each activity because a workflow does not maintain thread affinity between activities.</span></span> <span data-ttu-id="a1de6-108">Tato podpora runtime jejich výsledné chování je, že při spouštění pracovního postupu s <xref:System.Activities.WorkflowInvoker> uvnitř <xref:System.Transactions.TransactionScope>, je zaručeno, že všechny aktivity spustit v kontextu vedlejším transakce vytvořené <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="a1de6-108">With this runtime support, the resulting behavior is that when executing a workflow with <xref:System.Activities.WorkflowInvoker> inside a <xref:System.Transactions.TransactionScope>, all activities are guaranteed to run under the context of the ambient transaction created by the <xref:System.Transactions.TransactionScope>.</span></span>  
  
 <span data-ttu-id="a1de6-109">Pracovní postup může mít pouze jeden vedlejším transakci pro každou instanci pracovního postupu; vnořené transakce nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a1de6-109">A workflow can have only a single ambient transaction for each workflow instance; nested transactions are not available.</span></span> <span data-ttu-id="a1de6-110">I když pracovní postup obsahuje <xref:System.Activities.Statements.TransactionScope> aktivity, to nevytvoří novou vnitřní transakci.</span><span class="sxs-lookup"><span data-stu-id="a1de6-110">Even if the workflow contains a <xref:System.Activities.Statements.TransactionScope> activity, this does not create a new inner transaction.</span></span> <span data-ttu-id="a1de6-111">Místo toho vedlejším transakce, která byla vytvořena mimo pracovní postup znovu použije.</span><span class="sxs-lookup"><span data-stu-id="a1de6-111">Instead, this reuses the ambient transaction that was created outside the workflow.</span></span>  
  
 <span data-ttu-id="a1de6-112">Ukázka začíná nový <xref:System.Transactions.TransactionScope>, vytiskne ID transakce a začne pracovního postupu pomocí <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="a1de6-112">The sample begins a new <xref:System.Transactions.TransactionScope>, prints the transaction ID and begins a workflow using <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="a1de6-113">Pracovní postup vytiskne transakce ID znovu zobrazující to je stejné transakci a pak spustí <xref:System.Activities.Statements.TransactionScope>, potom dokončí.</span><span class="sxs-lookup"><span data-stu-id="a1de6-113">The workflow prints the transaction ID again, showing that it is the same transaction, then runs a <xref:System.Activities.Statements.TransactionScope>, then completes.</span></span> <span data-ttu-id="a1de6-114"><xref:System.Activities.WorkflowInvoker.Invoke%2A> Volání na <xref:System.Activities.WorkflowInvoker> je synchronní, takže původní vlákno zablokuje, dokud dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a1de6-114">The <xref:System.Activities.WorkflowInvoker.Invoke%2A> call on <xref:System.Activities.WorkflowInvoker> is synchronous so the original thread blocks until the workflow completes.</span></span> <span data-ttu-id="a1de6-115">Po dokončení pracovního postupu transakce je dokončena a uvolnění prostředků.</span><span class="sxs-lookup"><span data-stu-id="a1de6-115">Once the workflow is complete, the transaction is completed and resources disposed.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a1de6-116">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="a1de6-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="a1de6-117">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení ImperativeTransactionSample.sln.</span><span class="sxs-lookup"><span data-stu-id="a1de6-117">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ImperativeTransactionSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a1de6-118">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a1de6-118">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a1de6-119">Pokud chcete spustit řešení, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="a1de6-119">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a1de6-120">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="a1de6-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a1de6-121">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a1de6-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a1de6-122">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a1de6-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a1de6-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a1de6-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`  
  
## <a name="see-also"></a><span data-ttu-id="a1de6-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1de6-124">See Also</span></span>
