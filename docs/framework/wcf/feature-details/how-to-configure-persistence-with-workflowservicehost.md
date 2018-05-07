---
title: 'Postupy: Konfigurace trvalosti pomocí třídy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 9035ded1ca533d9b2107d90f605e15c9ce915965
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Postupy: Konfigurace trvalosti pomocí třídy WorkflowServiceHost
Toto téma popisuje postup konfigurace úložiště Instance pracovního postupu SQL funkci tak, aby zapnout stálost pro pracovní postupy hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost> pomocí konfiguračního souboru. Před použitím funkce ukládání Instance pracovního postupu SQL musíte vytvořit databázi SQL, který je použitý k zachování instancí pracovních postupů. Další informace najdete v tématu [postupy: povolení trvalost SQL pro pracovní postupy a pracovní postup služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Konfigurace úložiště Instance pracovního postupu SQL v konfiguraci  
  
1.  Vlastnosti úložiště instance SQL pracovního postupu můžete nakonfigurovat přes <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, chování služby, který vám umožní změnit nastavení prostřednictvím konfigurační soubor XML. Následující příklad konfigurace ukazuje, jak nakonfigurovat úložiště instance pracovního postupu SQL pomocí <`sqlWorkflowInstanceStore`> element chování v konfiguračním souboru.  
  
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
  
     Další informace o tom, jak nakonfigurovat úložiště instance pracovního postupu SQL najdete v tématu [postupy: povolení trvalost SQL pro pracovní postupy a pracovní postup služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Další informace o jednotlivých nastaveních pro <`sqlWorkflowInstanceStore`> elementu chování, najdete v části [úložiště Instance pracovního postupu SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric poskytuje vlastní úložiště trvalosti. Další informace najdete v tématu [Windows Server App Fabric trvalost](http://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  V předchozím příkladu konfigurace používá zjednodušená konfigurace. Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>Konfigurace úložiště Instance pracovního postupu SQL v kódu  
  
1.  Vlastnosti úložiště instance SQL pracovního postupu můžete nakonfigurovat přes <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, chování služby, který vám umožní změnit nastavení prostřednictvím kódu. Následující příklad ukazuje, jak nakonfigurovat úložiště instance pracovního postupu SQL pomocí <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> chování elementu v kódu  
  
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
  
     Další informace o tom, jak nakonfigurovat úložiště instance pracovního postupu SQL najdete v tématu [postupy: povolení trvalost SQL pro pracovní postupy a pracovní postup služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Další informace o jednotlivých nastaveních pro <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> chování elementu, najdete v části [úložiště Instance pracovního postupu SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server App Fabric poskytuje vlastní úložiště trvalosti. Další informace najdete v tématu [Windows Server App Fabric trvalost](http://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  V předchozím příkladu konfigurace používá zjednodušená konfigurace. Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Příklad způsobu konfigurace trvalosti prostřednictvím kódu programu naleznete v části [postupy: povolení trvalosti pro pracovní postupy a pracovní postup služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Trvalost pracovního postupu](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [Windows Server App Fabric trvalost](http://go.microsoft.com/fwlink/?LinkId=193121)
