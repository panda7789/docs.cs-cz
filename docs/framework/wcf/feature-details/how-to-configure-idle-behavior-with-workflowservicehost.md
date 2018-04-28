---
title: 'Postupy: Konfigurace chování při nečinnosti pomocí WorkflowServiceHost'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 55cc10357e8ae6b5458ca3440e1728cb578208b3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="4d948-102">Postupy: Konfigurace chování při nečinnosti pomocí WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="4d948-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="4d948-103">Když narazí záložka, která musí být obnoven, pomocí některé externí podnětem, například při k instanci pracovního postupu se čeká na zprávu, která se dodávají pomocí přejděte nečinnosti pracovních postupů <xref:System.ServiceModel.Activities.Receive> aktivity.</span><span class="sxs-lookup"><span data-stu-id="4d948-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="4d948-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> je chování, které vám umožní určit čas mezi při přechodu nečinnosti instance služby, a pokud je instance jako trvalý, nebo odpojeno.</span><span class="sxs-lookup"><span data-stu-id="4d948-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="4d948-105">Obsahuje dvě vlastnosti, které umožňují nastavit tyto časové úseky.</span><span class="sxs-lookup"><span data-stu-id="4d948-105">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="4d948-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> Určuje časový interval mezi při přechodu nečinnosti instance služby pracovního postupu a když je trvalé instance služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4d948-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="4d948-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> Určuje časový interval mezi když pracovní postup služby instance přejde nečinnosti a když instance služby pracovního postupu je odpojen, kde uvolnění znamená uložením instance na ukládání instance a odebere ji z paměti.</span><span class="sxs-lookup"><span data-stu-id="4d948-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="4d948-108">Toto téma vysvětluje, jak nakonfigurovat <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="4d948-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="4d948-109">Ke konfiguraci WorkflowIdleBehavior</span><span class="sxs-lookup"><span data-stu-id="4d948-109">To configure WorkflowIdleBehavior</span></span>  
  
1.  <span data-ttu-id="4d948-110">Přidat <`workflowIdle`> elementu, který chcete <`behavior`> v rámci <`serviceBehaviors`> elementu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4d948-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="4d948-111">`timeToUnload` Atribut určuje časové období mezi při přechodu nečinnosti instance pracovního postupu služby a služby pracovního postupu je odpojen.</span><span class="sxs-lookup"><span data-stu-id="4d948-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="4d948-112">`timeToPersist` Atribut určuje časové období mezi při přechodu nečinnosti instance služby pracovního postupu a když je trvalé instance služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="4d948-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="4d948-113">Výchozí hodnota pro `timeToUnload` je 1 minuta.</span><span class="sxs-lookup"><span data-stu-id="4d948-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="4d948-114">Výchozí hodnota pro `timeToPersist` je <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="4d948-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="4d948-115">Pokud chcete do nečinnosti instancí mějte na paměti, ale je uchoval pro odolnost, nastavte hodnoty tak, aby `timeToPersist`  <  `timeToUnload`.</span><span class="sxs-lookup"><span data-stu-id="4d948-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="4d948-116">Pokud chcete zabránit odpojení nečinnosti instancí, nastavte `timeToUnload` k <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="4d948-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4d948-117"> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, najdete v části [rozšíření hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="4d948-117"> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4d948-118">V předchozím příkladu konfigurace používá zjednodušená konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4d948-118">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="4d948-119">Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="4d948-119">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="4d948-120">Chcete-li změnit chování při nečinnosti v kódu</span><span class="sxs-lookup"><span data-stu-id="4d948-120">To change idle behavior in code</span></span>  
  
-   <span data-ttu-id="4d948-121">Následující příklad změní dobu čekání před uložením a uvolňování prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="4d948-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4d948-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d948-122">See Also</span></span>  
 [<span data-ttu-id="4d948-123">Rozšiřitelnost hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="4d948-123">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [<span data-ttu-id="4d948-124">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="4d948-124">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="4d948-125">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="4d948-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
