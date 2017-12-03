---
title: "Postupy: vytvoření vlastní Instance úložiště"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 593c4e9d-8a49-4e12-8257-cee5e6b4c075
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e820815a7047d91065db5308cc289f063191511
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-instance-store"></a><span data-ttu-id="e5617-102">Postupy: vytvoření vlastní Instance úložiště</span><span class="sxs-lookup"><span data-stu-id="e5617-102">How to: Create a Custom Instance Store</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="e5617-103">obsahuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, úložiště instance, které používá systém SQL Server se zachovat data pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e5617-103"> contains <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, an instance store that uses SQL Server to persist workflow data.</span></span> <span data-ttu-id="e5617-104">Pokud vaše aplikace je potřeba zachovat data pracovního postupu na jiné médium, například jiné databázi nebo systému souborů, můžete implementovat vlastní instance úložiště.</span><span class="sxs-lookup"><span data-stu-id="e5617-104">If your application is required to persist workflow data to another medium, such as a different database or a file system, you can implement a custom instance store.</span></span> <span data-ttu-id="e5617-105">Vlastní instance úložiště je vytvořeno tím, že rozšíří abstraktní <xref:System.Runtime.DurableInstancing.InstanceStore> třídy a metody, které jsou požadovány pro implementaci implementace.</span><span class="sxs-lookup"><span data-stu-id="e5617-105">A custom instance store is created by extending the abstract <xref:System.Runtime.DurableInstancing.InstanceStore> class and implementing the methods that are required for the implementation.</span></span> <span data-ttu-id="e5617-106">Pro úplnou implementaci vlastní instance úložiště, najdete v článku [podnikové procesu nákupu](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="e5617-106">For a complete implementation of a custom instance store, see the [Corporate Purchase Process](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) sample.</span></span>  
  
## <a name="implementing-the-begintrycommand-method"></a><span data-ttu-id="e5617-107">Implementace metody BeginTryCommand</span><span class="sxs-lookup"><span data-stu-id="e5617-107">Implementing the BeginTryCommand method</span></span>  
 <span data-ttu-id="e5617-108"><xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> Odesílají na ukládání instance modul trvalost.</span><span class="sxs-lookup"><span data-stu-id="e5617-108">The <xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> is sent to the instance store by the persistence engine.</span></span> <span data-ttu-id="e5617-109">Typ `command` parametr označuje příkazu, na který je spouštěna; tento parametr může být z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="e5617-109">The type of the `command` parameter indicates which command is being executed; this parameter can be of the following types:</span></span>  
  
-   <span data-ttu-id="e5617-110"><xref:System.Activities.DurableInstancing.SaveWorkflowCommand>: Modul trvalost odešle tento příkaz do ukládání instance pracovního postupu se má uložit trvale na střední úložiště.</span><span class="sxs-lookup"><span data-stu-id="e5617-110"><xref:System.Activities.DurableInstancing.SaveWorkflowCommand>: The persistence engine sends this command to the instance store when a workflow is to be persisted to the storage medium.</span></span> <span data-ttu-id="e5617-111">Trvalost dat pracovního postupu je poskytnutá metodě v <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> členem `command` parametr.</span><span class="sxs-lookup"><span data-stu-id="e5617-111">The workflow persistence data is provided to the method in the <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> member of the `command` parameter.</span></span>  
  
-   <span data-ttu-id="e5617-112"><xref:System.Activities.DurableInstancing.LoadWorkflowCommand>: Když pracovní postup je třeba načíst z úložiště střední modul trvalost odešle tento příkaz k úložišti instance.</span><span class="sxs-lookup"><span data-stu-id="e5617-112"><xref:System.Activities.DurableInstancing.LoadWorkflowCommand>: The persistence engine sends this command to the instance store when a workflow is to be loaded from the storage medium.</span></span> <span data-ttu-id="e5617-113">Načíst ID instance pracovního postupu je poskytnutá metodě v `instanceId` parametr <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> vlastnost `context` parametr.</span><span class="sxs-lookup"><span data-stu-id="e5617-113">The instance ID of the workflow to be loaded is provided to the method in the `instanceId` parameter of the <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> property of the `context` parameter.</span></span>  
  
-   <span data-ttu-id="e5617-114"><xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>: Trvalost modul odešle tento příkaz k instanci při uložení <xref:System.ServiceModel.Activities.WorkflowServiceHost> musí být registrován jako vlastníka zámku.</span><span class="sxs-lookup"><span data-stu-id="e5617-114"><xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>: The persistence engine sends this command to the instance store when a <xref:System.ServiceModel.Activities.WorkflowServiceHost> must be registered as a lock owner.</span></span> <span data-ttu-id="e5617-115">ID instance pracovního postupu aktuální by měly být zadané instance úložiště pomocí <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> metodu `context` parametr.</span><span class="sxs-lookup"><span data-stu-id="e5617-115">The instance ID of the current workflow should be provided to the instance store using <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> method of the `context` parameter.</span></span>  
  
     <span data-ttu-id="e5617-116">Následující fragment kódu ukazuje, jak implementovat příkaz CreateWorkflowOwner přiřadit vlastníka explicitní zámku.</span><span class="sxs-lookup"><span data-stu-id="e5617-116">The following code snippet demonstrates how to implement the CreateWorkflowOwner command to assign an explicit lock owner.</span></span>  
  
    ```  
    XName WFInstanceScopeName = XName.Get(scopeName, "<namespace>");  
    ...  
    CreateWorkflowOwnerCommand createCommand = new CreateWorkflowOwnerCommand()  
    {  
        InstanceOwnerMetadata =  
        {  
            { WorkflowHostTypeName, new InstanceValue(WFInstanceScopeName) },  
        }  
    };  
    InstanceHandle ownerHandle = store.CreateInstanceHandle();  
    store.DefaultInstanceOwner = store.Execute(  
                                   ownerHandle,  
                                   createCommand,  
                                   TimeSpan.FromSeconds(30)).InstanceOwner;  
    childInstance.AddInitialInstanceValues(new Dictionary<XName, object>() { { WorkflowHostTypeName, WFInstanceScopeName } });  
    ```  
  
-   <span data-ttu-id="e5617-117"><xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>: Modul trvalost odešle tento příkaz do ukládání instance ID instance vlastníka zámku lze odebrat z úložiště instance.</span><span class="sxs-lookup"><span data-stu-id="e5617-117"><xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>: The persistence engine sends this command to the instance store when the instance ID of a lock owner can be removed from the instance store.</span></span> <span data-ttu-id="e5617-118">Stejně jako u <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>, ID vlastníka zámku by měl být součástí aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5617-118">As with <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>, the ID of the lock owner should be provided by the application.</span></span>  
  
     <span data-ttu-id="e5617-119">Následující fragment kódu ukazuje, jak chcete-li uvolnit zámek pomocí <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>.</span><span class="sxs-lookup"><span data-stu-id="e5617-119">The following code snippet demonstrates how to release a lock using <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>.</span></span>  
  
    ```  
    static void FreeHandleAndDeleteOwner(InstanceStore store, InstanceHandle handle)  
    {  
        handle.Free();  
        handle = store.CreateInstanceHandle(store.DefaultInstanceOwner);  
        try  
        {  
            // We need this sleep so that we dont prematurely delete the owner, we need time to update the database.  
            Thread.Sleep(10000);  
            store.Execute(handle, new DeleteWorkflowOwnerCommand(), TimeSpan.FromSeconds(10));  
        }  
        catch (InstancePersistenceCommandException ex) { Log.Inform(ex.Message); }  
        catch (InstanceOwnerException ex) { Log.Inform(ex.Message); }  
        catch (OperationCanceledException ex) { Log.Inform(ex.Message); }  
        catch (Exception ex) { Log.Inform(ex.Message); }  
        finally  
        {  
            handle.Free();  
            store.DefaultInstanceOwner = null;  
        }  
    }  
    ```  
  
     <span data-ttu-id="e5617-120">Výše uvedené metoda by měla být volána v bloku Try/Catch při spuštění podřízeného instance.</span><span class="sxs-lookup"><span data-stu-id="e5617-120">The above method should be called in a Try/Catch block when a child instance is run.</span></span>  
  
    ```  
    try  
    {  
        childInstance.Run();  
    }  
    catch (Exception)  
    {  
        throw ;  
    }  
    finally  
    {  
        FreeHandleAndDeleteOwner(store, ownerHandle);  
    }  
    ```  
  
-   <span data-ttu-id="e5617-121"><xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>: Modul trvalost odešle tento příkaz do instance úložiště instanci pracovního postupu se má načíst pomocí klíčem instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e5617-121"><xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>: The persistence engine sends this command to the instance store when a workflow instance is to be loaded using the workflow’s instance key.</span></span> <span data-ttu-id="e5617-122">ID instance klíče se dá určit pomocí <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> parametru příkazu.</span><span class="sxs-lookup"><span data-stu-id="e5617-122">The ID of the instance key can be determined by using the <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> parameter of the command.</span></span>  
  
-   <span data-ttu-id="e5617-123"><xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>: Modul trvalost odešle tento příkaz úložiště instance k načtení aktivační parametry pro trvalou pracovní postupy pro vytvoření hostitele pracovního postupu, který pak můžete načíst pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="e5617-123"><xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>: The persistence engine sends this command to the instance store to retrieve activation parameters for persisted workflows in order to create a workflow host that can then load workflows.</span></span> <span data-ttu-id="e5617-124">Tento příkaz odešle modul v reakci na vyvolání úložiště instance <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> k hostiteli po nalezení instanci, která je možné aktivovat.</span><span class="sxs-lookup"><span data-stu-id="e5617-124">This command is sent by the engine in response to the instance store raising the <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> to the host when it locates an instance that can be activated.</span></span> <span data-ttu-id="e5617-125">Instance úložiště by měl dotazovaný k určení, zda jsou pracovní postupy, které je možné aktivovat.</span><span class="sxs-lookup"><span data-stu-id="e5617-125">The instance store should be polled to determine if there are workflows that can be activated.</span></span>  
  
-   <span data-ttu-id="e5617-126"><xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>: Modul trvalost odešle tento příkaz úložiště instance k načtení instance spustitelného pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e5617-126"><xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>: The persistence engine sends this command to the instance store to load runnable workflow instances.</span></span> <span data-ttu-id="e5617-127">Tento příkaz odešle modul v reakci na vyvolání úložiště instance <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> k hostiteli po nalezení instanci, která lze spustit.</span><span class="sxs-lookup"><span data-stu-id="e5617-127">This command is sent by the engine in response to the instance store raising the <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> to the host when it locates an instance that can be run.</span></span> <span data-ttu-id="e5617-128">Instance úložiště by měl dotazování na pracovní postupy, které se dají spustit.</span><span class="sxs-lookup"><span data-stu-id="e5617-128">The instance store should poll for workflows that can be run.</span></span> <span data-ttu-id="e5617-129">Následující fragment kódu ukazuje, dotazování úložišti instance pracovních postupů, které lze spustit nebo aktivovat.</span><span class="sxs-lookup"><span data-stu-id="e5617-129">The following code snippet demonstrates polling an instance store for workflows that can be run or activated.</span></span>  
  
    ```  
    public void PollForEvents()  
    {  
        InstanceOwner[] storeOwners = this.GetInstanceOwners();  
  
        foreach (InstanceOwner owner in storeOwners)  
        {  
            foreach (InstancePersistenceEvent ppEvent in this.GetEvents(owner))  
            {  
                if (ppEvent.Equals(HasRunnableWorkflowEvent.Value))  
                {  
                    bool hasRunnable = GetRunnableEvents(this.StoreId, owner.InstanceOwnerId, isActivable);  
                    if (hasRunnable)  
                    {  
                        this.SignalEvent(ppEvent, owner);  
                    }  
                    else  
                    {  
                        this.ResetEvent(ppEvent, owner);  
                    }  
                }  
                else if(ppEvent.Equals(HasActivatableWorkflowEvent.Value))  
                {  
                   bool hasActivable = GetActivableEvents(this.StoreId, owner.InstanceOwnerId);  
                   if (hasActivable)  
                    {  
                        this.SignalEvent(ppEvent, owner);  
                    }  
                    else  
                    {  
                        this.ResetEvent(ppEvent, owner);  
                    }  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="e5617-130">Ve výše uvedeném fragmentu kódu ukládání instance dotazuje události, které jsou k dispozici a prověří každé z nich chcete-li zjistit, jestli je <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> událostí.</span><span class="sxs-lookup"><span data-stu-id="e5617-130">In the above code snippet, the instance store queries the events available and examines each one to determine if it is a <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> event.</span></span> <span data-ttu-id="e5617-131">Pokud je takový nalezen, <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> nazývá signál hostiteli odeslat příkaz k úložišti instance.</span><span class="sxs-lookup"><span data-stu-id="e5617-131">If one is found, <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> is called to signal the host to send a command to the instance store.</span></span>  <span data-ttu-id="e5617-132">Následující fragment kódu ukazuje implementaci obslužné rutiny pro tento příkaz.</span><span class="sxs-lookup"><span data-stu-id="e5617-132">The following code snippet demonstrates an implementation of a handler for this command.</span></span>  
  
    ```  
    If (command is TryLoadRunnableWorkflowCommand)  
    {  
        Owner owner;  
        CheckOwner(context, command.Name, out owner);                          
        // Checking instance.Owner is like an InstanceLockQueryResult.  
        context.QueriedInstanceStore(new InstanceLockQueryResult(context.InstanceView.InstanceId, context.InstanceView.InstanceOwner.InstanceOwnerId));  
  
        XName ownerService = null;  
        InstanceValue value;  
        Instance runnableInstance = default(Instance);  
        bool foundRunnableInstance = false;  
  
        value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, owner.Data);  
        if (value != null && value.Value is XName)  
        {  
            ownerService = (XName)value.Value;  
        }  
  
        foreach (KeyValuePair<Guid, Instance> instance in MemoryStore.instances)  
        {  
            if (instance.Value.Owner != Guid.Empty || instance.Value.Completed)  
            {  
                continue;  
            }  
  
            if (ownerService != null)  
            {  
                value = QueryPropertyBag(WorkflowNamespace.WorkflowHostType, instance.Value.Metadata);  
                if (value == null || ((XName)value.Value) != ownerService)  
                {  
                    continue;  
                }  
            }  
  
            value = QueryPropertyBag(WorkflowServiceNamespace.SuspendReason, instance.Value.Metadata);  
            if (value != null && value.Value != null && value.Value is string)  
            {  
                continue;  
            }  
  
            value = QueryPropertyBag(WorkflowNamespace.Status, instance.Value.Data);  
            if (value != null && value.Value is string && ((string)value.Value) == "Executing")  
            {  
                runnableInstance = instance.Value;  
                foundRunnableInstance = true;  
            }  
  
            if (!foundRunnableInstance)  
            {  
                value = QueryPropertyBag(XNamespace.Get("urn:schemas-microsoft-com:System.Activities/4.0/properties").GetName("TimerExpirationTime"), instance.Value.Data);  
                if (value != null && value.Value is DateTime && ((DateTime)value.Value) <= DateTime.UtcNow)  
                {                          
                    runnableInstance = instance.Value;  
                    foundRunnableInstance = true;  
                }  
            }  
  
            if (foundRunnableInstance)  
            {  
                runnableInstance.LockVersion++;  
                runnableInstance.Owner = context.InstanceView.InstanceOwner.InstanceOwnerId;  
                MemoryStore.instances[instance.Key] = runnableInstance;  
                context.BindInstance(instance.Key);  
                context.BindAcquiredLock(runnableInstance.LockVersion);  
  
                Dictionary<Guid, IDictionary<XName, InstanceValue>> associatedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();  
                Dictionary<Guid, IDictionary<XName, InstanceValue>> completedKeys = new Dictionary<Guid, IDictionary<XName, InstanceValue>>();  
                foreach (KeyValuePair<Guid, Key> keyEntry in MemoryStore.keys)  
                {  
                if (keyEntry.Value.Instance == context.InstanceView.InstanceId)  
                {  
                    if (keyEntry.Value.Completed)  
                    {  
                        completedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));  
                    }  
                    else  
                    {  
                        associatedKeys.Add(keyEntry.Key, DeserializePropertyBag(keyEntry.Value.Metadata));  
                    }  
                }  
            }  
  
            context.LoadedInstance(InstanceState.Initialized, DeserializePropertyBag(runnableInstance.Data), DeserializePropertyBag(runnableInstance.Metadata), associatedKeys, completedKeys);  
            break;  
        }  
    }  
    ```  
  
     <span data-ttu-id="e5617-133">Ve výše uvedeném fragmentu kódu vyhledá úložiště instance spustitelného instancí.</span><span class="sxs-lookup"><span data-stu-id="e5617-133">In the above code snippet, the instance store searches for runnable instances.</span></span> <span data-ttu-id="e5617-134">Pokud je nalezena instance, je vázána na kontextu spuštění a načíst.</span><span class="sxs-lookup"><span data-stu-id="e5617-134">If an instance is found, it is bound to the execution context and loaded.</span></span>  
  
## <a name="using-a-custom-instance-store"></a><span data-ttu-id="e5617-135">Pomocí vlastních instance úložiště</span><span class="sxs-lookup"><span data-stu-id="e5617-135">Using a custom instance store</span></span>  
 <span data-ttu-id="e5617-136">Implementovat vlastní instance úložiště, přiřaďte mu instance úložiště instance k <xref:System.Activities.WorkflowApplication.InstanceStore%2A>a implementovat <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e5617-136">To implement a custom instance store, assign an instance of the instance store to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A>, and implement the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> method.</span></span>  <span data-ttu-id="e5617-137">Najdete v článku [postupy: vytvoření a spuštění dlouhém pracovním postupu spuštění](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) kurz pro konkrétní.</span><span class="sxs-lookup"><span data-stu-id="e5617-137">See the [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) tutorial for specifics.</span></span>  
  
## <a name="a-sample-instance-store"></a><span data-ttu-id="e5617-138">Instance úložiště ukázka</span><span class="sxs-lookup"><span data-stu-id="e5617-138">A sample instance store</span></span>  
 <span data-ttu-id="e5617-139">Následující ukázka kódu je úplná instance implementace úložiště, provedených od [podnikové procesu nákupu](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="e5617-139">The following code sample is a complete instance store implementation, taken from the [Corporate Purchase Process](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) sample.</span></span> <span data-ttu-id="e5617-140">Toto úložiště instance trvá data pracovního postupu k souboru pomocí XML.</span><span class="sxs-lookup"><span data-stu-id="e5617-140">This instance store persists workflow data to a file using XML.</span></span>  
  
```  
using System;  
using System.Activities.DurableInstancing;  
using System.Collections.Generic;  
using System.IO;  
using System.Runtime.DurableInstancing;  
using System.Runtime.Serialization;  
using System.ServiceModel.Persistence;  
using System.Xml;  
using System.Xml.Linq;  
  
namespace Microsoft.Samples.WF.PurchaseProcess  
{  
  
    public class XmlWorkflowInstanceStore : InstanceStore  
    {  
        Guid ownerInstanceID;  
  
        public XmlWorkflowInstanceStore() : this(Guid.NewGuid())  
        {  
  
        }  
  
        public XmlWorkflowInstanceStore(Guid id)  
        {  
            ownerInstanceID = id;  
        }  
  
        //Synchronous version of the Begin/EndTryCommand functions  
        protected override bool TryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout)  
        {  
            return EndTryCommand(BeginTryCommand(context, command, timeout, null, null));  
        }  
  
        //The persistence engine will send a variety of commands to the configured InstanceStore,  
        //such as CreateWorkflowOwnerCommand, SaveWorkflowCommand, and LoadWorkflowCommand.  
        //This method is where we will handle those commands  
        protected override IAsyncResult BeginTryCommand(InstancePersistenceContext context, InstancePersistenceCommand command, TimeSpan timeout, AsyncCallback callback, object state)  
        {  
            IDictionary<XName, InstanceValue> data = null;  
  
            //The CreateWorkflowOwner command instructs the instance store to create a new instance owner bound to the instanace handle  
            if (command is CreateWorkflowOwnerCommand)  
            {  
                context.BindInstanceOwner(ownerInstanceID, Guid.NewGuid());  
            }  
            //The SaveWorkflow command instructs the instance store to modify the instance bound to the instance handle or an instance key  
            else if (command is SaveWorkflowCommand)  
            {  
                SaveWorkflowCommand saveCommand = (SaveWorkflowCommand)command;  
                data = saveCommand.InstanceData;  
  
                Save(data);  
            }  
            //The LoadWorkflow command instructs the instance store to lock and load the instance bound to the identifier in the instance handle  
            else if (command is LoadWorkflowCommand)  
            {  
                string fileName = IOHelper.GetFileName(this.ownerInstanceID);  
  
                try  
                {  
                    using (FileStream inputStream = new FileStream(fileName, FileMode.Open))  
                    {  
                        data = LoadInstanceDataFromFile(inputStream);  
                        //load the data into the persistence Context  
                        context.LoadedInstance(InstanceState.Initialized, data, null, null, null);  
                    }  
                }  
                catch (Exception exception)  
                {  
                    throw new PersistenceException(exception.Message);  
                }  
            }  
  
            return new CompletedAsyncResult<bool>(true, callback, state);  
        }  
  
        protected override bool EndTryCommand(IAsyncResult result)  
        {  
            return CompletedAsyncResult<bool>.End(result);  
        }  
  
        //Reads data from xml file and creates a dictionary based off of that.  
        IDictionary<XName, InstanceValue> LoadInstanceDataFromFile(Stream inputStream)  
        {  
            IDictionary<XName, InstanceValue> data = new Dictionary<XName, InstanceValue>();  
  
            NetDataContractSerializer s = new NetDataContractSerializer();  
  
            XmlReader rdr = XmlReader.Create(inputStream);  
            XmlDocument doc = new XmlDocument();  
            doc.Load(rdr);  
  
            XmlNodeList instances = doc.GetElementsByTagName("InstanceValue");  
            foreach (XmlElement instanceElement in instances)  
            {  
                XmlElement keyElement = (XmlElement)instanceElement.SelectSingleNode("descendant::key");  
                XName key = (XName)DeserializeObject(s, keyElement);  
  
                XmlElement valueElement = (XmlElement)instanceElement.SelectSingleNode("descendant::value");  
                object value = DeserializeObject(s, valueElement);  
                InstanceValue instVal = new InstanceValue(value);  
  
                data.Add(key, instVal);  
            }  
  
            return data;  
        }  
  
        object DeserializeObject(NetDataContractSerializer serializer, XmlElement element)  
        {  
            object deserializedObject = null;  
  
            MemoryStream stm = new MemoryStream();  
            XmlDictionaryWriter wtr = XmlDictionaryWriter.CreateTextWriter(stm);  
            element.WriteContentTo(wtr);  
            wtr.Flush();  
            stm.Position = 0;  
  
            deserializedObject = serializer.Deserialize(stm);  
  
            return deserializedObject;  
        }  
  
        //Saves the persistence data to an xml file.  
        void Save(IDictionary<XName, InstanceValue> instanceData)  
        {  
            string fileName = IOHelper.GetFileName(this.ownerInstanceID);  
            XmlDocument doc = new XmlDocument();  
            doc.LoadXml("<InstanceValues/>");  
  
            foreach (KeyValuePair<XName,InstanceValue> valPair in instanceData)  
            {  
                XmlElement newInstance = doc.CreateElement("InstanceValue");  
  
                XmlElement newKey = SerializeObject("key", valPair.Key, doc);  
                newInstance.AppendChild(newKey);  
  
                XmlElement newValue = SerializeObject("value", valPair.Value.Value, doc);  
                newInstance.AppendChild(newValue);  
  
                doc.DocumentElement.AppendChild(newInstance);  
            }  
            doc.Save(fileName);  
       }  
  
        XmlElement SerializeObject(string elementName, object o, XmlDocument doc)  
        {  
            NetDataContractSerializer s = new NetDataContractSerializer();  
            XmlElement newElement = doc.CreateElement(elementName);  
            MemoryStream stm = new MemoryStream();  
  
            s.Serialize(stm, o);  
            stm.Position = 0;  
            StreamReader rdr = new StreamReader(stm);  
            newElement.InnerXml = rdr.ReadToEnd();  
  
            return newElement;  
        }  
    }  
}  
```
