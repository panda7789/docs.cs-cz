---
title: 'Postupy: Konfigurace chování při nečinnosti pomocí WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 67be47f97e57792e2f1e14505d3cd121729db33b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185086"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="0d5ed-102">Postupy: Konfigurace chování při nečinnosti pomocí WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="0d5ed-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="0d5ed-103">Pracovní postupy jsou nečinné, když narazí na záložku, která musí být obnovena některými externími podněty, například když instance pracovního postupu čeká na doručení zprávy pomocí <xref:System.ServiceModel.Activities.Receive> aktivity.</span><span class="sxs-lookup"><span data-stu-id="0d5ed-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="0d5ed-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>je chování, které umožňuje určit čas mezi tím, kdy instance služby přejde nečinnosti a kdy je instance trvalá nebo uvolněná.</span><span class="sxs-lookup"><span data-stu-id="0d5ed-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="0d5ed-105">Obsahuje dvě vlastnosti, které umožňují nastavit tyto časové rozsahy.</span><span class="sxs-lookup"><span data-stu-id="0d5ed-105">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="0d5ed-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>určuje časový rozsah mezi tím, kdy instance služby pracovního postupu přejde nečinnosti a kdy je instance služby pracovního postupu trvalá.</span><span class="sxs-lookup"><span data-stu-id="0d5ed-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="0d5ed-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>určuje časový rozsah mezi tím, kdy instance služby pracovního postupu přejde nečinnosti a kdy je instance služby pracovního postupu uvolněna, kde uvolnění znamená uchování instance do úložiště instancí a její odebrání z paměti.</span><span class="sxs-lookup"><span data-stu-id="0d5ed-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="0d5ed-108">Toto téma vysvětluje, <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> jak nakonfigurovat v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="0d5ed-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="0d5ed-109">Konfigurace funkce WorkflowIdleBehavior</span><span class="sxs-lookup"><span data-stu-id="0d5ed-109">To configure WorkflowIdleBehavior</span></span>  
  
1. <span data-ttu-id="0d5ed-110">Přidejte `workflowIdle` prvek <> `behavior` do prvku `serviceBehaviors` <> v rámci prvku <>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0d5ed-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="0d5ed-111">Atribut `timeToUnload` určuje časové období mezi tím, kdy instance služby pracovního postupu nečinnosti a kdy je služba pracovního postupu uvolněna.</span><span class="sxs-lookup"><span data-stu-id="0d5ed-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="0d5ed-112">Atribut `timeToPersist` určuje časové období mezi tím, kdy instance služby pracovního postupu přejde nečinnosti a kdy je instance služby pracovního postupu trvalá.</span><span class="sxs-lookup"><span data-stu-id="0d5ed-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="0d5ed-113">Výchozí hodnota `timeToUnload` pro je 1 minuta.</span><span class="sxs-lookup"><span data-stu-id="0d5ed-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="0d5ed-114">Výchozí hodnota `timeToPersist` pro <xref:System.TimeSpan.MaxValue>je .</span><span class="sxs-lookup"><span data-stu-id="0d5ed-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="0d5ed-115">Pokud chcete zachovat nečinnosti instance v paměti, ale zachovat je `timeToPersist`  <  `timeToUnload`pro robustnost, nastavte hodnoty tak, aby .</span><span class="sxs-lookup"><span data-stu-id="0d5ed-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="0d5ed-116">Pokud chcete zabránit uvolnění nečinných instancí, <xref:System.TimeSpan.MaxValue>nastavte na `timeToUnload` .</span><span class="sxs-lookup"><span data-stu-id="0d5ed-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="0d5ed-117">Další informace <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>o [aplikaci naleznete v tématu Rozšiřitelnost hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="0d5ed-117">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="0d5ed-118">Předchozí ukázka konfigurace používá zjednodušenou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="0d5ed-118">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="0d5ed-119">Další informace naleznete v [tématu Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="0d5ed-119">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="0d5ed-120">Změna nečinnosti v kódu</span><span class="sxs-lookup"><span data-stu-id="0d5ed-120">To change idle behavior in code</span></span>  
  
- <span data-ttu-id="0d5ed-121">Následující příklad změní čas čekání před uchování a uvolnění programově.</span><span class="sxs-lookup"><span data-stu-id="0d5ed-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0d5ed-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d5ed-122">See also</span></span>

- [<span data-ttu-id="0d5ed-123">Rozšiřitelnost hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="0d5ed-123">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="0d5ed-124">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="0d5ed-124">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="0d5ed-125">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="0d5ed-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
