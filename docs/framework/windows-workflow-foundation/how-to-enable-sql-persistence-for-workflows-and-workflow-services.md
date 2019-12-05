---
title: 'Postupy: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů'
ms.date: 03/30/2017
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: bef95dbeaaa96678a66ba94494a0207c7314c326
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802580"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="650fa-102">Postupy: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="650fa-102">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="650fa-103">Toto téma popisuje, jak nakonfigurovat funkci úložiště instance pracovního postupu SQL tak, aby umožňovala trvalé uchovávání pracovních postupů a služeb pracovních postupů programově i pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="650fa-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>

<span data-ttu-id="650fa-104">Windows Server App Fabric zjednodušuje proces konfigurace trvalosti.</span><span class="sxs-lookup"><span data-stu-id="650fa-104">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="650fa-105">Další informace najdete v tématu [Konfigurace trvalosti aplikace App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee790848(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="650fa-105">For more information, see [App Fabric Persistence Configuration](https://docs.microsoft.com/previous-versions/appfabric/ee790848(v=azure.10)).</span></span>

<span data-ttu-id="650fa-106">Před použitím funkce úložiště instance pracovního postupu SQL vytvořte databázi, kterou funkce používá k zachování instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="650fa-106">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="650fa-107">Program pro nastavení [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kopíruje soubory skriptu SQL přidružené k funkci úložiště instancí pracovních postupů SQL do složky%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN.</span><span class="sxs-lookup"><span data-stu-id="650fa-107">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="650fa-108">Tyto soubory skriptu spusťte v databázi SQL Server 2005 nebo SQL Server 2008, kterou chcete, aby úložiště instancí pracovních postupů SQL použilo k zachování instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="650fa-108">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="650fa-109">Nejprve spusťte soubor SqlWorkflowInstanceStoreSchema. SQL a potom spusťte soubor SqlWorkflowInstanceStoreLogic. SQL.</span><span class="sxs-lookup"><span data-stu-id="650fa-109">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>

> [!NOTE]
> <span data-ttu-id="650fa-110">Chcete-li vyčistit databázi trvalosti, aby měla novou databázi, spusťte skripty v%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="650fa-110">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>
>
> 1. <span data-ttu-id="650fa-111">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="650fa-111">SqlWorkflowInstanceStoreSchema.sql</span></span>
> 2. <span data-ttu-id="650fa-112">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="650fa-112">SqlWorkflowInstanceStoreLogic.sql</span></span>

> [!IMPORTANT]
> <span data-ttu-id="650fa-113">Pokud nevytvoříte databázi trvalosti, funkce úložiště instance pracovního postupu SQL vyvolá výjimku, která je podobná následujícímu, když se hostitel pokusí uchovat pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="650fa-113">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>
>
> <span data-ttu-id="650fa-114">System. data. SqlClient. SqlException: nepovedlo se najít uloženou proceduru System. Activities. DurableInstancing. CreateLockOwner.</span><span class="sxs-lookup"><span data-stu-id="650fa-114">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>

<span data-ttu-id="650fa-115">Následující části popisují, jak povolit trvalost pro pracovní postupy a služby pracovních postupů pomocí úložiště instance pracovního postupu SQL.</span><span class="sxs-lookup"><span data-stu-id="650fa-115">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> <span data-ttu-id="650fa-116">Další informace o vlastnostech úložiště instancí pracovních postupů SQL najdete v tématu [vlastnosti úložiště instance pracovního postupu SQL](properties-of-sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="650fa-116">For more information about properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](properties-of-sql-workflow-instance-store.md).</span></span>

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="650fa-117">Povolení trvalosti pro samoobslužné pracovní postupy, které používají WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="650fa-117">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>

<span data-ttu-id="650fa-118">Trvalost můžete povolit pro pracovní postupy v místním prostředí, které používají <xref:System.Activities.WorkflowApplication> programově pomocí modelu <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> objektů.</span><span class="sxs-lookup"><span data-stu-id="650fa-118">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="650fa-119">Následující postup obsahuje kroky.</span><span class="sxs-lookup"><span data-stu-id="650fa-119">The following procedure contains steps to do this.</span></span>

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="650fa-120">Postup povolení trvalosti pro pracovní postupy v místním prostředí</span><span class="sxs-lookup"><span data-stu-id="650fa-120">To enable persistence for self-hosted workflows</span></span>

1. <span data-ttu-id="650fa-121">Přidejte odkaz na System. Activities. DurableInstancing. dll.</span><span class="sxs-lookup"><span data-stu-id="650fa-121">Add a reference to System.Activities.DurableInstancing.dll.</span></span>

2. <span data-ttu-id="650fa-122">Přidejte následující příkaz v horní části zdrojového souboru po existující příkazy using.</span><span class="sxs-lookup"><span data-stu-id="650fa-122">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. <span data-ttu-id="650fa-123">Vytvořte <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> a přiřaďte ji <xref:System.Activities.WorkflowApplication.InstanceStore%2A> <xref:System.Activities.WorkflowApplication>, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="650fa-123">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > <span data-ttu-id="650fa-124">V závislosti na vaší edici SQL Server se název serveru připojovacího řetězce může lišit.</span><span class="sxs-lookup"><span data-stu-id="650fa-124">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

4. <span data-ttu-id="650fa-125">Vyvolejte metodu <xref:System.Activities.WorkflowApplication.Persist%2A> v objektu <xref:System.Activities.WorkflowApplication> pro zachování pracovního postupu, nebo <xref:System.Activities.WorkflowApplication.Unload%2A> metodu pro zachování a uvolnění pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="650fa-125">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="650fa-126">Můžete také zpracovat událost <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> vyvolanou objektem <xref:System.Activities.WorkflowApplication> a vrátit odpovídající člen (<xref:System.Activities.PersistableIdleAction.Persist> nebo <xref:System.Activities.PersistableIdleAction.Unload>) <xref:System.Activities.PersistableIdleAction>.</span><span class="sxs-lookup"><span data-stu-id="650fa-126">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> <span data-ttu-id="650fa-127">Podrobné pokyny najdete v tématu [Postupy: vytvoření a spuštění dlouho běžícího pracovního postupu](how-to-create-and-run-a-long-running-workflow.md) v [kurzu Začínáme](getting-started-tutorial.md) .</span><span class="sxs-lookup"><span data-stu-id="650fa-127">See the [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](getting-started-tutorial.md) for step by step instructions.</span></span>

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="650fa-128">Povolení trvalosti pro samoobslužné služby pracovních postupů, které používají hostitele</span><span class="sxs-lookup"><span data-stu-id="650fa-128">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>

<span data-ttu-id="650fa-129">Můžete povolit trvalost pro samoobslužné služby pracovních postupů, které používají <xref:System.ServiceModel.WorkflowServiceHost> programově pomocí <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> třídy nebo třídy <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A>.</span><span class="sxs-lookup"><span data-stu-id="650fa-129">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="650fa-130">Použití třídy SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="650fa-130">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>

<span data-ttu-id="650fa-131">Následující postup obsahuje kroky pro použití třídy <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> k povolení trvalosti pro samoobslužné služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="650fa-131">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="650fa-132">Postup povolení trvalosti pomocí SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="650fa-132">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>

1. <span data-ttu-id="650fa-133">Přidejte odkaz na System. ServiceModel. dll.</span><span class="sxs-lookup"><span data-stu-id="650fa-133">Add a reference to the System.ServiceModel.dll.</span></span>

2. <span data-ttu-id="650fa-134">Přidejte následující příkaz v horní části zdrojového souboru po existující příkazy using.</span><span class="sxs-lookup"><span data-stu-id="650fa-134">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. <span data-ttu-id="650fa-135">Vytvořte instanci `WorkflowServiceHost` a přidejte koncové body pro službu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="650fa-135">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. <span data-ttu-id="650fa-136">Vytvořte objekt `SqlWorkflowInstanceStoreBehavior` a nastavte vlastnosti objektu chování.</span><span class="sxs-lookup"><span data-stu-id="650fa-136">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. <span data-ttu-id="650fa-137">Otevřete hostitele služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="650fa-137">Open the workflow service host.</span></span>

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="650fa-138">Použití vlastnosti DurableInstancingOptions</span><span class="sxs-lookup"><span data-stu-id="650fa-138">Using the DurableInstancingOptions Property</span></span>

<span data-ttu-id="650fa-139">Při použití `SqlWorkflowInstanceStoreBehavior` je `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` nastavena na objekt `SqlWorkflowInstanceStore` vytvořený pomocí hodnot konfigurace.</span><span class="sxs-lookup"><span data-stu-id="650fa-139">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="650fa-140">Můžete to samé provést programově pro nastavení vlastnosti <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> `WorkflowServiceHost` bez použití třídy `SqlWorkflowInstanceStoreBehavior`, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="650fa-140">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="650fa-141">Povolení trvalosti u hostovaných služeb pracovních postupů, které používají hostitele s použitím konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="650fa-141">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>

<span data-ttu-id="650fa-142">Můžete povolit trvalost pro samoobslužné služby nebo aktivační službu procesů systému Windows (WAS) – hostované služby pracovního postupu pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="650fa-142">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="650fa-143">Služba pracovního postupu, která je hostovaná, používá službu WorkflowServiceHost jako samoobslužné služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="650fa-143">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>

<span data-ttu-id="650fa-144">`SqlWorkflowInstanceStoreBehavior`, což je chování služby, které umožňuje pohodlně měnit vlastnosti [úložiště instancí pracovních postupů SQL](sql-workflow-instance-store.md) prostřednictvím konfigurace XML.</span><span class="sxs-lookup"><span data-stu-id="650fa-144">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="650fa-145">U hostovaných služeb pracovních postupů použijte soubor Web. config.</span><span class="sxs-lookup"><span data-stu-id="650fa-145">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="650fa-146">Následující příklad konfigurace ukazuje, jak nakonfigurovat úložiště instance pracovního postupu SQL pomocí elementu `sqlWorkflowInstanceStore` chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="650fa-146">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>

```xml
<serviceBehaviors>
    <behavior name="">
        <sqlWorkflowInstanceStore
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"
                    instanceEncodingOption="GZip | None"
                    instanceCompletionAction="DeleteAll | DeleteNothing"
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"
                    hostLockRenewalPeriod="00:00:30"
                    runnableInstancesDetectionPeriod="00:00:05" />

    </behavior>
</serviceBehaviors>
```

<span data-ttu-id="650fa-147">Pokud nenastavíte hodnoty pro `connectionString` nebo vlastnost `connectionStringName`, úložiště instance pracovního postupu SQL použije výchozí pojmenovaný připojovací řetězec `DefaultSqlWorkflowInstanceStoreConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="650fa-147">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>

<span data-ttu-id="650fa-148">Při použití `SqlWorkflowInstanceStoreBehavior` je `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` nastavena na objekt `SqlWorkflowInstanceStore` vytvořený pomocí hodnot konfigurace.</span><span class="sxs-lookup"><span data-stu-id="650fa-148">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="650fa-149">Můžete to samé provést programově a použít `SqlWorkflowInstanceStore` s `WorkflowServiceHost` bez použití prvku chování služby.</span><span class="sxs-lookup"><span data-stu-id="650fa-149">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> <span data-ttu-id="650fa-150">Doporučujeme Neukládat citlivé informace, jako jsou uživatelská jména a hesla, do souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="650fa-150">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="650fa-151">Pokud ukládáte citlivé informace do souboru Web. config, měli byste zabezpečený přístup k souboru Web. config pomocí seznamů Access Control systému souborů (ACL).</span><span class="sxs-lookup"><span data-stu-id="650fa-151">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="650fa-152">Kromě toho můžete také zabezpečit konfigurační hodnoty v rámci konfiguračního souboru, jak je uvedeno v části [šifrování informací o konfiguraci pomocí chráněné konfigurace](https://docs.microsoft.com/en-us/previous-versions/aspnet/53tyfkaw(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="650fa-152">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](https://docs.microsoft.com/en-us/previous-versions/aspnet/53tyfkaw(v=vs.100)).</span></span>

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="650fa-153">Elementy Machine. config související s funkcí úložiště instance pracovního postupu SQL</span><span class="sxs-lookup"><span data-stu-id="650fa-153">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>

<span data-ttu-id="650fa-154">Instalace [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] přidá do souboru Machine. config následující prvky týkající se funkce úložiště instance pracovního postupu SQL:</span><span class="sxs-lookup"><span data-stu-id="650fa-154">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>

- <span data-ttu-id="650fa-155">Přidá do souboru Machine. config následující prvek rozšíření chování, aby bylo možné v konfiguračním souboru použít prvek chování služby \<sqlWorkflowInstanceStore > a nakonfigurovat trvalost pro vaše služby.</span><span class="sxs-lookup"><span data-stu-id="650fa-155">Adds the following behavior extension element to the Machine.config file so that you can use the \<sqlWorkflowInstanceStore> service behavior element in the configuration file to configure persistence for your services.</span></span>

    ```xml
    <configuration>
        <system.serviceModel>
            <extensions>
                <behaviorExtensions>
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
                </behaviorExtensions>
            </extensions>
        </system.serviceModel>
    </configuration>
    ```
