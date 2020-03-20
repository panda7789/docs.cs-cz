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
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="5489a-102">Postupy: Konfigurace chování pracovního postupu nezpracované výjimky pomocí třídy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="5489a-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="5489a-103">Toto <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> chování umožňuje určit akci, která má být vykonána, pokud <xref:System.ServiceModel.Activities.WorkflowServiceHost>dojde k neošetřené výjimce v rámci pracovního postupu hostovaného v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="5489a-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="5489a-104">Toto téma ukazuje, jak nakonfigurovat toto chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="5489a-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="5489a-105">Konfigurace funkce WorkflowUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="5489a-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1. <span data-ttu-id="5489a-106">Přidejte `workflowUnhandledException` prvek <> `behavior` do prvku `serviceBehaviors` <> v `action` rámci elementu <> pomocí atributu k určení akce, která má být v případě, že dojde k neošetřené výjimce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5489a-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
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
    > <span data-ttu-id="5489a-107">Předchozí ukázka konfigurace používá zjednodušenou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="5489a-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="5489a-108">Další informace naleznete v [tématu Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="5489a-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="5489a-109">Toto chování lze nakonfigurovat v kódu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="5489a-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="5489a-110">Atribut `action` prvku <`workflowUnhandledException`> lze nastavit na jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="5489a-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="5489a-111">**Opustit**</span><span class="sxs-lookup"><span data-stu-id="5489a-111">**abandon**</span></span>  
     <span data-ttu-id="5489a-112">Přeruší instanci v paměti bez dotyku stavu trvalé instance (to znamená vrátit zpět do posledního bodu uchování).</span><span class="sxs-lookup"><span data-stu-id="5489a-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="5489a-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="5489a-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="5489a-114">Přeruší instanci v paměti a aktualizuje trvalé instance, které mají být pozastaveny.</span><span class="sxs-lookup"><span data-stu-id="5489a-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="5489a-115">**Zrušit**</span><span class="sxs-lookup"><span data-stu-id="5489a-115">**cancel**</span></span>  
     <span data-ttu-id="5489a-116">Volá obslužné rutiny zrušení pro instanci a potom dokončí instanci v paměti, která může také odebrat z úložiště instancí</span><span class="sxs-lookup"><span data-stu-id="5489a-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="5489a-117">**Ukončit**</span><span class="sxs-lookup"><span data-stu-id="5489a-117">**terminate**</span></span>  
     <span data-ttu-id="5489a-118">Dokončí instanci v paměti a odebere ji z úložiště instancí.</span><span class="sxs-lookup"><span data-stu-id="5489a-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="5489a-119">Další informace <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>naleznete v [tématu Rozšiřitelnost hostitele služby Pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="5489a-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5489a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5489a-120">See also</span></span>

- [<span data-ttu-id="5489a-121">Rozšiřitelnost hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="5489a-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="5489a-122">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="5489a-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
