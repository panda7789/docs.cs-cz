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
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Postupy: Konfigurace sledování pomocí WorkflowServiceHost
Toto téma vysvětluje, jak nakonfigurovat sledování pro pracovní postup, který je [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] hostovaný v <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Je nakonfigurována pomocí souboru Web. config zadáním chování služby.  
  
### <a name="configure-tracking-in-configuration"></a>Konfigurace sledování v konfiguraci  
  
1. Přidejte <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí `behavior` elementu <> v konfiguračním souboru, jak je znázorněno v následujícím příkladu.  
  
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
    > Předchozí konfigurační ukázka používá zjednodušenou konfiguraci. Další informace najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md).  
  
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
  
     Další informace o sledování profilů najdete v tématu [sledování profilů](../../windows-workflow-foundation/tracking-profiles.md).  
  
     Další informace o obecném sledování najdete v tématu [sledování a trasování pracovních postupů](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Konfigurace sledování v kódu  
  
1. Přidejte <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> chování v kódu, jak je znázorněno v následujícím příkladu.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     Předchozí ukázka kódu přidá <xref:System.Activities.Tracking.EtwTrackingParticipant> a určí název sledovacího profilu. Sledování profilů se vytváří v <`trackingProfile`> elementu v prvku <`tracking`>, jak je znázorněno v předchozí části.  
  
     Další informace o sledování profilů najdete v tématu [sledování profilů](../../windows-workflow-foundation/tracking-profiles.md).  
  
     Další informace o obecném sledování najdete v tématu [sledování a trasování pracovních postupů](../../windows-workflow-foundation/workflow-tracking-and-tracing.md). Příklad konfigurace sledování programově najdete v tématu [Konfigurace sledování pracovního postupu](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Viz také

- [Zjednodušená konfigurace pro služby WCF](../samples/simplified-configuration-for-wcf-services.md)
- [Služby pracovních postupů](workflow-services.md)
- [Sledování profilů](../../windows-workflow-foundation/tracking-profiles.md)
