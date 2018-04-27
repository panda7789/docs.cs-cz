---
title: Správa pozastavenou instancí
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f5073e9de217637141d7e3c9d70bb6a0b7a9cd0
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="suspended-instance-management"></a><span data-ttu-id="387d5-102">Správa pozastavenou instancí</span><span class="sxs-lookup"><span data-stu-id="387d5-102">Suspended Instance Management</span></span>
<span data-ttu-id="387d5-103">Tento příklad ukazuje, jak spravovat instancí pracovních postupů, které byly pozastaveny.</span><span class="sxs-lookup"><span data-stu-id="387d5-103">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="387d5-104">Výchozí akce pro <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> je `AbandonAndSuspend`.</span><span class="sxs-lookup"><span data-stu-id="387d5-104">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="387d5-105">To znamená, že ve výchozím nastavení, neošetřených výjimek vyvolaných z instance pracovního postupu hostované v <xref:System.ServiceModel.WorkflowServiceHost> způsobí, že instance má-li být uvolněn z paměti (opuštění) a trvale nebo trvalé verze instance označeno jako pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="387d5-105">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="387d5-106">Instanci pracovního postupu pozastavenou nebude možné spustit až po jejím pozastavení.</span><span class="sxs-lookup"><span data-stu-id="387d5-106">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>  
  
 <span data-ttu-id="387d5-107">Ukázka ukazuje, jak můžete implementovat nástroj příkazového řádku dotazu pro pozastavenou instance a poskytnout možnost obnovit nebo ukončení instance uživatele.</span><span class="sxs-lookup"><span data-stu-id="387d5-107">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="387d5-108">V této ukázce služby pracovního postupu záměrně vyvolá výjimku, způsobuje mohla stát pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="387d5-108">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="387d5-109">Nástroj příkazového řádku pak slouží k dotazování pro instanci a následně obnovit nebo ukončení instance.</span><span class="sxs-lookup"><span data-stu-id="387d5-109">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="387d5-110">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="387d5-110">Demonstrates</span></span>  
 <span data-ttu-id="387d5-111"><xref:System.ServiceModel.WorkflowServiceHost> s <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> v modelu Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="387d5-111"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="387d5-112">Diskusní</span><span class="sxs-lookup"><span data-stu-id="387d5-112">Discussion</span></span>  
 <span data-ttu-id="387d5-113">Nástroj příkazového řádku, které jsou implementované v této ukázce je specifická pro implementace úložiště instance SQL, který se dodává v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="387d5-113">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="387d5-114">Pokud máte vlastní implementaci instance úložiště, pak tento nástroj můžete přizpůsobit tak, že nahradíte `WorkflowInstanceCommand` implementace v ukázce s implementací, které jsou specifické pro instance úložiště.</span><span class="sxs-lookup"><span data-stu-id="387d5-114">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>  
  
 <span data-ttu-id="387d5-115">Zadaná implementace spouští příkazy SQL úložiště instance SQL přímo do seznamu pozastavenou instance, a přitom spoléhá na <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> přidán do <xref:System.ServiceModel.WorkflowServiceHost> Chcete-li obnovit nebo ukončení instance.</span><span class="sxs-lookup"><span data-stu-id="387d5-115">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="387d5-116">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="387d5-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="387d5-117">Tato ukázka vyžaduje, že jsou povoleny následující součásti systému Windows:</span><span class="sxs-lookup"><span data-stu-id="387d5-117">This sample requires that the following Windows components are enabled:</span></span>  
  
    1.  <span data-ttu-id="387d5-118">Server Microsoft zpráv fronty (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="387d5-118">Microsoft Message Queues (MSMQ) Server</span></span>  
  
    2.  <span data-ttu-id="387d5-119">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="387d5-119">SQL Server Express</span></span>  
  
2.  <span data-ttu-id="387d5-120">Nastavení databáze systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="387d5-120">Set up the SQL Server database.</span></span>  
  
    1.  <span data-ttu-id="387d5-121">Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazovém řádku spusťte "setup.cmd" z adresáře ukázka SuspendedInstanceManagement, který provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="387d5-121">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>  
  
        1.  <span data-ttu-id="387d5-122">Vytvoří databázi trvalost pomocí SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="387d5-122">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="387d5-123">Pokud už existuje databáze trvalost, pak je vyřadit a znovu vytvořit</span><span class="sxs-lookup"><span data-stu-id="387d5-123">If the persistence database already exists, then it is dropped and re-created</span></span>  
  
        2.  <span data-ttu-id="387d5-124">Nastaví databázi trvalosti.</span><span class="sxs-lookup"><span data-stu-id="387d5-124">Sets up the database for persistence.</span></span>  
  
        3.  <span data-ttu-id="387d5-125">Přidá IIS APPPOOL\DefaultAppPool a NT AUTHORITY\Network Service InstanceStoreUsers roli, která byla definována při nastavení databáze pro trvalost.</span><span class="sxs-lookup"><span data-stu-id="387d5-125">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>  
  
3.  <span data-ttu-id="387d5-126">Nastavte fronta služby.</span><span class="sxs-lookup"><span data-stu-id="387d5-126">Set up the service queue.</span></span>  
  
    1.  <span data-ttu-id="387d5-127">V [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], klikněte pravým tlačítkem myši **SampleWorkflowApp** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="387d5-127">In [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>  
  
    2.  <span data-ttu-id="387d5-128">Zkompilování a spuštění SampleWorkflowApp stisknutím **F5**.</span><span class="sxs-lookup"><span data-stu-id="387d5-128">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="387d5-129">Tím se vytvoří požadované fronty.</span><span class="sxs-lookup"><span data-stu-id="387d5-129">This will create the required queue.</span></span>  
  
    3.  <span data-ttu-id="387d5-130">Stiskněte klávesu **Enter** zastavit SampleWorkflowApp.</span><span class="sxs-lookup"><span data-stu-id="387d5-130">Press **Enter** to stop the SampleWorkflowApp.</span></span>  
  
    4.  <span data-ttu-id="387d5-131">Otevřete konzolu pro správu počítače spuštěním Compmgmt.msc z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="387d5-131">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>  
  
    5.  <span data-ttu-id="387d5-132">Rozbalte položku **služby a aplikace**, **služby Řízení front zpráv**, **soukromé fronty**.</span><span class="sxs-lookup"><span data-stu-id="387d5-132">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
    6.  <span data-ttu-id="387d5-133">Klikněte pravým tlačítkem **ReceiveTx** fronty a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="387d5-133">Right click the **ReceiveTx** queue and select **Properties**.</span></span>  
  
    7.  <span data-ttu-id="387d5-134">Vyberte **zabezpečení** kartě a povolit **Everyone** tak, aby měl oprávnění k **přijímat zprávy**, **prohlížet zprávy**, a  **Odeslat zprávu**.</span><span class="sxs-lookup"><span data-stu-id="387d5-134">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>  
  
4.  <span data-ttu-id="387d5-135">Nyní spusťte ukázku.</span><span class="sxs-lookup"><span data-stu-id="387d5-135">Now, run the sample.</span></span>  
  
    1.  <span data-ttu-id="387d5-136">V [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], znovu spusťte projekt SampleWorkflowApp bez ladění stisknutím **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="387d5-136">In [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="387d5-137">V okně konzoly budou vytištěny dvě adresy koncových bodů: jeden pro koncový bod aplikace a pak další z <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="387d5-137">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="387d5-138">Instance pracovního postupu je poté jste vytvořili, a sledování záznamů u dané instance se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="387d5-138">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="387d5-139">Instance pracovního postupu vyvolá výjimku způsobuje instanci systému na jde je pozastavit a byl zrušen.</span><span class="sxs-lookup"><span data-stu-id="387d5-139">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>  
  
    2.  <span data-ttu-id="387d5-140">Nástroj příkazového řádku pak lze provádět další akce na všech těchto instancí.</span><span class="sxs-lookup"><span data-stu-id="387d5-140">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="387d5-141">Tady je syntax argumenty pro příkazový řádek::</span><span class="sxs-lookup"><span data-stu-id="387d5-141">The syntax for command line arguments is as follows::</span></span>  
  
         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`  
  
         <span data-ttu-id="387d5-142">Jsou podporované příkazy: `Query`, `Resume`, a `Terminate`.</span><span class="sxs-lookup"><span data-stu-id="387d5-142">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="387d5-143">Identifikátor InstanceId přepínač je potřeba jenom pro `Resume` a `Terminate` operace.</span><span class="sxs-lookup"><span data-stu-id="387d5-143">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="387d5-144">Pro čištění (volitelné)</span><span class="sxs-lookup"><span data-stu-id="387d5-144">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="387d5-145">Otevřete konzolu pro správu počítače spuštěním Compmgmt.msc z `vs2010` příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="387d5-145">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>  
  
2.  <span data-ttu-id="387d5-146">Rozbalte položku **služby a aplikace**, **služby Řízení front zpráv**, **soukromé fronty**.</span><span class="sxs-lookup"><span data-stu-id="387d5-146">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
3.  <span data-ttu-id="387d5-147">Odstranit **ReceiveTx** fronty.</span><span class="sxs-lookup"><span data-stu-id="387d5-147">Delete the **ReceiveTx** queue.</span></span>  
  
4.  <span data-ttu-id="387d5-148">Chcete-li odebrat databázi trvalost, spusťte cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="387d5-148">To remove the persistence database, run cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="387d5-149">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="387d5-149">The samples may already be installed on your machine.</span></span> <span data-ttu-id="387d5-150">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="387d5-150">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="387d5-151">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="387d5-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="387d5-152">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="387d5-152">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
