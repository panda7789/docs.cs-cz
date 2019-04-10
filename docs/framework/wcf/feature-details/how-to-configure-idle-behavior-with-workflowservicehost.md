---
title: 'Postupy: Konfigurace chování při nečinnosti pomocí WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: a676f03b4e6f9dd210b843a6f3bf00c735889500
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330152"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Postupy: Konfigurace chování při nečinnosti pomocí WorkflowServiceHost
Když narazí záložku, která se musí obnovit některé externí podnětů, například při instance pracovního postupu čeká na zprávu, která se dodávají pomocí funkce Přejít nečinných pracovních postupů <xref:System.ServiceModel.Activities.Receive> aktivity. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> je chování, které vám umožní určit čas mezi při přechodu nečinné instance služby, a když instance je zachována nebo byla uvolněna. Obsahuje dvě vlastnosti, které umožňují nastavit tyto časové úseky. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> Určuje časový interval mezi při přechodu nečinné instance pracovního postupu služby a když instance služby pracovního postupu je trvalá. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> Určuje časový interval mezi když pracovní postup služby instance přejde nečinnosti a instance služby pracovního postupu je uvolněn, kde uvolnění znamená to, že zachování instanci v úložišti instancí a odebere ji z paměti. Toto téma vysvětluje, jak nakonfigurovat <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> v konfiguračním souboru.  
  
### <a name="to-configure-workflowidlebehavior"></a>Ke konfiguraci WorkflowIdleBehavior  
  
1. Přidat <`workflowIdle`> element <`behavior`> element v rámci <`serviceBehaviors`> element, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     `timeToUnload` Atribut určuje časové období mezi při přechodu nečinné instance pracovního postupu služby a služby pracovního postupu je uvolněn. `timeToPersist` Atribut určuje časové období mezi při přechodu nečinné instance pracovního postupu služby a když instance služby pracovního postupu je trvalá. Výchozí hodnota pro `timeToUnload` je 1 minuta. Výchozí hodnota pro `timeToPersist` je <xref:System.TimeSpan.MaxValue>. Pokud chcete zachovat nečinné instance v paměti, ale zachovat pro odolnost, nastavte hodnoty tak, aby `timeToPersist`  <  `timeToUnload`. Pokud chcete zabránit uvolňován nečinné instance, nastavte `timeToUnload` k <xref:System.TimeSpan.MaxValue>. Další informace o <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, naleznete v tématu [rozšíření hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    >  Zjednodušená konfigurace používá předchozí ukázka konfigurace. Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Chcete-li změnit chování při nečinnosti v kódu  
  
-   Následující příklad změní dobu čekání před uložením a uvolnění prostřednictvím kódu programu.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Rozšíření hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)
- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
