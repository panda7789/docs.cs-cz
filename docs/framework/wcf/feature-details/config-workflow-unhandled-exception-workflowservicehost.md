---
title: 'Postupy: Konfigurace chování pracovního postupu nezpracované výjimky pomocí třídy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: aec2fd80e10ae1959b29c0883d51c4045517d792
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957260"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Postupy: Konfigurace chování pracovního postupu nezpracované výjimky pomocí třídy WorkflowServiceHost
Je chování, které umožňuje určit akci, která se má provést, pokud dojde k neošetřené výjimce v rámci pracovního postupu, který je hostovaný v <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> V tomto tématu se dozvíte, jak nakonfigurovat toto chování v konfiguračním souboru.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>Konfigurace WorkflowUnhandledExceptionBehavior  
  
1. Přidejte <`workflowUnhandledException`> prvek do <`behavior`> element v rámci <`serviceBehaviors`> elementu pomocí `action` atributu pro určení akce, která se má provést, když dojde k neošetřené výjimce, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > Předchozí konfigurační ukázka používá zjednodušenou konfiguraci. Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Toto chování lze nakonfigurovat v kódu, jak je znázorněno v následujícím příkladu.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     Atribut prvku <`workflowUnhandledException`> může být nastaven na jednu z následujících hodnot: `action`  
  
     **abandon**  
     Přeruší instanci v paměti, aniž by se dotkla trvalého stavu instance (tj. návrat k poslednímu bodu trvalého uložení).  
  
     **abandonAndSuspend**  
     Přeruší instanci v paměti a aktualizuje trvale pozastavenou instanci.  
  
     **operaci**  
     Volá obslužné rutiny zrušení pro instanci a pak dokončí instanci v paměti, což může také odebrat z úložiště instance.  
  
     **ruší**  
     Dokončí instanci v paměti a odebere ji z úložiště instance.  
  
     Další informace o <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>najdete v tématu [rozšiřitelnost hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Viz také:

- [Rozšiřitelnost hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
