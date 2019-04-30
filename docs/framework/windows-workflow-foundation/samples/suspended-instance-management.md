---
title: Správa pozastavené instance
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: ace4d2baef8f6b030790deaa5b1c20bb4b0cd30d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785902"
---
# <a name="suspended-instance-management"></a><span data-ttu-id="5aec4-102">Správa pozastavené instance</span><span class="sxs-lookup"><span data-stu-id="5aec4-102">Suspended Instance Management</span></span>
<span data-ttu-id="5aec4-103">Tento příklad ukazuje, jak spravovat instancí pracovních postupů, které byly pozastaveny.</span><span class="sxs-lookup"><span data-stu-id="5aec4-103">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="5aec4-104">Výchozí akce pro <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> je `AbandonAndSuspend`.</span><span class="sxs-lookup"><span data-stu-id="5aec4-104">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="5aec4-105">To znamená, že ve výchozím nastavení, neošetřené výjimky vyvolané z instance pracovního postupu hostitelem <xref:System.ServiceModel.WorkflowServiceHost> způsobí, že instance, která má být uvolněn z paměti (opuštěných) a verze durable/trvalé instance, kterou chcete označit, jak je pozastavena.</span><span class="sxs-lookup"><span data-stu-id="5aec4-105">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="5aec4-106">Instance pracovního postupu pozastavené nebude možné spustit až po jejím nezruší.</span><span class="sxs-lookup"><span data-stu-id="5aec4-106">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>

 <span data-ttu-id="5aec4-107">Vzorek ukazuje, jak nástroj příkazového řádku lze provést dotaz pro pozastavené instance a poskytnout uživateli možnost obnovit nebo ukončení instance.</span><span class="sxs-lookup"><span data-stu-id="5aec4-107">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="5aec4-108">V této ukázce Služba pracovního postupu záměrně vyvolá výjimku, vyvolá zablokuje.</span><span class="sxs-lookup"><span data-stu-id="5aec4-108">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="5aec4-109">Nástroj příkazového řádku pak umožňuje zadat dotaz pro instanci a následně obnovit nebo ukončení instance.</span><span class="sxs-lookup"><span data-stu-id="5aec4-109">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="5aec4-110">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="5aec4-110">Demonstrates</span></span>
 <span data-ttu-id="5aec4-111"><xref:System.ServiceModel.WorkflowServiceHost> s <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> ve Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="5aec4-111"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in Windows Workflow Foundation (WF).</span></span>

## <a name="discussion"></a><span data-ttu-id="5aec4-112">Diskuse</span><span class="sxs-lookup"><span data-stu-id="5aec4-112">Discussion</span></span>
 <span data-ttu-id="5aec4-113">Nástroj příkazového řádku, které jsou implementovány v této ukázce je specifické pro implementaci úložiště instance SQL, který se dodává v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5aec4-113">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="5aec4-114">Pokud máte vlastní implementaci v úložišti instancí, pak tento nástroj můžete přizpůsobit tak, že nahradíte `WorkflowInstanceCommand` implementace v ukázce s implementací, které jsou specifické pro vaše úložiště instancí.</span><span class="sxs-lookup"><span data-stu-id="5aec4-114">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>

 <span data-ttu-id="5aec4-115">Poskytnutou implementační spouští příkazy SQL pro ukládání instance SQL přímo na seznamu pozastavené instance, a spoléhá na <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> přidán do <xref:System.ServiceModel.WorkflowServiceHost> za účelem obnovení nebo ukončení instance.</span><span class="sxs-lookup"><span data-stu-id="5aec4-115">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5aec4-116">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="5aec4-116">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="5aec4-117">Tato ukázka vyžaduje, že jsou povoleny následující součásti Windows:</span><span class="sxs-lookup"><span data-stu-id="5aec4-117">This sample requires that the following Windows components are enabled:</span></span>

    1. <span data-ttu-id="5aec4-118">Server Microsoft zpráv fronty (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="5aec4-118">Microsoft Message Queues (MSMQ) Server</span></span>

    2. <span data-ttu-id="5aec4-119">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="5aec4-119">SQL Server Express</span></span>

2. <span data-ttu-id="5aec4-120">Nastavení databáze SQL serveru.</span><span class="sxs-lookup"><span data-stu-id="5aec4-120">Set up the SQL Server database.</span></span>

    1. <span data-ttu-id="5aec4-121">Z příkazového řádku sady Visual Studio 2010 spusťte "setup.cmd" adresáře ukázka SuspendedInstanceManagement, který provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="5aec4-121">From a Visual Studio 2010 command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>

        1. <span data-ttu-id="5aec4-122">Vytvoří databáze trvalosti pomocí SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="5aec4-122">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="5aec4-123">Pokud už existuje databáze trvalosti, pak je vyřadit a znovu vytvořit</span><span class="sxs-lookup"><span data-stu-id="5aec4-123">If the persistence database already exists, then it is dropped and re-created</span></span>

        2. <span data-ttu-id="5aec4-124">Nastaví databáze trvalosti.</span><span class="sxs-lookup"><span data-stu-id="5aec4-124">Sets up the database for persistence.</span></span>

        3. <span data-ttu-id="5aec4-125">Přidá IIS APPPOOL\DefaultAppPool a NT AUTHORITY\Network Service InstanceStoreUsers roli, která byla definována při nastavení databáze trvalosti.</span><span class="sxs-lookup"><span data-stu-id="5aec4-125">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>

3. <span data-ttu-id="5aec4-126">Nastavení služby queue.</span><span class="sxs-lookup"><span data-stu-id="5aec4-126">Set up the service queue.</span></span>

    1. <span data-ttu-id="5aec4-127">V sadě Visual Studio 2010, klikněte pravým tlačítkem myši **SampleWorkflowApp** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="5aec4-127">In Visual Studio 2010, right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>

    2. <span data-ttu-id="5aec4-128">Kompilace a spuštění SampleWorkflowApp stisknutím kombinace kláves **F5**.</span><span class="sxs-lookup"><span data-stu-id="5aec4-128">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="5aec4-129">Tím se vytvoří požadované frontě.</span><span class="sxs-lookup"><span data-stu-id="5aec4-129">This will create the required queue.</span></span>

    3. <span data-ttu-id="5aec4-130">Stisknutím klávesy **Enter** zastavit SampleWorkflowApp.</span><span class="sxs-lookup"><span data-stu-id="5aec4-130">Press **Enter** to stop the SampleWorkflowApp.</span></span>

    4. <span data-ttu-id="5aec4-131">Otevřete konzolu pro správu počítače spuštěním Compmgmt.msc z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5aec4-131">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>

    5. <span data-ttu-id="5aec4-132">Rozbalte **služby a aplikace**, **služby Řízení front zpráv**, **soukromé fronty**.</span><span class="sxs-lookup"><span data-stu-id="5aec4-132">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

    6. <span data-ttu-id="5aec4-133">Klikněte pravým tlačítkem myši **ReceiveTx** zařadit do fronty a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5aec4-133">Right click the **ReceiveTx** queue and select **Properties**.</span></span>

    7. <span data-ttu-id="5aec4-134">Vyberte **zabezpečení** kartu a povolit **Everyone** oprávnění pro **přijímat zprávy**, **prohlížet zprávy**, a  **Odeslat zprávu**.</span><span class="sxs-lookup"><span data-stu-id="5aec4-134">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>

4. <span data-ttu-id="5aec4-135">Nyní spusťte ukázku.</span><span class="sxs-lookup"><span data-stu-id="5aec4-135">Now, run the sample.</span></span>

    1. <span data-ttu-id="5aec4-136">V sadě Visual Studio 2010, spusťte projekt SampleWorkflowApp znovu bez ladění stisknutím kombinace kláves **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="5aec4-136">In Visual Studio 2010, run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="5aec4-137">Dvě adresy koncových bodů budou zobrazeny v okně konzoly: jeden pro koncový bod aplikace a pak ostatní z <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="5aec4-137">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="5aec4-138">Instance pracovního postupu se pak vytvoří a sledování záznamů pro tuto instanci se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="5aec4-138">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="5aec4-139">Instance pracovního postupu vyvolá výjimku, způsobující instance, kterou chcete pozastavit a byla přerušena.</span><span class="sxs-lookup"><span data-stu-id="5aec4-139">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>

    2. <span data-ttu-id="5aec4-140">Nástroj příkazového řádku je pak možné provádět další akce na kteroukoli z těchto instancí.</span><span class="sxs-lookup"><span data-stu-id="5aec4-140">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="5aec4-141">Syntaxe pro argumenty příkazového řádku je následující:</span><span class="sxs-lookup"><span data-stu-id="5aec4-141">The syntax for command line arguments is as follows::</span></span>

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         <span data-ttu-id="5aec4-142">Podporované příkazy: `Query`, `Resume`, a `Terminate`.</span><span class="sxs-lookup"><span data-stu-id="5aec4-142">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="5aec4-143">InstanceId přepínač je potřeba jenom pro `Resume` a `Terminate` operace.</span><span class="sxs-lookup"><span data-stu-id="5aec4-143">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="5aec4-144">Vyčistit (volitelné)</span><span class="sxs-lookup"><span data-stu-id="5aec4-144">To cleanup (Optional)</span></span>

1. <span data-ttu-id="5aec4-145">Otevřete konzolu pro správu počítače spuštěním Compmgmt.msc z `vs2010` příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5aec4-145">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>

2. <span data-ttu-id="5aec4-146">Rozbalte **služby a aplikace**, **služby Řízení front zpráv**, **soukromé fronty**.</span><span class="sxs-lookup"><span data-stu-id="5aec4-146">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

3. <span data-ttu-id="5aec4-147">Odstranit **ReceiveTx** fronty.</span><span class="sxs-lookup"><span data-stu-id="5aec4-147">Delete the **ReceiveTx** queue.</span></span>

4. <span data-ttu-id="5aec4-148">Pokud chcete odebrat databáze stálost, spusťte cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="5aec4-148">To remove the persistence database, run cleanup.cmd.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="5aec4-149">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="5aec4-149">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5aec4-150">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="5aec4-150">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5aec4-151">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="5aec4-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5aec4-152">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5aec4-152">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
