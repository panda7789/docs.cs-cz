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
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a>Postupy: povolení trvalost SQL pro pracovní postupy a služeb pracovních postupů
Toto téma popisuje postup konfigurace úložiště Instance pracovního postupu SQL funkci tak, aby zapnout stálost pro vaše pracovní postupy a pracovní postup služby prostřednictvím kódu programu a pomocí konfiguračního souboru.  
  
 Windows Server App Fabric zjednodušuje proces konfigurace trvalosti. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Konfigurace trvalosti infrastruktury aplikace](http://go.microsoft.com/fwlink/?LinkId=201204)  
  
 Před použitím funkce ukládání Instance pracovního postupu SQL, vytvořte databázi, která používá funkci k zachování instancí pracovních postupů. [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Nastavení program zkopíruje soubory skriptu SQL přidružené k funkci úložiště Instance pracovního postupu SQL do složky %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN. Spustit tyto soubory skriptu pro databázi systému SQL Server 2005 nebo SQL Server 2008, které chcete úložiště Instance SQL pracovního postupu, který chcete použít k uchování instancí pracovních postupů. Nejprve spustit soubor SqlWorkflowInstanceStoreSchema.sql a potom spusťte soubor SqlWorkflowInstanceStoreLogic.sql.  
  
> [!NOTE]
>  Chcete-li vyčištění databáze trvalost mít novou databázi, spusťte skripty v %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN v uvedeném pořadí.  
>   
>  1.  SqlWorkflowInstanceStoreSchema.sql  
> 2.  SqlWorkflowInstanceStoreLogic.sql  
  
> [!IMPORTANT]
>  Pokud nevytvoříte trvalost databáze, funkce ukládání Instance pracovního postupu SQL vyvolá výjimku podobné následující, když se hostitel pokusí zachovat pracovní postupy.  
>   
>  System.Data.SqlClient.SqlException: Nelze nalézt uloženou proceduru 'System.Activities.DurableInstancing.CreateLockOwner.  
  
 Následující části popisují postup povolení trvalosti pro pracovní postupy a pomocí ukládání Instance pracovního postupu SQL služby pracovních postupů. [!INCLUDE[crabout](../../../includes/crabout-md.md)]vlastnosti úložiště Instance pracovního postupu SQL, najdete v části [vlastnosti z pracovní postup Instance úložiště SQL](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).  
  
## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a>Povolení trvalosti pro pracovní postupy Self-Hosted, použít WorkflowApplication  
 Můžete povolit trvalost vlastním hostováním pracovních postupů, které používají <xref:System.Activities.WorkflowApplication> programově pomocí <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> objektový model. Následující postup obsahuje kroky, jak to provést.  
  
#### <a name="to-enable-persistence-for-self-hosted-workflows"></a>Chcete-li povolit trvalost pro pracovní postupy s vlastním hostováním  
  
1.  Přidáte odkaz na System.Activites.DurableInstancing.dll.  
  
2.  Přidejte následující příkaz v horní části souboru se zdrojovým po existující příkazy "použití".  
  
    ```csharp  
    using System.Activities.DurableInstancing;  
    ```  
  
3.  Vytvořit <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> a přiřadit ji ke <xref:System.Activities.WorkflowApplication.InstanceStore%2A> z <xref:System.Activities.WorkflowApplication> jak je znázorněno v následujícím příkladu kódu.  
  
    ```csharp  
    SqlWorkflowInstanceStore store =   
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");  
  
    WorkflowApplication wfApp =  
        new WorkflowApplication(new Workflow1());  
  
    wfApp.InstanceStore = store;  
    ```  
  
    > [!NOTE]
    >  V závislosti na vaší edicí systému SQL Server může být jiný název připojovacího řetězce serveru.  
  
4.  Vyvolání <xref:System.Activities.WorkflowApplication.Persist%2A> metodu <xref:System.Activities.WorkflowApplication> objekt pro zachování pracovního postupu, nebo <xref:System.Activities.WorkflowApplication.Unload%2A> metoda zachování a uvolnění pracovního postupu. Můžete také zpracovat <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> aktivováno událostí <xref:System.Activities.WorkflowApplication> objektu a vrátí odpovídající (<xref:System.Activities.PersistableIdleAction.Persist> nebo <xref:System.Activities.PersistableIdleAction.Unload>) členem <xref:System.Activities.PersistableIdleAction>.  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        return PersistableIdleAction.Persist;  
    };  
    ```  
  
> [!NOTE]
>  Najdete v článku [uchování aplikace pracovního postupu](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md) ukázku v [trvalost](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) příklad povolení trvalosti pro pracovní postupy pomocí <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>a [postupy: vytvoření a spuštění s dlouhým Spuštěný pracovní postup](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) krok [kurzu Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) pokyny krok za krokem.  
  
## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a>Povolení trvalosti pro Self-Hosted služby pracovního postupu, který použít hostitele služby pracovního postupu  
 Můžete povolit trvalost pro samoobslužné hostovaných pracovních postupů služby, které používají <xref:System.ServiceModel.WorkflowServiceHost> programově pomocí <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> třídy nebo <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> třídy.  
  
### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a>Používání třídy SqlWorkflowInstanceStoreBehavior  
 Následující postup obsahuje kroky při použití <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> třídy zapnout stálost pro samoobslužné hostovaných pracovních postupů služby.  
  
##### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a>Chcete-li povolit trvalost pomocí SqlWorkflowInstanceStoreBehavior  
  
1.  Přidáte odkaz na System.ServiceModel.dll.  
  
2.  Přidejte následující příkaz v horní části souboru se zdrojovým po existující příkazy "použití".  
  
    ```csharp  
    using System.ServiceModel.Activities.Description;  
    ```  
  
3.  Vytvoření instance `WorkflowServiceHost` a přidat koncové body služby pracovního postupu.  
  
    ```  
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));  
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");  
    ```  
  
4.  Vytvořit `SqlWorkflowInstanceStoreBehavior` objektu a vlastnosti objektu chování.  
  
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
  
    ```vb  
    host.Open();  
    ```  
  
> [!IMPORTANT]
>  Najdete v článku [předdefinované konfigurace](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md) ukázku v [trvalost](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) příklad povolení trvalosti pro pracovní postup služby pomocí `SqlWorkflowInstanceStoreBehavior` – třída.  
  
### <a name="using-the-durableinstancingoptions-property"></a>Pomocí vlastnosti DurableInstancingOptions  
 Když `SqlWorkflowInstanceStoreBehavior` platí, `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` je nastaven na `SqlWorkflowInstanceStore` objekt vytvořený pomocí hodnoty konfigurace. Můžete provést stejný prostřednictvím kódu programu se nastavit <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> vlastnost `WorkflowServiceHost` bez použití `SqlWorkflowInstanceStoreBehavior` třídy, jak je znázorněno v následujícím příkladu kódu.  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a>Povolení trvalosti pro služby WAS-Hosted pracovního postupu, který pomocí hostitele služby pracovního postupu pomocí konfiguračního souboru  
 Trvalost pro vlastním hostováním nebo Windows Process Activation Service WAS hostovaný pracovní postup služby můžete povolit pomocí konfiguračního souboru. Služby WAS hostovaný pracovní postup používá hostitele služby pracovního postupu, stejně jako služeb vlastním hostováním pracovních postupů.  
  
 `SqlWorkflowInstanceStoreBehavior`, Chování služby, který vám umožní snadno změnit [úložiště Instance pracovního postupu SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) vlastnosti prostřednictvím konfigurační soubor XML. Pro služby hostované WAS pracovního postupu použijte v souboru Web.config. Následující příklad konfigurace ukazuje, jak nakonfigurovat úložiště Instance pracovního postupu SQL pomocí `sqlWorkflowInstanceStore` chování element v konfiguračním souboru.  
  
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
  
 Pokud není nastaveno hodnoty `connectionString` nebo `connectionStringName` vlastnost úložiště Instance SQL pracovní postup používá výchozí připojovací řetězec s názvem `DefaultSqlWorkflowInstanceStoreConnectionString`.  
  
 Když `SqlWorkflowInstanceStoreBehavior` platí, `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` je nastaven na `SqlWorkflowInstanceStore` objekt vytvořený pomocí hodnoty konfigurace. Můžete provést stejný prostřednictvím kódu programu pro použití `SqlWorkflowInstanceStore` s `WorkflowServiceHost` bez použití elementu chování služby.  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
> [!IMPORTANT]
>  Doporučuje se neukládejte citlivé informace, například uživatelská jména a hesla v souboru Web.config. Pokud ukládáte citlivé informace v souboru Web.config, je nutné zabezpečit přístup k souboru Web.config pomocí systému souborů, které jsou seznamy řízení přístupu (ACL). Kromě toho můžete také zabezpečit hodnoty konfigurace v konfiguračním souboru jak je uvedeno v [šifrování informací pomocí chráněné konfigurace](http://go.microsoft.com/fwlink/?LinkId=178419).  
  
### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a>Machine.config elementy související s funkcí SQL ukládání Instance pracovního postupu  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Instalace přidá související s funkcí SQL ukládání Instance pracovního postupu k souboru Machine.config následující prvky:  
  
-   Přidá k souboru Machine.config následující element rozšíření chování, takže můžete použít <`sqlWorkflowInstanceStore`> element chování služby v konfiguračním souboru konfigurace trvalosti pro vaše služby.  
  
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
