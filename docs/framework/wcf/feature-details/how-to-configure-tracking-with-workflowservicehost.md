---
title: 'Postupy: Konfigurace sledování pomocí WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 3f78b77849d6da7dfff3bdcba90bb4d5200186a7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464159"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Postupy: Konfigurace sledování pomocí WorkflowServiceHost
Toto téma vysvětluje, jak [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] nakonfigurovat sledování <xref:System.ServiceModel.Activities.WorkflowServiceHost>pracovního postupu hostovaného v aplikaci . Je konfigurován prostřednictvím souboru Web.config zadáním chování služby.  
  
### <a name="configure-tracking-in-configuration"></a>Konfigurace sledování v konfiguraci  
  
1. Přidejte <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí `behavior` <> element u konfiguračního souboru, jak je znázorněno v následujícím příkladu.  
  
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
    > Předchozí ukázka konfigurace používá zjednodušenou konfiguraci. Další informace naleznete v [tématu Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Předchozí ukázka <xref:System.Activities.Tracking.EtwTrackingParticipant> konfigurace přidá a určuje název profilu sledování. Profily sledování jsou `trackingProfile` vytvořeny v elementu <> v rámci prvku <`tracking`>. Profil sledování obsahuje sledování dotazů, které umožňují účastníkovi sledování přihlásit k odběru událostí pracovního postupu, které jsou vydávány při změně stavu instance pracovního postupu za běhu. Následující příklad ukazuje, jak vytvořit profil sledování.  
  
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
  
     Další informace o sledování profilů naleznete v [tématu Sledování profilů](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Další informace o sledování obecně naleznete v [tématu Sledování a trasování pracovního postupu](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Konfigurace sledování v kódu  
  
1. Přidejte <xref:System.Activities.Tracking.EtwTrackingParticipant> použití <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> chování v kódu, jak je znázorněno v následujícím příkladu.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     Předchozí ukázka kódu <xref:System.Activities.Tracking.EtwTrackingParticipant> přidá a určuje název profilu sledování. Profily sledování jsou `trackingProfile` vytvořeny v <`tracking`> prvku v rámci prvku <>, jak je znázorněno v předchozí části.  
  
     Další informace o sledování profilů naleznete v [tématu Sledování profilů](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Další informace o sledování obecně naleznete v [tématu Sledování a trasování pracovního postupu](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Příklad programové konfigurace sledování naleznete v [tématu Konfigurace sledování pracovního postupu](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Viz také

- [Zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Sledování profilů](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
