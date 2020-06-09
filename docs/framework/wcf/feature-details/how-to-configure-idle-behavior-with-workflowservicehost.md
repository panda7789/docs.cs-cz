---
title: 'Postupy: Konfigurace chování při nečinnosti pomocí WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 8b9fa36408d5f2bc5445ebeccba61f71417935e7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599123"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="8026a-102">Postupy: Konfigurace chování při nečinnosti pomocí WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="8026a-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="8026a-103">Pracovní postupy se přestanou nečinné, pokud se objeví záložka, která musí být obnovena některým externím podnětem, například když instance pracovního postupu čeká na doručení zprávy pomocí <xref:System.ServiceModel.Activities.Receive> aktivity.</span><span class="sxs-lookup"><span data-stu-id="8026a-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="8026a-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>je chování, které umožňuje zadat čas mezi tím, kdy instance služby přestane být v nečinnosti a kdy je instance trvalá nebo odpojená.</span><span class="sxs-lookup"><span data-stu-id="8026a-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="8026a-105">Obsahuje dvě vlastnosti, které vám umožní nastavit tyto časové rozsahy.</span><span class="sxs-lookup"><span data-stu-id="8026a-105">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="8026a-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>Určuje časové období mezi tím, kdy instance služby pracovního postupu přestane být aktivní a když je instance služby pracovního postupu trvalá.</span><span class="sxs-lookup"><span data-stu-id="8026a-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="8026a-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>Určuje časový rozsah mezi tím, kdy se instance služby pracovního postupu nečinný a když se instance služby pracovního postupu uvolní, kde uvolnění znamená trvalé uložení instance do úložiště instancí a jeho odebrání z paměti.</span><span class="sxs-lookup"><span data-stu-id="8026a-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="8026a-108">Toto téma vysvětluje, jak nakonfigurovat <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="8026a-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="8026a-109">Konfigurace WorkflowIdleBehavior</span><span class="sxs-lookup"><span data-stu-id="8026a-109">To configure WorkflowIdleBehavior</span></span>  
  
1. <span data-ttu-id="8026a-110">Do prvku `workflowIdle` <> prvku <> přidejte prvek <> `behavior` `serviceBehaviors` , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8026a-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="8026a-111">`timeToUnload`Atribut určuje časové období mezi tím, kdy instance služby pracovního postupu přestane být v nečinnosti, a když je služba pracovního postupu uvolněna.</span><span class="sxs-lookup"><span data-stu-id="8026a-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="8026a-112">`timeToPersist`Atribut určuje časové období mezi tím, kdy instance služby pracovního postupu přestane být aktivní a když je instance služby pracovního postupu trvalá.</span><span class="sxs-lookup"><span data-stu-id="8026a-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="8026a-113">Výchozí hodnota pro `timeToUnload` je 1 minuta.</span><span class="sxs-lookup"><span data-stu-id="8026a-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="8026a-114">Výchozí hodnota pro `timeToPersist` je <xref:System.TimeSpan.MaxValue> .</span><span class="sxs-lookup"><span data-stu-id="8026a-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="8026a-115">Pokud chcete zachovat nečinné instance v paměti, ale zachovat je odolnosti, nastavte hodnoty tak, aby `timeToPersist`  <  `timeToUnload` .</span><span class="sxs-lookup"><span data-stu-id="8026a-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="8026a-116">Chcete-li zabránit nečinným instancím v uvolnění, nastavte `timeToUnload` na <xref:System.TimeSpan.MaxValue> .</span><span class="sxs-lookup"><span data-stu-id="8026a-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="8026a-117">Další informace o najdete <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> v tématu [rozšiřitelnost hostitele služby pracovního postupu](workflow-service-host-extensibility.md) .</span><span class="sxs-lookup"><span data-stu-id="8026a-117">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8026a-118">Předchozí konfigurační ukázka používá zjednodušenou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="8026a-118">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="8026a-119">Další informace najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="8026a-119">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="8026a-120">Změna chování při nečinnosti v kódu</span><span class="sxs-lookup"><span data-stu-id="8026a-120">To change idle behavior in code</span></span>  
  
- <span data-ttu-id="8026a-121">Následující příklad mění čas, který se má počkat, než se programově zachovají a uvolňuje.</span><span class="sxs-lookup"><span data-stu-id="8026a-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8026a-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="8026a-122">See also</span></span>

- [<span data-ttu-id="8026a-123">Rozšiřitelnost hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="8026a-123">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)
- [<span data-ttu-id="8026a-124">Zjednodušená konfigurace</span><span class="sxs-lookup"><span data-stu-id="8026a-124">Simplified Configuration</span></span>](../simplified-configuration.md)
- [<span data-ttu-id="8026a-125">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="8026a-125">Workflow Services</span></span>](workflow-services.md)
