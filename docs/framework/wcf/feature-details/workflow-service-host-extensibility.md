---
title: Rozšíření hostitele služby pracovního postupu
ms.date: 03/30/2017
ms.assetid: c0e8f7bb-cb13-49ec-852f-b85d7c23972f
ms.openlocfilehash: eb35b9211bc55ee66f5bb5600ef86f40d4145191
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464002"
---
# <a name="workflow-service-host-extensibility"></a>Rozšíření hostitele služby pracovního postupu
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]poskytuje <xref:System.ServiceModel.Activities.WorkflowServiceHost> třídu pro hostování služeb pracovního postupu. Tato třída se používá, když vlastní hostování služby pracovního postupu ve spravované aplikaci nebo služby systému Windows. Tato třída se také používá při hostování služby pracovního postupu s Internetovou informační službou (IIS) nebo službou aktivace procesů systému Windows (WAS). Třída <xref:System.ServiceModel.Activities.WorkflowServiceHost> poskytuje body rozšíření, které umožňují přidávat vlastní rozšíření, změnit chování nečinnosti a hostovat pracovní postupy neslužby (pracovní postupy, které nepoužívají aktivity zasílání zpráv).  
  
## <a name="workflow-service-host-extensions"></a>Rozšíření hostitele služby pracovního postupu  
 Obsahuje <xref:System.ServiceModel.Activities.WorkflowServiceHost> <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> vlastnost typu, <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager> který poskytuje metody pro <xref:System.ServiceModel.Activities.WorkflowServiceHost>přidání rozšíření do . Pomocí <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metody můžete přidat rozšíření pro každou instanci služby pracovního postupu. Zadaný delegát je volán k vytvoření nového rozšíření při vytvoření nebo načtení instance služby pracovního postupu z úložiště trvalosti. Pomocí <xref:System.Activities.Hosting.WorkflowInstanceExtensionManager.Add%2A> metody přidejte rozšíření pro každého hostitele služby pracovního postupu, jedna instance rozšíření je sdílena pro všechny instance služby pracovního postupu.  
  
## <a name="react-to-unhandled-exceptions"></a>Reagovat na neošetřené výjimky  
 Umožňuje <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> zadat akci, která má být v případě, že dojde k neošetřené výjimce v rámci služby pracovního postupu. Vlastnost <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior.Action%2A> určuje jednu <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> z hodnot:  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Abandon>– Přeruší instanci služby pracovního postupu.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.AbandonAndSuspend>– Vrátí se zpět do posledního trvalého stavu a pozastaví instanci služby pracovního postupu. K tomu dochází pouze v případě, že pracovní postup již byl zachován alespoň jednou. Pokud ne instance pracovního postupu je přerušena.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel>– Zruší instanci.  
  
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Terminate>– Ukončí instanci.  
  
 Toto chování lze nakonfigurovat v kódu, jak je znázorněno v následujícím příkladu.  
  
```csharp  
host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.Abandon });  
```  
  
 Lze jej také nakonfigurovat v konfiguračním souboru, jak je znázorněno v následujícím příkladu.  
  
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
  
## <a name="hosting-non-service-workflows"></a>Hostování pracovních postupů, které nejsou službami  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>lze použít k hostování neservisních pracovních postupů nebo pracovních <xref:System.ServiceModel.Activities.Receive> postupů, které nezačínají aktivitou nebo pracovními postupy, které nepoužívají aktivity zasílání zpráv. Služby pracovního <xref:System.ServiceModel.Activities.Receive> postupu obvykle začínají aktivitou. Když <xref:System.ServiceModel.Activities.WorkflowServiceHost> obdrží zprávu pro službu pracovního postupu, pokud není již spuštěna (nebo trvalá) je vytvořena nová instance služby pracovního postupu. Pokud pracovní postup nezačíná příjem aktivity, nelze spustit odesláním zprávy, protože neexistuje žádná aktivita pro příjem zprávy. Chcete-li hostovat pracovní postup bez <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> služby, odvoděte třídu z a přepsat <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A>, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A>a <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A>. Přepište, <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetInstanceId%2A> pokud chcete zadat upřednostňované ID instance. Přepsáním <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnGetCreationContext%2A> vytvoříte vlastní kontext vytvoření pracovního <xref:System.ServiceModel.Activities.WorkflowCreationContext>postupu nebo naplníte instanci existujícího . Přepsáním <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint.OnResolveBookmark%2A> ručně extrahujete záložku z příchozí zprávy. Pokud přepsat tuto metodu, <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> musíte vyvolat v jeho těle tak, aby reagovat na zprávu odeslanou WorkflowHostingEndpoint. Pokud tak neučiníte, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> může být nakonec překročen limit. V obousměrné smlouvy, může být možné zjistit <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> selhání vyvolat z důvodu selhání klienta přijímat odpovědi. V jednosměrných smlouvách nemusí rozpoznat chybu, že <xref:System.ServiceModel.Activities.WorkflowHostingResponseContext.SendResponse%2A> se nepodařilo volat, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> dokud není příliš pozdě, po překročení limitu škrticí klapky. Další informace naleznete [v tématu WorkflowHostingEndpoint Resume Bookmark](../../../../docs/framework/windows-workflow-foundation/samples/workflowhostingendpoint-resume-bookmark.md)Chcete-li vytvořit novou instanci pracovního postupu bez služby, deklarujte servisní smlouvu, která definuje operaci, která vytvoří novou instanci. Operace vytvoření by měla trvat řetězec IDictionary,\<objekt> předat všechny požadované parametry pracovního postupu. Tato smlouva je implicitně <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>implementována -derived třídy. Při hostování pracovního postupu přidejte instanci <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>odvozené <xref:System.ServiceModel.Activities.WorkflowServiceHost.AddServiceEndpoint%2A> třídy <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>do hostitele voláním a voláním . Chcete-li vytvořit instanci <xref:System.ServiceModel.ChannelFactory%601> pracovního postupu, vytvořte typ a volání <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>servisní smlouvy . Potom můžete volat operaci vytvoření definovanou v servisní smlouvě.  
  
## <a name="see-also"></a>Viz také

- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Aktivity zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
