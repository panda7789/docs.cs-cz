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
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Postupy: Konfigurace sledování pomocí třídy WorkflowServiceHost
Toto téma vysvětluje postup konfigurace sledování [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] pracovního postupu hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Prostřednictvím souboru Web.config je nakonfigurován tak, že zadáte chování služby.  
  
### <a name="configure-tracking-in-configuration"></a>Konfigurace sledování v konfiguraci  
  
1. Přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <`behavior`> element v konfiguračním souboru, jak je znázorněno v následujícím příkladu.  
  
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
    >  Zjednodušená konfigurace používá předchozí ukázka konfigurace. Další informace najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Přidá předchozí ukázka konfigurace <xref:System.Activities.Tracking.EtwTrackingParticipant> a sleduje Určuje název profilu. Sledování profily jsou vytvořené v <`trackingProfile`> v elementu <`tracking`> element. Profil sledování obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu. Následující příklad ukazuje postup vytvoření profilu sledování.  
  
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
  
     Další informace o sledování obecně naleznete v tématu [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Konfigurace sledování v kódu  
  
1. Přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> chování v kódu, jak je znázorněno v následujícím příkladu.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     Předchozí příklad kódu přidá <xref:System.Activities.Tracking.EtwTrackingParticipant> a sleduje Určuje název profilu. Sledování profily jsou vytvořené v <`trackingProfile`> v elementu <`tracking`> element, jak je znázorněno v předchozí části.  
  
     Další informace o sledování profilů najdete v tématu [sledování profilů](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Další informace o sledování obecně naleznete v tématu [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Příklad konfigurace sledování prostřednictvím kódu programu najdete v části [konfigurace sledování pracovního postupu](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Viz také:

- [Zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Sledování profilů](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
