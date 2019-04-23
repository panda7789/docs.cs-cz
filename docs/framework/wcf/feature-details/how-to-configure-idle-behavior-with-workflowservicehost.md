---
title: 'Postupy: Konfigurace chování při nečinnosti pomocí WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: a676f03b4e6f9dd210b843a6f3bf00c735889500
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330152"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="d6715-102">Postupy: Konfigurace chování při nečinnosti pomocí WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="d6715-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="d6715-103">Když narazí záložku, která se musí obnovit některé externí podnětů, například při instance pracovního postupu čeká na zprávu, která se dodávají pomocí funkce Přejít nečinných pracovních postupů <xref:System.ServiceModel.Activities.Receive> aktivity.</span><span class="sxs-lookup"><span data-stu-id="d6715-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="d6715-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> je chování, které vám umožní určit čas mezi při přechodu nečinné instance služby, a když instance je zachována nebo byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="d6715-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="d6715-105">Obsahuje dvě vlastnosti, které umožňují nastavit tyto časové úseky.</span><span class="sxs-lookup"><span data-stu-id="d6715-105">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="d6715-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> Určuje časový interval mezi při přechodu nečinné instance pracovního postupu služby a když instance služby pracovního postupu je trvalá.</span><span class="sxs-lookup"><span data-stu-id="d6715-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="d6715-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> Určuje časový interval mezi když pracovní postup služby instance přejde nečinnosti a instance služby pracovního postupu je uvolněn, kde uvolnění znamená to, že zachování instanci v úložišti instancí a odebere ji z paměti.</span><span class="sxs-lookup"><span data-stu-id="d6715-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="d6715-108">Toto téma vysvětluje, jak nakonfigurovat <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="d6715-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="d6715-109">Ke konfiguraci WorkflowIdleBehavior</span><span class="sxs-lookup"><span data-stu-id="d6715-109">To configure WorkflowIdleBehavior</span></span>  
  
1. <span data-ttu-id="d6715-110">Přidat <`workflowIdle`> element <`behavior`> element v rámci <`serviceBehaviors`> element, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d6715-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="d6715-111">`timeToUnload` Atribut určuje časové období mezi při přechodu nečinné instance pracovního postupu služby a služby pracovního postupu je uvolněn.</span><span class="sxs-lookup"><span data-stu-id="d6715-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="d6715-112">`timeToPersist` Atribut určuje časové období mezi při přechodu nečinné instance pracovního postupu služby a když instance služby pracovního postupu je trvalá.</span><span class="sxs-lookup"><span data-stu-id="d6715-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="d6715-113">Výchozí hodnota pro `timeToUnload` je 1 minuta.</span><span class="sxs-lookup"><span data-stu-id="d6715-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="d6715-114">Výchozí hodnota pro `timeToPersist` je <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="d6715-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="d6715-115">Pokud chcete zachovat nečinné instance v paměti, ale zachovat pro odolnost, nastavte hodnoty tak, aby `timeToPersist`  <  `timeToUnload`.</span><span class="sxs-lookup"><span data-stu-id="d6715-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="d6715-116">Pokud chcete zabránit uvolňován nečinné instance, nastavte `timeToUnload` k <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="d6715-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="d6715-117">Další informace o <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, naleznete v tématu [rozšíření hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="d6715-117">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d6715-118">Zjednodušená konfigurace používá předchozí ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d6715-118">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="d6715-119">Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d6715-119">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="d6715-120">Chcete-li změnit chování při nečinnosti v kódu</span><span class="sxs-lookup"><span data-stu-id="d6715-120">To change idle behavior in code</span></span>  
  
-   <span data-ttu-id="d6715-121">Následující příklad změní dobu čekání před uložením a uvolnění prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="d6715-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d6715-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6715-122">See also</span></span>

- [<span data-ttu-id="d6715-123">Rozšiřitelnost hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="d6715-123">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="d6715-124">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="d6715-124">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="d6715-125">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="d6715-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
