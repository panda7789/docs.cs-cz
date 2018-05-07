---
title: 'Postupy: konfigurace sledování pomocí hostitele služby pracovního postupu'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 56b9f95019995cdb55ec36769ff179ce1125c4b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Postupy: konfigurace sledování pomocí hostitele služby pracovního postupu
Toto téma vysvětluje postup konfigurace sledování pro [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] pracovního postupu hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Pomocí souboru Web.config je nakonfigurován tak, že zadáte chování služby.  
  
### <a name="configure-tracking-in-configuration"></a>Konfigurace sledování v konfiguraci  
  
1.  Přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <`behavior`> element v konfiguračním souboru, jak je znázorněno v následujícím příkladu.  
  
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
    >  V předchozím příkladu konfigurace používá zjednodušená konfigurace. Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     V předchozím příkladu konfigurace přidá <xref:System.Activities.Tracking.EtwTrackingParticipant> a určuje sledování název profilu. Sledování profily jsou vytvořené v <`trackingProfile`> v rámci <`tracking`> elementu. Sledování profil obsahuje dotazy pro sledování, které umožňují sledování účastník přihlásit k odběru událostí pracovního postupu, které jsou vygenerované při změně stavu instance pracovního postupu za běhu. Následující příklad ukazuje, jak můžete vytvořit profil sledování.  
  
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
  
     Další informace o sledování profilů najdete v tématu [sledování profily](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Další informace o sledování obecně najdete v tématu [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Konfigurace sledování v kódu  
  
1.  Přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> chování v kódu, jak je znázorněno v následujícím příkladu.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     Přidá v předchozím příkladu kódu <xref:System.Activities.Tracking.EtwTrackingParticipant> a určuje sledování název profilu. Sledování profily jsou vytvořené v <`trackingProfile`> v rámci <`tracking`> elementu, jak je uvedeno v předchozí části.  
  
     Další informace o sledování profilů najdete v tématu [sledování profily](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Další informace o sledování obecně najdete v tématu [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Příklad konfigurace sledování prostřednictvím kódu programu naleznete v části [konfigurace sledování pro pracovní postup](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Viz také  
 [Zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Sledování profilů](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
