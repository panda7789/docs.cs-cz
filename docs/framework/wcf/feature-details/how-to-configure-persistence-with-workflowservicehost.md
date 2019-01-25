---
title: 'Postupy: Konfigurace trvalosti pomocí třídy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 2b340a46d10ef517d46a6e85fdb2f8e332cd0b46
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530321"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Postupy: Konfigurace trvalosti pomocí třídy WorkflowServiceHost
Toto téma popisuje postup konfigurace funkce SQL Store Instance pracovního postupu pro povolení trvalosti pro pracovní postupy hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost> pomocí konfiguračního souboru. Před použitím funkce SQL Store Instance pracovního postupu musíte vytvořit databázi SQL, který se používá k uchování instance pracovního postupu. Další informace najdete v tématu [jak: Povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Ke konfiguraci Store Instance pracovního postupu SQL v konfiguraci  
  
1.  Vlastnosti úložiště instancí pracovních postupů SQL je možné nakonfigurovat pomocí <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, chování služby, který vám umožní změnit nastavení prostřednictvím konfigurace XML. Následující příklad konfigurace ukazuje postup při konfiguraci úložiště instancí pracovních postupů SQL s použitím <`sqlWorkflowInstanceStore`> prvek chování v konfiguračním souboru.  
  
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
  
     Další informace o tom, jak nakonfigurovat úložiště instancí pracovních postupů SQL najdete v tématu [jak: Povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Další informace o jednotlivých nastaveních pro <`sqlWorkflowInstanceStore`> prvek chování, naleznete v tématu [Store Instance pracovního postupu SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric poskytuje své vlastní úložiště pro trvalé. Další informace najdete v tématu [systému Windows Server App Fabric trvalost](https://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  Předchozí příklad konfigurace používá zjednodušené konfigurace. Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>Ke konfiguraci Store Instance pracovního postupu SQL v kódu  
  
1.  Vlastnosti úložiště instancí pracovních postupů SQL je možné nakonfigurovat pomocí <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, chování služby, který vám umožní změnit nastavení prostřednictvím kódu. Následující příklad ukazuje, jak nakonfigurovat úložiště instancí pracovních postupů SQL s použitím <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> prvek chování v kódu  
  
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
  
     Další informace o tom, jak nakonfigurovat úložiště instancí pracovních postupů SQL najdete v tématu [jak: Povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Další informace o jednotlivých nastaveních pro <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> chování prvku, naleznete v tématu [Store Instance pracovního postupu SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric poskytuje své vlastní úložiště pro trvalé. Další informace najdete v tématu [systému Windows Server App Fabric trvalost](https://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  Předchozí příklad konfigurace používá zjednodušené konfigurace. Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Příklad toho, jak prostřednictvím kódu programu Konfigurace trvalosti najdete v části [jak: Povolení trvalosti pro pracovní postupy a služby pracovních postupů](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Viz také:
- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Trvalost pracovního postupu](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [Windows Server App Fabric trvalosti](https://go.microsoft.com/fwlink/?LinkId=193121)
