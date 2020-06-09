---
title: Rozšíření hostitele služby pracovního postupu
ms.date: 03/30/2017
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
ms.openlocfilehash: 4c2edec8c23e27f019b95223c998c72069384c75
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594891"
---
# <a name="workflow-service-host-extensibility"></a>Rozšíření hostitele služby pracovního postupu
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]poskytuje <xref:System.ServiceModel.Activities.WorkflowServiceHost> třídu pro hostování služeb pracovního postupu. Tato třída se používá při samoobslužném hostování služby pracovního postupu ve spravované aplikaci nebo službě systému Windows. Tato třída se používá také při hostování služby pracovního postupu pomocí služby Internetová informační služba (IIS) nebo aktivační služby procesů systému Windows (WAS). <xref:System.ServiceModel.Activities.WorkflowServiceHost>Třída poskytuje Rozšiřovací body, které umožňují přidat vlastní rozšíření, změnit chování při nečinnosti a hostovat pracovní postupy bez služby (pracovní postupy, které nepoužívají aktivity zasílání zpráv).  
  
## <a name="workflow-service-host-extensions"></a>Rozšíření hostitele služby pracovního postupu  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>Obsahuje <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> vlastnost typu <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager> , která poskytuje metody pro přidání rozšíření do <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Použijte <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metodu k přidání rozšíření pro každou instanci služby pracovního postupu. Pokud je instance služby pracovního postupu vytvořena nebo načtena z úložiště trvalosti, je zadaný delegát zavolán k vytvoření nového rozšíření. Pomocí <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metody můžete přidat rozšíření pro každého hostitele služby pracovního postupu, jedna instance rozšíření se sdílí pro všechny instance služby pracovního postupu.  
  
## <a name="react-to-unhandled-exceptions"></a>Reagovat na neošetřené výjimky  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>Umožňuje zadat akci, která se má provést, pokud dojde k neošetřené výjimce v rámci služby pracovního postupu. <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A>Vlastnost určuje jednu z <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> hodnot:  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Abandon>– Přeruší instanci služby pracovního postupu.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.AbandonAndSuspend>– Vrátí se zpátky do posledního trvalého stavu a pozastaví instanci služby pracovního postupu. K tomu dochází pouze v případě, že pracovní postup byl již nejméně jednou uložen. V případě, že instance pracovního postupu není přerušena.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>– Zruší instanci.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Terminate>– Ukončí instanci.  
  
 Toto chování lze nakonfigurovat v kódu, jak je znázorněno v následujícím příkladu.  
  
```csharp  
host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.Abandon });  
```  
  
 Dá se taky nakonfigurovat v konfiguračním souboru, jak je znázorněno v následujícím příkladu.  
  
```xml
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <workflowUnhandledExceptionBehavior action="Abandon" />
        </behavior>  
      </serviceBehaviors>  
</behaviors>
```  
  
## <a name="hosting-non-service-workflows"></a>Hostování pracovních postupů bez služby  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>dá se použít k hostování pracovních postupů bez služby nebo pracovních postupů, které buď nezačínají <xref:System.ServiceModel.Activities.Receive> aktivitou, nebo pracovními postupy, které nepoužívají aktivity zasílání zpráv. Služby pracovního postupu obvykle začínají <xref:System.ServiceModel.Activities.Receive> aktivitou. Když <xref:System.ServiceModel.Activities.WorkflowServiceHost> obdrží zprávu pro službu pracovního postupu, pokud ještě není spuštěná (nebo je trvalá), vytvoří se nová instance služby pracovního postupu. Pokud pracovní postup nezačíná aktivitou Receive, nelze ho spustit odesláním zprávy, protože neexistují žádné aktivity k přijetí zprávy. Chcete-li hostovat pracovní postup bez služby, odvodit třídu z <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> a přepsat <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> , <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> a <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> . Přepsat <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> , pokud chcete zadat ID upřednostňované instance. Přepsáním <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> můžete vytvořit vlastní kontext vytváření pracovního postupu nebo naplnit instanci existující <xref:System.ServiceModel.Activities.WorkflowCreationContext> . Přepsat <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> pro ruční extrakci záložky z příchozí zprávy. Pokud přepíšete tuto metodu, musíte vyvolat <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> v jejím těle, aby bylo možné reagovat na zprávu odeslanou do WorkflowHostingEndpoint. Pokud to neuděláte, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> může být nakonec překročen limit. V rámci oboustranných kontraktů může být možné rozpoznat selhání při vyvolání <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> z důvodu neúspěšného přijetí odpovědi klienta. V rámci jednosměrných smluv možná nebudete schopni volat chybu <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> , dokud není příliš pozdě, po <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> překročení limitu omezení. Další informace najdete na [záložce WorkflowHostingEndpoint Resume](../../windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)pro vytvoření nové instance pracovního postupu bez služby, Declare kontraktu služby definující operaci, která vytvoří novou instanci. Operace vytvoření by měla přebírat rozhraní IDictionary \<string, object> k předání požadovaných parametrů pracovního postupu. Tato smlouva je implicitně implementovaná <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> třídou odvozenou od třídy. Při hostování pracovního postupu přidejte instanci <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> odvozené třídy do hostitele voláním <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A> a voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> . Pokud chcete vytvořit instanci pracovního postupu, vytvořte <xref:System.ServiceModel.ChannelFactory%601> Typ kontraktu služby a zavolejte <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> . Pak můžete zavolat operaci vytvoření definovanou v kontraktu služby.  
  
## <a name="see-also"></a>Viz také

- [Služby pracovních postupů](workflow-services.md)
- [Aktivity zasílání zpráv](messaging-activities.md)
