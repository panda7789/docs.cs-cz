---
title: "Postupy: Konfigurace trvalosti pomocí třídy WorkflowServiceHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41211eb1d104e0e540e257cffd4647c6fff9fb25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="28459-102">Postupy: Konfigurace trvalosti pomocí třídy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="28459-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="28459-103">Toto téma popisuje postup konfigurace úložiště Instance pracovního postupu SQL funkci tak, aby zapnout stálost pro pracovní postupy hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost> pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="28459-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="28459-104">Před použitím funkce ukládání Instance pracovního postupu SQL musíte vytvořit databázi SQL, který je použitý k zachování instancí pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="28459-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="28459-105">[Postupy: povolení trvalost SQL pro pracovní postupy a pracovní postup služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="28459-105"> [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="28459-106">Konfigurace úložiště Instance pracovního postupu SQL v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="28459-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1.  <span data-ttu-id="28459-107">Vlastnosti úložiště instance SQL pracovního postupu můžete nakonfigurovat přes <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, chování služby, který vám umožní změnit nastavení prostřednictvím konfigurační soubor XML.</span><span class="sxs-lookup"><span data-stu-id="28459-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="28459-108">Následující příklad konfigurace ukazuje, jak nakonfigurovat úložiště instance pracovního postupu SQL pomocí <`sqlWorkflowInstanceStore`> element chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="28459-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="28459-109">Konfigurace úložiště instance pracovního postupu SQL najdete v tématu [postupy: povolení trvalost SQL pro pracovní postupy a pracovní postup služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="28459-109"> how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="28459-110">jednotlivá nastavení pro <`sqlWorkflowInstanceStore`> elementu chování, najdete v části [úložiště Instance pracovního postupu SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="28459-110"> the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="28459-111">Windows Server App Fabric poskytuje vlastní úložiště trvalosti.</span><span class="sxs-lookup"><span data-stu-id="28459-111">Windows Server App Fabric provides its own persistence store.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="28459-112">[Windows Server App Fabric trvalost](http://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="28459-112"> [Windows Server App Fabric Persistence](http://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="28459-113">V předchozím příkladu konfigurace používá zjednodušená konfigurace.</span><span class="sxs-lookup"><span data-stu-id="28459-113">The preceding configuration example uses simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="28459-114">[Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="28459-114"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="28459-115">Konfigurace úložiště Instance pracovního postupu SQL v kódu</span><span class="sxs-lookup"><span data-stu-id="28459-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1.  <span data-ttu-id="28459-116">Vlastnosti úložiště instance SQL pracovního postupu můžete nakonfigurovat přes <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, chování služby, který vám umožní změnit nastavení prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="28459-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="28459-117">Následující příklad ukazuje, jak nakonfigurovat úložiště instance pracovního postupu SQL pomocí <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> chování elementu v kódu</span><span class="sxs-lookup"><span data-stu-id="28459-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="28459-118">Konfigurace úložiště instance pracovního postupu SQL najdete v tématu [postupy: povolení trvalost SQL pro pracovní postupy a pracovní postup služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="28459-118"> how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="28459-119">jednotlivá nastavení pro <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> chování elementu, najdete v části [úložiště Instance pracovního postupu SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="28459-119"> the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="28459-120">Windows Server App Fabric poskytuje vlastní úložiště trvalosti.</span><span class="sxs-lookup"><span data-stu-id="28459-120">Windows Server App Fabric provides its own persistence store.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="28459-121">[Windows Server App Fabric trvalost](http://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="28459-121"> [Windows Server App Fabric Persistence](http://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="28459-122">V předchozím příkladu konfigurace používá zjednodušená konfigurace.</span><span class="sxs-lookup"><span data-stu-id="28459-122">The preceding configuration example uses simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="28459-123">[Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="28459-123"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="28459-124">Příklad způsobu konfigurace trvalosti prostřednictvím kódu programu naleznete v části [postupy: povolení trvalosti pro pracovní postupy a pracovní postup služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="28459-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28459-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="28459-125">See Also</span></span>  
 [<span data-ttu-id="28459-126">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="28459-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="28459-127">Trvalost pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="28459-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [<span data-ttu-id="28459-128">Windows Server App Fabric trvalost</span><span class="sxs-lookup"><span data-stu-id="28459-128">Windows Server App Fabric Persistence</span></span>](http://go.microsoft.com/fwlink/?LinkId=193121)
