---
title: 'Postupy: konfigurace sledování pomocí hostitele služby pracovního postupu'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 56b9f95019995cdb55ec36769ff179ce1125c4b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490731"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="1d5b5-102">Postupy: konfigurace sledování pomocí hostitele služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1d5b5-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="1d5b5-103">Toto téma vysvětluje postup konfigurace sledování pro [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] pracovního postupu hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="1d5b5-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="1d5b5-104">Pomocí souboru Web.config je nakonfigurován tak, že zadáte chování služby.</span><span class="sxs-lookup"><span data-stu-id="1d5b5-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="1d5b5-105">Konfigurace sledování v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="1d5b5-105">Configure Tracking in Configuration</span></span>  
  
1.  <span data-ttu-id="1d5b5-106">Přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <`behavior`> element v konfiguračním souboru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1d5b5-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
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
    >  <span data-ttu-id="1d5b5-107">V předchozím příkladu konfigurace používá zjednodušená konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1d5b5-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="1d5b5-108">Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="1d5b5-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="1d5b5-109">V předchozím příkladu konfigurace přidá <xref:System.Activities.Tracking.EtwTrackingParticipant> a určuje sledování název profilu.</span><span class="sxs-lookup"><span data-stu-id="1d5b5-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="1d5b5-110">Sledování profily jsou vytvořené v <`trackingProfile`> v rámci <`tracking`> elementu.</span><span class="sxs-lookup"><span data-stu-id="1d5b5-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="1d5b5-111">Sledování profil obsahuje dotazy pro sledování, které umožňují sledování účastník přihlásit k odběru událostí pracovního postupu, které jsou vygenerované při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="1d5b5-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="1d5b5-112">Následující příklad ukazuje, jak můžete vytvořit profil sledování.</span><span class="sxs-lookup"><span data-stu-id="1d5b5-112">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     <span data-ttu-id="1d5b5-113">Další informace o sledování profilů najdete v tématu [sledování profily](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1d5b5-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="1d5b5-114">Další informace o sledování obecně najdete v tématu [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="1d5b5-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="1d5b5-115">Konfigurace sledování v kódu</span><span class="sxs-lookup"><span data-stu-id="1d5b5-115">Configure Tracking in Code</span></span>  
  
1.  <span data-ttu-id="1d5b5-116">Přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> chování v kódu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1d5b5-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="1d5b5-117">Přidá v předchozím příkladu kódu <xref:System.Activities.Tracking.EtwTrackingParticipant> a určuje sledování název profilu.</span><span class="sxs-lookup"><span data-stu-id="1d5b5-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="1d5b5-118">Sledování profily jsou vytvořené v <`trackingProfile`> v rámci <`tracking`> elementu, jak je uvedeno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="1d5b5-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="1d5b5-119">Další informace o sledování profilů najdete v tématu [sledování profily](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1d5b5-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="1d5b5-120">Další informace o sledování obecně najdete v tématu [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="1d5b5-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="1d5b5-121">Příklad konfigurace sledování prostřednictvím kódu programu naleznete v části [konfigurace sledování pro pracovní postup](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="1d5b5-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d5b5-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d5b5-122">See Also</span></span>  
 [<span data-ttu-id="1d5b5-123">Zjednodušená konfigurace pro služby WCF</span><span class="sxs-lookup"><span data-stu-id="1d5b5-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)  
 [<span data-ttu-id="1d5b5-124">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="1d5b5-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="1d5b5-125">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="1d5b5-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
