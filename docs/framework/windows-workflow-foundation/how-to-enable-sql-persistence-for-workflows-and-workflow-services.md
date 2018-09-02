---
title: 'Postupy: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 55869c3c8a957de98962378cc1a93e7058e24e38
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386731"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="e5f55-102">Postupy: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e5f55-102">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="e5f55-103">Toto téma popisuje postup konfigurace funkce SQL Store Instance pracovního postupu pro povolení trvalosti pro pracovní postupy a služby pracovních postupů, jak prostřednictvím kódu programu a pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="e5f55-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>  
  
<span data-ttu-id="e5f55-104">Windows Server App Fabric zjednodušuje proces konfigurace trvalosti.</span><span class="sxs-lookup"><span data-stu-id="e5f55-104">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="e5f55-105">Další informace najdete v tématu [konfigurace trvalosti infrastruktury aplikace](https://go.microsoft.com/fwlink/?LinkId=201204)</span><span class="sxs-lookup"><span data-stu-id="e5f55-105">For more information, see [App Fabric Persistence Configuration](https://go.microsoft.com/fwlink/?LinkId=201204)</span></span>  
  
<span data-ttu-id="e5f55-106">Před použitím funkce SQL Store Instance pracovního postupu, vytvořte databázi, která používá funkci k uchování instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e5f55-106">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="e5f55-107">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Nastavení program zkopíruje soubory skriptu SQL přidružený k funkci SQL Store Instance pracovního postupu do složky %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN.</span><span class="sxs-lookup"><span data-stu-id="e5f55-107">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="e5f55-108">Spusťte tyto soubory skriptu pro databázi systému SQL Server 2005 nebo SQL Server 2008, který má Store Instance pracovního postupu SQL použít k uchování instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e5f55-108">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="e5f55-109">Nejprve spusťte SqlWorkflowInstanceStoreSchema.sql souboru a pak spusťte soubor SqlWorkflowInstanceStoreLogic.sql.</span><span class="sxs-lookup"><span data-stu-id="e5f55-109">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>

> [!NOTE]
> <span data-ttu-id="e5f55-110">Vyčištění databáze stálost k nové databázi, spuštěním skriptů v %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e5f55-110">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>  
>
> 1. <span data-ttu-id="e5f55-111">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="e5f55-111">SqlWorkflowInstanceStoreSchema.sql</span></span>
> 2. <span data-ttu-id="e5f55-112">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="e5f55-112">SqlWorkflowInstanceStoreLogic.sql</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5f55-113">Pokud nevytvoříte databáze trvalosti, funkci SQL Store Instance pracovního postupu výjimku podobný následujícímu hostiteli se pokusí uchovávat pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="e5f55-113">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>  
> 
> <span data-ttu-id="e5f55-114">System.Data.SqlClient.SqlException: Nelze nalézt uloženou proceduru 'System.Activities.DurableInstancing.CreateLockOwner.</span><span class="sxs-lookup"><span data-stu-id="e5f55-114">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>  

<span data-ttu-id="e5f55-115">Následující části popisují postup povolení trvalosti pro pracovní postupy a služby pracovních postupů pomocí Store Instance pracovního postupu SQL.</span><span class="sxs-lookup"><span data-stu-id="e5f55-115">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> <span data-ttu-id="e5f55-116">Další informace o vlastnostech Store Instance pracovního postupu SQL najdete v tématu [vlastnosti z SQL pracovního postupu Instance Store](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="e5f55-116">For more information about properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).</span></span>  

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="e5f55-117">Povolení trvalosti pro pracovní postupy místním používajících WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="e5f55-117">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>

<span data-ttu-id="e5f55-118">Můžete zapnout stálost v místním prostředí pracovních postupů, které používají <xref:System.Activities.WorkflowApplication> prostřednictvím kódu programu pomocí <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> objektový model.</span><span class="sxs-lookup"><span data-stu-id="e5f55-118">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="e5f55-119">Následující postup obsahuje kroky k tomu.</span><span class="sxs-lookup"><span data-stu-id="e5f55-119">The following procedure contains steps to do this.</span></span>  

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="e5f55-120">K povolení trvalosti pro pracovní postupy v místním prostředí</span><span class="sxs-lookup"><span data-stu-id="e5f55-120">To enable persistence for self-hosted workflows</span></span>

1.  <span data-ttu-id="e5f55-121">Přidejte odkaz na System.Activites.DurableInstancing.dll.</span><span class="sxs-lookup"><span data-stu-id="e5f55-121">Add a reference to System.Activites.DurableInstancing.dll.</span></span>  
  
2.  <span data-ttu-id="e5f55-122">Přidejte následující příkaz v horní části souboru se zdrojovým za stávající příkazy "pomocí".</span><span class="sxs-lookup"><span data-stu-id="e5f55-122">Add the following statement at the top of the source file after the existing "using" statements.</span></span>  
  
    ```csharp  
    using System.Activities.DurableInstancing;  
    ```  
  
3.  <span data-ttu-id="e5f55-123">Vytvoření <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> a přiřaďte ho <xref:System.Activities.WorkflowApplication.InstanceStore%2A> z <xref:System.Activities.WorkflowApplication> jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="e5f55-123">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>
  
    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```
  
   > [!NOTE]
   > <span data-ttu-id="e5f55-124">V závislosti na vaší edici systému SQL Server může být jiný server název připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="e5f55-124">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>  
  
4. <span data-ttu-id="e5f55-125">Vyvolat <xref:System.Activities.WorkflowApplication.Persist%2A> metodu <xref:System.Activities.WorkflowApplication> objekt pro zachování pracovního postupu, nebo <xref:System.Activities.WorkflowApplication.Unload%2A> metodu pro uchování a uvolnit pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="e5f55-125">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="e5f55-126">Můžete také zpracovávat <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> událostí vyvolaných <xref:System.Activities.WorkflowApplication> objekt a vrátí odpovídající (<xref:System.Activities.PersistableIdleAction.Persist> nebo <xref:System.Activities.PersistableIdleAction.Unload>) člen <xref:System.Activities.PersistableIdleAction>.</span><span class="sxs-lookup"><span data-stu-id="e5f55-126">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>  
  
   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> <span data-ttu-id="e5f55-127">Najdete v článku [uchování aplikace pracovního postupu](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md) ukázku v [trvalost](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) příklad povolení trvalosti pro pracovní postupy pomocí <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>a [postupy: vytvoření a spuštění dlouhodobého Spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) kroku [kurz Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) pokyny krok za krokem.</span><span class="sxs-lookup"><span data-stu-id="e5f55-127">See the [Persisting a Workflow Application](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md) sample at [Persistence](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) for an example of enabling persistence for workflows using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, and the [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) for step by step instructions.</span></span>  

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="e5f55-128">Povolení trvalosti pro pracovní postup služby místním, použít hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e5f55-128">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>

<span data-ttu-id="e5f55-129">Můžete povolit trvalost pro služby v místním prostředí pracovních postupů, které používají <xref:System.ServiceModel.WorkflowServiceHost> prostřednictvím kódu programu pomocí <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> třídy nebo <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> třídy.</span><span class="sxs-lookup"><span data-stu-id="e5f55-129">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>  

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="e5f55-130">Používání třídy SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="e5f55-130">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>  

<span data-ttu-id="e5f55-131">Následující postup obsahuje kroky pro použití <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> třídy k povolení trvalosti pro služby pracovních postupů v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="e5f55-131">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>  

##### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="e5f55-132">Chcete-li zapnout stálost pomocí SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="e5f55-132">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>

1.  <span data-ttu-id="e5f55-133">Přidejte odkaz na System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="e5f55-133">Add a reference to the System.ServiceModel.dll.</span></span>  
  
2.  <span data-ttu-id="e5f55-134">Přidejte následující příkaz v horní části souboru se zdrojovým za stávající příkazy "pomocí".</span><span class="sxs-lookup"><span data-stu-id="e5f55-134">Add the following statement at the top of the source file after the existing "using" statements.</span></span>  
  
    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3.  <span data-ttu-id="e5f55-135">Vytvoření instance `WorkflowServiceHost` a přidají koncové body pro službu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e5f55-135">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>  
  
    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));  
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");  
    ``` 

4.  <span data-ttu-id="e5f55-136">Vytvoření `SqlWorkflowInstanceStoreBehavior` objektu a chcete-li nastavit vlastnosti chování objektu.</span><span class="sxs-lookup"><span data-stu-id="e5f55-136">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>  
  
    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5.  <span data-ttu-id="e5f55-137">Otevření hostitele služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e5f55-137">Open the workflow service host.</span></span>

    ```csharp
    host.Open();
    ```

> [!IMPORTANT]
> <span data-ttu-id="e5f55-138">Najdete v článku [integrovaných konfiguračních](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md) ukázku v [trvalost](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) příklad povolení trvalosti pro pracovní postup služby pomocí `SqlWorkflowInstanceStoreBehavior` třídy.</span><span class="sxs-lookup"><span data-stu-id="e5f55-138">See the [Built-in Configuration](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md) sample at [Persistence](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) for an example of enabling persistence for workflow services using the `SqlWorkflowInstanceStoreBehavior` class.</span></span>  

### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="e5f55-139">Pomocí vlastnosti DurableInstancingOptions</span><span class="sxs-lookup"><span data-stu-id="e5f55-139">Using the DurableInstancingOptions Property</span></span>

<span data-ttu-id="e5f55-140">Při `SqlWorkflowInstanceStoreBehavior` se použije `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` je nastavena na `SqlWorkflowInstanceStore` objekt vytvořený pomocí hodnoty konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e5f55-140">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="e5f55-141">Můžete provést stejný prostřednictvím kódu programu k nastavení <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> vlastnost `WorkflowServiceHost` bez použití `SqlWorkflowInstanceStoreBehavior` třídy, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="e5f55-141">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>  

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="e5f55-142">Povolení trvalosti pro pracovní postup služby WAS-Hosted, použít hostitele služby pracovního postupu pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="e5f55-142">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>

<span data-ttu-id="e5f55-143">Povolení trvalosti pro pracovní postup v místním prostředí nebo Windows Process Activation Service WAS hostované služby pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="e5f55-143">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="e5f55-144">Služba WAS hostované pracovního postupu používá hostitele služby pracovního postupu jako v místním prostředí pracovního postupu služby.</span><span class="sxs-lookup"><span data-stu-id="e5f55-144">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>  
  
<span data-ttu-id="e5f55-145">`SqlWorkflowInstanceStoreBehavior`, Chování služby, který vám umožní snadno změnit [Store Instance pracovního postupu SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) vlastnosti prostřednictvím konfigurace XML.</span><span class="sxs-lookup"><span data-stu-id="e5f55-145">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="e5f55-146">Pro služby WAS hostované pracovního postupu použijte soubor Web.config.</span><span class="sxs-lookup"><span data-stu-id="e5f55-146">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="e5f55-147">Následující příklad konfigurace ukazuje postup při konfiguraci Store Instance pracovního postupu SQL s použitím `sqlWorkflowInstanceStore` prvek chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="e5f55-147">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>  
  
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
  
<span data-ttu-id="e5f55-148">Pokud nenastavíte hodnoty `connectionString` nebo `connectionStringName` vlastnost, Store Instance SQL pracovní postup používá výchozí připojovací řetězec s názvem `DefaultSqlWorkflowInstanceStoreConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="e5f55-148">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>  
  
<span data-ttu-id="e5f55-149">Při `SqlWorkflowInstanceStoreBehavior` se použije `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` je nastavena na `SqlWorkflowInstanceStore` objekt vytvořený pomocí hodnoty konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e5f55-149">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="e5f55-150">Můžete provést stejný prostřednictvím kódu programu k použití `SqlWorkflowInstanceStore` s `WorkflowServiceHost` bez použití elementu chování služby.</span><span class="sxs-lookup"><span data-stu-id="e5f55-150">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>  
  
```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```
  
> [!IMPORTANT]
> <span data-ttu-id="e5f55-151">Doporučuje se, že v souboru Web.config neukládejte citlivé informace, jako jsou uživatelská jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="e5f55-151">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="e5f55-152">Pokud ukládáte citlivých informací v souboru Web.config, by měl zabezpečený přístup k souboru Web.config pomocí systému souborů seznamů řízení přístupu (ACL).</span><span class="sxs-lookup"><span data-stu-id="e5f55-152">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="e5f55-153">Kromě toho můžete také zabezpečit hodnoty konfigurace v konfiguračním souboru jak je uvedeno v [šifrování konfigurační informace pomocí Protected Configuration](https://go.microsoft.com/fwlink/?LinkId=178419).</span><span class="sxs-lookup"><span data-stu-id="e5f55-153">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](https://go.microsoft.com/fwlink/?LinkId=178419).</span></span>

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="e5f55-154">Machine.config elementy související s funkcí SQL Store Instance pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e5f55-154">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>

<span data-ttu-id="e5f55-155">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Instalací přidá následující elementy související s funkcí SQL Store Instance pracovního postupu k souboru Machine.config:</span><span class="sxs-lookup"><span data-stu-id="e5f55-155">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>  

-   <span data-ttu-id="e5f55-156">Přidá následující element rozšíření chování k souboru Machine.config, takže můžete použít <`sqlWorkflowInstanceStore`> element chování služby v konfiguračním souboru konfigurace trvalosti pro vaše služby.</span><span class="sxs-lookup"><span data-stu-id="e5f55-156">Adds the following behavior extension element to the Machine.config file so that you can use the <`sqlWorkflowInstanceStore`> service behavior element in the configuration file to configure persistence for your services.</span></span>

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
