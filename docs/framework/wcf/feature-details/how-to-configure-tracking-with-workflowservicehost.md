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
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Postupy: Konfigurace sledování pomocí třídy WorkflowServiceHost
Toto téma vysvětluje, jak nakonfigurovat sledování pro pracovní [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] postup, který <xref:System.ServiceModel.Activities.WorkflowServiceHost>je hostovaný v. Je nakonfigurována pomocí souboru Web. config zadáním chování služby.  
  
### <a name="configure-tracking-in-configuration"></a>Konfigurace sledování v konfiguraci  
  
1. Přidejte pomocí elementu <`behavior`> v konfiguračním souboru, jak je znázorněno v následujícím příkladu. <xref:System.Activities.Tracking.EtwTrackingParticipant>  
  
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
    > Předchozí konfigurační ukázka používá zjednodušenou konfiguraci. Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Předchozí konfigurační ukázka přidá <xref:System.Activities.Tracking.EtwTrackingParticipant> a určí název sledovacího profilu. Sledování profilů se vytváří v <`trackingProfile`> elementu v rámci elementu <`tracking`>. Profil sledování obsahuje sledovací dotazy, které umožňují sledování účastníka přihlásit k odběru událostí pracovního postupu, které jsou emitovány při změně stavu instance pracovního postupu za běhu. Následující příklad ukazuje, jak vytvořit profil sledování.  
  
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
  
     Další informace o sledování profilů najdete v tématu [sledování profilů](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Další informace o obecném sledování najdete v tématu [sledování a trasování pracovních postupů](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Konfigurace sledování v kódu  
  
1. <xref:System.Activities.Tracking.EtwTrackingParticipant> Přidejte<xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> pomocí chování v kódu, jak je znázorněno v následujícím příkladu.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     Předchozí ukázka kódu přidá <xref:System.Activities.Tracking.EtwTrackingParticipant> a určí název sledovacího profilu. Sledování profilů se vytváří v <`trackingProfile`> elementu v prvku <`tracking`>, jak je znázorněno v předchozí části.  
  
     Další informace o sledování profilů najdete v tématu [sledování profilů](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Další informace o obecném sledování najdete v tématu [sledování a trasování pracovních postupů](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Příklad konfigurace sledování programově najdete v tématu [Konfigurace sledování pracovního postupu](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Viz také:

- [Zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Sledování profilů](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
