---
title: "Postupy: povolení trvalost SQL pro pracovní postupy a služeb pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
caps.latest.revision: "36"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0b06479f1a649e60e141e807db091e207636edef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="3ad0a-102">Postupy: povolení trvalost SQL pro pracovní postupy a služeb pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="3ad0a-102">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>
<span data-ttu-id="3ad0a-103">Toto téma popisuje postup konfigurace úložiště Instance pracovního postupu SQL funkci tak, aby zapnout stálost pro vaše pracovní postupy a pracovní postup služby prostřednictvím kódu programu a pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>  
  
 <span data-ttu-id="3ad0a-104">Windows Server App Fabric zjednodušuje proces konfigurace trvalosti.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-104">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="3ad0a-105">[Konfigurace trvalosti infrastruktury aplikace](http://go.microsoft.com/fwlink/?LinkId=201204)</span><span class="sxs-lookup"><span data-stu-id="3ad0a-105"> [App Fabric Persistence Configuration](http://go.microsoft.com/fwlink/?LinkId=201204)</span></span>  
  
 <span data-ttu-id="3ad0a-106">Před použitím funkce ukládání Instance pracovního postupu SQL, vytvořte databázi, která používá funkci k zachování instancí pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-106">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="3ad0a-107">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Nastavení program zkopíruje soubory skriptu SQL přidružené k funkci úložiště Instance pracovního postupu SQL do složky %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-107">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="3ad0a-108">Spustit tyto soubory skriptu pro databázi systému SQL Server 2005 nebo SQL Server 2008, které chcete úložiště Instance SQL pracovního postupu, který chcete použít k uchování instancí pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-108">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="3ad0a-109">Nejprve spustit soubor SqlWorkflowInstanceStoreSchema.sql a potom spusťte soubor SqlWorkflowInstanceStoreLogic.sql.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-109">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ad0a-110">Chcete-li vyčištění databáze trvalost mít novou databázi, spusťte skripty v %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-110">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>  
>   
>  1.  <span data-ttu-id="3ad0a-111">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="3ad0a-111">SqlWorkflowInstanceStoreSchema.sql</span></span>  
> 2.  <span data-ttu-id="3ad0a-112">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="3ad0a-112">SqlWorkflowInstanceStoreLogic.sql</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3ad0a-113">Pokud nevytvoříte trvalost databáze, funkce ukládání Instance pracovního postupu SQL vyvolá výjimku podobné následující, když se hostitel pokusí zachovat pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-113">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>  
>   
>  <span data-ttu-id="3ad0a-114">System.Data.SqlClient.SqlException: Nelze nalézt uloženou proceduru 'System.Activities.DurableInstancing.CreateLockOwner.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-114">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>  
  
 <span data-ttu-id="3ad0a-115">Následující části popisují postup povolení trvalosti pro pracovní postupy a pomocí ukládání Instance pracovního postupu SQL služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-115">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="3ad0a-116">vlastnosti úložiště Instance pracovního postupu SQL, najdete v části [vlastnosti z pracovní postup Instance úložiště SQL](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="3ad0a-116"> properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).</span></span>  
  
## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="3ad0a-117">Povolení trvalosti pro pracovní postupy Self-Hosted, použít WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="3ad0a-117">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>  
 <span data-ttu-id="3ad0a-118">Můžete povolit trvalost vlastním hostováním pracovních postupů, které používají <xref:System.Activities.WorkflowApplication> programově pomocí <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> objektový model.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-118">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="3ad0a-119">Následující postup obsahuje kroky, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-119">The following procedure contains steps to do this.</span></span>  
  
#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="3ad0a-120">Chcete-li povolit trvalost pro pracovní postupy s vlastním hostováním</span><span class="sxs-lookup"><span data-stu-id="3ad0a-120">To enable persistence for self-hosted workflows</span></span>  
  
1.  <span data-ttu-id="3ad0a-121">Přidáte odkaz na System.Activites.DurableInstancing.dll.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-121">Add a reference to System.Activites.DurableInstancing.dll.</span></span>  
  
2.  <span data-ttu-id="3ad0a-122">Přidejte následující příkaz v horní části souboru se zdrojovým po existující příkazy "použití".</span><span class="sxs-lookup"><span data-stu-id="3ad0a-122">Add the following statement at the top of the source file after the existing "using" statements.</span></span>  
  
    ```csharp  
    using System.Activities.DurableInstancing;  
    ```  
  
3.  <span data-ttu-id="3ad0a-123">Vytvořit <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> a přiřadit ji ke <xref:System.Activities.WorkflowApplication.InstanceStore%2A> z <xref:System.Activities.WorkflowApplication> jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-123">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>  
  
    ```csharp  
    SqlWorkflowInstanceStore store =   
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");  
  
    WorkflowApplication wfApp =  
        new WorkflowApplication(new Workflow1());  
  
    wfApp.InstanceStore = store;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="3ad0a-124">V závislosti na vaší edicí systému SQL Server může být jiný název připojovacího řetězce serveru.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-124">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>  
  
4.  <span data-ttu-id="3ad0a-125">Vyvolání <xref:System.Activities.WorkflowApplication.Persist%2A> metodu <xref:System.Activities.WorkflowApplication> objekt pro zachování pracovního postupu, nebo <xref:System.Activities.WorkflowApplication.Unload%2A> metoda zachování a uvolnění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-125">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="3ad0a-126">Můžete také zpracovat <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> aktivováno událostí <xref:System.Activities.WorkflowApplication> objektu a vrátí odpovídající (<xref:System.Activities.PersistableIdleAction.Persist> nebo <xref:System.Activities.PersistableIdleAction.Unload>) členem <xref:System.Activities.PersistableIdleAction>.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-126">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        return PersistableIdleAction.Persist;  
    };  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="3ad0a-127">Najdete v článku [uchování aplikace pracovního postupu](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md) ukázku v [trvalost](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) příklad povolení trvalosti pro pracovní postupy pomocí <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>a [postupy: vytvoření a spuštění s dlouhým Spuštěný pracovní postup](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) krok [kurzu Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) pokyny krok za krokem.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-127">See the [Persisting a Workflow Application](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md) sample at [Persistence](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) for an example of enabling persistence for workflows using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, and the [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) for step by step instructions.</span></span>  
  
## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="3ad0a-128">Povolení trvalosti pro Self-Hosted služby pracovního postupu, který použít hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3ad0a-128">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>  
 <span data-ttu-id="3ad0a-129">Můžete povolit trvalost pro samoobslužné hostovaných pracovních postupů služby, které používají <xref:System.ServiceModel.WorkflowServiceHost> programově pomocí <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> třídy nebo <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> třídy.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-129">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>  
  
### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="3ad0a-130">Používání třídy SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="3ad0a-130">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>  
 <span data-ttu-id="3ad0a-131">Následující postup obsahuje kroky při použití <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> třídy zapnout stálost pro samoobslužné hostovaných pracovních postupů služby.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-131">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>  
  
##### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="3ad0a-132">Chcete-li povolit trvalost pomocí SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="3ad0a-132">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>  
  
1.  <span data-ttu-id="3ad0a-133">Přidáte odkaz na System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-133">Add a reference to the System.ServiceModel.dll.</span></span>  
  
2.  <span data-ttu-id="3ad0a-134">Přidejte následující příkaz v horní části souboru se zdrojovým po existující příkazy "použití".</span><span class="sxs-lookup"><span data-stu-id="3ad0a-134">Add the following statement at the top of the source file after the existing "using" statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Activities.Description;  
    ```  
  
3.  <span data-ttu-id="3ad0a-135">Vytvoření instance `WorkflowServiceHost` a přidat koncové body služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-135">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>  
  
    ```  
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));  
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");  
    ```  
  
4.  <span data-ttu-id="3ad0a-136">Vytvořit `SqlWorkflowInstanceStoreBehavior` objektu a vlastnosti objektu chování.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-136">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>  
  
    ```csharp  
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);  
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);  
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;  
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;  
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;  
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");  
    host.Description.Behaviors.Add(instanceStoreBehavior);  
    ```  
  
5.  <span data-ttu-id="3ad0a-137">Otevření hostitele služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-137">Open the workflow service host.</span></span>  
  
    ```vb  
    host.Open();  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="3ad0a-138">Najdete v článku [předdefinované konfigurace](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md) ukázku v [trvalost](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) příklad povolení trvalosti pro pracovní postup služby pomocí `SqlWorkflowInstanceStoreBehavior` – třída.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-138">See the [Built-in Configuration](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md) sample at [Persistence](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) for an example of enabling persistence for workflow services using the `SqlWorkflowInstanceStoreBehavior` class.</span></span>  
  
### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="3ad0a-139">Pomocí vlastnosti DurableInstancingOptions</span><span class="sxs-lookup"><span data-stu-id="3ad0a-139">Using the DurableInstancingOptions Property</span></span>  
 <span data-ttu-id="3ad0a-140">Když `SqlWorkflowInstanceStoreBehavior` platí, `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` je nastaven na `SqlWorkflowInstanceStore` objekt vytvořený pomocí hodnoty konfigurace.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-140">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="3ad0a-141">Můžete provést stejný prostřednictvím kódu programu se nastavit <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> vlastnost `WorkflowServiceHost` bez použití `SqlWorkflowInstanceStoreBehavior` třídy, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-141">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="3ad0a-142">Povolení trvalosti pro služby WAS-Hosted pracovního postupu, který pomocí hostitele služby pracovního postupu pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="3ad0a-142">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>  
 <span data-ttu-id="3ad0a-143">Trvalost pro vlastním hostováním nebo Windows Process Activation Service WAS hostovaný pracovní postup služby můžete povolit pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-143">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="3ad0a-144">Služby WAS hostovaný pracovní postup používá hostitele služby pracovního postupu, stejně jako služeb vlastním hostováním pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-144">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>  
  
 <span data-ttu-id="3ad0a-145">`SqlWorkflowInstanceStoreBehavior`, Chování služby, který vám umožní snadno změnit [úložiště Instance pracovního postupu SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) vlastnosti prostřednictvím konfigurační soubor XML.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-145">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="3ad0a-146">Pro služby hostované WAS pracovního postupu použijte v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-146">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="3ad0a-147">Následující příklad konfigurace ukazuje, jak nakonfigurovat úložiště Instance pracovního postupu SQL pomocí `sqlWorkflowInstanceStore` chování element v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-147">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>  
  
```xml  
<serviceBehaviors>  
    <behavior name="">  
        <sqlWorkflowInstanceStore   
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                    instanceEncodingOption="GZip | None"  
                    instanceCompletionAction="DeleteAll | DeleteNothing"  
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"  
                    hostLockRenewalPeriod="00:00:30"   
                    runnableInstancesDetectionPeriod="00:00:05">  
  
        <sqlWorkflowInstanceStore/>  
    </behavior>  
</serviceBehaviors>  
```  
  
 <span data-ttu-id="3ad0a-148">Pokud není nastaveno hodnoty `connectionString` nebo `connectionStringName` vlastnost úložiště Instance SQL pracovní postup používá výchozí připojovací řetězec s názvem `DefaultSqlWorkflowInstanceStoreConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-148">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>  
  
 <span data-ttu-id="3ad0a-149">Když `SqlWorkflowInstanceStoreBehavior` platí, `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` je nastaven na `SqlWorkflowInstanceStore` objekt vytvořený pomocí hodnoty konfigurace.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-149">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="3ad0a-150">Můžete provést stejný prostřednictvím kódu programu pro použití `SqlWorkflowInstanceStore` s `WorkflowServiceHost` bez použití elementu chování služby.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-150">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="3ad0a-151">Doporučuje se neukládejte citlivé informace, například uživatelská jména a hesla v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-151">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="3ad0a-152">Pokud ukládáte citlivé informace v souboru Web.config, je nutné zabezpečit přístup k souboru Web.config pomocí systému souborů, které jsou seznamy řízení přístupu (ACL).</span><span class="sxs-lookup"><span data-stu-id="3ad0a-152">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="3ad0a-153">Kromě toho můžete také zabezpečit hodnoty konfigurace v konfiguračním souboru jak je uvedeno v [šifrování informací pomocí chráněné konfigurace](http://go.microsoft.com/fwlink/?LinkId=178419).</span><span class="sxs-lookup"><span data-stu-id="3ad0a-153">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](http://go.microsoft.com/fwlink/?LinkId=178419).</span></span>  
  
### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="3ad0a-154">Machine.config elementy související s funkcí SQL ukládání Instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="3ad0a-154">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>  
 <span data-ttu-id="3ad0a-155">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Instalace přidá související s funkcí SQL ukládání Instance pracovního postupu k souboru Machine.config následující prvky:</span><span class="sxs-lookup"><span data-stu-id="3ad0a-155">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>  
  
-   <span data-ttu-id="3ad0a-156">Přidá k souboru Machine.config následující element rozšíření chování, takže můžete použít <`sqlWorkflowInstanceStore`> element chování služby v konfiguračním souboru konfigurace trvalosti pro vaše služby.</span><span class="sxs-lookup"><span data-stu-id="3ad0a-156">Adds the following behavior extension element to the Machine.config file so that you can use the <`sqlWorkflowInstanceStore`> service behavior element in the configuration file to configure persistence for your services.</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>  
            <extensions>  
                <behaviorExtensions>  
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
                </behaviorExtensions>  
            </extensions>  
        <system.serviceModel>  
    <configuration>  
    ```
