---
title: 'Postupy: Konfigurace sledování pomocí WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 54594a8f464e77062c658606db6bc941e319f71d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599097"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="def63-102">Postupy: Konfigurace sledování pomocí WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="def63-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="def63-103">Toto téma vysvětluje, jak nakonfigurovat sledování pro pracovní postup, který je [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] hostovaný v <xref:System.ServiceModel.Activities.WorkflowServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="def63-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="def63-104">Je nakonfigurována pomocí souboru Web. config zadáním chování služby.</span><span class="sxs-lookup"><span data-stu-id="def63-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="def63-105">Konfigurace sledování v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="def63-105">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="def63-106">Přidejte <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí `behavior` elementu <> v konfiguračním souboru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="def63-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="def63-107">Předchozí konfigurační ukázka používá zjednodušenou konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="def63-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="def63-108">Další informace najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="def63-108">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="def63-109">Předchozí konfigurační ukázka přidá <xref:System.Activities.Tracking.EtwTrackingParticipant> a určí název sledovacího profilu.</span><span class="sxs-lookup"><span data-stu-id="def63-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="def63-110">Sledování profilů se vytváří v <`trackingProfile`> elementu v rámci elementu <`tracking`>.</span><span class="sxs-lookup"><span data-stu-id="def63-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="def63-111">Profil sledování obsahuje sledovací dotazy, které umožňují sledování účastníka přihlásit k odběru událostí pracovního postupu, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="def63-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="def63-112">Následující příklad ukazuje, jak vytvořit profil sledování.</span><span class="sxs-lookup"><span data-stu-id="def63-112">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     <span data-ttu-id="def63-113">Další informace o sledování profilů najdete v tématu [sledování profilů](../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="def63-113">For more information about tracking profiles, see [Tracking Profiles](../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="def63-114">Další informace o obecném sledování najdete v tématu [sledování a trasování pracovních postupů](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="def63-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="def63-115">Konfigurace sledování v kódu</span><span class="sxs-lookup"><span data-stu-id="def63-115">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="def63-116">Přidejte <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> chování v kódu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="def63-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="def63-117">Předchozí ukázka kódu přidá <xref:System.Activities.Tracking.EtwTrackingParticipant> a určí název sledovacího profilu.</span><span class="sxs-lookup"><span data-stu-id="def63-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="def63-118">Sledování profilů se vytváří v <`trackingProfile`> elementu v prvku <`tracking`>, jak je znázorněno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="def63-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="def63-119">Další informace o sledování profilů najdete v tématu [sledování profilů](../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="def63-119">For more information about tracking profiles, see [Tracking Profiles](../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="def63-120">Další informace o obecném sledování najdete v tématu [sledování a trasování pracovních postupů](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="def63-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="def63-121">Příklad konfigurace sledování programově najdete v tématu [Konfigurace sledování pracovního postupu](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="def63-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="def63-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="def63-122">See also</span></span>

- [<span data-ttu-id="def63-123">Zjednodušená konfigurace pro služby WCF</span><span class="sxs-lookup"><span data-stu-id="def63-123">Simplified Configuration for WCF Services</span></span>](../samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="def63-124">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="def63-124">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="def63-125">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="def63-125">Tracking Profiles</span></span>](../../windows-workflow-foundation/tracking-profiles.md)
