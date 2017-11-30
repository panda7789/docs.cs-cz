---
title: "Použití TransactedReceiveScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23117014b688f0b440da3cec8620023eaf212f71
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="use-of-transactedreceivescope"></a><span data-ttu-id="21ffc-102">Použití TransactedReceiveScope</span><span class="sxs-lookup"><span data-stu-id="21ffc-102">Use of TransactedReceiveScope</span></span>
<span data-ttu-id="21ffc-103">Tento příklad ukazuje postup toku transakce z klienta na server pomocí <xref:System.Activities.Statements.TransactionScope> vytvořit novou transakci na straně klienta a <xref:System.ServiceModel.Activities.TransactedReceiveScope> přijmout zprávu s sdružení transakcí a obor životnost transakce na serveru.</span><span class="sxs-lookup"><span data-stu-id="21ffc-103">This sample shows how to flow a transaction from a client to a server using <xref:System.Activities.Statements.TransactionScope> to create a new transaction on the client and a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to receive a message with a flowed transaction and scope the lifetime of the transaction on the server.</span></span> <span data-ttu-id="21ffc-104">Ukázkový soubor obsahuje dva projekty, které plnění rolí klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="21ffc-104">The sample consists of two projects that fill the roles of client and server.</span></span>  
  
## <a name="client-application"></a><span data-ttu-id="21ffc-105">Klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="21ffc-105">Client Application</span></span>  
 <span data-ttu-id="21ffc-106">Klientská aplikace spustí pracovní postup, který vypíše ID distribuované transakce, odešle zprávu do serveru, tok transakce, obdrží odpověď, znovu vytiskne ID distribuované transakce a dokončení.</span><span class="sxs-lookup"><span data-stu-id="21ffc-106">The client application runs a workflow that prints the distributed transaction ID, sends a message to the server, flows the transaction, receives the reply, prints the distributed transaction ID again and completes.</span></span> <span data-ttu-id="21ffc-107">Pokud je ID distribuované transakce původně výtisků, je prázdný identifikátor GUID, protože transakce je jenom místní.</span><span class="sxs-lookup"><span data-stu-id="21ffc-107">When the distributed transaction ID is initially prints, it is an empty GUID as the transaction is still only local.</span></span>  
  
## <a name="server-application"></a><span data-ttu-id="21ffc-108">Aplikace serveru</span><span class="sxs-lookup"><span data-stu-id="21ffc-108">Server Application</span></span>  
 <span data-ttu-id="21ffc-109">Serverový projekt je podobný, ale pracovní postup je hostován v <xref:System.ServiceModel.Activities.WorkflowServiceHost> protože musí naslouchat na koncový bod pro zprávu od klienta.</span><span class="sxs-lookup"><span data-stu-id="21ffc-109">The server project is similar, however, the workflow is hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> because it must listen on an endpoint for the message from the client.</span></span> <span data-ttu-id="21ffc-110">Pracovní postup se jedná o <xref:System.ServiceModel.Activities.TransactedReceiveScope>, který obdrží sdružení transakcí z klienta, zobrazí zprávu, která byla odeslána, vytiskne ID distribuované transakce a odešle odpověď klientovi.</span><span class="sxs-lookup"><span data-stu-id="21ffc-110">The workflow is centered on the <xref:System.ServiceModel.Activities.TransactedReceiveScope>, which receives the flowed transaction from the client, prints the message that was sent, prints the distributed transaction ID and sends the reply to the client.</span></span> <span data-ttu-id="21ffc-111">ID distribuované transakce je teď prázdný identifikátor GUID a pokud aktivitu deklaracemi transakce byla přidána do textu <xref:System.ServiceModel.Activities.TransactedReceiveScope>, by provést pod sdružení transakcí.</span><span class="sxs-lookup"><span data-stu-id="21ffc-111">The distributed transaction ID is now a non-empty GUID and if a transaction-aware activity was added to the body of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>, it would execute under the flowed transaction.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="21ffc-112">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="21ffc-112">To run the sample</span></span>  
  
1.  <span data-ttu-id="21ffc-113">Otevřete řešení TransactedReceiveScope.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="21ffc-113">Open the TransactedReceiveScope.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="21ffc-114">Sestavte řešení, stiskněte CTRL + SHIFT + B nebo vyberte **sestavit řešení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="21ffc-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="21ffc-115">Po sestavení proběhla úspěšně, klikněte pravým tlačítkem na řešení a vyberte **nastavit projekty po spuštění**.</span><span class="sxs-lookup"><span data-stu-id="21ffc-115">Once the build has succeeded, right-click the solution and select **Set Startup Projects**.</span></span> <span data-ttu-id="21ffc-116">V dialogovém okně vyberte **více projektů po spuštění** a zajistit akci pro oba projekty **spustit**.</span><span class="sxs-lookup"><span data-stu-id="21ffc-116">From the dialog, select **Multiple Startup Projects** and ensure the action for both projects is **Start**.</span></span>  
  
4.  <span data-ttu-id="21ffc-117">Stisknutím klávesy F5 nebo vyberte **spustit ladění** z **ladění** nabídky.</span><span class="sxs-lookup"><span data-stu-id="21ffc-117">Press F5 or select **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="21ffc-118">Alternativně můžete stisknutím kláves CTRL + F5 nebo vybrat **spustit bez ladění** z **ladění** nabídku spustit bez ladění.</span><span class="sxs-lookup"><span data-stu-id="21ffc-118">Alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="21ffc-119">Server musí být spuštěn před spuštěním klienta.</span><span class="sxs-lookup"><span data-stu-id="21ffc-119">The server must be running prior to starting the client.</span></span> <span data-ttu-id="21ffc-120">Výstup z okna konzoly, který je hostitelem služby určuje, kdy bylo zahájeno.</span><span class="sxs-lookup"><span data-stu-id="21ffc-120">The output from the console window hosting the service indicates when it has started.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="21ffc-121">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="21ffc-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="21ffc-122">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="21ffc-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="21ffc-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="21ffc-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="21ffc-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="21ffc-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`