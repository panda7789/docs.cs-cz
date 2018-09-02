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
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a>Postupy: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů

Toto téma popisuje postup konfigurace funkce SQL Store Instance pracovního postupu pro povolení trvalosti pro pracovní postupy a služby pracovních postupů, jak prostřednictvím kódu programu a pomocí konfiguračního souboru.  
  
Windows Server App Fabric zjednodušuje proces konfigurace trvalosti. Další informace najdete v tématu [konfigurace trvalosti infrastruktury aplikace](https://go.microsoft.com/fwlink/?LinkId=201204)  
  
Před použitím funkce SQL Store Instance pracovního postupu, vytvořte databázi, která používá funkci k uchování instance pracovního postupu. [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Nastavení program zkopíruje soubory skriptu SQL přidružený k funkci SQL Store Instance pracovního postupu do složky %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN. Spusťte tyto soubory skriptu pro databázi systému SQL Server 2005 nebo SQL Server 2008, který má Store Instance pracovního postupu SQL použít k uchování instance pracovního postupu. Nejprve spusťte SqlWorkflowInstanceStoreSchema.sql souboru a pak spusťte soubor SqlWorkflowInstanceStoreLogic.sql.

> [!NOTE]
> Vyčištění databáze stálost k nové databázi, spuštěním skriptů v %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN v uvedeném pořadí.  
>
> 1. SqlWorkflowInstanceStoreSchema.sql
> 2. SqlWorkflowInstanceStoreLogic.sql

> [!IMPORTANT]
> Pokud nevytvoříte databáze trvalosti, funkci SQL Store Instance pracovního postupu výjimku podobný následujícímu hostiteli se pokusí uchovávat pracovních postupů.  
> 
> System.Data.SqlClient.SqlException: Nelze nalézt uloženou proceduru 'System.Activities.DurableInstancing.CreateLockOwner.  

Následující části popisují postup povolení trvalosti pro pracovní postupy a služby pracovních postupů pomocí Store Instance pracovního postupu SQL. Další informace o vlastnostech Store Instance pracovního postupu SQL najdete v tématu [vlastnosti z SQL pracovního postupu Instance Store](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).  

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a>Povolení trvalosti pro pracovní postupy místním používajících WorkflowApplication

Můžete zapnout stálost v místním prostředí pracovních postupů, které používají <xref:System.Activities.WorkflowApplication> prostřednictvím kódu programu pomocí <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> objektový model. Následující postup obsahuje kroky k tomu.  

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a>K povolení trvalosti pro pracovní postupy v místním prostředí

1.  Přidejte odkaz na System.Activites.DurableInstancing.dll.  
  
2.  Přidejte následující příkaz v horní části souboru se zdrojovým za stávající příkazy "pomocí".  
  
    ```csharp  
    using System.Activities.DurableInstancing;  
    ```  
  
3.  Vytvoření <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> a přiřaďte ho <xref:System.Activities.WorkflowApplication.InstanceStore%2A> z <xref:System.Activities.WorkflowApplication> jak je znázorněno v následujícím příkladu kódu.
  
    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```
  
   > [!NOTE]
   > V závislosti na vaší edici systému SQL Server může být jiný server název připojovacího řetězce.  
  
4. Vyvolat <xref:System.Activities.WorkflowApplication.Persist%2A> metodu <xref:System.Activities.WorkflowApplication> objekt pro zachování pracovního postupu, nebo <xref:System.Activities.WorkflowApplication.Unload%2A> metodu pro uchování a uvolnit pracovní postup. Můžete také zpracovávat <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> událostí vyvolaných <xref:System.Activities.WorkflowApplication> objekt a vrátí odpovídající (<xref:System.Activities.PersistableIdleAction.Persist> nebo <xref:System.Activities.PersistableIdleAction.Unload>) člen <xref:System.Activities.PersistableIdleAction>.  
  
   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> Najdete v článku [uchování aplikace pracovního postupu](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md) ukázku v [trvalost](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) příklad povolení trvalosti pro pracovní postupy pomocí <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>a [postupy: vytvoření a spuštění dlouhodobého Spuštění pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) kroku [kurz Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) pokyny krok za krokem.  

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a>Povolení trvalosti pro pracovní postup služby místním, použít hostitele služby pracovního postupu

Můžete povolit trvalost pro služby v místním prostředí pracovních postupů, které používají <xref:System.ServiceModel.WorkflowServiceHost> prostřednictvím kódu programu pomocí <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> třídy nebo <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> třídy.  

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a>Používání třídy SqlWorkflowInstanceStoreBehavior  

Následující postup obsahuje kroky pro použití <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> třídy k povolení trvalosti pro služby pracovních postupů v místním prostředí.  

##### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a>Chcete-li zapnout stálost pomocí SqlWorkflowInstanceStoreBehavior

1.  Přidejte odkaz na System.ServiceModel.dll.  
  
2.  Přidejte následující příkaz v horní části souboru se zdrojovým za stávající příkazy "pomocí".  
  
    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3.  Vytvoření instance `WorkflowServiceHost` a přidají koncové body pro službu pracovního postupu.  
  
    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));  
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");  
    ``` 

4.  Vytvoření `SqlWorkflowInstanceStoreBehavior` objektu a chcete-li nastavit vlastnosti chování objektu.  
  
    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5.  Otevření hostitele služby pracovního postupu.

    ```csharp
    host.Open();
    ```

> [!IMPORTANT]
> Najdete v článku [integrovaných konfiguračních](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md) ukázku v [trvalost](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) příklad povolení trvalosti pro pracovní postup služby pomocí `SqlWorkflowInstanceStoreBehavior` třídy.  

### <a name="using-the-durableinstancingoptions-property"></a>Pomocí vlastnosti DurableInstancingOptions

Při `SqlWorkflowInstanceStoreBehavior` se použije `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` je nastavena na `SqlWorkflowInstanceStore` objekt vytvořený pomocí hodnoty konfigurace. Můžete provést stejný prostřednictvím kódu programu k nastavení <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> vlastnost `WorkflowServiceHost` bez použití `SqlWorkflowInstanceStoreBehavior` třídy, jak je znázorněno v následujícím příkladu kódu.  

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a>Povolení trvalosti pro pracovní postup služby WAS-Hosted, použít hostitele služby pracovního postupu pomocí konfiguračního souboru

Povolení trvalosti pro pracovní postup v místním prostředí nebo Windows Process Activation Service WAS hostované služby pomocí konfiguračního souboru. Služba WAS hostované pracovního postupu používá hostitele služby pracovního postupu jako v místním prostředí pracovního postupu služby.  
  
`SqlWorkflowInstanceStoreBehavior`, Chování služby, který vám umožní snadno změnit [Store Instance pracovního postupu SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) vlastnosti prostřednictvím konfigurace XML. Pro služby WAS hostované pracovního postupu použijte soubor Web.config. Následující příklad konfigurace ukazuje postup při konfiguraci Store Instance pracovního postupu SQL s použitím `sqlWorkflowInstanceStore` prvek chování v konfiguračním souboru.  
  
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
  
Pokud nenastavíte hodnoty `connectionString` nebo `connectionStringName` vlastnost, Store Instance SQL pracovní postup používá výchozí připojovací řetězec s názvem `DefaultSqlWorkflowInstanceStoreConnectionString`.  
  
Při `SqlWorkflowInstanceStoreBehavior` se použije `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` je nastavena na `SqlWorkflowInstanceStore` objekt vytvořený pomocí hodnoty konfigurace. Můžete provést stejný prostřednictvím kódu programu k použití `SqlWorkflowInstanceStore` s `WorkflowServiceHost` bez použití elementu chování služby.  
  
```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```
  
> [!IMPORTANT]
> Doporučuje se, že v souboru Web.config neukládejte citlivé informace, jako jsou uživatelská jména a hesla. Pokud ukládáte citlivých informací v souboru Web.config, by měl zabezpečený přístup k souboru Web.config pomocí systému souborů seznamů řízení přístupu (ACL). Kromě toho můžete také zabezpečit hodnoty konfigurace v konfiguračním souboru jak je uvedeno v [šifrování konfigurační informace pomocí Protected Configuration](https://go.microsoft.com/fwlink/?LinkId=178419).

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a>Machine.config elementy související s funkcí SQL Store Instance pracovního postupu

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Instalací přidá následující elementy související s funkcí SQL Store Instance pracovního postupu k souboru Machine.config:  

-   Přidá následující element rozšíření chování k souboru Machine.config, takže můžete použít <`sqlWorkflowInstanceStore`> element chování služby v konfiguračním souboru konfigurace trvalosti pro vaše služby.

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
