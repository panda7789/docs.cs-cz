---
title: 'Postupy: Konfigurace sledování pomocí WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 962dfda9fc5780cc3ac7211464bb3a9be8b7fa90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185061"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="8bf06-102">Postupy: Konfigurace sledování pomocí WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="8bf06-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="8bf06-103">Toto téma vysvětluje, jak [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] nakonfigurovat sledování <xref:System.ServiceModel.Activities.WorkflowServiceHost>pracovního postupu hostovaného v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="8bf06-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="8bf06-104">Je konfigurován prostřednictvím souboru Web.config zadáním chování služby.</span><span class="sxs-lookup"><span data-stu-id="8bf06-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="8bf06-105">Konfigurace sledování v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="8bf06-105">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="8bf06-106">Přidejte <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí `behavior` <> element u konfiguračního souboru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8bf06-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>
       </serviceBehaviors>  
    <behaviors>  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="8bf06-107">Předchozí ukázka konfigurace používá zjednodušenou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="8bf06-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="8bf06-108">Další informace naleznete v [tématu Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="8bf06-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="8bf06-109">Předchozí ukázka <xref:System.Activities.Tracking.EtwTrackingParticipant> konfigurace přidá a určuje název profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="8bf06-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="8bf06-110">Profily sledování jsou `trackingProfile` vytvořeny v elementu <> v rámci prvku <`tracking`>.</span><span class="sxs-lookup"><span data-stu-id="8bf06-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="8bf06-111">Profil sledování obsahuje sledování dotazů, které umožňují účastníkovi sledování přihlásit k odběru událostí pracovního postupu, které jsou vydávány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="8bf06-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="8bf06-112">Následující příklad ukazuje, jak vytvořit profil sledování.</span><span class="sxs-lookup"><span data-stu-id="8bf06-112">The following example shows how to create a tracking profile.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <tracking>
         <trackingProfile name="Sample Tracking Profile">  
            <workflow activityDefinitionId="*">  
               <workflowInstanceQueries>  
                 <workflowInstanceQuery>  
                    <states>  
                       <state name="Started"/>  
                       <state name="Completed"/>  
                    </states>  
                </workflowInstanceQuery>  
             </workflowInstanceQueries>  
           </workflow>  
         </trackingProfile>
       </tracking>  
    </system.serviceModel>  
    ```  
  
     <span data-ttu-id="8bf06-113">Další informace o sledování profilů naleznete v [tématu Sledování profilů](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8bf06-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="8bf06-114">Další informace o sledování obecně naleznete v [tématu Sledování a trasování pracovního postupu](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="8bf06-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="8bf06-115">Konfigurace sledování v kódu</span><span class="sxs-lookup"><span data-stu-id="8bf06-115">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="8bf06-116">Přidejte <xref:System.Activities.Tracking.EtwTrackingParticipant> použití <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> chování v kódu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8bf06-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="8bf06-117">Předchozí ukázka kódu <xref:System.Activities.Tracking.EtwTrackingParticipant> přidá a určuje název profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="8bf06-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="8bf06-118">Profily sledování jsou `trackingProfile` vytvořeny v <`tracking`> prvku v rámci prvku <>, jak je znázorněno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="8bf06-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="8bf06-119">Další informace o sledování profilů naleznete v [tématu Sledování profilů](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8bf06-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="8bf06-120">Další informace o sledování obecně naleznete v [tématu Sledování a trasování pracovního postupu](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="8bf06-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="8bf06-121">Příklad programové konfigurace sledování naleznete v [tématu Konfigurace sledování pracovního postupu](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8bf06-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf06-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bf06-122">See also</span></span>

- [<span data-ttu-id="8bf06-123">Zjednodušená konfigurace pro služby WCF</span><span class="sxs-lookup"><span data-stu-id="8bf06-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="8bf06-124">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="8bf06-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="8bf06-125">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="8bf06-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
