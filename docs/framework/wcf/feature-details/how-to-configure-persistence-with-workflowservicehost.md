---
title: 'Postupy: Konfigurace trvalosti pomocí třídy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 2cae73bd503afec6ddd1faf435645ebc21f4fc76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968486"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Postupy: Konfigurace trvalosti pomocí třídy WorkflowServiceHost
Toto téma popisuje, jak nakonfigurovat funkci úložiště instance pracovního postupu SQL pro povolení trvalosti pro pracovní postupy <xref:System.ServiceModel.Activities.WorkflowServiceHost> hostované v nástroji pomocí konfiguračního souboru. Před použitím funkce úložiště instance pracovního postupu SQL je nutné vytvořit databázi SQL, která se používá k zachování instancí pracovního postupu. Další informace najdete v tématu [jak: Povolte trvalost SQL pro pracovní postupy a služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)pracovních postupů.  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Konfigurace úložiště instance pracovního postupu SQL v konfiguraci  
  
1. Vlastnosti úložiště instancí pracovních postupů SQL lze konfigurovat prostřednictvím rozhraní <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, což je chování služby, které umožňuje změnit nastavení prostřednictvím konfigurace XML. Následující příklad konfigurace ukazuje, jak nakonfigurovat úložiště instance pracovního postupu SQL pomocí elementu <`sqlWorkflowInstanceStore`> chování v konfiguračním souboru.  
  
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
            <sqlWorkflowInstanceStore/>  
        </behavior>  
    </serviceBehaviors>  
    ```  
  
     Další informace o tom, jak nakonfigurovat úložiště instancí pracovních postupů SQL, najdete [v tématu How to: Povolte trvalost SQL pro pracovní postupy a služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)pracovních postupů. Další informace o jednotlivých nastaveních prvku <`sqlWorkflowInstanceStore`> chování najdete v tématu [úložiště instance pracovního postupu SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric poskytuje vlastní úložiště trvalosti. Další informace najdete v tématu [trvalost Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    > Předchozí příklad konfigurace používá zjednodušenou konfiguraci. Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) .  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>Konfigurace úložiště instance pracovního postupu SQL v kódu  
  
1. Vlastnosti úložiště instance pracovního postupu SQL lze konfigurovat prostřednictvím rozhraní <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, což je chování služby, které umožňuje změnit nastavení prostřednictvím kódu. Následující příklad ukazuje, jak nakonfigurovat úložiště instance pracovního postupu SQL pomocí <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> elementu Behavior v kódu  
  
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
  
     Další informace o tom, jak nakonfigurovat úložiště instancí pracovních postupů SQL, najdete [v tématu How to: Povolte trvalost SQL pro pracovní postupy a služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)pracovních postupů. Další informace o jednotlivých nastaveních <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> prvku chování najdete v tématu [úložiště instance pracovního postupu SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric poskytuje vlastní úložiště trvalosti. Další informace najdete v tématu [trvalost Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    > Předchozí příklad konfigurace používá zjednodušenou konfiguraci. Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) .  
  
     Příklad, jak nakonfigurovat trvalost programově, najdete v tématu [How to: Povolte trvalost pro pracovní postupy a služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md)pracovních postupů.  
  
## <a name="see-also"></a>Viz také:

- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Trvalost pracovního postupu](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [Trvalost prostředků Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193121)
