---
title: 'Postupy: Konfigurace chování pracovního postupu nezpracované výjimky pomocí třídy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: cd3729019b5371b5313bba3814758c723c0d448a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318741"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Postupy: Konfigurace chování pracovního postupu nezpracované výjimky pomocí třídy WorkflowServiceHost
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Je chování, které vám umožní zadat akce má být provedena, pokud dojde k neošetřené výjimce v pracovním postupu hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Toto téma ukazuje, jak konfigurovat toto chování v konfiguračním souboru.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>Ke konfiguraci WorkflowUnhandledExceptionBehavior  
  
1. Přidat <`workflowUnhandledException`> element v <`behavior`> element v rámci <`serviceBehaviors`> element, pomocí `action` atribut k určení akce má být provedena, když dojde k neošetřené výjimce, jak je znázorněno v následujícím příkladu.  
  
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
    >  Zjednodušená konfigurace používá předchozí ukázka konfigurace. Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Toto chování lze nastavit v kódu, jak je znázorněno v následujícím příkladu.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     `action` Atribut <`workflowUnhandledException`> element můžete nastavit na jedno z následujících hodnot:  
  
     **abandon**  
     Zruší instance v paměti bez zásahu do stavu trvalé instanci (který se vrátit k poslední bod trvalého).  
  
     **abandonAndSuspend**  
     Zruší instance v paměti a aktualizuje trvalou instanci bude pozastavena.  
  
     **Zrušit**  
     Obslužné rutiny zrušení volání pro instanci a pak dokončí instance v paměti, což může také odebrat z úložiště instancí  
  
     **terminate**  
     Dokončení instance v paměti a odstraní ji z úložiště instancí.  
  
     Další informace o <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, naleznete v tématu [rozšíření hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Viz také:

- [Rozšíření hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
