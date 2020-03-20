---
title: 'Postupy: Konfigurace chování pracovního postupu nezpracované výjimky pomocí třídy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 69c6b1ce11d735181390a0c67df2f8dbea4f906c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185315"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Postupy: Konfigurace chování pracovního postupu nezpracované výjimky pomocí třídy WorkflowServiceHost
Toto <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> chování umožňuje určit akci, která má být vykonána, pokud <xref:System.ServiceModel.Activities.WorkflowServiceHost>dojde k neošetřené výjimce v rámci pracovního postupu hostovaného v aplikaci . Toto téma ukazuje, jak nakonfigurovat toto chování v konfiguračním souboru.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>Konfigurace funkce WorkflowUnhandledExceptionBehavior  
  
1. Přidejte `workflowUnhandledException` prvek <> `behavior` do prvku `serviceBehaviors` <> v `action` rámci elementu <> pomocí atributu k určení akce, která má být v případě, že dojde k neošetřené výjimce, jak je znázorněno v následujícím příkladu.  
  
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
    > Předchozí ukázka konfigurace používá zjednodušenou konfiguraci. Další informace naleznete v [tématu Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Toto chování lze nakonfigurovat v kódu, jak je znázorněno v následujícím příkladu.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     Atribut `action` prvku <`workflowUnhandledException`> lze nastavit na jednu z následujících hodnot:  
  
     **Opustit**  
     Přeruší instanci v paměti bez dotyku stavu trvalé instance (to znamená vrátit zpět do posledního bodu uchování).  
  
     **abandonAndSuspend**  
     Přeruší instanci v paměti a aktualizuje trvalé instance, které mají být pozastaveny.  
  
     **Zrušit**  
     Volá obslužné rutiny zrušení pro instanci a potom dokončí instanci v paměti, která může také odebrat z úložiště instancí  
  
     **Ukončit**  
     Dokončí instanci v paměti a odebere ji z úložiště instancí.  
  
     Další informace <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>naleznete v [tématu Rozšiřitelnost hostitele služby Pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Viz také

- [Rozšiřitelnost hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
