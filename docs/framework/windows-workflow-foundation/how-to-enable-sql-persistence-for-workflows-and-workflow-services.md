---
title: 'Postupy: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů'
ms.date: 03/30/2017
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 4dc5648d748372828c5b9a36441bfb02eef045e1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460873"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a>Postupy: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů

Toto téma popisuje, jak nakonfigurovat funkci úložiště instance pracovního postupu SQL tak, aby umožňovala trvalé uchovávání pracovních postupů a služeb pracovních postupů programově i pomocí konfiguračního souboru.

Windows Server App Fabric zjednodušuje proces konfigurace trvalosti. Další informace najdete v tématu [Konfigurace trvalosti aplikace App Fabric](https://go.microsoft.com/fwlink/?LinkId=201204).

Před použitím funkce úložiště instance pracovního postupu SQL vytvořte databázi, kterou funkce používá k zachování instancí pracovního postupu. Program pro nastavení [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kopíruje soubory skriptu SQL přidružené k funkci úložiště instancí pracovních postupů SQL do složky%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN. Tyto soubory skriptu spusťte v databázi SQL Server 2005 nebo SQL Server 2008, kterou chcete, aby úložiště instancí pracovních postupů SQL použilo k zachování instancí pracovního postupu. Nejprve spusťte soubor SqlWorkflowInstanceStoreSchema. SQL a potom spusťte soubor SqlWorkflowInstanceStoreLogic. SQL.

> [!NOTE]
> Chcete-li vyčistit databázi trvalosti, aby měla novou databázi, spusťte skripty v%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN v uvedeném pořadí.
>
> 1. SqlWorkflowInstanceStoreSchema. SQL
> 2. SqlWorkflowInstanceStoreLogic. SQL

> [!IMPORTANT]
> Pokud nevytvoříte databázi trvalosti, funkce úložiště instance pracovního postupu SQL vyvolá výjimku, která je podobná následujícímu, když se hostitel pokusí uchovat pracovní postupy.
>
> System. data. SqlClient. SqlException: nepovedlo se najít uloženou proceduru System. Activities. DurableInstancing. CreateLockOwner.

Následující části popisují, jak povolit trvalost pro pracovní postupy a služby pracovních postupů pomocí úložiště instance pracovního postupu SQL. Další informace o vlastnostech úložiště instancí pracovních postupů SQL najdete v tématu [vlastnosti úložiště instance pracovního postupu SQL](properties-of-sql-workflow-instance-store.md).

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a>Povolení trvalosti pro samoobslužné pracovní postupy, které používají WorkflowApplication

Trvalost můžete povolit pro pracovní postupy v místním prostředí, které používají <xref:System.Activities.WorkflowApplication> programově pomocí modelu <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> objektů. Následující postup obsahuje kroky.

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a>Postup povolení trvalosti pro pracovní postupy v místním prostředí

1. Přidejte odkaz na System. Activities. DurableInstancing. dll.

2. Přidejte následující příkaz v horní části zdrojového souboru po existující příkazy using.

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. Vytvořte <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> a přiřaďte ji <xref:System.Activities.WorkflowApplication.InstanceStore%2A> <xref:System.Activities.WorkflowApplication>, jak je znázorněno v následujícím příkladu kódu.

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > V závislosti na vaší edici SQL Server se název serveru připojovacího řetězce může lišit.

4. Vyvolejte metodu <xref:System.Activities.WorkflowApplication.Persist%2A> v objektu <xref:System.Activities.WorkflowApplication> pro zachování pracovního postupu, nebo <xref:System.Activities.WorkflowApplication.Unload%2A> metodu pro zachování a uvolnění pracovního postupu. Můžete také zpracovat událost <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> vyvolanou objektem <xref:System.Activities.WorkflowApplication> a vrátit odpovídající člen (<xref:System.Activities.PersistableIdleAction.Persist> nebo <xref:System.Activities.PersistableIdleAction.Unload>) <xref:System.Activities.PersistableIdleAction>.

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> Podrobné pokyny najdete v tématu [Postupy: vytvoření a spuštění dlouho běžícího pracovního postupu](how-to-create-and-run-a-long-running-workflow.md) v [kurzu Začínáme](getting-started-tutorial.md) .

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a>Povolení trvalosti pro samoobslužné služby pracovních postupů, které používají hostitele

Můžete povolit trvalost pro samoobslužné služby pracovních postupů, které používají <xref:System.ServiceModel.WorkflowServiceHost> programově pomocí <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> třídy nebo třídy <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A>.

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a>Použití třídy SqlWorkflowInstanceStoreBehavior

Následující postup obsahuje kroky pro použití třídy <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> k povolení trvalosti pro samoobslužné služby pracovních postupů.

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a>Postup povolení trvalosti pomocí SqlWorkflowInstanceStoreBehavior

1. Přidejte odkaz na System. ServiceModel. dll.

2. Přidejte následující příkaz v horní části zdrojového souboru po existující příkazy using.

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. Vytvořte instanci `WorkflowServiceHost` a přidejte koncové body pro službu pracovního postupu.

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. Vytvořte objekt `SqlWorkflowInstanceStoreBehavior` a nastavte vlastnosti objektu chování.

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. Otevřete hostitele služby pracovního postupu.

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a>Použití vlastnosti DurableInstancingOptions

Při použití `SqlWorkflowInstanceStoreBehavior` je `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` nastavena na objekt `SqlWorkflowInstanceStore` vytvořený pomocí hodnot konfigurace. Můžete to samé provést programově pro nastavení vlastnosti <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> `WorkflowServiceHost` bez použití třídy `SqlWorkflowInstanceStoreBehavior`, jak je znázorněno v následujícím příkladu kódu.

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a>Povolení trvalosti u hostovaných služeb pracovních postupů, které používají hostitele s použitím konfiguračního souboru

Můžete povolit trvalost pro samoobslužné služby nebo aktivační službu procesů systému Windows (WAS) – hostované služby pracovního postupu pomocí konfiguračního souboru. Služba pracovního postupu, která je hostovaná, používá službu WorkflowServiceHost jako samoobslužné služby pracovních postupů.

`SqlWorkflowInstanceStoreBehavior`, což je chování služby, které umožňuje pohodlně měnit vlastnosti [úložiště instancí pracovních postupů SQL](sql-workflow-instance-store.md) prostřednictvím konfigurace XML. U hostovaných služeb pracovních postupů použijte soubor Web. config. Následující příklad konfigurace ukazuje, jak nakonfigurovat úložiště instance pracovního postupu SQL pomocí elementu `sqlWorkflowInstanceStore` chování v konfiguračním souboru.

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

Pokud nenastavíte hodnoty pro `connectionString` nebo vlastnost `connectionStringName`, úložiště instance pracovního postupu SQL použije výchozí pojmenovaný připojovací řetězec `DefaultSqlWorkflowInstanceStoreConnectionString`.

Při použití `SqlWorkflowInstanceStoreBehavior` je `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` nastavena na objekt `SqlWorkflowInstanceStore` vytvořený pomocí hodnot konfigurace. Můžete to samé provést programově a použít `SqlWorkflowInstanceStore` s `WorkflowServiceHost` bez použití prvku chování služby.

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> Doporučujeme Neukládat citlivé informace, jako jsou uživatelská jména a hesla, do souboru Web. config. Pokud ukládáte citlivé informace do souboru Web. config, měli byste zabezpečený přístup k souboru Web. config pomocí seznamů Access Control systému souborů (ACL). Kromě toho můžete také zabezpečit konfigurační hodnoty v rámci konfiguračního souboru, jak je uvedeno v části [šifrování informací o konfiguraci pomocí chráněné konfigurace](https://go.microsoft.com/fwlink/?LinkId=178419).

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a>Elementy Machine. config související s funkcí úložiště instance pracovního postupu SQL

Instalace [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] přidá do souboru Machine. config následující prvky týkající se funkce úložiště instance pracovního postupu SQL:

- Přidá do souboru Machine. config následující prvek rozšíření chování, aby bylo možné v konfiguračním souboru použít prvek chování služby \<sqlWorkflowInstanceStore > a nakonfigurovat trvalost pro vaše služby.

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
