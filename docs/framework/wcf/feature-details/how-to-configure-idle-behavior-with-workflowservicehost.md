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
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Postupy: Konfigurace chování při nečinnosti pomocí WorkflowServiceHost
Pracovní postupy jsou nečinné, když narazí na záložku, která musí být obnovena některými externími podněty, například když instance pracovního postupu čeká na doručení zprávy pomocí <xref:System.ServiceModel.Activities.Receive> aktivity. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>je chování, které umožňuje určit čas mezi tím, kdy instance služby přejde nečinnosti a kdy je instance trvalá nebo uvolněná. Obsahuje dvě vlastnosti, které umožňují nastavit tyto časové rozsahy. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>určuje časový rozsah mezi tím, kdy instance služby pracovního postupu přejde nečinnosti a kdy je instance služby pracovního postupu trvalá. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>určuje časový rozsah mezi tím, kdy instance služby pracovního postupu přejde nečinnosti a kdy je instance služby pracovního postupu uvolněna, kde uvolnění znamená uchování instance do úložiště instancí a její odebrání z paměti. Toto téma vysvětluje, <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> jak nakonfigurovat v konfiguračním souboru.  
  
### <a name="to-configure-workflowidlebehavior"></a>Konfigurace funkce WorkflowIdleBehavior  
  
1. Přidejte `workflowIdle` prvek <> `behavior` do prvku `serviceBehaviors` <> v rámci prvku <>, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Atribut `timeToUnload` určuje časové období mezi tím, kdy instance služby pracovního postupu nečinnosti a kdy je služba pracovního postupu uvolněna. Atribut `timeToPersist` určuje časové období mezi tím, kdy instance služby pracovního postupu přejde nečinnosti a kdy je instance služby pracovního postupu trvalá. Výchozí hodnota `timeToUnload` pro je 1 minuta. Výchozí hodnota `timeToPersist` pro <xref:System.TimeSpan.MaxValue>je . Pokud chcete zachovat nečinnosti instance v paměti, ale zachovat je `timeToPersist`  <  `timeToUnload`pro robustnost, nastavte hodnoty tak, aby . Pokud chcete zabránit uvolnění nečinných instancí, <xref:System.TimeSpan.MaxValue>nastavte na `timeToUnload` . Další informace <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>o [aplikaci naleznete v tématu Rozšiřitelnost hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    > Předchozí ukázka konfigurace používá zjednodušenou konfiguraci. Další informace naleznete v [tématu Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Změna nečinnosti v kódu  
  
- Následující příklad změní čas čekání před uchování a uvolnění programově.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Rozšiřitelnost hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)
- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
