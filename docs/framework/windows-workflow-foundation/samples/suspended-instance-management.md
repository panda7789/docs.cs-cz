---
title: Správa pozastavené instance
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: 3f1f4f8edcbe0e05067d3ca739ef3d5f4fe4d798
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715947"
---
# <a name="suspended-instance-management"></a><span data-ttu-id="e627a-102">Správa pozastavené instance</span><span class="sxs-lookup"><span data-stu-id="e627a-102">Suspended Instance Management</span></span>
<span data-ttu-id="e627a-103">Tato ukázka předvádí, jak spravovat instance pracovních postupů, které byly pozastaveny.</span><span class="sxs-lookup"><span data-stu-id="e627a-103">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="e627a-104">Výchozí akce pro <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> je `AbandonAndSuspend`.</span><span class="sxs-lookup"><span data-stu-id="e627a-104">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="e627a-105">To znamená, že ve výchozím nastavení se neošetřené výjimky vyvolané z instance pracovního postupu hostované v <xref:System.ServiceModel.WorkflowServiceHost> způsobí odstranění instance z paměti (opuštěno) a trvalá/trvalá verze instance, která bude označena jako pozastavená.</span><span class="sxs-lookup"><span data-stu-id="e627a-105">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="e627a-106">Instanci pozastaveného pracovního postupu nebude možné spustit, dokud nebude pozastavena.</span><span class="sxs-lookup"><span data-stu-id="e627a-106">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>

 <span data-ttu-id="e627a-107">Ukázka ukazuje, jak lze nástroj příkazového řádku implementovat pro dotaz na pozastavené instance a jak dát uživateli možnost obnovit nebo ukončit instanci.</span><span class="sxs-lookup"><span data-stu-id="e627a-107">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="e627a-108">V této ukázce služba pracovního postupu záměrně vyvolá výjimku, což způsobí, že by se pozastavila.</span><span class="sxs-lookup"><span data-stu-id="e627a-108">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="e627a-109">Nástroj příkazového řádku se pak dá použít k dotazování na instanci a následnému obnovení nebo ukončení instance.</span><span class="sxs-lookup"><span data-stu-id="e627a-109">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e627a-110">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="e627a-110">Demonstrates</span></span>
 <span data-ttu-id="e627a-111"><xref:System.ServiceModel.WorkflowServiceHost> s <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> v programovací model Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="e627a-111"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in Windows Workflow Foundation (WF).</span></span>

## <a name="discussion"></a><span data-ttu-id="e627a-112">Účely</span><span class="sxs-lookup"><span data-stu-id="e627a-112">Discussion</span></span>
 <span data-ttu-id="e627a-113">Nástroj příkazového řádku implementovaný v této ukázce je specifický pro implementaci úložiště instance SQL, která je dodávána v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e627a-113">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="e627a-114">Máte-li vlastní implementaci úložiště instance, můžete tento nástroj přizpůsobit nahrazením `WorkflowInstanceCommand`ch implementací v ukázce s implementacemi, které jsou specifické pro vaše úložiště instancí.</span><span class="sxs-lookup"><span data-stu-id="e627a-114">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>

 <span data-ttu-id="e627a-115">Zadaná implementace spouští příkazy SQL pro úložiště instance SQL přímo v seznamu pozastavených instancí a spoléhá na <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> přidáno do <xref:System.ServiceModel.WorkflowServiceHost>, aby bylo možné obnovit nebo ukončit instance.</span><span class="sxs-lookup"><span data-stu-id="e627a-115">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e627a-116">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="e627a-116">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e627a-117">Tato ukázka vyžaduje, aby byly povoleny následující součásti systému Windows:</span><span class="sxs-lookup"><span data-stu-id="e627a-117">This sample requires that the following Windows components are enabled:</span></span>

    1. <span data-ttu-id="e627a-118">Server služby MSMQ (Microsoft Message Queue)</span><span class="sxs-lookup"><span data-stu-id="e627a-118">Microsoft Message Queues (MSMQ) Server</span></span>

    2. <span data-ttu-id="e627a-119">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="e627a-119">SQL Server Express</span></span>

2. <span data-ttu-id="e627a-120">Nastavte databázi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e627a-120">Set up the SQL Server database.</span></span>

    1. <span data-ttu-id="e627a-121">Z příkazového řádku sady Visual Studio 2010 spusťte "Setup. cmd" z ukázkového adresáře SuspendedInstanceManagement, který provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="e627a-121">From a Visual Studio 2010 command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>

        1. <span data-ttu-id="e627a-122">Vytvoří databázi trvalosti pomocí SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="e627a-122">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="e627a-123">Pokud databáze trvalosti už existuje, pak se vynechá a znovu vytvoří.</span><span class="sxs-lookup"><span data-stu-id="e627a-123">If the persistence database already exists, then it is dropped and re-created</span></span>

        2. <span data-ttu-id="e627a-124">Nastaví databázi pro trvalost.</span><span class="sxs-lookup"><span data-stu-id="e627a-124">Sets up the database for persistence.</span></span>

        3. <span data-ttu-id="e627a-125">Přidá službu IIS APPPOOL\DefaultAppPool a NT AUTHORITY\Network Service do role InstanceStoreUsers, která byla definována při nastavování databáze pro trvalost.</span><span class="sxs-lookup"><span data-stu-id="e627a-125">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>

3. <span data-ttu-id="e627a-126">Nastavte frontu služby.</span><span class="sxs-lookup"><span data-stu-id="e627a-126">Set up the service queue.</span></span>

    1. <span data-ttu-id="e627a-127">V sadě Visual Studio 2010 klikněte pravým tlačítkem na projekt **SampleWorkflowApp** a klikněte na **nastavit jako spouštěný projekt**.</span><span class="sxs-lookup"><span data-stu-id="e627a-127">In Visual Studio 2010, right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>

    2. <span data-ttu-id="e627a-128">Zkompilujte a spusťte SampleWorkflowApp stisknutím klávesy **F5**.</span><span class="sxs-lookup"><span data-stu-id="e627a-128">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="e627a-129">Tím se vytvoří požadovaná fronta.</span><span class="sxs-lookup"><span data-stu-id="e627a-129">This will create the required queue.</span></span>

    3. <span data-ttu-id="e627a-130">Stisknutím klávesy **ENTER** zastavte SampleWorkflowApp.</span><span class="sxs-lookup"><span data-stu-id="e627a-130">Press **Enter** to stop the SampleWorkflowApp.</span></span>

    4. <span data-ttu-id="e627a-131">Spusťte compmgmt. msc z příkazového řádku a otevřete tak konzolu pro správu počítače.</span><span class="sxs-lookup"><span data-stu-id="e627a-131">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>

    5. <span data-ttu-id="e627a-132">Rozbalte **službu a aplikace**, **Služba Řízení front zpráv**a **soukromé fronty**.</span><span class="sxs-lookup"><span data-stu-id="e627a-132">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

    6. <span data-ttu-id="e627a-133">Klikněte pravým tlačítkem na frontu **ReceiveTx** a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="e627a-133">Right click the **ReceiveTx** queue and select **Properties**.</span></span>

    7. <span data-ttu-id="e627a-134">Vyberte kartu **zabezpečení** a umožněte **všem** , aby měli oprávnění **přijímat zprávy**, **prohlížet zprávy**a **odesílat zprávy**.</span><span class="sxs-lookup"><span data-stu-id="e627a-134">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>

4. <span data-ttu-id="e627a-135">Nyní spusťte ukázku.</span><span class="sxs-lookup"><span data-stu-id="e627a-135">Now, run the sample.</span></span>

    1. <span data-ttu-id="e627a-136">V aplikaci Visual Studio 2010 znovu spusťte projekt SampleWorkflowApp bez ladění stisknutím **kombinace kláves CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="e627a-136">In Visual Studio 2010, run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="e627a-137">V okně konzoly budou vytištěny dvě adresy koncových bodů: jeden pro koncový bod aplikace a další z <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="e627a-137">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="e627a-138">Instance pracovního postupu je pak vytvořena a sledování záznamů pro tuto instanci se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="e627a-138">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="e627a-139">Instance pracovního postupu vyvolá výjimku způsobující pozastavení a přerušení instance.</span><span class="sxs-lookup"><span data-stu-id="e627a-139">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>

    2. <span data-ttu-id="e627a-140">Nástroj příkazového řádku je pak možné použít k provedení dalších akcí na kterékoli z těchto instancí.</span><span class="sxs-lookup"><span data-stu-id="e627a-140">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="e627a-141">Syntaxe pro argumenty příkazového řádku je následující::</span><span class="sxs-lookup"><span data-stu-id="e627a-141">The syntax for command line arguments is as follows::</span></span>

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         <span data-ttu-id="e627a-142">Podporovány jsou následující příkazy: `Query`, `Resume`a `Terminate`.</span><span class="sxs-lookup"><span data-stu-id="e627a-142">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="e627a-143">Přepínač InstanceId je vyžadován pouze pro operace `Resume` a `Terminate`.</span><span class="sxs-lookup"><span data-stu-id="e627a-143">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="e627a-144">K vyčištění (volitelné)</span><span class="sxs-lookup"><span data-stu-id="e627a-144">To cleanup (Optional)</span></span>

1. <span data-ttu-id="e627a-145">Spusťte příkaz compmgmt. msc v `vs2010` příkazovém řádku a otevřete konzolu pro správu počítače.</span><span class="sxs-lookup"><span data-stu-id="e627a-145">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>

2. <span data-ttu-id="e627a-146">Rozbalte **službu a aplikace**, **Služba Řízení front zpráv**a **soukromé fronty**.</span><span class="sxs-lookup"><span data-stu-id="e627a-146">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

3. <span data-ttu-id="e627a-147">Odstraňte frontu **ReceiveTx** .</span><span class="sxs-lookup"><span data-stu-id="e627a-147">Delete the **ReceiveTx** queue.</span></span>

4. <span data-ttu-id="e627a-148">Chcete-li odebrat databázi trvalosti, spusťte příkaz Cleanup. cmd.</span><span class="sxs-lookup"><span data-stu-id="e627a-148">To remove the persistence database, run cleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e627a-149">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="e627a-149">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e627a-150">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="e627a-150">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e627a-151">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="e627a-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e627a-152">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e627a-152">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
