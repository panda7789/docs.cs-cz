---
title: Správa pozastavené instance
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: 784ec3cdda8eedb188c3c776ed412ea40baf37ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182793"
---
# <a name="suspended-instance-management"></a><span data-ttu-id="27005-102">Správa pozastavené instance</span><span class="sxs-lookup"><span data-stu-id="27005-102">Suspended Instance Management</span></span>
<span data-ttu-id="27005-103">Tato ukázka ukazuje, jak spravovat instance pracovního postupu, které byly pozastaveny.</span><span class="sxs-lookup"><span data-stu-id="27005-103">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="27005-104">Výchozí akce <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> pro `AbandonAndSuspend`je .</span><span class="sxs-lookup"><span data-stu-id="27005-104">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="27005-105">To znamená, že ve výchozím nastavení neošetřené výjimky <xref:System.ServiceModel.WorkflowServiceHost> vyzývané z instance pracovního postupu hostované v způsobí, že instance, která má být uvolněna z paměti (opuštěné) a trvalé/trvalé verze instance, které mají být označeny jako pozastavena.</span><span class="sxs-lookup"><span data-stu-id="27005-105">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="27005-106">Pozastavená instance pracovního postupu nebude možné spustit, dokud nebude nepozastavena.</span><span class="sxs-lookup"><span data-stu-id="27005-106">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>

 <span data-ttu-id="27005-107">Ukázka ukazuje, jak nástroj příkazového řádku může být implementována pro dotaz na pozastavené instance a jak dát uživateli možnost obnovit nebo ukončit instanci.</span><span class="sxs-lookup"><span data-stu-id="27005-107">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="27005-108">V této ukázce služba pracovního postupu záměrně vyvolá výjimku, což způsobí, že se pozastaví.</span><span class="sxs-lookup"><span data-stu-id="27005-108">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="27005-109">Nástroj příkazového řádku pak lze použít k dotazování na instanci a následně obnovit nebo ukončit instanci.</span><span class="sxs-lookup"><span data-stu-id="27005-109">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="27005-110">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="27005-110">Demonstrates</span></span>
 <span data-ttu-id="27005-111"><xref:System.ServiceModel.WorkflowServiceHost>s <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> a v základu pracovního postupu systému Windows (WF).</span><span class="sxs-lookup"><span data-stu-id="27005-111"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in Windows Workflow Foundation (WF).</span></span>

## <a name="discussion"></a><span data-ttu-id="27005-112">Diskuse</span><span class="sxs-lookup"><span data-stu-id="27005-112">Discussion</span></span>
 <span data-ttu-id="27005-113">Nástroj příkazového řádku implementovaný v této ukázce je [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]specifický pro implementaci úložiště instancí SQL, která je dodávána v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="27005-113">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="27005-114">Pokud máte vlastní implementaci úložiště instancí, můžete tento nástroj `WorkflowInstanceCommand` upravit nahrazením implementací v ukázce implementacemi, které jsou specifické pro úložiště instancí.</span><span class="sxs-lookup"><span data-stu-id="27005-114">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>

 <span data-ttu-id="27005-115">Zapředpokladuovaná implementace spouští příkazy SQL proti úložišti instancí SQL přímo <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> do <xref:System.ServiceModel.WorkflowServiceHost> seznamu pozastavených instancí a spoléhá na přidání do instance, aby bylo možné instance obnovit nebo ukončit.</span><span class="sxs-lookup"><span data-stu-id="27005-115">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="27005-116">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="27005-116">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="27005-117">Tato ukázka vyžaduje, aby byly povoleny následující součásti systému Windows:</span><span class="sxs-lookup"><span data-stu-id="27005-117">This sample requires that the following Windows components are enabled:</span></span>

    1. <span data-ttu-id="27005-118">Server front zpráv (MSMQ) společnosti Microsoft</span><span class="sxs-lookup"><span data-stu-id="27005-118">Microsoft Message Queues (MSMQ) Server</span></span>

    2. <span data-ttu-id="27005-119">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="27005-119">SQL Server Express</span></span>

2. <span data-ttu-id="27005-120">Nastavte databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="27005-120">Set up the SQL Server database.</span></span>

    1. <span data-ttu-id="27005-121">Z příkazového řádku sady Visual Studio 2010 spusťte soubor setup.cmd z ukázkového adresáře SuspendedInstanceManagement, který provádí následující akce:</span><span class="sxs-lookup"><span data-stu-id="27005-121">From a Visual Studio 2010 command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>

        1. <span data-ttu-id="27005-122">Vytvoří databázi trvalosti pomocí sql server express.</span><span class="sxs-lookup"><span data-stu-id="27005-122">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="27005-123">Pokud databáze trvalosti již existuje, je vynechána a znovu vytvořena.</span><span class="sxs-lookup"><span data-stu-id="27005-123">If the persistence database already exists, then it is dropped and re-created</span></span>

        2. <span data-ttu-id="27005-124">Nastaví databázi pro trvalost.</span><span class="sxs-lookup"><span data-stu-id="27005-124">Sets up the database for persistence.</span></span>

        3. <span data-ttu-id="27005-125">Přidá iis APPPOOL\DefaultAppPool a NT AUTHORITY\Network Service do role InstanceStoreUsers, která byla definována při nastavování databáze pro trvalost.</span><span class="sxs-lookup"><span data-stu-id="27005-125">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>

3. <span data-ttu-id="27005-126">Nastavte frontu služeb.</span><span class="sxs-lookup"><span data-stu-id="27005-126">Set up the service queue.</span></span>

    1. <span data-ttu-id="27005-127">V sadě Visual Studio 2010 klikněte pravým tlačítkem myši na projekt **SampleWorkflowApp** a klikněte na **příkaz Nastavit jako spouštěcí projekt**.</span><span class="sxs-lookup"><span data-stu-id="27005-127">In Visual Studio 2010, right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>

    2. <span data-ttu-id="27005-128">Zkompilujte a spusťte SampleWorkflowApp stisknutím **klávesy F5**.</span><span class="sxs-lookup"><span data-stu-id="27005-128">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="27005-129">Tím se vytvoří požadovaná fronta.</span><span class="sxs-lookup"><span data-stu-id="27005-129">This will create the required queue.</span></span>

    3. <span data-ttu-id="27005-130">Stisknutím **klávesy Enter** ukončete aplikaci SampleWorkflowApp.</span><span class="sxs-lookup"><span data-stu-id="27005-130">Press **Enter** to stop the SampleWorkflowApp.</span></span>

    4. <span data-ttu-id="27005-131">Otevřete konzolu správa počítače spuštěním souboru Compmgmt.msc z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="27005-131">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>

    5. <span data-ttu-id="27005-132">Rozbalte **položku Služby a aplikace**, **Služba řízení front zpráv**, Soukromé **fronty**.</span><span class="sxs-lookup"><span data-stu-id="27005-132">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

    6. <span data-ttu-id="27005-133">Klepněte pravým tlačítkem myši na frontu **ReceiveTx** a vyberte příkaz **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="27005-133">Right click the **ReceiveTx** queue and select **Properties**.</span></span>

    7. <span data-ttu-id="27005-134">Vyberte kartu **Zabezpečení** a povolte **všem** oprávnění k **přijímání zpráv**, **náhledu zprávy**a **odeslat zprávu**.</span><span class="sxs-lookup"><span data-stu-id="27005-134">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>

4. <span data-ttu-id="27005-135">Teď spusťte ukázku.</span><span class="sxs-lookup"><span data-stu-id="27005-135">Now, run the sample.</span></span>

    1. <span data-ttu-id="27005-136">V sadě Visual Studio 2010 spusťte projekt SampleWorkflowApp znovu bez ladění stisknutím **kombinace kláves Ctrl+F5**.</span><span class="sxs-lookup"><span data-stu-id="27005-136">In Visual Studio 2010, run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="27005-137">V okně konzoly budou vytištěny dvě adresy koncového bodu: jedna pro <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>koncový bod aplikace a pak druhá z .</span><span class="sxs-lookup"><span data-stu-id="27005-137">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="27005-138">Poté se vytvoří instance pracovního postupu a v okně konzoly se zobrazí záznamy sledování pro tuto instanci.</span><span class="sxs-lookup"><span data-stu-id="27005-138">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="27005-139">Instance pracovního postupu vyvolá výjimku, která způsobí, že instance bude pozastavena a přerušena.</span><span class="sxs-lookup"><span data-stu-id="27005-139">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>

    2. <span data-ttu-id="27005-140">Nástroj příkazového řádku lze potom použít k další akci v některé z těchto instancí.</span><span class="sxs-lookup"><span data-stu-id="27005-140">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="27005-141">Syntaxe argumentů příkazového řádku je následující::</span><span class="sxs-lookup"><span data-stu-id="27005-141">The syntax for command line arguments is as follows::</span></span>

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         <span data-ttu-id="27005-142">Podporované příkazy `Query`jsou: `Resume`, `Terminate`a .</span><span class="sxs-lookup"><span data-stu-id="27005-142">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="27005-143">Přepínač InstanceId je vyžadován `Resume` `Terminate` pouze pro a operace.</span><span class="sxs-lookup"><span data-stu-id="27005-143">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="27005-144">Vyčištění (volitelné)</span><span class="sxs-lookup"><span data-stu-id="27005-144">To cleanup (Optional)</span></span>

1. <span data-ttu-id="27005-145">Otevřete konzolu správa počítače spuštěním souboru `vs2010` Compmgmt.msc z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="27005-145">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>

2. <span data-ttu-id="27005-146">Rozbalte **položku Služby a aplikace**, **Služba řízení front zpráv**, Soukromé **fronty**.</span><span class="sxs-lookup"><span data-stu-id="27005-146">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

3. <span data-ttu-id="27005-147">Odstraňte frontu **ReceiveTx.**</span><span class="sxs-lookup"><span data-stu-id="27005-147">Delete the **ReceiveTx** queue.</span></span>

4. <span data-ttu-id="27005-148">Chcete-li odebrat databázi trvalosti, spusťte cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="27005-148">To remove the persistence database, run cleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27005-149">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="27005-149">The samples may already be installed on your machine.</span></span> <span data-ttu-id="27005-150">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="27005-150">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="27005-151">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="27005-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="27005-152">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="27005-152">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
