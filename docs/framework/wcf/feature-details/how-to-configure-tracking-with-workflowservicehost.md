---
title: 'Postupy: Konfigurace sledování pomocí třídy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: e0631cdb47bc88f7f588f4dfe6c44ea3d44f4e60
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336561"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="af53b-102">Postupy: Konfigurace sledování pomocí třídy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="af53b-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="af53b-103">Toto téma vysvětluje postup konfigurace sledování [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] pracovního postupu hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="af53b-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="af53b-104">Prostřednictvím souboru Web.config je nakonfigurován tak, že zadáte chování služby.</span><span class="sxs-lookup"><span data-stu-id="af53b-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="af53b-105">Konfigurace sledování v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="af53b-105">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="af53b-106">Přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <`behavior`> element v konfiguračním souboru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="af53b-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
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
    >  <span data-ttu-id="af53b-107">Zjednodušená konfigurace používá předchozí ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="af53b-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="af53b-108">Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="af53b-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="af53b-109">Přidá předchozí ukázka konfigurace <xref:System.Activities.Tracking.EtwTrackingParticipant> a sleduje Určuje název profilu.</span><span class="sxs-lookup"><span data-stu-id="af53b-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="af53b-110">Sledování profily jsou vytvořené v <`trackingProfile`> v elementu <`tracking`> element.</span><span class="sxs-lookup"><span data-stu-id="af53b-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="af53b-111">Profil sledování obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="af53b-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="af53b-112">Následující příklad ukazuje postup vytvoření profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="af53b-112">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     <span data-ttu-id="af53b-113">Další informace o sledování profilů najdete v tématu [sledování profilů](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="af53b-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="af53b-114">Další informace o sledování obecně naleznete v tématu [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="af53b-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="af53b-115">Konfigurace sledování v kódu</span><span class="sxs-lookup"><span data-stu-id="af53b-115">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="af53b-116">Přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> chování v kódu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="af53b-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="af53b-117">Předchozí příklad kódu přidá <xref:System.Activities.Tracking.EtwTrackingParticipant> a sleduje Určuje název profilu.</span><span class="sxs-lookup"><span data-stu-id="af53b-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="af53b-118">Sledování profily jsou vytvořené v <`trackingProfile`> v elementu <`tracking`> element, jak je znázorněno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="af53b-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="af53b-119">Další informace o sledování profilů najdete v tématu [sledování profilů](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="af53b-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="af53b-120">Další informace o sledování obecně naleznete v tématu [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="af53b-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="af53b-121">Příklad konfigurace sledování prostřednictvím kódu programu najdete v části [konfigurace sledování pracovního postupu](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="af53b-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af53b-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af53b-122">See also</span></span>

- [<span data-ttu-id="af53b-123">Zjednodušená konfigurace pro služby WCF</span><span class="sxs-lookup"><span data-stu-id="af53b-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="af53b-124">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="af53b-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="af53b-125">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="af53b-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
