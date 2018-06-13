---
title: 'Postupy: Konfigurace chování pracovního postupu nezpracované výjimky pomocí třídy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: e09575a7998f676ea188a0500f31012c25c19738
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489190"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Postupy: Konfigurace chování pracovního postupu nezpracované výjimky pomocí třídy WorkflowServiceHost
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Je chování, která umožňuje určit akci v případě, že dojde k neošetřené výjimce v pracovním postupu hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Toto téma ukazuje, jak pro konfiguraci tohoto chování v konfiguračním souboru.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>Ke konfiguraci WorkflowUnhandledExceptionBehavior  
  
1.  Přidat <`workflowUnhandledException`> element v <`behavior`> v rámci <`serviceBehaviors`> element, pomocí `action` atribut k určení akce má provést, když dojde k neošetřené výjimce, jak je znázorněno v následujícím příkladu.  
  
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
    >  V předchozím příkladu konfigurace používá zjednodušená konfigurace. Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Toto chování lze konfigurovat v kódu, jak je znázorněno v následujícím příkladu.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     `action` Atribut <`workflowUnhandledException`> element můžete nastavit na jedno z následujících hodnot:  
  
     **Chyby**  
     Zruší instance v paměti bez zásahu stav trvalou instance (která se vrátit zpět k vytvoření posledního bodu zachovat).  
  
     **abandonAndSuspend**  
     Zruší instance v paměti a aktualizuje trvalou instanci pozastaví.  
  
     **Zrušit**  
     Obslužné rutiny zrušení volání pro instanci a pak dokončí instance v paměti, což může také k jeho odebrání z obchodu instance  
  
     **Ukončení**  
     Dokončení instance v paměti a odstraní ji z instance úložiště.  
  
     Další informace o <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, najdete v části [rozšíření hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřitelnost hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
