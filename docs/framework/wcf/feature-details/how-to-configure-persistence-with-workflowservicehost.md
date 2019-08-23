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
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="c2018-102">Postupy: Konfigurace trvalosti pomocí třídy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="c2018-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="c2018-103">Toto téma popisuje, jak nakonfigurovat funkci úložiště instance pracovního postupu SQL pro povolení trvalosti pro pracovní postupy <xref:System.ServiceModel.Activities.WorkflowServiceHost> hostované v nástroji pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="c2018-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="c2018-104">Před použitím funkce úložiště instance pracovního postupu SQL je nutné vytvořit databázi SQL, která se používá k zachování instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c2018-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="c2018-105">Další informace najdete v tématu [jak: Povolte trvalost SQL pro pracovní postupy a služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="c2018-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="c2018-106">Konfigurace úložiště instance pracovního postupu SQL v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="c2018-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1. <span data-ttu-id="c2018-107">Vlastnosti úložiště instancí pracovních postupů SQL lze konfigurovat prostřednictvím rozhraní <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, což je chování služby, které umožňuje změnit nastavení prostřednictvím konfigurace XML.</span><span class="sxs-lookup"><span data-stu-id="c2018-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="c2018-108">Následující příklad konfigurace ukazuje, jak nakonfigurovat úložiště instance pracovního postupu SQL pomocí elementu <`sqlWorkflowInstanceStore`> chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="c2018-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
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
  
     <span data-ttu-id="c2018-109">Další informace o tom, jak nakonfigurovat úložiště instancí pracovních postupů SQL, najdete [v tématu How to: Povolte trvalost SQL pro pracovní postupy a služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="c2018-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="c2018-110">Další informace o jednotlivých nastaveních prvku <`sqlWorkflowInstanceStore`> chování najdete v tématu [úložiště instance pracovního postupu SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="c2018-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="c2018-111">Windows Server App Fabric poskytuje vlastní úložiště trvalosti.</span><span class="sxs-lookup"><span data-stu-id="c2018-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="c2018-112">Další informace najdete v tématu [trvalost Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="c2018-112">For more information, see [Windows Server App Fabric Persistence](https://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c2018-113">Předchozí příklad konfigurace používá zjednodušenou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="c2018-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="c2018-114">Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="c2018-114">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="c2018-115">Konfigurace úložiště instance pracovního postupu SQL v kódu</span><span class="sxs-lookup"><span data-stu-id="c2018-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1. <span data-ttu-id="c2018-116">Vlastnosti úložiště instance pracovního postupu SQL lze konfigurovat prostřednictvím rozhraní <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, což je chování služby, které umožňuje změnit nastavení prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="c2018-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="c2018-117">Následující příklad ukazuje, jak nakonfigurovat úložiště instance pracovního postupu SQL pomocí <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> elementu Behavior v kódu</span><span class="sxs-lookup"><span data-stu-id="c2018-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
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
  
     <span data-ttu-id="c2018-118">Další informace o tom, jak nakonfigurovat úložiště instancí pracovních postupů SQL, najdete [v tématu How to: Povolte trvalost SQL pro pracovní postupy a služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="c2018-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="c2018-119">Další informace o jednotlivých nastaveních <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> prvku chování najdete v tématu [úložiště instance pracovního postupu SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="c2018-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="c2018-120">Windows Server App Fabric poskytuje vlastní úložiště trvalosti.</span><span class="sxs-lookup"><span data-stu-id="c2018-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="c2018-121">Další informace najdete v tématu [trvalost Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="c2018-121">For more information, see [Windows Server App Fabric Persistence](https://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c2018-122">Předchozí příklad konfigurace používá zjednodušenou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="c2018-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="c2018-123">Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="c2018-123">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="c2018-124">Příklad, jak nakonfigurovat trvalost programově, najdete v tématu [How to: Povolte trvalost pro pracovní postupy a služby](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md)pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="c2018-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2018-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2018-125">See also</span></span>

- [<span data-ttu-id="c2018-126">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="c2018-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="c2018-127">Trvalost pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="c2018-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [<span data-ttu-id="c2018-128">Trvalost prostředků Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="c2018-128">Windows Server App Fabric Persistence</span></span>](https://go.microsoft.com/fwlink/?LinkId=193121)
