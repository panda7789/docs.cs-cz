---
title: 'Postupy: Konfigurace sledování pomocí třídy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 5781878270272f5ef894c68dc23b9433029e1d41
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968496"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="2d24b-102">Postupy: Konfigurace sledování pomocí třídy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="2d24b-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="2d24b-103">Toto téma vysvětluje, jak nakonfigurovat sledování pro pracovní [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] postup, který <xref:System.ServiceModel.Activities.WorkflowServiceHost>je hostovaný v.</span><span class="sxs-lookup"><span data-stu-id="2d24b-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="2d24b-104">Je nakonfigurována pomocí souboru Web. config zadáním chování služby.</span><span class="sxs-lookup"><span data-stu-id="2d24b-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="2d24b-105">Konfigurace sledování v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="2d24b-105">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="2d24b-106">Přidejte pomocí elementu <`behavior`> v konfiguračním souboru, jak je znázorněno v následujícím příkladu. <xref:System.Activities.Tracking.EtwTrackingParticipant></span><span class="sxs-lookup"><span data-stu-id="2d24b-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
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
    > <span data-ttu-id="2d24b-107">Předchozí konfigurační ukázka používá zjednodušenou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="2d24b-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="2d24b-108">Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="2d24b-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="2d24b-109">Předchozí konfigurační ukázka přidá <xref:System.Activities.Tracking.EtwTrackingParticipant> a určí název sledovacího profilu.</span><span class="sxs-lookup"><span data-stu-id="2d24b-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="2d24b-110">Sledování profilů se vytváří v <`trackingProfile`> elementu v rámci elementu <`tracking`>.</span><span class="sxs-lookup"><span data-stu-id="2d24b-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="2d24b-111">Profil sledování obsahuje sledovací dotazy, které umožňují sledování účastníka přihlásit k odběru událostí pracovního postupu, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="2d24b-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="2d24b-112">Následující příklad ukazuje, jak vytvořit profil sledování.</span><span class="sxs-lookup"><span data-stu-id="2d24b-112">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     <span data-ttu-id="2d24b-113">Další informace o sledování profilů najdete v tématu [sledování profilů](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="2d24b-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="2d24b-114">Další informace o obecném sledování najdete v tématu [sledování a trasování pracovních postupů](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="2d24b-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="2d24b-115">Konfigurace sledování v kódu</span><span class="sxs-lookup"><span data-stu-id="2d24b-115">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="2d24b-116"><xref:System.Activities.Tracking.EtwTrackingParticipant> Přidejte<xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> pomocí chování v kódu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2d24b-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="2d24b-117">Předchozí ukázka kódu přidá <xref:System.Activities.Tracking.EtwTrackingParticipant> a určí název sledovacího profilu.</span><span class="sxs-lookup"><span data-stu-id="2d24b-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="2d24b-118">Sledování profilů se vytváří v <`trackingProfile`> elementu v prvku <`tracking`>, jak je znázorněno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="2d24b-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="2d24b-119">Další informace o sledování profilů najdete v tématu [sledování profilů](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="2d24b-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="2d24b-120">Další informace o obecném sledování najdete v tématu [sledování a trasování pracovních postupů](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="2d24b-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="2d24b-121">Příklad konfigurace sledování programově najdete v tématu [Konfigurace sledování pracovního postupu](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="2d24b-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d24b-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d24b-122">See also</span></span>

- [<span data-ttu-id="2d24b-123">Zjednodušená konfigurace pro služby WCF</span><span class="sxs-lookup"><span data-stu-id="2d24b-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="2d24b-124">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="2d24b-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="2d24b-125">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="2d24b-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
