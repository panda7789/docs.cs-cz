---
title: 'Postupy: Konfigurace trvalosti pomocí WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 628a6b57b2d356aadadd96ebec312ef979aca6df
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501626"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="888e3-102">Postupy: Konfigurace trvalosti pomocí WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="888e3-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="888e3-103">Toto téma popisuje postup konfigurace funkce SQL Store Instance pracovního postupu pro povolení trvalosti pro pracovní postupy hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost> pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="888e3-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="888e3-104">Před použitím funkce SQL Store Instance pracovního postupu musíte vytvořit databázi SQL, který se používá k uchování instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="888e3-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="888e3-105">Další informace najdete v tématu [postupy: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="888e3-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="888e3-106">Ke konfiguraci Store Instance pracovního postupu SQL v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="888e3-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1.  <span data-ttu-id="888e3-107">Vlastnosti úložiště instancí pracovních postupů SQL je možné nakonfigurovat pomocí <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, chování služby, který vám umožní změnit nastavení prostřednictvím konfigurace XML.</span><span class="sxs-lookup"><span data-stu-id="888e3-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="888e3-108">Následující příklad konfigurace ukazuje postup při konfiguraci úložiště instancí pracovních postupů SQL s použitím <`sqlWorkflowInstanceStore`> prvek chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="888e3-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
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
  
     <span data-ttu-id="888e3-109">Další informace o tom, jak nakonfigurovat úložiště instancí pracovních postupů SQL najdete v tématu [postupy: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="888e3-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="888e3-110">Další informace o jednotlivých nastaveních pro <`sqlWorkflowInstanceStore`> prvek chování, naleznete v tématu [Store Instance pracovního postupu SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="888e3-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="888e3-111">Windows Server App Fabric poskytuje své vlastní úložiště pro trvalé.</span><span class="sxs-lookup"><span data-stu-id="888e3-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="888e3-112">Další informace najdete v tématu [systému Windows Server App Fabric trvalost](https://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="888e3-112">For more information, see [Windows Server App Fabric Persistence](https://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="888e3-113">Předchozí příklad konfigurace používá zjednodušené konfigurace.</span><span class="sxs-lookup"><span data-stu-id="888e3-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="888e3-114">Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="888e3-114">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="888e3-115">Ke konfiguraci Store Instance pracovního postupu SQL v kódu</span><span class="sxs-lookup"><span data-stu-id="888e3-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1.  <span data-ttu-id="888e3-116">Vlastnosti úložiště instancí pracovních postupů SQL je možné nakonfigurovat pomocí <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, chování služby, který vám umožní změnit nastavení prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="888e3-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="888e3-117">Následující příklad ukazuje, jak nakonfigurovat úložiště instancí pracovních postupů SQL s použitím <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> prvek chování v kódu</span><span class="sxs-lookup"><span data-stu-id="888e3-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
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
  
     <span data-ttu-id="888e3-118">Další informace o tom, jak nakonfigurovat úložiště instancí pracovních postupů SQL najdete v tématu [postupy: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="888e3-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="888e3-119">Další informace o jednotlivých nastaveních pro <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> chování prvku, naleznete v tématu [Store Instance pracovního postupu SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="888e3-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="888e3-120">Windows Server App Fabric poskytuje své vlastní úložiště pro trvalé.</span><span class="sxs-lookup"><span data-stu-id="888e3-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="888e3-121">Další informace najdete v tématu [systému Windows Server App Fabric trvalost](https://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="888e3-121">For more information, see [Windows Server App Fabric Persistence](https://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="888e3-122">Předchozí příklad konfigurace používá zjednodušené konfigurace.</span><span class="sxs-lookup"><span data-stu-id="888e3-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="888e3-123">Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="888e3-123">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="888e3-124">Příklad toho, jak prostřednictvím kódu programu Konfigurace trvalosti najdete v části [postupy: povolení trvalosti pro pracovní postupy a služby pracovních postupů](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="888e3-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="888e3-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="888e3-125">See Also</span></span>  
 [<span data-ttu-id="888e3-126">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="888e3-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="888e3-127">Trvalost pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="888e3-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [<span data-ttu-id="888e3-128">Windows Server App Fabric trvalosti</span><span class="sxs-lookup"><span data-stu-id="888e3-128">Windows Server App Fabric Persistence</span></span>](https://go.microsoft.com/fwlink/?LinkId=193121)
