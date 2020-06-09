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
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Postupy: Konfigurace chování při nečinnosti pomocí WorkflowServiceHost
Pracovní postupy se přestanou nečinné, pokud se objeví záložka, která musí být obnovena některým externím podnětem, například když instance pracovního postupu čeká na doručení zprávy pomocí <xref:System.ServiceModel.Activities.Receive> aktivity. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>je chování, které umožňuje zadat čas mezi tím, kdy instance služby přestane být v nečinnosti a kdy je instance trvalá nebo odpojená. Obsahuje dvě vlastnosti, které vám umožní nastavit tyto časové rozsahy. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>Určuje časové období mezi tím, kdy instance služby pracovního postupu přestane být aktivní a když je instance služby pracovního postupu trvalá. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>Určuje časový rozsah mezi tím, kdy se instance služby pracovního postupu nečinný a když se instance služby pracovního postupu uvolní, kde uvolnění znamená trvalé uložení instance do úložiště instancí a jeho odebrání z paměti. Toto téma vysvětluje, jak nakonfigurovat <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> v konfiguračním souboru.  
  
### <a name="to-configure-workflowidlebehavior"></a>Konfigurace WorkflowIdleBehavior  
  
1. Do prvku `workflowIdle` <> prvku <> přidejte prvek <> `behavior` `serviceBehaviors` , jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     `timeToUnload`Atribut určuje časové období mezi tím, kdy instance služby pracovního postupu přestane být v nečinnosti, a když je služba pracovního postupu uvolněna. `timeToPersist`Atribut určuje časové období mezi tím, kdy instance služby pracovního postupu přestane být aktivní a když je instance služby pracovního postupu trvalá. Výchozí hodnota pro `timeToUnload` je 1 minuta. Výchozí hodnota pro `timeToPersist` je <xref:System.TimeSpan.MaxValue> . Pokud chcete zachovat nečinné instance v paměti, ale zachovat je odolnosti, nastavte hodnoty tak, aby `timeToPersist`  <  `timeToUnload` . Chcete-li zabránit nečinným instancím v uvolnění, nastavte `timeToUnload` na <xref:System.TimeSpan.MaxValue> . Další informace o najdete <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> v tématu [rozšiřitelnost hostitele služby pracovního postupu](workflow-service-host-extensibility.md) .  
  
    > [!NOTE]
    > Předchozí konfigurační ukázka používá zjednodušenou konfiguraci. Další informace najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Změna chování při nečinnosti v kódu  
  
- Následující příklad mění čas, který se má počkat, než se programově zachovají a uvolňuje.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Rozšiřitelnost hostitele služby pracovního postupu](workflow-service-host-extensibility.md)
- [Zjednodušená konfigurace](../simplified-configuration.md)
- [Služby pracovních postupů](workflow-services.md)
