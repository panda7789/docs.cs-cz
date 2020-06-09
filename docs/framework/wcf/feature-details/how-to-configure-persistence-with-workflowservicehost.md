---
title: 'Postupy: Konfigurace trvalosti pomocí WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 4ed9c76f091e75cf6ba7658f0314d2e21bbe962e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599110"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Postupy: Konfigurace trvalosti pomocí WorkflowServiceHost
Toto téma popisuje, jak nakonfigurovat funkci úložiště instance pracovního postupu SQL pro povolení trvalosti pro pracovní postupy hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost> nástroji pomocí konfiguračního souboru. Před použitím funkce úložiště instance pracovního postupu SQL je nutné vytvořit databázi SQL, která se používá k zachování instancí pracovního postupu. Další informace najdete v tématu [Postup: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Konfigurace úložiště instance pracovního postupu SQL v konfiguraci  
  
1. Vlastnosti úložiště instancí pracovních postupů SQL lze konfigurovat prostřednictvím rozhraní, což je <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> chování služby, které umožňuje změnit nastavení prostřednictvím konfigurace XML. Následující příklad konfigurace ukazuje, jak nakonfigurovat úložiště instance pracovního postupu SQL pomocí `sqlWorkflowInstanceStore` elementu <> chování v konfiguračním souboru.  
  
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
  
     Další informace o tom, jak nakonfigurovat úložiště instancí pracovních postupů SQL, najdete v tématu [Postup: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Další informace o jednotlivých nastaveních `sqlWorkflowInstanceStore` prvku <> chování najdete v tématu [úložiště instance pracovního postupu SQL](../../windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric poskytuje vlastní úložiště trvalosti. Další informace najdete v tématu [trvalost Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).  
  
    > [!NOTE]
    > Předchozí příklad konfigurace používá zjednodušenou konfiguraci. Další informace najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md) .  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>Konfigurace úložiště instance pracovního postupu SQL v kódu  
  
1. Vlastnosti úložiště instance pracovního postupu SQL lze konfigurovat prostřednictvím rozhraní, což je <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> chování služby, které umožňuje změnit nastavení prostřednictvím kódu. Následující příklad ukazuje, jak nakonfigurovat úložiště instance pracovního postupu SQL pomocí <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> elementu Behavior v kódu  
  
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
  
     Další informace o tom, jak nakonfigurovat úložiště instancí pracovních postupů SQL, najdete v tématu [Postup: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](../../windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Další informace o jednotlivých nastaveních <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> prvku chování najdete v tématu [úložiště instance pracovního postupu SQL](../../windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric poskytuje vlastní úložiště trvalosti. Další informace najdete v tématu [trvalost Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).  
  
    > [!NOTE]
    > Předchozí příklad konfigurace používá zjednodušenou konfiguraci. Další informace najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md) .  
  
     Příklad, jak nakonfigurovat trvalost programově, najdete v tématu [Postup: povolení trvalosti pro pracovní postupy a služby pracovních postupů](../../windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Viz také

- [Služby pracovních postupů](workflow-services.md)
- [Trvalost pracovního postupu](../../windows-workflow-foundation/workflow-persistence.md)
- [Trvalost prostředků Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))
