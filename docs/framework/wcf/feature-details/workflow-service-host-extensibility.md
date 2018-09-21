---
title: Rozšíření hostitele služby pracovního postupu
ms.date: 03/30/2017
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
ms.openlocfilehash: 6541558601c8f5daf255f2e7e5d774e41b59be2d
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46518464"
---
# <a name="workflow-service-host-extensibility"></a>Rozšíření hostitele služby pracovního postupu
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] poskytuje <xref:System.ServiceModel.Activities.WorkflowServiceHost> třídy pro hostování služeb pracovních postupů. Tato třída se používá, když jsou samoobslužné hostování služby pracovního postupu ve spravované aplikaci nebo službu Windows. Tato třída se používá také při hostování služby pracovního procesu pomocí Internetové informační služby (IIS) nebo Windows Process Activation Service (WAS). <xref:System.ServiceModel.Activities.WorkflowServiceHost> Třída poskytuje Rozšiřovací body, které umožňují přidat vlastní rozšíření, změnit chování při nečinnosti a hostitelem bez služby pracovních postupů (pracovní postupy, které nepoužívají zasílání zpráv aktivity).  
  
## <a name="workflow-service-host-extensions"></a>Rozšíření hostitele služby pracovního postupu  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> Obsahuje <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> vlastnost typu <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager> , který poskytuje metody pro přidání rozšíření <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Použití <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metody přidání rozšíření pro každou repliku služby pracovního postupu. Delegát zadané je volána k vytvoření nové rozšíření, když je vytvořen nebo načten z úložiště stálost instance služby pracovního postupu. Použití <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metody přidání rozšíření pro každého hostitele služby pracovního postupu pro všechny instance služby pracovního postupu se sdílí jednu instanci rozšíření.  
  
## <a name="react-to-unhandled-exceptions"></a>Reakce na neošetřených výjimek  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Umožňuje zadat akce má být provedena, pokud dojde k neošetřené výjimce v rámci služby pracovních postupů. <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A> Vlastnost určuje jeden z <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> hodnoty:  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Abandon> – Přeruší instance služby pracovního postupu.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.AbandonAndSuspend> – Vrátí zpět do posledního trvalého stavu a pozastaví instanci služby pracovního postupu. K tomu dochází pouze pokud pracovní postup již byla trvale uložena alespoň jednou. Pokud není instance pracovního postupu byl přerušen.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel> – Instance zruší.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Terminate> – Instance se ukončí.  
  
 Toto chování lze nastavit v kódu, jak je znázorněno v následujícím příkladu.  
  
```csharp  
host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.Abandon });  
```  
  
 To lze také nastavit v konfiguračním souboru, jak je znázorněno v následujícím příkladu.  
  
```xml
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <workflowUnhandledExceptionBehavior action="Abandon" />        
        </behavior>  
      </serviceBehaviors>  
```  
  
## <a name="hosting-non-service-workflows"></a>Hostování pracovních postupů bez služby  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> je možné k hostování pracovní postupy bez služby nebo pracovní postupy, které buď nezačínají <xref:System.ServiceModel.Activities.Receive> aktivity nebo pracovních postupů, které nepoužívají zasílání zpráv aktivity. Služby pracovních postupů obvykle začínají <xref:System.ServiceModel.Activities.Receive> aktivity. Když <xref:System.ServiceModel.Activities.WorkflowServiceHost> přijme zprávu služby pracovního postupu, pokud dosud není spuštěn (nebo trvalé) nové instance služby pracovního postupu je vytvořena. Pokud pracovní postup nezačíná aktivitu Receive, nelze spustit odesláním zprávy, protože neexistuje žádná aktivita zpráva. K hostování pracovního postupu bez služby, odvoďte třídu z <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> a přepsat <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A>, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A>, a <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A>. Přepsat <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> Pokud byste chtěli poskytnout ID upřednostňované instance. Přepsat <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> k vytvoření vlastní pracovní postup vytvoření kontextu nebo naplnit instanci existující <xref:System.ServiceModel.Activities.WorkflowCreationContext>. Přepsat <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> ručně extrahovat záložky z příchozí zprávy. Pokud tuto metodu přepíšete, je nutné vyvolat <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> v těle tak, aby reagovat na zprávy odeslané WorkflowHostingEndpoint. Je-li to provést <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> může nakonec překročen limit. V kontraktech obousměrný, může být schopna zjistit vaše selhání, který má být vyvolán <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> z důvodu selhání klienta trvá příjem odpovědi. V jednosměrné kontrakty, nemusí rozpoznat chybu o selhání volání <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> až bude příliš pozdě po <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> překročil limit omezení. Další informace najdete v tématu [záložku obnovení WorkflowHostingEndpoint](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)Chcete-li vytvořit novou instanci pracovního postupu bez služby, deklarujte kontraktu služby, který definuje operace, která vytvoří novou instanci. Operace vytvoření zabere IDictionary\<řetězec, objekt > předat všechny požadované parametry pracovního postupu. Tato smlouva je implicitně implementované <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>-odvozené třídy. Při hostování pracovního postupu, přidat instanci <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>-odvozené třídy pro hostitele voláním <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A> a volat <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Chcete-li vytvořit instanci pracovního postupu, vytvořte <xref:System.ServiceModel.ChannelFactory%601> typ kontraktu služby a volání <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>. Potom můžete zavolat operaci vytvoření definované v servisní smlouvě.  
  
## <a name="see-also"></a>Viz také  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Aktivity zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
