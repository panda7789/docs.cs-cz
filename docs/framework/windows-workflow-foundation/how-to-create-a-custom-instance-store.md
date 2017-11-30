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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c383d3af92ba2f76f8ba09bc194220c170beaa0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-custom-instance-store"></a>Postupy: vytvoření vlastní Instance úložiště
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]obsahuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, úložiště instance, které používá systém SQL Server se zachovat data pracovního postupu. Pokud vaše aplikace je potřeba zachovat data pracovního postupu na jiné médium, například jiné databázi nebo systému souborů, můžete implementovat vlastní instance úložiště. Vlastní instance úložiště je vytvořeno tím, že rozšíří abstraktní <xref:System.Runtime.DurableInstancing.InstanceStore> třídy a metody, které jsou požadovány pro implementaci implementace. Pro úplnou implementaci vlastní instance úložiště, najdete v článku [podnikové procesu nákupu](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) ukázka.  
  
## <a name="implementing-the-begintrycommand-method"></a>Implementace metody BeginTryCommand  
 <xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> Odesílají na ukládání instance modul trvalost. Typ `command` parametr označuje příkazu, na který je spouštěna; tento parametr může být z následujících typů:  
  
-   <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>: Modul trvalost odešle tento příkaz do ukládání instance pracovního postupu se má uložit trvale na střední úložiště. Trvalost dat pracovního postupu je poskytnutá metodě v <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> členem `command` parametr.  
  
-   <xref:System.Activities.DurableInstancing.LoadWorkflowCommand>: Když pracovní postup je třeba načíst z úložiště střední modul trvalost odešle tento příkaz k úložišti instance. Načíst ID instance pracovního postupu je poskytnutá metodě v `instanceId` parametr <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> vlastnost `context` parametr.  
  
-   <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>: Trvalost modul odešle tento příkaz k instanci při uložení <xref:System.ServiceModel.Activities.WorkflowServiceHost> musí být registrován jako vlastníka zámku. ID instance pracovního postupu aktuální by měly být zadané instance úložiště pomocí <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> metodu `context` parametr.  
  
     Následující fragment kódu ukazuje, jak implementovat příkaz CreateWorkflowOwner přiřadit vlastníka explicitní zámku.  
  
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
  
-   <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>: Modul trvalost odešle tento příkaz do ukládání instance ID instance vlastníka zámku lze odebrat z úložiště instance. Stejně jako u <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>, ID vlastníka zámku by měl být součástí aplikace.  
  
     Následující fragment kódu ukazuje, jak chcete-li uvolnit zámek pomocí <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>.  
  
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
  
     Výše uvedené metoda by měla být volána v bloku Try/Catch při spuštění podřízeného instance.  
  
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
  
-   <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>: Modul trvalost odešle tento příkaz do instance úložiště instanci pracovního postupu se má načíst pomocí klíčem instance pracovního postupu. ID instance klíče se dá určit pomocí <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> parametru příkazu.  
  
-   <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>: Modul trvalost odešle tento příkaz úložiště instance k načtení aktivační parametry pro trvalou pracovní postupy pro vytvoření hostitele pracovního postupu, který pak můžete načíst pracovních postupů. Tento příkaz odešle modul v reakci na vyvolání úložiště instance <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> k hostiteli po nalezení instanci, která je možné aktivovat. Instance úložiště by měl dotazovaný k určení, zda jsou pracovní postupy, které je možné aktivovat.  
  
-   <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>: Modul trvalost odešle tento příkaz úložiště instance k načtení instance spustitelného pracovního postupu. Tento příkaz odešle modul v reakci na vyvolání úložiště instance <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> k hostiteli po nalezení instanci, která lze spustit. Instance úložiště by měl dotazování na pracovní postupy, které se dají spustit. Následující fragment kódu ukazuje, dotazování úložišti instance pracovních postupů, které lze spustit nebo aktivovat.  
  
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
  
     Ve výše uvedeném fragmentu kódu ukládání instance dotazuje události, které jsou k dispozici a prověří každé z nich chcete-li zjistit, jestli je <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> událostí. Pokud je takový nalezen, <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> nazývá signál hostiteli odeslat příkaz k úložišti instance.  Následující fragment kódu ukazuje implementaci obslužné rutiny pro tento příkaz.  
  
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
  
     Ve výše uvedeném fragmentu kódu vyhledá úložiště instance spustitelného instancí. Pokud je nalezena instance, je vázána na kontextu spuštění a načíst.  
  
## <a name="using-a-custom-instance-store"></a>Pomocí vlastních instance úložiště  
 Implementovat vlastní instance úložiště, přiřaďte mu instance úložiště instance k <xref:System.Activities.WorkflowApplication.InstanceStore%2A>a implementovat <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> metoda.  Najdete v článku [postupy: vytvoření a spuštění dlouhém pracovním postupu spuštění](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) kurz pro konkrétní.  
  
## <a name="a-sample-instance-store"></a>Instance úložiště ukázka  
 Následující ukázka kódu je úplná instance implementace úložiště, provedených od [podnikové procesu nákupu](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) ukázka. Toto úložiště instance trvá data pracovního postupu k souboru pomocí XML.  
  
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
