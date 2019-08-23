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
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="cf4cd-102">Postupy: Konfigurace chování pracovního postupu nezpracované výjimky pomocí třídy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="cf4cd-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="cf4cd-103">Je chování, které umožňuje určit akci, která se má provést, pokud dojde k neošetřené výjimce v rámci pracovního postupu, který je hostovaný v <xref:System.ServiceModel.Activities.WorkflowServiceHost>. <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior></span><span class="sxs-lookup"><span data-stu-id="cf4cd-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="cf4cd-104">V tomto tématu se dozvíte, jak nakonfigurovat toto chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="cf4cd-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="cf4cd-105">Konfigurace WorkflowUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="cf4cd-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1. <span data-ttu-id="cf4cd-106">Přidejte <`workflowUnhandledException`> prvek do <`behavior`> element v rámci <`serviceBehaviors`> elementu pomocí `action` atributu pro určení akce, která se má provést, když dojde k neošetřené výjimce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="cf4cd-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
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
    > <span data-ttu-id="cf4cd-107">Předchozí konfigurační ukázka používá zjednodušenou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="cf4cd-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="cf4cd-108">Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="cf4cd-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="cf4cd-109">Toto chování lze nakonfigurovat v kódu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="cf4cd-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="cf4cd-110">Atribut prvku <`workflowUnhandledException`> může být nastaven na jednu z následujících hodnot: `action`</span><span class="sxs-lookup"><span data-stu-id="cf4cd-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="cf4cd-111">**abandon**</span><span class="sxs-lookup"><span data-stu-id="cf4cd-111">**abandon**</span></span>  
     <span data-ttu-id="cf4cd-112">Přeruší instanci v paměti, aniž by se dotkla trvalého stavu instance (tj. návrat k poslednímu bodu trvalého uložení).</span><span class="sxs-lookup"><span data-stu-id="cf4cd-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="cf4cd-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="cf4cd-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="cf4cd-114">Přeruší instanci v paměti a aktualizuje trvale pozastavenou instanci.</span><span class="sxs-lookup"><span data-stu-id="cf4cd-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="cf4cd-115">**operaci**</span><span class="sxs-lookup"><span data-stu-id="cf4cd-115">**cancel**</span></span>  
     <span data-ttu-id="cf4cd-116">Volá obslužné rutiny zrušení pro instanci a pak dokončí instanci v paměti, což může také odebrat z úložiště instance.</span><span class="sxs-lookup"><span data-stu-id="cf4cd-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="cf4cd-117">**ruší**</span><span class="sxs-lookup"><span data-stu-id="cf4cd-117">**terminate**</span></span>  
     <span data-ttu-id="cf4cd-118">Dokončí instanci v paměti a odebere ji z úložiště instance.</span><span class="sxs-lookup"><span data-stu-id="cf4cd-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     <span data-ttu-id="cf4cd-119">Další informace o <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>najdete v tématu [rozšiřitelnost hostitele služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="cf4cd-119">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf4cd-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf4cd-120">See also</span></span>

- [<span data-ttu-id="cf4cd-121">Rozšiřitelnost hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="cf4cd-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="cf4cd-122">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="cf4cd-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
