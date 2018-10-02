---
title: Řešení potíží – korelace
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: fecfaf7374823bb19a4ad3d7f6cb2dbbdf139703
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48027920"
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="75068-102">Řešení potíží – korelace</span><span class="sxs-lookup"><span data-stu-id="75068-102">Troubleshooting Correlation</span></span>
<span data-ttu-id="75068-103">Korelace se používá k propojení zprávy služby pracovního postupu k sobě navzájem a pro instanci pracovního postupu správný, ale pokud není správně nakonfigurována, nebude přijímat zprávy a aplikace nebude fungovat správně.</span><span class="sxs-lookup"><span data-stu-id="75068-103">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="75068-104">Toto téma obsahuje základní informace o několik metod pro řešení potíží s korelace a také uvádí některé běžné problémy, které může dojít, když použijete korelace.</span><span class="sxs-lookup"><span data-stu-id="75068-104">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>

## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="75068-105">Zpracování události UnknownMessageReceived</span><span class="sxs-lookup"><span data-stu-id="75068-105">Handle the UnknownMessageReceived Event</span></span>
 <span data-ttu-id="75068-106"><xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> Události dojde, když je přijata Neznámá zpráva podle služby, včetně zpráv, které nemůže být přiřazeny k existující instanci.</span><span class="sxs-lookup"><span data-stu-id="75068-106">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="75068-107">V místním prostředí služby mohou být zpracovány tuto událost v hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="75068-107">For self-hosted services, this event can be handled in the host application.</span></span>

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 <span data-ttu-id="75068-108">Pro hostované webové služby, může být zpracována tato událost odvození třídy z <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> a přepsáním <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="75068-108">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>

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

 <span data-ttu-id="75068-109">Tato vlastní <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> lze zadat v `svc` souboru služby.</span><span class="sxs-lookup"><span data-stu-id="75068-109">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>

```
<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>
```

 <span data-ttu-id="75068-110">Po vyvolání Tato obslužná rutina zprávy lze načíst s použitím <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> vlastnost <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>a bude vypadat podobně jako následující zpráva.</span><span class="sxs-lookup"><span data-stu-id="75068-110">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>

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

 <span data-ttu-id="75068-111">Kontrola zprávy odeslána <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> obslužná rutina může poskytnout příčiny o Proč není korelaci zprávy do instance služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75068-111">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="75068-112">Používání sledování můžete sledovat průběh pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="75068-112">Use Tracking to Monitor the Progress of the Workflow</span></span>
 <span data-ttu-id="75068-113">Sledování poskytuje způsob, jak monitorovat průběh pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75068-113">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="75068-114">Ve výchozím nastavení jsou vydávány sledování záznamů pro pracovní postup události životního cyklu, události životního cyklu aktivit, šíření chyb a záložku obnovení.</span><span class="sxs-lookup"><span data-stu-id="75068-114">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="75068-115">Kromě toho může být vygenerována vlastní záznamy sledování vlastních aktivit.</span><span class="sxs-lookup"><span data-stu-id="75068-115">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="75068-116">Při řešení potíží – korelace, jsou zvláště užitečná sledování záznamů, záložku obnovení záznamů a chyby šíření hodnoty záznamů aktivit.</span><span class="sxs-lookup"><span data-stu-id="75068-116">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="75068-117">Aktivita sledování záznamů je možné určit aktuální průběh pracovního postupu a může pomoct identifikovat, které zasílání zpráv aktivity je aktuálně čeká na zprávy.</span><span class="sxs-lookup"><span data-stu-id="75068-117">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="75068-118">Záložku obnovení záznamů jsou užitečné, protože označují, že byla přijata zpráva tímto pracovním postupem a chyby šíření záznamy obsahují záznam o všechny chyby, v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="75068-118">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="75068-119">Chcete-li povolit sledování, zadejte požadovaný <xref:System.Activities.Tracking.TrackingParticipant> v <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> z <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="75068-119">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="75068-120">V následujícím příkladu `ConsoleTrackingParticipant` (z [vlastní sledování](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) ukázkové) je nakonfigurován s použitím výchozí profil sledování tracking profile.</span><span class="sxs-lookup"><span data-stu-id="75068-120">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 <span data-ttu-id="75068-121">Sledování účastník, jako je například ConsoleTrackingParticipant je užitečné pro pracovní postup v místním prostředí služby, které mají okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="75068-121">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="75068-122">Pro hostované webové služby, třeba použít účastníkem sledování, která zaznamenává informace o sledování do odolného úložiště, jako je například předdefinované <xref:System.Activities.Tracking.EtwTrackingParticipant>, nebo vlastní sledování účastník, který protokoluje informace do souboru.</span><span class="sxs-lookup"><span data-stu-id="75068-122">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file.</span></span>

 <span data-ttu-id="75068-123">Další informace o sledování a konfiguraci sledování pro služby hostované webového pracovního procesu, naleznete v tématu [pracovního postupu pro sledování a trasování](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [konfigurace sledování pracovního postupu](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)a [ Sledování &#91;ukázky WF&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) ukázky.</span><span class="sxs-lookup"><span data-stu-id="75068-123">For more information about tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>

## <a name="use-wcf-tracing"></a><span data-ttu-id="75068-124">Použít trasování WCF</span><span class="sxs-lookup"><span data-stu-id="75068-124">Use WCF Tracing</span></span>
 <span data-ttu-id="75068-125">Trasování WCF obsahuje trasování toku zpráv do a ze služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="75068-125">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="75068-126">Tyto informace trasování jsou užitečné při řešení problémů korelace, zejména u korelace na základě obsahu.</span><span class="sxs-lookup"><span data-stu-id="75068-126">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="75068-127">Povolení trasování, určete naslouchací procesy požadované trasování v `system.diagnostics` část `web.config` souboru, pokud služba pracovního postupu je Web hostovaný, nebo `app.config` souboru, pokud je služba pracovního postupu v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="75068-127">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="75068-128">Chcete-li zahrnout obsah zprávy do souboru trasování, zadejte `true` pro `logEntireMessage` v `messageLogging` element v `diagnostics` část `system.serviceModel`.</span><span class="sxs-lookup"><span data-stu-id="75068-128">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="75068-129">V následujícím příkladu je nakonfigurované trasovací informace, včetně obsahu zpráv, má být zapsán do souboru s názvem `service.svclog`.</span><span class="sxs-lookup"><span data-stu-id="75068-129">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>

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

 <span data-ttu-id="75068-130">Chcete-li zobrazit trasovací informace, které je součástí `service.svclog`, [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) se používá.</span><span class="sxs-lookup"><span data-stu-id="75068-130">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="75068-131">To je zvlášť užitečné při řešení potíží – korelace na základě obsahu problémy, protože můžete zobrazit obsah zprávy a podívejte se, právě co je předávána a určuje, zda odpovídá <xref:System.ServiceModel.CorrelationQuery> pro korelaci založené na obsahu.</span><span class="sxs-lookup"><span data-stu-id="75068-131">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> <span data-ttu-id="75068-132">Další informace o trasování WCF najdete v tématu [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), a [pomocí trasování řešení potíží s aplikací](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="75068-132">For more information about WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="75068-133">Běžné problémy korelace místní Exchange</span><span class="sxs-lookup"><span data-stu-id="75068-133">Common Context Exchange Correlation Issues</span></span>
 <span data-ttu-id="75068-134">Určité typy korelace vyžadovat, že se konkrétní typ vazby používá pro korelaci fungovat správně.</span><span class="sxs-lookup"><span data-stu-id="75068-134">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="75068-135">Mezi příklady patří korelace požadavku a odpovědi, která vyžaduje Obousměrná vazba například <xref:System.ServiceModel.BasicHttpBinding>a korelace kontextové výměny, který vyžaduje základě kontextu vazby, jako <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="75068-135">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="75068-136">Většina vazby podporují obousměrné operace, nejedná se o běžný problém pro korelace požadavku a odpovědi, ale jenom na několik na základě kontextu vazby, včetně <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, a <xref:System.ServiceModel.NetTcpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="75068-136">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="75068-137">Jednu z těchto vazeb se nepoužívá, počáteční volání služby pracovního postupu bude úspěšné, ale následná volání nebudou úspěšná následujícím <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="75068-137">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>

```Output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 <span data-ttu-id="75068-138">Informace o kontextu, který slouží pro korelaci kontextu může být vrácen <xref:System.ServiceModel.Activities.SendReply> k <xref:System.ServiceModel.Activities.Receive> aktivitu, která inicializuje korelaci kontextu při použití obousměrný operaci, nebo je možné zadat tak volající Pokud je operace jednosměrná.</span><span class="sxs-lookup"><span data-stu-id="75068-138">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="75068-139">Pokud není kontext odesílaných volající nebo vrácený služby pracovního postupu a pak stejné <xref:System.ServiceModel.FaultException> popsané dříve se vrátí, pokud je vyvolána následná operace.</span><span class="sxs-lookup"><span data-stu-id="75068-139">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>

## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="75068-140">Běžné problémy korelace požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="75068-140">Common Request-Reply Correlation Issues</span></span>
 <span data-ttu-id="75068-141">Korelace požadavku a odpovědi se používá s <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár pro implementaci obousměrný operace ve službě pracovních postupů a se <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár, který vyvolá obousměrný operaci na jiném webu Služba.</span><span class="sxs-lookup"><span data-stu-id="75068-141">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="75068-142">Při vyvolání obousměrný operace ve službě WCF, služba může být buď tradiční služba WCF imperativní založený na kódu nebo to může být služba pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="75068-142">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based WCF service or it can be a workflow service.</span></span> <span data-ttu-id="75068-143">Použití korelace požadavku a odpovědi Obousměrná vazba musí být použita, jako například <xref:System.ServiceModel.BasicHttpBinding>, a operace musí být obousměrné.</span><span class="sxs-lookup"><span data-stu-id="75068-143">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>

 <span data-ttu-id="75068-144">Pokud má služba pracovního postupu obousměrný operace v paralelní nebo překrývající se <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> nebo <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> páry a potom implicitní korelace postupovat při správě poskytované <xref:System.ServiceModel.Activities.WorkflowServiceHost>nemusí být dostatečné, zejména ve scénářích vysoké zatížení, a nemusí správně směrovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="75068-144">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="75068-145">K tomuto problému zabránit, doporučujeme vám, že je vždy explicitně zadat <xref:System.ServiceModel.Activities.CorrelationHandle> při použití korelace požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="75068-145">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="75068-146">Při použití **SendAndReceiveReply** a **ReceiveAndSendReply** šablony z části zasílání zpráv **nástrojů** v Návrháři pracovních postupů <xref:System.ServiceModel.Activities.CorrelationHandle> explicitně nakonfigurované ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="75068-146">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="75068-147">Při vytváření pracovního postupu pomocí kódu, <xref:System.ServiceModel.Activities.CorrelationHandle> je zadán v <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> sady první aktivity v páru.</span><span class="sxs-lookup"><span data-stu-id="75068-147">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="75068-148">V následujícím příkladu <xref:System.ServiceModel.Activities.Receive> aktivita je konfigurována s explicitní <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> zadané v poli <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="75068-148">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>

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

 <span data-ttu-id="75068-149">Mezi není povolena trvalost <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> pár nebo <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> pár.</span><span class="sxs-lookup"><span data-stu-id="75068-149">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="75068-150">No-persist zóny se vytvoří s platností dokončením obě aktivity.</span><span class="sxs-lookup"><span data-stu-id="75068-150">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="75068-151">Pokud aktivita, jako je aktivita zpoždění, je v této zóně no-persist a způsobí, že pracovní postup na nečinnost, nezachovají pracovní postup i v případě, pokud je hostitel konfigurován k uchování pracovních postupů, kdy se stanou nečinné.</span><span class="sxs-lookup"><span data-stu-id="75068-151">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="75068-152">Pokud aktivity, jako je aktivita zachovat, se pokusí explicitně zachovat v zóně trvalého Ne, je závažnou výjimku vyvolána, přerušení pracovního postupu a <xref:System.ServiceModel.FaultException> je vrátit zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="75068-152">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="75068-153">Zpráva kritické výjimky "System.InvalidOperationException: uchování aktivity nelze zahrnout do dočasných bloků.".</span><span class="sxs-lookup"><span data-stu-id="75068-153">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="75068-154">Tato výjimka není vrátit zpět volajícímu, ale můžete pozorovat, pokud je povoleno sledování.</span><span class="sxs-lookup"><span data-stu-id="75068-154">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="75068-155">Zpráva pro <xref:System.ServiceModel.FaultException> vrátit zpět volajícímu je "operaci nelze provést, protože dokončení instance pracovního postupu"5836145b 7da2 - 49 d 0-a052-a49162adeab6"".</span><span class="sxs-lookup"><span data-stu-id="75068-155">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>

 <span data-ttu-id="75068-156">Další informace o korelace požadavku a odpovědi najdete v tématu [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="75068-156">For more information about request-reply correlation, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span></span>

## <a name="common-content-correlation-issues"></a><span data-ttu-id="75068-157">Běžné problémy obsahu korelace</span><span class="sxs-lookup"><span data-stu-id="75068-157">Common Content Correlation Issues</span></span>
 <span data-ttu-id="75068-158">Korelace na základě obsahu se používá v případě služby pracovního postupu přijímá více zpráv a část dat ve výměně zpráv určuje požadovanou instanci.</span><span class="sxs-lookup"><span data-stu-id="75068-158">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="75068-159">Korelace na základě obsahu používá tato data ve zprávě, jako je číslo nebo pořadí ID zákazníka, pro směrování zpráv do instance pracovního postupu správné.</span><span class="sxs-lookup"><span data-stu-id="75068-159">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="75068-160">Tato část popisuje několik běžných problémů, které mohou nastat při používání korelace na základě obsahu.</span><span class="sxs-lookup"><span data-stu-id="75068-160">This section describes several common issues that may occur when using content-based correlation.</span></span>

### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="75068-161">Ujistěte se, že je jedinečné identifikační údaje</span><span class="sxs-lookup"><span data-stu-id="75068-161">Ensure the Identifying Data Is Unique</span></span>
 <span data-ttu-id="75068-162">Data, která se používá k identifikaci instance se po zahašování použije na klíč korelace.</span><span class="sxs-lookup"><span data-stu-id="75068-162">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="75068-163">Chcete-li zaručit, že data, která slouží pro korelaci je jedinečný, jinak může dojít a způsobit zpráv se nesprávně směrovanými kolizí v klíči hash musí věnovat pozornost.</span><span class="sxs-lookup"><span data-stu-id="75068-163">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="75068-164">Například korelace založen pouze na název zákazníka může způsobit ke kolizi, protože může být více zákazníků, kteří mají stejný název.</span><span class="sxs-lookup"><span data-stu-id="75068-164">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="75068-165">Dvojtečka (:) by neměl používá jako součást data, která slouží ke sladění zprávy, protože se už používá pro vymezení klíč a hodnotu, která tvoří řetězec, který se následně mají hodnotu hash dotazu zprávu.</span><span class="sxs-lookup"><span data-stu-id="75068-165">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="75068-166">Pokud trvalost, se používá, ujistěte se, že aktuální identifikační data nebyla použita dříve drženého instancí.</span><span class="sxs-lookup"><span data-stu-id="75068-166">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="75068-167">Dočasně zakážete trvalost může pomoci identifikovat problém.</span><span class="sxs-lookup"><span data-stu-id="75068-167">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="75068-168">Trasování WCF slouží k zobrazení počítané korelace klíč a je užitečné pro ladění tento druh problému.</span><span class="sxs-lookup"><span data-stu-id="75068-168">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>

### <a name="race-conditions"></a><span data-ttu-id="75068-169">Konflikty časování</span><span class="sxs-lookup"><span data-stu-id="75068-169">Race Conditions</span></span>
 <span data-ttu-id="75068-170">Existuje malé mezera v době mezi službu přijetí zprávy a korelace ve skutečnosti inicializovaný, během které zpracování zprávy budou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="75068-170">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="75068-171">Pokud služby pracovního postupu inicializuje korelaci založené na obsahu s využitím dat předávaných od klienta přes jednocestnou operaci a odesílá okamžité zpracování zpráv, ignorují se tyto zprávy během tohoto intervalu.</span><span class="sxs-lookup"><span data-stu-id="75068-171">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="75068-172">Toho se lze vyvarovat pomocí obousměrné operace inicializace korelace, nebo pomocí <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="75068-172">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>

### <a name="correlation-query-issues"></a><span data-ttu-id="75068-173">Korelace dotazů problémy</span><span class="sxs-lookup"><span data-stu-id="75068-173">Correlation Query Issues</span></span>
 <span data-ttu-id="75068-174">Korelace dotazů se používají k určení, jaká data ve zprávě se používá ke korelaci zprávy.</span><span class="sxs-lookup"><span data-stu-id="75068-174">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="75068-175">Tato data je určen pomocí dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="75068-175">This data is specified by using an XPath query.</span></span> <span data-ttu-id="75068-176">Pokud zprávy do služby nejsou distribuovanou i v případě, že všechno, co se zobrazí správný, je jednou z možných strategií pro řešení potíží s zadat hodnotu literálu, který se shoduje s hodnotou data zprávy místo dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="75068-176">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="75068-177">Pokud chcete zadat hodnotu literálu, použijte `string` funkce.</span><span class="sxs-lookup"><span data-stu-id="75068-177">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="75068-178">V následujícím příkladu <xref:System.ServiceModel.MessageQuerySet> je nakonfigurován na použití hodnota literálu `11445` pro `OrderId` a dotaz XPath je označené jako komentář.</span><span class="sxs-lookup"><span data-stu-id="75068-178">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>

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

 <span data-ttu-id="75068-179">Pokud se dotaz XPath je správně nakonfigurovaná tak, že nebudou načtena žádná data pro korelace, vrátí se chyba s následující zprávou: "korelační dotaz vrátil prázdnou sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="75068-179">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="75068-180">Ujistěte se, že jsou správně nakonfigurované korelačních dotazů pro koncový bod."</span><span class="sxs-lookup"><span data-stu-id="75068-180">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="75068-181">Jeden rychlý způsob, jak toto řešení je dotaz XPath nahraďte hodnotu literálu jak je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="75068-181">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="75068-182">Tomuto problému může dojít, pokud pomocí Tvůrce dotazů XPath v **přidat inicializátory korelace** nebo **definice vlastnosti CorrelatesOn** dialogová okna a služba pracovního postupu používá zprávy smlouvy.</span><span class="sxs-lookup"><span data-stu-id="75068-182">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="75068-183">V následujícím příkladu je definován třídou kontraktu zprávy.</span><span class="sxs-lookup"><span data-stu-id="75068-183">In the following example, a message contract class is defined.</span></span>

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

 <span data-ttu-id="75068-184">Používá tento kontrakt zprávy <xref:System.ServiceModel.Activities.Receive> aktivity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="75068-184">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="75068-185">`CartId` v záhlaví zprávy slouží ke sladění zpráva, která má správné instanci.</span><span class="sxs-lookup"><span data-stu-id="75068-185">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="75068-186">Pokud dotaz XPath, který načte `CartId` je vytvořený pomocí dialogových oken korelace v Návrháři postupu provádění následujících nesprávnou XPath dotaz.</span><span class="sxs-lookup"><span data-stu-id="75068-186">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 <span data-ttu-id="75068-187">Tento dotaz XPath by byly správné Pokud <xref:System.ServiceModel.Activities.Receive> aktivita používá parametry pro data, ale protože ho používá zprávy smlouvy je nesprávný.</span><span class="sxs-lookup"><span data-stu-id="75068-187">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="75068-188">Následující dotaz XPath je správný výraz XPath dotaz pro načtení `CartId` z hlavičky.</span><span class="sxs-lookup"><span data-stu-id="75068-188">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>

```
sm:header()/tempuri:CartId
```

<span data-ttu-id="75068-189">To můžete potvrdit prozkoumáním tělo zprávy.</span><span class="sxs-lookup"><span data-stu-id="75068-189">This can be confirmed by examining the body of the message.</span></span>

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

<span data-ttu-id="75068-190">Následující příklad ukazuje <xref:System.ServiceModel.Activities.Receive> aktivity, které jsou nakonfigurované pro `AddItem` operaci, která používá předchozí kontraktu zprávy přijímat data.</span><span class="sxs-lookup"><span data-stu-id="75068-190">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="75068-191">Dotaz XPath je správně nakonfigurován.</span><span class="sxs-lookup"><span data-stu-id="75068-191">The XPath query is correctly configured.</span></span>

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
