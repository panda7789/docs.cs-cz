---
title: 'Postupy: Vytvoření Store Instance vlastní'
ms.date: 03/30/2017
ms.assetid: 593c4e9d-8a49-4e12-8257-cee5e6b4c075
ms.openlocfilehash: de3602b928a861500e7984fe88bbb2176d58b840
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503187"
---
# <a name="how-to-create-a-custom-instance-store"></a>Postupy: Vytvoření Store Instance vlastní

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] obsahuje <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, úložiště instance, který používá systém SQL Server k uchování dat pracovního postupu. Pokud vaše aplikace je potřeba zachovat data pracovního postupu do jiného média, například jinou databázi nebo systému souborů, můžete implementovat vlastní instance úložiště. Vytvoření vlastní instance úložiště tím, že rozšíří abstraktní <xref:System.Runtime.DurableInstancing.InstanceStore> třídy a implementace metody, které jsou vyžadovány pro implementaci. Úplnou implementaci vlastní instance úložiště, najdete v článku [podnikové procesu nákupu](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) vzorku.

## <a name="implementing-the-begintrycommand-method"></a>Implementace metody BeginTryCommand

<xref:System.Runtime.DurableInstancing.InstanceStore.BeginTryCommand%2A> Motorem stálost odesílají do úložiště instancí. Typ `command` parametr vyplývá, který příkaz se zpracovává, tento parametr může být z následujících typů:

- <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>: Modul trvalost tento příkaz odešle do úložiště instancí pracovního postupu se ukládají do úložiště média. V metodě k dispozici data trvalost pracovního postupu <xref:System.Activities.DurableInstancing.SaveWorkflowCommand.InstanceData%2A> člena `command` parametru.

- <xref:System.Activities.DurableInstancing.LoadWorkflowCommand>: Trvalost modul pošle tento příkaz v úložišti instancí, když pracovní postup má být načteny z paměťovému médiu. ID instance pracovního postupu, který se má načíst je k dispozici v metodě `instanceId` parametr <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.InstanceView%2A> vlastnost `context` parametru.

- <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>: Odešle modul trvalost, tento příkaz k instanci při ukládání <xref:System.ServiceModel.Activities.WorkflowServiceHost> musí být registrovaný jako vlastník zámku. ID instance pracovního postupu aktuální by měl být poskytnut úložiště pomocí instance <xref:System.Runtime.DurableInstancing.InstancePersistenceContext.BindInstanceOwner%2A> metodu `context` parametru.

     Následující fragment kódu ukazuje, jak implementovat příkaz CreateWorkflowOwner přiřadit vlastníka explicitní uzamčení.

    ```csharp
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

- <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>: ID instance vlastník zámku lze odebrat z úložiště instance, motorem stálost odešle tento příkaz v úložišti instancí. Stejně jako u <xref:System.Activities.DurableInstancing.CreateWorkflowOwnerCommand>, by měly být zadané ID vlastníka zámku aplikace.

     Následující fragment kódu ukazuje, jak k uvolnění zámku pomocí <xref:System.Activities.DurableInstancing.DeleteWorkflowOwnerCommand>.

    ```csharp
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

     Výše uvedené metody lze volat v bloku Try/Catch při spuštění instance podřízené.

    ```csharp
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

- <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand>: Instance pracovního postupu se načíst klíč instance pracovního postupu motorem stálost odešle tento příkaz v úložišti instancí. ID instance klíč můžete určit pomocí <xref:System.Activities.DurableInstancing.LoadWorkflowByInstanceKeyCommand.LookupInstanceKey%2A> parametru příkazu.

- <xref:System.Activities.DurableInstancing.QueryActivatableWorkflowsCommand>: Modul trvalost odešle tento příkaz v úložišti instancí se načíst aktivační parametry pro trvalý pracovní postupy k vytvoření hostitele pracovního postupu, který pak načíst pracovní postupy. Tento příkaz odešle modulem v reakci na zvýšení úložiště instance <xref:System.Activities.DurableInstancing.HasActivatableWorkflowEvent> na hostitele, pokud je možné vyhledat instanci, která je možné aktivovat. Chcete-li zjistit, zda jsou pracovní postupy, které je možné aktivovat by měl dotazovaný v úložišti instancí.

- <xref:System.Activities.DurableInstancing.TryLoadRunnableWorkflowCommand>: Modul trvalost odešle tento příkaz v úložišti instancí načíst spustitelné instance pracovního postupu. Tento příkaz odešle modulem v reakci na zvýšení úložiště instance <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> na hostitele, pokud je možné vyhledat instanci, která je možné spustit. V úložišti instancí by dotazování na pracovní postupy, které je možné spustit. Následující fragment kódu ukazuje dotazování úložiště instancí pracovních postupů, které můžete spustit nebo aktivovat.

    ```csharp
    public void PollForEvents()
    {
        InstanceOwner[] storeOwners = this.GetInstanceOwners();

        foreach (InstanceOwner owner in storeOwners)
        {
            foreach (InstancePersistenceEvent ppEvent in this.GetEvents(owner))
            {
                if (ppEvent.Equals(HasRunnableWorkflowEvent.Value))
                {
                    bool hasRunnable = GetRunnableEvents(this.StoreId, owner.InstanceOwnerId, isActivatable);
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
                   bool hasActivatable = GetActivatableEvents(this.StoreId, owner.InstanceOwnerId);
                   if (hasActivatable)
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

     Ve výše uvedeném fragmentu kódu v úložišti instancí dotazuje dostupná událostem a zkontroluje každý z nich k určení, zda se jedná <xref:System.Activities.DurableInstancing.HasRunnableWorkflowEvent> událostí. Pokud ho najde, <xref:System.Runtime.DurableInstancing.InstanceStore.SignalEvent%2A> je volána k signalizaci hostitele odeslat příkaz do úložiště instancí. Následující fragment kódu ukazuje implementaci obslužné rutiny pro tento příkaz.

    ```csharp
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

    Ve výše uvedeném fragmentu kódu v úložišti instancí hledá spustitelných instancí. Pokud se instance nenajde, je vázané na kontext spuštění a načtení.

## <a name="using-a-custom-instance-store"></a>Použití vlastní instance store

K implementaci ukládání vlastní instance, přiřadit instanci v úložišti instancí na <xref:System.Activities.WorkflowApplication.InstanceStore%2A>a implementovat <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> metoda. Zobrazit [jak: Vytvoření a spuštění dlouhém pracovním postupu spuštění](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) kurz pro konkrétní.

## <a name="a-sample-instance-store"></a>Úložiště instancí vzorku

Následující ukázka kódu je úplná instance implementace úložiště, na základě [podnikové procesu nákupu](../../../docs/framework/windows-workflow-foundation/samples/corporate-purchase-process.md) vzorku. Toto úložiště instance se uchovávají data pracovního postupu do souboru s použitím XML.

```csharp
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
