---
title: "Rozšíření hostitele služby pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: caff90b66007310c7b3ad24f2f084cc2282a7021
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-service-host-extensibility"></a>Rozšíření hostitele služby pracovního postupu
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]poskytuje <xref:System.ServiceModel.Activities.WorkflowServiceHost> třídu pro hostování služeb pracovních postupů. Tato třída se používá, když jsou vlastní hostování služby pracovního postupu ve spravované aplikaci nebo službu systému Windows. Tato třída se používá také při hostování služby pracovního postupu pomocí Internetové informační služby (IIS) nebo služby Aktivace procesů systému Windows (WAS). <xref:System.ServiceModel.Activities.WorkflowServiceHost> Třída poskytuje rozšíření body, které vám umožní přidat vlastní rozšíření, změňte chování při nečinnosti a hostitele bez služby pracovních postupů (pracovní postupy, které nepoužívají zasílání zpráv aktivity).  
  
## <a name="workflow-service-host-extensions"></a>Rozšíření hostitele služby pracovního postupu  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost> Obsahuje <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> vlastnost typu <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager> , který poskytuje metody pro přidání rozšíření pro <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Použití <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metoda pro přidání rozšíření pro každou instanci služby pracovního postupu. Delegát zadaný je volána k vytvoření nové rozšíření, když je vytvořen nebo načten z úložiště trvalosti instance služby pracovního postupu. Použití <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metoda pro přidání rozšíření pro každého hostitele služby pracovního postupu, jednu instanci rozšíření je sdílena pro všechny instance služby pracovního postupu.  
  
## <a name="react-to-unhandled-exceptions"></a>Reagování na neošetřených výjimek  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Umožňuje určit akci v případě, že dojde k neošetřené výjimce v rámci služby pracovních postupů. <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A> Vlastnost určuje jeden z <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> hodnoty:  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Abandon>– Zruší instance služby pracovního postupu.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.AbandonAndSuspend>– Vrátí zpátky na posledního trvalého stavu a pozastaví instance služby pracovního postupu. Pouze k tomu dojde, pokud již byla obsahuje pracovní postup trvalé alespoň jednou. Pokud není k instanci pracovního postupu byla přerušena.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>– Zruší instance.  
  
-   <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Terminate>– Ukončí instance.  
  
 Toto chování lze konfigurovat v kódu, jak je znázorněno v následujícím příkladu.  
  
```csharp  
host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.Abandon });  
```  
  
 Můžete také nastavit v konfiguračním souboru, jak je znázorněno v následujícím příkladu.  
  
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
  
## <a name="hosting-non-service-workflows"></a>Hostování bez služby pracovních postupů  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>lze použít k hostování pracovních postupů bez služby a pracovní postupy, které buď nemají na začátku <xref:System.ServiceModel.Activities.Receive> aktivity nebo pracovní postupy, které nepoužívají aktivity zasílání zpráv. Za normálních okolností začínat služeb pracovních postupů <xref:System.ServiceModel.Activities.Receive> aktivity. Když <xref:System.ServiceModel.Activities.WorkflowServiceHost> přijme zprávu o služby pracovního postupu, pokud ještě není spuštěná (nebo trvalé) novou instanci služby pracovního postupu je vytvořen. Pokud pracovní postup nezačíná aktivitu Receive, nelze spustit odesláním zprávy, protože nebude žádná aktivita zpráva. K hostování bez služby pracovního postupu, odvození třídy z <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> a přepsání <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A>, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A>, a <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A>. Přepsání <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> Pokud byste chtěli poskytnout ID upřednostňované instance. Přepsání <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> vytvořit vlastní pracovní postup vytvoření kontextu nebo naplnit instanci existující <xref:System.ServiceModel.Activities.WorkflowCreationContext>. Přepsání <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> ručně extrahovat Záložka z příchozí zprávy. Pokud tuto metodu přepíšete, je nutné vyvolat <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> v jeho obsahu tak, aby reagovat na zprávu odeslat WorkflowHostingEndpoint. Pokud neprovedete, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> může nakonec překročen limit. V kontraktech obousměrný, může být schopna zjistit váš neúspěch při vyvolání <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> z důvodu selhání klienta obdrží odpověď. V jednosměrné kontrakty, nemusí rozpoznat chybu systému selhání volání <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> dokud nebude příliš pozdní po <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> byl překročen limit omezení. Další informace najdete v tématu [WorkflowHostingEndpoint obnovit záložku](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)Pokud chcete vytvořit novou instanci pracovního postupu bez služby, deklarovat kontraktu služby, který definuje operace, která vytvoří novou instanci. Operace vytváření zabere IDictionary\<řetězec, objekt > předat všechny požadované parametry pracovního postupu. Tato smlouva je implicitně implementované <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>-odvozené třídy. Při hostování pracovního postupu, přidá instanci <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>-odvozené třídy k hostiteli voláním <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A> a volání <!--zz xref:System.ServiceModel.Activities.WorkflowServiceHost.Open%2A--> `System.ServiceModel.Activities.WorkflowServiceHost.Open`. K vytvoření instance pracovního postupu, vytvoření <xref:System.ServiceModel.ChannelFactory%601> typu kontraktu služby a volání <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>. Potom můžete volat operace vytvoření definované v vaší kontrakt služby.  
  
## <a name="see-also"></a>Viz také  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Aktivity zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
