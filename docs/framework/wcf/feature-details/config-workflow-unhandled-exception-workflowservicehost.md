---
title: "Postupy: Konfigurace chování pracovního postupu nezpracované výjimky pomocí třídy WorkflowServiceHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ac014e5854f697c73ff8277104f22081c3417391
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
    >  V předchozím příkladu konfigurace používá zjednodušená konfigurace. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Toto chování lze konfigurovat v kódu, jak je znázorněno v následujícím příkladu.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     `action` Atribut <`workflowUnhandledException`> element můžete nastavit na jedno z následujících hodnot:  
  
     **chyby**  
     Zruší instance v paměti bez zásahu stav trvalou instance (která se vrátit zpět k vytvoření posledního bodu zachovat).  
  
     **abandonAndSuspend**  
     Zruší instance v paměti a aktualizuje trvalou instanci pozastaví.  
  
     **Zrušit**  
     Obslužné rutiny zrušení volání pro instanci a pak dokončí instance v paměti, což může také k jeho odebrání z obchodu instance  
  
     **ukončení**  
     Dokončení instance v paměti a odstraní ji z instance úložiště.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, najdete v části [rozšíření hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
