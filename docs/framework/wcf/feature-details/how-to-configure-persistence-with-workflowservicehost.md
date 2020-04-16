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
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="c6d5a-102">Postupy: Konfigurace trvalosti pomocí WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="c6d5a-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="c6d5a-103">Toto téma popisuje, jak nakonfigurovat funkci úložiště instancí pracovního <xref:System.ServiceModel.Activities.WorkflowServiceHost> postupu SQL tak, aby umožňovala trvalost pro pracovní postupy hostované v aplikaci pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="c6d5a-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="c6d5a-104">Před použitím funkce ÚLOŽIŠTĚ instancí pracovního postupu SQL je nutné vytvořit databázi SQL, která se používá k uchování instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c6d5a-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="c6d5a-105">Další informace naleznete v [tématu How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="c6d5a-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="c6d5a-106">Konfigurace úložiště instancí pracovního postupu SQL v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="c6d5a-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1. <span data-ttu-id="c6d5a-107">Vlastnosti úložiště instancí pracovního postupu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>SQL lze konfigurovat pomocí chování služby , které umožňuje změnit nastavení pomocí konfigurace XML.</span><span class="sxs-lookup"><span data-stu-id="c6d5a-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="c6d5a-108">Následující příklad konfigurace ukazuje, jak nakonfigurovat úložiště instancí pracovního postupu SQL pomocí elementu <`sqlWorkflowInstanceStore`> chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="c6d5a-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
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
  
     <span data-ttu-id="c6d5a-109">Další informace o konfiguraci úložiště instancí pracovního postupu SQL naleznete v [tématu How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="c6d5a-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="c6d5a-110">Další informace o jednotlivých nastaveních prvku chování <`sqlWorkflowInstanceStore`> naleznete v tématu SQL Workflow Instance [Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="c6d5a-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="c6d5a-111">Windows Server App Fabric poskytuje vlastní úložiště trvalosti.</span><span class="sxs-lookup"><span data-stu-id="c6d5a-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="c6d5a-112">Další informace naleznete v tématu [Trvalosti prostředků na aplikaci Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="c6d5a-112">For more information, see [Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c6d5a-113">Předchozí příklad konfigurace používá zjednodušenou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="c6d5a-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="c6d5a-114">Další informace naleznete v [tématu Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="c6d5a-114">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="c6d5a-115">Konfigurace úložiště instancí pracovního postupu SQL v kódu</span><span class="sxs-lookup"><span data-stu-id="c6d5a-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1. <span data-ttu-id="c6d5a-116">Vlastnosti úložiště instancí pracovního postupu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>SQL lze nakonfigurovat prostřednictvím chování služby, které umožňuje změnit nastavení prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="c6d5a-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="c6d5a-117">Následující příklad ukazuje, jak nakonfigurovat úložiště instancí pracovního postupu SQL pomocí elementu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior v kódu</span><span class="sxs-lookup"><span data-stu-id="c6d5a-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
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
  
     <span data-ttu-id="c6d5a-118">Další informace o konfiguraci úložiště instancí pracovního postupu SQL naleznete v [tématu How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="c6d5a-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="c6d5a-119">Další informace o jednotlivých <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> nastaveních prvku chování naleznete v tématu [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="c6d5a-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="c6d5a-120">Windows Server App Fabric poskytuje vlastní úložiště trvalosti.</span><span class="sxs-lookup"><span data-stu-id="c6d5a-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="c6d5a-121">Další informace naleznete v tématu [Trvalosti prostředků na aplikaci Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="c6d5a-121">For more information, see [Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c6d5a-122">Předchozí příklad konfigurace používá zjednodušenou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="c6d5a-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="c6d5a-123">Další informace naleznete v [tématu Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="c6d5a-123">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="c6d5a-124">Příklad, jak programově nakonfigurovat trvalost, najdete v tématu [Postup: Povolit trvalost pro pracovní postupy a služby pracovního postupu](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="c6d5a-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6d5a-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6d5a-125">See also</span></span>

- [<span data-ttu-id="c6d5a-126">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="c6d5a-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="c6d5a-127">Trvalost pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="c6d5a-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- <span data-ttu-id="c6d5a-128">[Trvalosti prostředků infrastruktury aplikací systému Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c6d5a-128">[Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))</span></span>
