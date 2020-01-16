---
title: 'Postupy: Konfigurace trvalosti pomocí třídy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 7b65b89db674a624f7dfbf8ca816e0f0c2d2ff80
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963468"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="e9ae4-102">Postupy: Konfigurace trvalosti pomocí třídy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="e9ae4-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="e9ae4-103">Toto téma popisuje, jak nakonfigurovat funkci úložiště instance pracovního postupu SQL pro povolení trvalosti pro pracovní postupy hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost> pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="e9ae4-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="e9ae4-104">Před použitím funkce úložiště instance pracovního postupu SQL je nutné vytvořit databázi SQL, která se používá k zachování instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e9ae4-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="e9ae4-105">Další informace najdete v tématu [Postup: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="e9ae4-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="e9ae4-106">Konfigurace úložiště instance pracovního postupu SQL v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="e9ae4-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1. <span data-ttu-id="e9ae4-107">Vlastnosti úložiště instance pracovního postupu SQL je možné nakonfigurovat prostřednictvím <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, což je chování služby, které umožňuje změnit nastavení prostřednictvím konfigurace XML.</span><span class="sxs-lookup"><span data-stu-id="e9ae4-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="e9ae4-108">Následující příklad konfigurace ukazuje, jak nakonfigurovat úložiště instance pracovního postupu SQL pomocí`sqlWorkflowInstanceStore`< > prvku chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="e9ae4-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
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
  
     <span data-ttu-id="e9ae4-109">Další informace o tom, jak nakonfigurovat úložiště instancí pracovních postupů SQL, najdete v tématu [Postup: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="e9ae4-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="e9ae4-110">Další informace o jednotlivých nastaveních prvku <`sqlWorkflowInstanceStore`> chování najdete v tématu [úložiště instancí pracovních postupů SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="e9ae4-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="e9ae4-111">Windows Server App Fabric poskytuje vlastní úložiště trvalosti.</span><span class="sxs-lookup"><span data-stu-id="e9ae4-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="e9ae4-112">Další informace najdete v tématu [trvalost Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="e9ae4-112">For more information, see [Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e9ae4-113">Předchozí příklad konfigurace používá zjednodušenou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e9ae4-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="e9ae4-114">Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="e9ae4-114">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="e9ae4-115">Konfigurace úložiště instance pracovního postupu SQL v kódu</span><span class="sxs-lookup"><span data-stu-id="e9ae4-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1. <span data-ttu-id="e9ae4-116">Vlastnosti úložiště instance pracovního postupu SQL lze konfigurovat prostřednictvím <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, což je chování služby, které umožňuje změnit nastavení prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="e9ae4-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="e9ae4-117">Následující příklad ukazuje, jak nakonfigurovat úložiště instance pracovního postupu SQL pomocí elementu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> chování v kódu</span><span class="sxs-lookup"><span data-stu-id="e9ae4-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
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
  
     <span data-ttu-id="e9ae4-118">Další informace o tom, jak nakonfigurovat úložiště instancí pracovních postupů SQL, najdete v tématu [Postup: povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="e9ae4-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="e9ae4-119">Další informace o jednotlivých nastaveních prvku <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> chování najdete v tématu [úložiště instance pracovního postupu SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="e9ae4-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="e9ae4-120">Windows Server App Fabric poskytuje vlastní úložiště trvalosti.</span><span class="sxs-lookup"><span data-stu-id="e9ae4-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="e9ae4-121">Další informace najdete v tématu [trvalost Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="e9ae4-121">For more information, see [Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e9ae4-122">Předchozí příklad konfigurace používá zjednodušenou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e9ae4-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="e9ae4-123">Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="e9ae4-123">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="e9ae4-124">Příklad, jak nakonfigurovat trvalost programově, najdete v tématu [Postup: povolení trvalosti pro pracovní postupy a služby pracovních postupů](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="e9ae4-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9ae4-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9ae4-125">See also</span></span>

- [<span data-ttu-id="e9ae4-126">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e9ae4-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="e9ae4-127">Trvalost pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e9ae4-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- <span data-ttu-id="e9ae4-128">[Trvalost prostředků Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e9ae4-128">[Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))</span></span>
