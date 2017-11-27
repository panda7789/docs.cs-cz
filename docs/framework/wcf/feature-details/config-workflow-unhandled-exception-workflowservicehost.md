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
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="1d21d-102">Postupy: Konfigurace chování pracovního postupu nezpracované výjimky pomocí třídy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="1d21d-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="1d21d-103"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Je chování, která umožňuje určit akci v případě, že dojde k neošetřené výjimce v pracovním postupu hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="1d21d-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="1d21d-104">Toto téma ukazuje, jak pro konfiguraci tohoto chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="1d21d-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="1d21d-105">Ke konfiguraci WorkflowUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="1d21d-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1.  <span data-ttu-id="1d21d-106">Přidat <`workflowUnhandledException`> element v <`behavior`> v rámci <`serviceBehaviors`> element, pomocí `action` atribut k určení akce má provést, když dojde k neošetřené výjimce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1d21d-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
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
    >  <span data-ttu-id="1d21d-107">V předchozím příkladu konfigurace používá zjednodušená konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1d21d-107">The preceding configuration sample is using simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="1d21d-108">[Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="1d21d-108"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="1d21d-109">Toto chování lze konfigurovat v kódu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1d21d-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="1d21d-110">`action` Atribut <`workflowUnhandledException`> element můžete nastavit na jedno z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="1d21d-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="1d21d-111">**chyby**</span><span class="sxs-lookup"><span data-stu-id="1d21d-111">**abandon**</span></span>  
     <span data-ttu-id="1d21d-112">Zruší instance v paměti bez zásahu stav trvalou instance (která se vrátit zpět k vytvoření posledního bodu zachovat).</span><span class="sxs-lookup"><span data-stu-id="1d21d-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="1d21d-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="1d21d-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="1d21d-114">Zruší instance v paměti a aktualizuje trvalou instanci pozastaví.</span><span class="sxs-lookup"><span data-stu-id="1d21d-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="1d21d-115">**Zrušit**</span><span class="sxs-lookup"><span data-stu-id="1d21d-115">**cancel**</span></span>  
     <span data-ttu-id="1d21d-116">Obslužné rutiny zrušení volání pro instanci a pak dokončí instance v paměti, což může také k jeho odebrání z obchodu instance</span><span class="sxs-lookup"><span data-stu-id="1d21d-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="1d21d-117">**ukončení**</span><span class="sxs-lookup"><span data-stu-id="1d21d-117">**terminate**</span></span>  
     <span data-ttu-id="1d21d-118">Dokončení instance v paměti a odstraní ji z instance úložiště.</span><span class="sxs-lookup"><span data-stu-id="1d21d-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="1d21d-119"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, najdete v části [rozšíření hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="1d21d-119"> <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d21d-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d21d-120">See Also</span></span>  
 [<span data-ttu-id="1d21d-121">Rozšíření hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1d21d-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [<span data-ttu-id="1d21d-122">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="1d21d-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
