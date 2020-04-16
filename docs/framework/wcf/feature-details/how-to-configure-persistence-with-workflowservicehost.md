---
title: 'Postupy: Konfigurace trvalosti pomocí WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 4bfa66a895ae9af9cb87ff110dc82c8a8a922b49
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463838"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Postupy: Konfigurace trvalosti pomocí WorkflowServiceHost
Toto téma popisuje, jak nakonfigurovat funkci úložiště instancí pracovního <xref:System.ServiceModel.Activities.WorkflowServiceHost> postupu SQL tak, aby umožňovala trvalost pro pracovní postupy hostované v aplikaci pomocí konfiguračního souboru. Před použitím funkce ÚLOŽIŠTĚ instancí pracovního postupu SQL je nutné vytvořit databázi SQL, která se používá k uchování instancí pracovního postupu. Další informace naleznete v [tématu How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Konfigurace úložiště instancí pracovního postupu SQL v konfiguraci  
  
1. Vlastnosti úložiště instancí pracovního postupu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>SQL lze konfigurovat pomocí chování služby , které umožňuje změnit nastavení pomocí konfigurace XML. Následující příklad konfigurace ukazuje, jak nakonfigurovat úložiště instancí pracovního postupu SQL pomocí elementu <`sqlWorkflowInstanceStore`> chování v konfiguračním souboru.  
  
    ```xml  
    <serviceBehaviors>  
        <behavior name="">  
            <sqlWorkflowInstanceStore
                 connectionString="provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                 instanceEncodingOption="GZip | None"  
                 instanceCompletionAction="DeleteAll | DeleteNothing"  
                 instanceLockedExceptionAction="NoRetry | SimpleRetry | AggressiveRetry"  
                 hostLockRenewalPeriod="00:00:30"
                 runnableInstancesDetectionPeriod="00:00:05">  
            </sqlWorkflowInstanceStore>  
        </behavior>  
    </serviceBehaviors>  
    ```  
  
     Další informace o konfiguraci úložiště instancí pracovního postupu SQL naleznete v [tématu How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Další informace o jednotlivých nastaveních prvku chování <`sqlWorkflowInstanceStore`> naleznete v tématu SQL Workflow Instance [Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric poskytuje vlastní úložiště trvalosti. Další informace naleznete v tématu [Trvalosti prostředků na aplikaci Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).  
  
    > [!NOTE]
    > Předchozí příklad konfigurace používá zjednodušenou konfiguraci. Další informace naleznete v [tématu Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>Konfigurace úložiště instancí pracovního postupu SQL v kódu  
  
1. Vlastnosti úložiště instancí pracovního postupu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>SQL lze nakonfigurovat prostřednictvím chování služby, které umožňuje změnit nastavení prostřednictvím kódu. Následující příklad ukazuje, jak nakonfigurovat úložiště instancí pracovního postupu SQL pomocí elementu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior v kódu  
  
    ```csharp  
    host.Description.Behaviors.Add(new SqlWorkflowInstanceStoreBehavior  
    {  
       ConnectionString = "provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true",  
       InstanceEncodingOption = "GZip | None",  
       InstanceCompletionAction = "DeleteAll | DeleteNothing",  
       InstanceLockedExceptionAction = "NoRetry | SimpleRetry | AggressiveRetry",  
       HostLockRenewalPeriod = new TimeSpan(00, 00, 30),  
       RunnableInstancesDetectionPeriod = new TimeSpan(00, 00, 05)  
    });  
    ```  
  
     Další informace o konfiguraci úložiště instancí pracovního postupu SQL naleznete v [tématu How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Další informace o jednotlivých <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> nastaveních prvku chování naleznete v tématu [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric poskytuje vlastní úložiště trvalosti. Další informace naleznete v tématu [Trvalosti prostředků na aplikaci Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).  
  
    > [!NOTE]
    > Předchozí příklad konfigurace používá zjednodušenou konfiguraci. Další informace naleznete v [tématu Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Příklad, jak programově nakonfigurovat trvalost, najdete v tématu [Postup: Povolit trvalost pro pracovní postupy a služby pracovního postupu](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Viz také

- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Trvalost pracovního postupu](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [Trvalosti prostředků infrastruktury aplikací systému Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))
