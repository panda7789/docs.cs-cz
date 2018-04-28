---
title: Řešení potíží – korelace
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5bdf111e6802692aef893cf9dcae88f0f51aa467
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="bf50b-102">Řešení potíží – korelace</span><span class="sxs-lookup"><span data-stu-id="bf50b-102">Troubleshooting Correlation</span></span>
<span data-ttu-id="bf50b-103">Korelace se používá k propojení zpráv služby pracovního postupu se vzájemně k sobě a k instanci pracovního postupu správný, ale pokud není správně nakonfigurována, nebude přijaty zprávy a aplikace nebude správně fungovat.</span><span class="sxs-lookup"><span data-stu-id="bf50b-103">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="bf50b-104">Toto téma obsahuje přehled několik metod pro řešení potíží s korelace a také uvádí některé běžné problémy, které může dojít, když používáte korelace.</span><span class="sxs-lookup"><span data-stu-id="bf50b-104">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>  
  
## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="bf50b-105">Zpracovat událost UnknownMessageReceived</span><span class="sxs-lookup"><span data-stu-id="bf50b-105">Handle the UnknownMessageReceived Event</span></span>  
 <span data-ttu-id="bf50b-106"><xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> Události dojde, když je neznámá zpráva přijatých služby, včetně zprávy, které nelze vztažen k existující instanci.</span><span class="sxs-lookup"><span data-stu-id="bf50b-106">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="bf50b-107">Tato událost může pro samoobslužné hostované služby, ošetřit v hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bf50b-107">For self-hosted services, this event can be handled in the host application.</span></span>  
  
```csharp  
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)  
{  
    Console.WriteLine("Unknown Message Received:");  
    Console.WriteLine(e.Message);  
};  
```  
  
 <span data-ttu-id="bf50b-108">Pro hostované webové služby, tato událost může ošetřit odvození třídy z <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> a přepsáním <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="bf50b-108">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>  
  
```csharp  
class CustomFactory : WorkflowServiceHostFactory  
{  
    protected override WorkflowServiceHost CreateWorkflowServiceHost(Activity activity, Uri[] baseAddresses)  
    {  
        // Create the WorkflowServiceHost.  
        WorkflowServiceHost host = new WorkflowServiceHost(activity, baseAddresses);  
  
        // Handle the UnknownMessageReceived event.  
        host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)  
        {  
            Console.WriteLine("Unknown Message Received:");  
            Console.WriteLine(e.Message);  
        };  
  
        return host;  
    }  
}  
```  
  
 <span data-ttu-id="bf50b-109">Tato vlastní <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> lze zadat v `svc` soubor služby.</span><span class="sxs-lookup"><span data-stu-id="bf50b-109">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>  
  
```  
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>  
```  
  
 <span data-ttu-id="bf50b-110">Po vyvolání této obslužné rutiny zprávy můžete načíst pomocí <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> vlastnost <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>a bude připomínat následující zpráva.</span><span class="sxs-lookup"><span data-stu-id="bf50b-110">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>  
  
```Output  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <To s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://localhost:8080/OrderService</To>  
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>  
  </s:Header>  
  <s:Body>  
    <AddItem xmlns="http://tempuri.org/">  
      <Item>Books</Item>  
    </AddItem>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="bf50b-111">Probíhá kontrola zpráv odeslaných <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> obslužná rutina může poskytnout proč zpráva není korelovat na instanci služby pracovního postupu, který následuje.</span><span class="sxs-lookup"><span data-stu-id="bf50b-111">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>  
  
## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="bf50b-112">Používání sledování pro monitorování průběhu pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="bf50b-112">Use Tracking to Monitor the Progress of the Workflow</span></span>  
 <span data-ttu-id="bf50b-113">Sledování poskytuje způsob, jak monitorovat průběh pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bf50b-113">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="bf50b-114">Ve výchozím nastavení jsou záznamy o sledování vygenerované pro pracovní postup události životního cyklu, události životního cyklu aktivity, šíření selhání a obnovení záložku.</span><span class="sxs-lookup"><span data-stu-id="bf50b-114">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="bf50b-115">Kromě toho můžete vlastní sledování záznamů vysílaných vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="bf50b-115">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="bf50b-116">Při řešení potíží – korelace, aktivita sledování záznamy, na záložku obnovení záznamy a záznamy šíření selhání jsou velmi užitečné.</span><span class="sxs-lookup"><span data-stu-id="bf50b-116">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="bf50b-117">Aktivita sledování záznamů slouží k určení aktuální průběh pracovního postupu a může pomoct identifikovat, které zasílání zpráv aktivity je aktuálně čeká na zprávy.</span><span class="sxs-lookup"><span data-stu-id="bf50b-117">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="bf50b-118">Záložku obnovení záznamy jsou užitečné, protože označují, že v tomto pracovním postupu byla přijata zpráva a selhání šíření záznamů poskytnout záznam všech chyb v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="bf50b-118">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="bf50b-119">Chcete-li povolit sledování, zadejte požadovanou <xref:System.Activities.Tracking.TrackingParticipant> v <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> z <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="bf50b-119">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="bf50b-120">V následujícím příkladu `ConsoleTrackingParticipant` (z [vlastní sledování](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) ukázkové) je nakonfigurována pomocí výchozí sledování profil.</span><span class="sxs-lookup"><span data-stu-id="bf50b-120">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>  
  
```csharp  
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="bf50b-121">Sledování účastník například ConsoleTrackingParticipant je užitečné pro služeb vlastním hostováním pracovních postupů, které mají okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="bf50b-121">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="bf50b-122">Pro hostované webové služby, třeba použít sledování účastník, který zaznamenává informace o sledování odolná úložiště, jako je například integrované <xref:System.Activities.Tracking.EtwTrackingParticipant>, nebo vlastní sledování člena, který protokoluje informace do souboru, například `TextWriterTrackingParticpant` z [ Sledování pomocí textového souboru](../../../../docs/framework/windows-workflow-foundation/samples/tracking-using-a-text-file.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="bf50b-122">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file, such as the `TextWriterTrackingParticpant` from the [Tracking Using a Text File](../../../../docs/framework/windows-workflow-foundation/samples/tracking-using-a-text-file.md) sample.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="bf50b-123"> sledování a konfigurace sledování pro službu Web hostovaný pracovní postup, najdete v části [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [konfigurace sledování pro pracovní postup](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)a [sledování &#91;WF Ukázky&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) ukázky.</span><span class="sxs-lookup"><span data-stu-id="bf50b-123"> tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>  
  
## <a name="use-wcf-tracing"></a><span data-ttu-id="bf50b-124">Pomocí trasování WCF</span><span class="sxs-lookup"><span data-stu-id="bf50b-124">Use WCF Tracing</span></span>  
 <span data-ttu-id="bf50b-125">Trasování WCF poskytuje trasování toku zpráv do a ze služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="bf50b-125">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="bf50b-126">Tyto informace trasování jsou užitečné při řešení problémů korelace, hlavně pro korelace na základě obsahu.</span><span class="sxs-lookup"><span data-stu-id="bf50b-126">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="bf50b-127">Povolení trasování, zadejte požadované trasování – moduly naslouchání v `system.diagnostics` části `web.config` souboru pokud hostované webové služby pracovního postupu nebo `app.config` soubor, pokud se hostuje sama služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bf50b-127">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="bf50b-128">Chcete-li zahrnout obsah zprávy v trasovacím souboru, zadejte `true` pro `logEntireMessage` v `messageLogging` element v `diagnostics` části `system.serviceModel`.</span><span class="sxs-lookup"><span data-stu-id="bf50b-128">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="bf50b-129">V následujícím příkladu je nakonfigurované informace trasování, včetně obsahu zprávy, k zápisu do souboru, který je pojmenován `service.svclog`.</span><span class="sxs-lookup"><span data-stu-id="bf50b-129">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information" propagateActivity="true">  
        <listeners>  
          <add name="corr"/>  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="corr"/>  
        </listeners>  
      </source>  
    </sources>  
  
    <sharedListeners>  
      <add name="corr" type="System.Diagnostics.XmlWriterTraceListener" initializeData="c:\logs\service.svclog">  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
  
  <system.serviceModel>  
    <diagnostics>  
      <messageLogging logEntireMessage="true" logMalformedMessages="false"  
         logMessagesAtServiceLevel="false" logMessagesAtTransportLevel="true" maxSizeOfMessageToLog="2147483647">  
      </messageLogging>  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="bf50b-130">Chcete-li zobrazit informace trasování, která je součástí `service.svclog`, [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) se používá.</span><span class="sxs-lookup"><span data-stu-id="bf50b-130">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="bf50b-131">To je obzvláště užitečná při řešení potíží – korelace na základě obsahu problémy, protože můžete zobrazit obsah zprávy a zobrazit přesně co je předávána, a zda odpovídá <xref:System.ServiceModel.CorrelationQuery> pro korelace na základě obsahu.</span><span class="sxs-lookup"><span data-stu-id="bf50b-131">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="bf50b-132"> WCF trasování, najdete v části [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), a [pomocí trasování řešení vaše aplikace](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="bf50b-132"> WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>  
  
## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="bf50b-133">Běžné problémy korelace Exchange kontextu</span><span class="sxs-lookup"><span data-stu-id="bf50b-133">Common Context Exchange Correlation Issues</span></span>  
 <span data-ttu-id="bf50b-134">Určité typy korelace vyžadují, aby určitý typ vazby se používá pro korelaci fungovala správně.</span><span class="sxs-lookup"><span data-stu-id="bf50b-134">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="bf50b-135">Mezi příklady patří korelace požadavku a odpovědi, které vyžaduje obousměrný vazbu, jako <xref:System.ServiceModel.BasicHttpBinding>a korelace kontextové výměny, který vyžaduje, na základě kontextu vazby, jako <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="bf50b-135">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="bf50b-136">Většina vazby podporu obousměrný operací, nejedná se o běžné problémy, se pro korelace požadavku a odpovědi, ale existují jen někteří z nich na základě kontextu vazby, včetně <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, a <xref:System.ServiceModel.NetTcpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="bf50b-136">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="bf50b-137">Jednu z těchto vazeb se nepoužívá, počáteční volání služby pracovního postupu bude úspěšné, ale následná volání nebudou úspěšná s následující <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="bf50b-137">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>  
  
```Output  
There is no context attached to the incoming message for the service   
and the current operation is not marked with "CanCreateInstance = true".   
In order to communicate with this service check whether the incoming binding   
supports the context protocol and has a valid context initialized.  
```  
  
 <span data-ttu-id="bf50b-138">Informace o kontextu, který slouží pro korelaci kontext může být vrácen pouze <xref:System.ServiceModel.Activities.SendReply> k <xref:System.ServiceModel.Activities.Receive> aktivity, která inicializuje kontext korelace, když pomocí obousměrné operaci, nebo ji lze zadat volající Pokud byla operace jednosměrná.</span><span class="sxs-lookup"><span data-stu-id="bf50b-138">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="bf50b-139">Pokud není kontextu poslal volající nebo vrácené služby pracovního postupu pak stejné <xref:System.ServiceModel.FaultException> popsané dříve bude vrácen, pokud následné operace je volána.</span><span class="sxs-lookup"><span data-stu-id="bf50b-139">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>  
  
 <span data-ttu-id="bf50b-140">Další informace najdete v tématu [kontextová výměna](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="bf50b-140">For more information, see [Context Exchange](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).</span></span>  
  
## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="bf50b-141">Běžné problémy korelace požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="bf50b-141">Common Request-Reply Correlation Issues</span></span>  
 <span data-ttu-id="bf50b-142">Korelace požadavku a odpovědi se používá s <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár implementovat obousměrný operace ve službě pracovního postupu a s <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár, který vyvolá obousměrný operaci v jiný Web Služba.</span><span class="sxs-lookup"><span data-stu-id="bf50b-142">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="bf50b-143">Při vyvolání obousměrný operace ve službě WCF, služba může být buď tradiční imperativní založené na kódu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, nebo může být služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="bf50b-143">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or it can be a workflow service.</span></span> <span data-ttu-id="bf50b-144">Použít korelace požadavku a odpovědi vazba obousměrná musí být použita, jako například <xref:System.ServiceModel.BasicHttpBinding>, a operace musí být obousměrné.</span><span class="sxs-lookup"><span data-stu-id="bf50b-144">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>  
  
 <span data-ttu-id="bf50b-145">Pokud službu pracovní postup obsahuje obousměrný operace paralelní nebo překrývající se <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> nebo <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> páry pak implicitní korelace zpracování Správa poskytovaná v rámci <xref:System.ServiceModel.Activities.WorkflowServiceHost>nemusí být plně dostačující, zejména ve scénářích velkými nároky a zprávy nebudou směrovány správně.</span><span class="sxs-lookup"><span data-stu-id="bf50b-145">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="bf50b-146">Chcete-li zabránit výskytu tohoto problému, doporučujeme, aby vždy explicitně zadáte <xref:System.ServiceModel.Activities.CorrelationHandle> při použití korelace požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="bf50b-146">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="bf50b-147">Při použití **SendAndReceiveReply** a **ReceiveAndSendReply** šablony z části zasílání zpráv **sada nástrojů** v Návrháři pracovních postupů <xref:System.ServiceModel.Activities.CorrelationHandle> explicitně nakonfigurované ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="bf50b-147">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="bf50b-148">Při vytváření pracovního postupu pomocí kódu, <xref:System.ServiceModel.Activities.CorrelationHandle> je uveden v <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> první aktivitu v páru.</span><span class="sxs-lookup"><span data-stu-id="bf50b-148">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="bf50b-149">V následujícím příkladu <xref:System.ServiceModel.Activities.Receive> aktivity je nakonfigurován pomocí explicitního <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> zadaný v <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="bf50b-149">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = ... // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 <span data-ttu-id="bf50b-150">Mezi není povolena trvalost <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár nebo <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár.</span><span class="sxs-lookup"><span data-stu-id="bf50b-150">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="bf50b-151">Je vytvořena zóna no-persist trvající až do dokončení obou aktivity.</span><span class="sxs-lookup"><span data-stu-id="bf50b-151">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="bf50b-152">Pokud aktivity, jako je například aktivitu zpoždění je v této zóně no-persist a pracovní postup na nečinnost, pracovní postup neuchovává i v případě, pokud hostitel je nakonfigurovaný pro uchování pracovních postupů, kdy se stanou nečinné.</span><span class="sxs-lookup"><span data-stu-id="bf50b-152">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="bf50b-153">Pokud aktivity, jako je například aktivitu zachovat pokusí explicitně zachovat v zóně ne zachovat, závažná je vyvolána výjimka, přerušení pracovního postupu a <xref:System.ServiceModel.FaultException> je vrácen volajícímu.</span><span class="sxs-lookup"><span data-stu-id="bf50b-153">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="bf50b-154">Zpráva o závažné výjimce "System.InvalidOperationException: zachování aktivity nemůžou být obsažené v rámci bloků žádné trvalost.".</span><span class="sxs-lookup"><span data-stu-id="bf50b-154">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="bf50b-155">Tato výjimka není vrácen volajícímu ale může být dodržen, pokud je povoleno sledování.</span><span class="sxs-lookup"><span data-stu-id="bf50b-155">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="bf50b-156">Zpráva pro <xref:System.ServiceModel.FaultException> vrácen volajícímu je "operaci nelze provést, protože instance pracovního postupu '5836145b-7da2 - 49 d 0-a052-a49162adeab6' byla dokončena".</span><span class="sxs-lookup"><span data-stu-id="bf50b-156">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="bf50b-157"> korelace požadavku a odpovědi, najdete v části [požadavku a odpovědi](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="bf50b-157"> request-reply correlation, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span></span>  
  
## <a name="common-content-correlation-issues"></a><span data-ttu-id="bf50b-158">Běžné problémy obsahu korelace</span><span class="sxs-lookup"><span data-stu-id="bf50b-158">Common Content Correlation Issues</span></span>  
 <span data-ttu-id="bf50b-159">Korelace na základě obsahu se používá při služby pracovního postupu přijímá více zpráv a část dat v výměně zpráv určuje požadovanou instanci.</span><span class="sxs-lookup"><span data-stu-id="bf50b-159">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="bf50b-160">Korelace na základě obsahu používá tato data ve zprávě, jako je například číslo nebo pořadí ID zákazníka, pro směrování zpráv do instance správný pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bf50b-160">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="bf50b-161">Tato část popisuje několik běžné problémy, které mohou nastat při použití korelace na základě obsahu.</span><span class="sxs-lookup"><span data-stu-id="bf50b-161">This section describes several common issues that may occur when using content-based correlation.</span></span>  
  
### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="bf50b-162">Ujistěte se, že je jedinečné identifikační Data</span><span class="sxs-lookup"><span data-stu-id="bf50b-162">Ensure the Identifying Data Is Unique</span></span>  
 <span data-ttu-id="bf50b-163">Data, která se používá k identifikaci instance je algoritmus hash, do klíče korelace.</span><span class="sxs-lookup"><span data-stu-id="bf50b-163">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="bf50b-164">Dbát musí zaručit, že data, která se používá pro korelačního jedinečné, jinak může dojít a způsobit zpráv, které mají být nesprávně směrovanými kolizí v klíči hash.</span><span class="sxs-lookup"><span data-stu-id="bf50b-164">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="bf50b-165">Například existuje korelace pouze podle jméno zákazníka mohou způsobit kolize, protože může být více zákazníků, kteří mají stejný název.</span><span class="sxs-lookup"><span data-stu-id="bf50b-165">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="bf50b-166">Jako součást data, která slouží ke sladění zprávu, protože se již používá pro vymezení klíč a hodnotu a vytvořit řetězec, který je následně rozdělí dotazu zprávu nepoužívejte dvojtečkou (:).</span><span class="sxs-lookup"><span data-stu-id="bf50b-166">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="bf50b-167">Pokud trvalost se používá, ujistěte se, že data aktuálního identifikační nebyl použit dříve drženého instancí.</span><span class="sxs-lookup"><span data-stu-id="bf50b-167">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="bf50b-168">Dočasně zakázat trvalost může pomoci identifikovat potíže.</span><span class="sxs-lookup"><span data-stu-id="bf50b-168">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="bf50b-169">WCF trasování můžete použít k zobrazení počítané korelace klíč a slouží k ladění tento druh problému.</span><span class="sxs-lookup"><span data-stu-id="bf50b-169">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>  
  
### <a name="race-conditions"></a><span data-ttu-id="bf50b-170">Konflikty časování</span><span class="sxs-lookup"><span data-stu-id="bf50b-170">Race Conditions</span></span>  
 <span data-ttu-id="bf50b-171">Existuje malé mezera v době mezi službu přijetí zprávy a korelace ve skutečnosti inicializován, během které následné zprávy budou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="bf50b-171">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="bf50b-172">Pokud služby pracovního procesu inicializuje korelace na základě obsahu pomocí dat předávaných přes Jednosměrná operace z klienta, a odesílá okamžitou následné zprávy, se tyto zprávy ignorovat během tohoto intervalu.</span><span class="sxs-lookup"><span data-stu-id="bf50b-172">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="bf50b-173">Tím se vyhnout pomocí obousměrné operace k chybě při inicializaci korelaci nebo pomocí <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="bf50b-173">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>  
  
### <a name="correlation-query-issues"></a><span data-ttu-id="bf50b-174">Korelace dotazu problémy</span><span class="sxs-lookup"><span data-stu-id="bf50b-174">Correlation Query Issues</span></span>  
 <span data-ttu-id="bf50b-175">Korelace dotazy se používají k určení, jaká data ve zprávě slouží ke sladění zprávy.</span><span class="sxs-lookup"><span data-stu-id="bf50b-175">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="bf50b-176">Tato data je určena pomocí dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="bf50b-176">This data is specified by using an XPath query.</span></span> <span data-ttu-id="bf50b-177">Pokud zprávy a pokuste se službu nejsou distribuovanou, i když všechno, co se zdá být správné, je jednou z možných strategií pro řešení potíží s zadejte literálu hodnotu, která odpovídá hodnotě data zpráv místo dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="bf50b-177">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="bf50b-178">Pokud chcete zadat literálovou hodnotou, použijte `string` funkce.</span><span class="sxs-lookup"><span data-stu-id="bf50b-178">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="bf50b-179">V následujícím příkladu <xref:System.ServiceModel.MessageQuerySet> je nakonfigurovaný na použití hodnotu literálu `11445` pro `OrderId` a dotaz XPath je označeno jako komentář.</span><span class="sxs-lookup"><span data-stu-id="bf50b-179">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>  
  
```csharp  
MessageQuerySet = new MessageQuerySet  
{  
    {  
        "OrderId",   
        //new XPathMessageQuery("sm:body()/tempuri:StartOrderResponse/tempuri:OrderId")  
        new XPathMessageQuery("string('11445')")  
    }  
}  
```  
  
 <span data-ttu-id="bf50b-180">Pokud dotaz XPath není správně nakonfigurovaná tak, že je načíst žádná data korelace, vrátí se chybu s následující zprávou: "dotazu korelace poskytuje prázdnou sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="bf50b-180">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="bf50b-181">Ujistěte se, že jsou správně nakonfigurovány korelace dotazy pro koncový bod."</span><span class="sxs-lookup"><span data-stu-id="bf50b-181">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="bf50b-182">Jeden rychlý způsob, jak toto řešení je nahradit dotaz XPath s literálovou hodnotou, jak je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="bf50b-182">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="bf50b-183">Tento problém může dojít, pokud používáte Tvůrce dotazů XPath v **přidat inicializátory korelace** nebo **CorrelatesOn definice** dialogových oken a služby pracovního postupu používá kontrakty zpráv.</span><span class="sxs-lookup"><span data-stu-id="bf50b-183">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="bf50b-184">V následujícím příkladu je definován třídou kontraktu zprávy.</span><span class="sxs-lookup"><span data-stu-id="bf50b-184">In the following example, a message contract class is defined.</span></span>  
  
```csharp  
[MessageContract]  
public class AddItemMessage  
{  
    [MessageHeader]  
    public string CartId;  
  
    [MessageBodyMember]  
    public string Item;  
}  
```  
  
 <span data-ttu-id="bf50b-185">Tento kontrakt zprávy používá <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="bf50b-185">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="bf50b-186">`CartId` v záhlaví zprávy slouží ke sladění zprávu, která se správnou instanci.</span><span class="sxs-lookup"><span data-stu-id="bf50b-186">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="bf50b-187">Pokud dotaz XPath, který načte `CartId` je vytvořený pomocí korelace dialogová okna v Návrháři pracovních postupů, následující nesprávnou XPath vygenerovat dotaz.</span><span class="sxs-lookup"><span data-stu-id="bf50b-187">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>  
  
```  
sm:body()/xg0:AddItemMessage/xg0:CartId  
```  
  
 <span data-ttu-id="bf50b-188">Tento dotaz XPath by byly správné Pokud <xref:System.ServiceModel.Activities.Receive> aktivita používá parametry pro data, ale vzhledem k tomu, že používá kontrakt zprávy je nesprávný.</span><span class="sxs-lookup"><span data-stu-id="bf50b-188">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="bf50b-189">Následující dotaz XPath je správný dotaz XPath pro načtení `CartId` z hlavičky.</span><span class="sxs-lookup"><span data-stu-id="bf50b-189">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>  
  
```  
sm:header()/tempuri:CartId  
```  
  
 <span data-ttu-id="bf50b-190">To jde potvrdit tak, že prověří tělo zprávy.</span><span class="sxs-lookup"><span data-stu-id="bf50b-190">This can be confirmed by examining the body of the message.</span></span>  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <Action s:mustUnderstand="1" xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none">http://tempuri.org/IService/AddItem</Action>  
    <h:CartId xmlns:h="http://tempuri.org/">80c95b41-c98d-4660-a6c1-99412206e54c</h:CartId>  
  </s:Header>  
  <s:Body>  
    <AddItemMessage xmlns="http://tempuri.org/">  
      <Item>Books</Item>  
    </AddItemMessage>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="bf50b-191">Následující příklad ukazuje <xref:System.ServiceModel.Activities.Receive> aktivity, které jsou nakonfigurované pro `AddItem` operací, která používá předchozí kontrakt zprávy přijímat data.</span><span class="sxs-lookup"><span data-stu-id="bf50b-191">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="bf50b-192">Dotaz XPath je správně nakonfigurován.</span><span class="sxs-lookup"><span data-stu-id="bf50b-192">The XPath query is correctly configured.</span></span>  
  
```xaml  
<Receive CorrelatesWith="[CCHandle] OperationName="AddItem" ServiceContractName="p:IService">  
  <Receive.CorrelatesOn>  
    <XPathMessageQuery x:Key="key1">  
      <XPathMessageQuery.Namespaces>  
        <ssx:XPathMessageContextMarkup>  
          <x:String x:Key="xg0">http://schemas.datacontract.org/2004/07/MessageContractWFService</x:String>  
        </ssx:XPathMessageContextMarkup>  
      </XPathMessageQuery.Namespaces>sm:header()/tempuri:CartId</XPathMessageQuery>  
  </Receive.CorrelatesOn>  
  <ReceiveMessageContent DeclaredMessageType="m:AddItemMessage">  
    <p1:OutArgument x:TypeArguments="m:AddItemMessage">[AddItemMessage]</p1:OutArgument>  
  </ReceiveMessageContent>  
</Receive>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="bf50b-193"> korelace na základě obsahu najdete v části [na základě obsahu](../../../../docs/framework/wcf/feature-details/content-based-correlation.md) a [korelační kalkulačky](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="bf50b-193"> content-based correlation, see [Content Based](../../../../docs/framework/wcf/feature-details/content-based-correlation.md) and the [Correlated Calculator](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md) sample.</span></span>
