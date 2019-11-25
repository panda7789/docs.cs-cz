---
title: Řešení potíží – korelace
ms.date: 03/30/2017
ms.assetid: 98003875-233d-4512-a688-4b2a1b0b5371
ms.openlocfilehash: be48a55a87d199829de4038e7e2a7642c102acf2
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976022"
---
# <a name="troubleshooting-correlation"></a><span data-ttu-id="8dcdc-102">Řešení potíží – korelace</span><span class="sxs-lookup"><span data-stu-id="8dcdc-102">Troubleshooting Correlation</span></span>
<span data-ttu-id="8dcdc-103">Korelace se používá ke vzájemnému propojení zpráv služby pracovních postupů a ke správné instanci pracovního postupu, ale pokud není správně nakonfigurovaná, zprávy se neobdrží a aplikace nebudou fungovat správně.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-103">Correlation is used to relate workflow service messages to each other and to the correct workflow instance, but if it is not configured correctly, messages will not be received and applications will not work correctly.</span></span> <span data-ttu-id="8dcdc-104">V tomto tématu najdete přehled několika metod pro řešení problémů s korelací a také uvádí některé běžné problémy, které mohou nastat při použití korelace.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-104">This topic provides an overview of several methods for troubleshooting correlation issues, and also lists some common issues that can occur when you use correlation.</span></span>

## <a name="handle-the-unknownmessagereceived-event"></a><span data-ttu-id="8dcdc-105">Zpracování události UnknownMessageReceived</span><span class="sxs-lookup"><span data-stu-id="8dcdc-105">Handle the UnknownMessageReceived Event</span></span>
 <span data-ttu-id="8dcdc-106">K události <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> dojde, když služba obdrží neznámou zprávu, včetně zpráv, které nelze korelovat s existující instancí.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-106">The <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> event occurs when an unknown message is received by a service, including messages that cannot be correlated to an existing instance.</span></span> <span data-ttu-id="8dcdc-107">V případě samoobslužných služeb je možné tuto událost zpracovat v hostitelské aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-107">For self-hosted services, this event can be handled in the host application.</span></span>

```csharp
host.UnknownMessageReceived += delegate(object sender, UnknownMessageReceivedEventArgs e)
{
    Console.WriteLine("Unknown Message Received:");
    Console.WriteLine(e.Message);
};
```

 <span data-ttu-id="8dcdc-108">U služeb hostovaných na webu lze tuto událost zpracovat odvozením třídy z <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> a přepsáním <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-108">For Web-hosted services, this event can be handled by deriving a class from <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> and overriding <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory.CreateWorkflowServiceHost%2A>.</span></span>

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

 <span data-ttu-id="8dcdc-109">Tento vlastní <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> pak můžete zadat v souboru `svc` pro službu.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-109">This custom <xref:System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory> can then be specified in the `svc` file for the service.</span></span>

`<% @ServiceHost Language="C#" Service="OrderServiceWorkflow" Factory="CustomFactory" %>`

 <span data-ttu-id="8dcdc-110">Při vyvolání této obslužné rutiny lze zprávu načíst pomocí vlastnosti <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>a bude vypadat podobně jako následující zpráva.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-110">When this handler is invoked, the message can be retrieved by using the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs.Message%2A> property of the <xref:System.ServiceModel.UnknownMessageReceivedEventArgs>, and will resemble the following message.</span></span>

```xml
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

 <span data-ttu-id="8dcdc-111">Kontrola zpráv odeslaných do obslužné rutiny <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> může poskytnout přípravné informace o tom, proč se zpráva nekoreluje s instancí služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-111">Inspecting messages dispatched to the <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived> handler may provide clues about why the message did not correlate to an instance of the workflow service.</span></span>

## <a name="use-tracking-to-monitor-the-progress-of-the-workflow"></a><span data-ttu-id="8dcdc-112">Sledování průběhu pracovního postupu pomocí sledování</span><span class="sxs-lookup"><span data-stu-id="8dcdc-112">Use Tracking to Monitor the Progress of the Workflow</span></span>
 <span data-ttu-id="8dcdc-113">Sledování poskytuje způsob, jak monitorovat průběh pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-113">Tracking provides a way to monitor the progress of a workflow.</span></span> <span data-ttu-id="8dcdc-114">Ve výchozím nastavení jsou záznamy sledování vydávány pro události životního cyklu pracovního cyklu, události životního cyklu aktivity, šíření chyb a opětovné pokračování záložek.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-114">By default, tracking records are emitted for workflow life-cycle events, activity life-cycle events, fault propagation, and bookmark resumption.</span></span> <span data-ttu-id="8dcdc-115">Vlastní záznamy sledování je navíc možné vysílat vlastními aktivitami.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-115">Additionally, custom tracking records can be emitted by custom activities.</span></span> <span data-ttu-id="8dcdc-116">Při řešení potíží s korelacemi, záznamy sledování aktivity, pokračování záznamů a záznamy o šíření chyb jsou nejužitečnější.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-116">When troubleshooting correlation, the activity tracking records, the bookmark resumption records, and the fault propagation records are the most useful.</span></span> <span data-ttu-id="8dcdc-117">Záznamy sledování aktivit se dají použít k určení aktuálního průběhu pracovního postupu a můžou vám pomůžou určit, které aktivity zasílání zpráv aktuálně čekají na zprávy.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-117">The activity tracking records can be used to determine the current progress of the workflow and can help identify which messaging activity is currently waiting for messages.</span></span> <span data-ttu-id="8dcdc-118">Záznamy pokračování v záložek jsou užitečné, protože označují, že pracovní postup přijal zprávu, a záznamy o šíření chyb poskytují záznam všech chyb v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-118">Bookmark resumption records are useful because they indicate that a message was received by the workflow, and fault propagation records provide a record of any faults in the workflow.</span></span> <span data-ttu-id="8dcdc-119">Chcete-li povolit sledování, zadejte požadované <xref:System.Activities.Tracking.TrackingParticipant> v <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-119">To enable tracking, specify the desired <xref:System.Activities.Tracking.TrackingParticipant> in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.WorkflowExtensions%2A> of the <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="8dcdc-120">V následujícím příkladu je `ConsoleTrackingParticipant` (z [vlastní ukázky sledování](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) ) nakonfigurovaná pomocí výchozího profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-120">In the following example, the `ConsoleTrackingParticipant` (from the [Custom Tracking](../../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample) is configured by using the default tracking profile.</span></span>

```csharp
host.WorkflowExtensions.Add(new ConsoleTrackingParticipant());
```

 <span data-ttu-id="8dcdc-121">Sledování účastníka, jako je ConsoleTrackingParticipant, je užitečné pro samoobslužné služby pracovních postupů, které mají okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-121">A tracking participant such as the ConsoleTrackingParticipant is useful for self-hosted workflow services that have a console window.</span></span> <span data-ttu-id="8dcdc-122">V případě služby hostované na webu by se měla použít sledování účastníka, který zaznamenává informace o sledování do trvalého úložiště, jako je například integrovaná <xref:System.Activities.Tracking.EtwTrackingParticipant>, nebo vlastní účastník sledování, který zaznamená informace do souboru.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-122">For a Web-hosted service, a tracking participant that logs the tracking information to a durable store should be used, such as the built-in <xref:System.Activities.Tracking.EtwTrackingParticipant>, or a custom tracking participant that logs the information to a file.</span></span>

 <span data-ttu-id="8dcdc-123">Další informace o sledování a konfiguraci sledování pro službu pracovního postupu hostované na webu najdete v tématech [sledování a trasování pracovních postupů](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Konfigurace sledování pracovního postupu](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)a ukázky ukázek [ &#91;WF&#93; ](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) .</span><span class="sxs-lookup"><span data-stu-id="8dcdc-123">For more information about tracking and configuring tracking for a Web-hosted workflow service, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md), [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md), and the [Tracking &#91;WF Samples&#93;](../../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>

## <a name="use-wcf-tracing"></a><span data-ttu-id="8dcdc-124">Použití trasování WCF</span><span class="sxs-lookup"><span data-stu-id="8dcdc-124">Use WCF Tracing</span></span>
 <span data-ttu-id="8dcdc-125">Trasování WCF poskytuje trasování toku zpráv do a ze služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-125">WCF tracing provides tracing of the flow of messages to and from a workflow service.</span></span> <span data-ttu-id="8dcdc-126">Tyto trasovací informace jsou užitečné při řešení problémů korelace, zejména u korelace na základě obsahu.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-126">This tracing information is useful when troubleshooting correlation issues, especially for content-based correlation.</span></span> <span data-ttu-id="8dcdc-127">Chcete-li povolit trasování, zadejte požadované naslouchací procesy trasování v části `system.diagnostics` souboru `web.config`, pokud je služba pracovního postupu hostitelem webu nebo `app.config` soubor, pokud je služba pracovního postupu v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-127">To enable tracing, specify the desired trace listeners in the `system.diagnostics` section of the `web.config` file if the workflow service is Web-hosted, or the `app.config` file if the workflow service is self-hosted.</span></span> <span data-ttu-id="8dcdc-128">Chcete-li zahrnout obsah zpráv do trasovacího souboru, zadejte `true` pro `logEntireMessage` v prvku `messageLogging` v části `diagnostics` `system.serviceModel`.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-128">To include the contents of the messages in the trace file, specify `true` for `logEntireMessage` in the `messageLogging` element in the `diagnostics` section of `system.serviceModel`.</span></span> <span data-ttu-id="8dcdc-129">V následujícím příkladu jsou informace o trasování, včetně obsahu zpráv, nakonfigurované tak, aby se zapsaly do souboru s názvem `service.svclog`.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-129">In the following example, tracing information, including the content of the messages, is configured to be written to a file that is named `service.svclog`.</span></span>

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

 <span data-ttu-id="8dcdc-130">Chcete-li zobrazit informace o trasování, které jsou obsaženy v `service.svclog`, je použit [Nástroj Prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="8dcdc-130">To view the trace information that is contained in `service.svclog`, the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) is used.</span></span> <span data-ttu-id="8dcdc-131">To je užitečné hlavně při řešení problémů korelace na základě obsahu, protože můžete zobrazit obsah zprávy a přesně zjistit, co se předává, a zda odpovídá <xref:System.ServiceModel.CorrelationQuery> pro korelaci na základě obsahu.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-131">This is especially useful when troubleshooting content-based correlation issues because you can view the message contents and see exactly what is being passed, and whether it matches the <xref:System.ServiceModel.CorrelationQuery> for the content-based correlation.</span></span> <span data-ttu-id="8dcdc-132">Další informace o trasování WCF naleznete v tématu [Nástroj pro prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)a [používání trasování pro řešení potíží s aplikací](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="8dcdc-132">For more information about WCF tracing, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md), and [Using Tracing to Troubleshoot Your Application](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="common-context-exchange-correlation-issues"></a><span data-ttu-id="8dcdc-133">Problémy s korelací běžných kontextových Exchange</span><span class="sxs-lookup"><span data-stu-id="8dcdc-133">Common Context Exchange Correlation Issues</span></span>
 <span data-ttu-id="8dcdc-134">Určité typy korelace vyžadují, aby se při správné práci korelace použil konkrétní typ vazby.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-134">Certain types of correlation require that a specific type of binding is used for the correlation to work correctly.</span></span> <span data-ttu-id="8dcdc-135">Mezi příklady patří korelace požadavku a odpovědi, která vyžaduje obousměrnou vazbu, jako je <xref:System.ServiceModel.BasicHttpBinding>, a korelaci kontextu Exchange, která vyžaduje kontextovou vazbu, jako je například <xref:System.ServiceModel.BasicHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-135">Examples include request-reply correlation, which requires a two-way binding such as <xref:System.ServiceModel.BasicHttpBinding>, and context exchange correlation, which requires a context-based binding such as <xref:System.ServiceModel.BasicHttpContextBinding>.</span></span> <span data-ttu-id="8dcdc-136">Většina vazeb podporuje obousměrné operace, takže se nejedná o běžný problém korelace požadavek-odpověď, ale pouze několik kontextových vazeb, včetně <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>a <xref:System.ServiceModel.NetTcpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-136">Most bindings support two-way operations so this is not a common issue for request-reply correlation, but there are only a handful of context-based bindings including <xref:System.ServiceModel.BasicHttpContextBinding>, <xref:System.ServiceModel.WSHttpContextBinding>, and <xref:System.ServiceModel.NetTcpContextBinding>.</span></span> <span data-ttu-id="8dcdc-137">Pokud se jedna z těchto vazeb nepoužívá, bude počáteční volání služby pracovního postupu úspěšné, ale následující <xref:System.ServiceModel.FaultException>volání selžou.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-137">If one of these bindings is not used, the initial call to a workflow service will succeed, but subsequent calls will fail with the following <xref:System.ServiceModel.FaultException>.</span></span>

```output
There is no context attached to the incoming message for the service
and the current operation is not marked with "CanCreateInstance = true".
In order to communicate with this service check whether the incoming binding
supports the context protocol and has a valid context initialized.
```

 <span data-ttu-id="8dcdc-138">Kontextové informace, které se používají pro korelaci kontextu, mohou být vráceny <xref:System.ServiceModel.Activities.SendReply> do <xref:System.ServiceModel.Activities.Receive> aktivity, která inicializuje korelaci kontextu při použití obousměrné operace, nebo může být zadána volajícím v případě, že operace je jednosměrná.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-138">The context information that is used for context correlation can be returned by the <xref:System.ServiceModel.Activities.SendReply> to the <xref:System.ServiceModel.Activities.Receive> activity that initializes the context correlation when using a two-way operation, or it can be specified by the caller if the operation is one-way.</span></span> <span data-ttu-id="8dcdc-139">Pokud kontext není odesílán volajícím nebo vráceným službou pracovního postupu, bude po vyvolání následné operace vrácen stejný <xref:System.ServiceModel.FaultException> popsaný výše.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-139">If the context is not sent by the caller or returned by the workflow service, then the same <xref:System.ServiceModel.FaultException> described previously will be returned when a subsequent operation is invoked.</span></span>

## <a name="common-request-reply-correlation-issues"></a><span data-ttu-id="8dcdc-140">Běžné problémy s korelacemi požadavků a odpovědí</span><span class="sxs-lookup"><span data-stu-id="8dcdc-140">Common Request-Reply Correlation Issues</span></span>
 <span data-ttu-id="8dcdc-141">Korelace požadavku a odpovědi se používá s <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> páry k implementaci obousměrné operace ve službě pracovních postupů a s dvojicí <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply>, která vyvolává obousměrnou operaci v jiné webové službě.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-141">Request-reply correlation is used with a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair to implement a two-way operation in a workflow service and with a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair that invokes a two-way operation in another Web service.</span></span> <span data-ttu-id="8dcdc-142">Při volání obousměrné operace ve službě WCF může být služba buď tradiční imperativní služba WCF založená na kódu, nebo může být služba pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-142">When invoking a two-way operation in a WCF service, the service can be either a traditional imperative code-based WCF service or it can be a workflow service.</span></span> <span data-ttu-id="8dcdc-143">Pro použití korelace požadavku a odpovědi musí být použita Obousměrná vazba, například <xref:System.ServiceModel.BasicHttpBinding>, a operace musí být obousměrné.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-143">To use request-reply correlation a two-way binding must be used, such as <xref:System.ServiceModel.BasicHttpBinding>, and the operations must be two-way.</span></span>

 <span data-ttu-id="8dcdc-144">Pokud má služba pracovních postupů obousměrné operace paralelně nebo překrývající <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> nebo <xref:System.ServiceModel.Activities.Send>páry /<xref:System.ServiceModel.Activities.ReceiveReply>, pak implicitní Správa korelace, kterou poskytuje <xref:System.ServiceModel.Activities.WorkflowServiceHost>, nemusí být dostačující, zejména ve scénářích s vysokým důrazem a zprávy nemusí být správně směrovány.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-144">If the workflow service has two-way operations in parallel, or overlapping <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> or <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pairs, then the implicit correlation handle management provided by <xref:System.ServiceModel.Activities.WorkflowServiceHost> may not be sufficient, especially in high-stress scenarios, and messages may not be correctly routed.</span></span> <span data-ttu-id="8dcdc-145">Chcete-li zabránit tomu, aby k tomuto problému došlo, doporučujeme při použití korelace požadavek-odpověď vždy zadat <xref:System.ServiceModel.Activities.CorrelationHandle>.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-145">To prevent this issue from occurring, we recommend that you always explicitly specify a <xref:System.ServiceModel.Activities.CorrelationHandle> when using request-reply correlation.</span></span> <span data-ttu-id="8dcdc-146">Při použití šablon **SendAndReceiveReply** a **ReceiveAndSendReply** z části zasílání zpráv v sadě **nástrojů** návrháře pracovních postupů je <xref:System.ServiceModel.Activities.CorrelationHandle> ve výchozím nastavení explicitně nakonfigurován.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-146">When using the **SendAndReceiveReply** and **ReceiveAndSendReply** templates from the Messaging section of the **Toolbox** in the workflow designer, a <xref:System.ServiceModel.Activities.CorrelationHandle> is explicitly configured by default.</span></span> <span data-ttu-id="8dcdc-147">Při sestavování pracovního postupu pomocí kódu je <xref:System.ServiceModel.Activities.CorrelationHandle> určena v <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> první aktivity ve dvojici.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-147">When building a workflow by using code, the <xref:System.ServiceModel.Activities.CorrelationHandle> is specified in the <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> of the first activity in the pair.</span></span> <span data-ttu-id="8dcdc-148">V následujícím příkladu je <xref:System.ServiceModel.Activities.Receive> aktivita nakonfigurovaná s explicitní <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> zadanou v <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-148">In the following example, a <xref:System.ServiceModel.Activities.Receive> activity is configured with an explicit <xref:System.ServiceModel.Activities.CorrelationInitializer.CorrelationHandle%2A> specified in the <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.</span></span>

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

 <span data-ttu-id="8dcdc-149">Trvalost není povolená mezi <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> páry nebo dvojice <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply>.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-149">Persistence is not permitted between a <xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply> pair or a <xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply> pair.</span></span> <span data-ttu-id="8dcdc-150">Vytvoří se zóna bez trvalého uložení, která trvá až do dokončení obou aktivit.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-150">A no-persist zone is created that lasts until both activities have completed.</span></span> <span data-ttu-id="8dcdc-151">Pokud je aktivita, například aktivita zpoždění, v této zóně No-retrvalá a způsobí, že pracovní postup přestane být činný, pracovní postup zůstane neuložený ani v případě, že je hostitel nakonfigurovaný tak, aby zachoval pracovní postupy, když se stanou nečinné.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-151">If an activity, such as a delay activity, is in this no-persist zone and causes the workflow to become idle, the workflow will not persist even if it the host is configured to persist workflows when they become idle.</span></span> <span data-ttu-id="8dcdc-152">Pokud se aktivita, jako je trvalá aktivita, pokusí explicitně uchovat v zóně bez trvalého uložení, je vyvolána závažná výjimka, pracovní postup se přeruší a <xref:System.ServiceModel.FaultException> se vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-152">If an activity, such as a persist activity, attempts to explicitly persist in the no-persist zone, a fatal exception is thrown, the workflow aborts, and a <xref:System.ServiceModel.FaultException> is returned to the caller.</span></span> <span data-ttu-id="8dcdc-153">Zpráva o závažných výjimkách je "System. InvalidOperationException: trvalé aktivity nelze zahrnout do bloků trvalého uložení".</span><span class="sxs-lookup"><span data-stu-id="8dcdc-153">The fatal exception message is "System.InvalidOperationException: Persist activities cannot be contained within no persistence blocks.".</span></span> <span data-ttu-id="8dcdc-154">Tato výjimka se nevrátí volajícímu, ale může být pozorována v případě, že je povoleno sledování.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-154">This exception is not returned to the caller but can be observed if tracking is enabled.</span></span> <span data-ttu-id="8dcdc-155">Zpráva pro <xref:System.ServiceModel.FaultException> vrácena volajícímu je "operace nemohla být provedena, protože instance WorkflowInstance" 5836145b-7da2-49d0-A052-a49162adeab6 "byla dokončena".</span><span class="sxs-lookup"><span data-stu-id="8dcdc-155">The message for the <xref:System.ServiceModel.FaultException> returned to the caller is "The operation could not be performed because WorkflowInstance '5836145b-7da2-49d0-a052-a49162adeab6' has completed".</span></span>

 <span data-ttu-id="8dcdc-156">Další informace o korelaci požadavků a odpovědí najdete v tématu [požadavek-odpověď](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span><span class="sxs-lookup"><span data-stu-id="8dcdc-156">For more information about request-reply correlation, see [Request-Reply](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md).</span></span>

## <a name="common-content-correlation-issues"></a><span data-ttu-id="8dcdc-157">Běžné problémy korelace obsahu</span><span class="sxs-lookup"><span data-stu-id="8dcdc-157">Common Content Correlation Issues</span></span>
 <span data-ttu-id="8dcdc-158">Korelace na základě obsahu se používá v případě, že služba pracovního postupu přijímá více zpráv a část dat vyměňovaných zpráv identifikuje požadovanou instanci.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-158">Content-based correlation is used when a workflow service receives multiple messages and a piece of data in the exchanged messages identifies the desired instance.</span></span> <span data-ttu-id="8dcdc-159">Korelace na základě obsahu používá tato data ve zprávě, jako je číslo zákazníka nebo ID objednávky, ke směrování zpráv do správné instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-159">Content-based correlation uses this data in the message, such as a customer number or order ID, to route messages to the correct workflow instance.</span></span> <span data-ttu-id="8dcdc-160">Tato část popisuje několik běžných problémů, ke kterým může dojít při použití korelace na základě obsahu.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-160">This section describes several common issues that may occur when using content-based correlation.</span></span>

### <a name="ensure-the-identifying-data-is-unique"></a><span data-ttu-id="8dcdc-161">Ujistěte se, že identifikační data jsou jedinečná.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-161">Ensure the Identifying Data Is Unique</span></span>
 <span data-ttu-id="8dcdc-162">Data, která se používají k identifikaci instance, se zahashují do korelačního klíče.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-162">The data that is used to identify the instance is hashed into a correlation key.</span></span> <span data-ttu-id="8dcdc-163">Je nutné dbát na to, aby se data, která se používají pro korelace, mohla zajímat, nebo dojde k kolizi v klíči s hodnotou hash, která může vyskytnout chyby, a způsobit nesměrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-163">Care must be taken to guarantee that the data that is used for correlation is unique or else collisions in the hashed key might occur and cause messages to be misrouted.</span></span> <span data-ttu-id="8dcdc-164">Korelace založená jenom na názvu zákazníka může například způsobit kolizi, protože může existovat více zákazníků se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-164">For example, a correlation based only on a customer name may cause a collision because there may be multiple customers who have the same name.</span></span> <span data-ttu-id="8dcdc-165">Dvojtečka (:) neměl by být použit jako součást dat, která se používají ke korelaci zprávy, protože je již použita k vymezení klíče a hodnoty dotazu zprávy pro vytvoření řetězce, který je následně hash.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-165">The colon (:) should not be used as part of the data that is used to correlate the message because it is already used to delimit the message query’s key and value to form the string that is subsequently hashed.</span></span> <span data-ttu-id="8dcdc-166">Pokud se používá trvalost, ujistěte se, že aktuální identifikační data nebyla využívána dříve trvalou instancí.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-166">If persistence is being used, make sure that the current identifying data has not been used by a previously persisted instance.</span></span> <span data-ttu-id="8dcdc-167">Dočasné zakázání trvalého blokování může přispět k identifikaci tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-167">Temporarily disabling persistence can help identify this issue.</span></span> <span data-ttu-id="8dcdc-168">Trasování WCF lze použít k zobrazení počítaného korelačního klíče a je užitečné pro ladění tohoto typu problému.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-168">WCF tracing can be used to view the calculated correlation key and is useful for debugging this kind of issue.</span></span>

### <a name="race-conditions"></a><span data-ttu-id="8dcdc-169">Konflikty časování</span><span class="sxs-lookup"><span data-stu-id="8dcdc-169">Race Conditions</span></span>
 <span data-ttu-id="8dcdc-170">Mezi službou, která přijímá zprávu, existuje malá mezera a v rámci které se v současnosti inicializuje korelace, během které budou následné zprávy ignorovány.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-170">There is a small gap in time between the service receiving a message and the correlation actually being initialized, during which follow-up messages will be ignored.</span></span> <span data-ttu-id="8dcdc-171">Pokud služba pracovního postupu inicializuje korelaci založenou na obsahu pomocí dat předávaných z klienta přes jednosměrnou operaci a volající odesílá okamžité následné zprávy, budou tyto zprávy během tohoto intervalu ignorovány.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-171">If a workflow service initializes the content-based correlation by using data passed from the client over a one-way operation, and the caller sends immediate follow-up messages, these messages will be ignored during this interval.</span></span> <span data-ttu-id="8dcdc-172">K tomu je možné se vyhnout pomocí oboustranné operace pro inicializaci korelace nebo pomocí <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-172">This can be avoided by using a two-way operation to initialize the correlation, or by using a <xref:System.ServiceModel.Activities.TransactedReceiveScope>.</span></span>

### <a name="correlation-query-issues"></a><span data-ttu-id="8dcdc-173">Problémy s dotazem korelace</span><span class="sxs-lookup"><span data-stu-id="8dcdc-173">Correlation Query Issues</span></span>
 <span data-ttu-id="8dcdc-174">Korelační dotazy se používají k určení toho, jaká data se ve zprávě mají použít ke korelaci zprávy.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-174">Correlation queries are used to specify what data in a message is used to correlate the message.</span></span> <span data-ttu-id="8dcdc-175">Tato data se zadává pomocí dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-175">This data is specified by using an XPath query.</span></span> <span data-ttu-id="8dcdc-176">Pokud zprávy ke službě nejsou odesílány, i když vše vypadá jako správné, jedna strategie pro řešení potíží je zadat hodnotu literálu, která odpovídá hodnotě dat zprávy namísto dotazu XPath.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-176">If messages to a service are not being dispatched even though everything appears to be correct, one strategy for troubleshooting is to specify a literal value that matches the value of the message data instead of an XPath query.</span></span> <span data-ttu-id="8dcdc-177">Chcete-li zadat hodnotu literálu, použijte funkci `string`.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-177">To specify a literal value, use the `string` function.</span></span> <span data-ttu-id="8dcdc-178">V následujícím příkladu je <xref:System.ServiceModel.MessageQuerySet> nakonfigurována pro použití literálové hodnoty `11445` pro `OrderId` a dotaz XPath je zakomentován.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-178">In the following example, a <xref:System.ServiceModel.MessageQuerySet> is configured to use a literal value of `11445` for the `OrderId` and the XPath query is commented out.</span></span>

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

 <span data-ttu-id="8dcdc-179">Pokud je dotaz XPath nesprávně nakonfigurovaný tak, že nejsou načtená žádná korelační data, vrátí se chybová zpráva s následující zprávou: "korelační dotaz vrátil prázdnou sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-179">If an XPath query is configured incorrectly such that no correlation data is retrieved, a fault is returned with the following message: "A correlation query yielded an empty result set.</span></span> <span data-ttu-id="8dcdc-180">Ujistěte se prosím, že korelační dotazy pro koncový bod jsou správně nakonfigurované.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-180">Please ensure correlation queries for the endpoint are correctly configured."</span></span> <span data-ttu-id="8dcdc-181">Jedním z rychlých způsobů, jak tento problém vyřešit, je nahradit dotaz XPath hodnotou literálu, jak je popsáno v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-181">One quick way to troubleshoot this is to replace the XPath query with a literal value as described in the previous section.</span></span> <span data-ttu-id="8dcdc-182">K tomuto problému může dojít, pokud použijete Tvůrce dotazů XPath v dialogových oknech **Přidat Inicializátory korelace** nebo **definice vlastnosti CorrelatesOn** a vaše služba pracovního postupu používá kontrakty zpráv.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-182">This issue can occur if you use the XPath query builder in the **Add Correlation Initializers** or **CorrelatesOn Definition** dialog boxes and your workflow service uses message contracts.</span></span> <span data-ttu-id="8dcdc-183">V následujícím příkladu je definována třída kontraktu zpráv.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-183">In the following example, a message contract class is defined.</span></span>

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

 <span data-ttu-id="8dcdc-184">Tento kontrakt zprávy používá aktivita <xref:System.ServiceModel.Activities.Receive> v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-184">This message contract is used by a <xref:System.ServiceModel.Activities.Receive> activity in a workflow.</span></span> <span data-ttu-id="8dcdc-185">`CartId` v hlavičce zprávy se používá ke korelaci zprávy se správnou instancí.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-185">The `CartId` in the header of the message is used to correlate the message to the correct instance.</span></span> <span data-ttu-id="8dcdc-186">Pokud se dotaz XPath, který načítá `CartId`, vytvoří pomocí dialogových oken korelace v Návrháři pracovních postupů, vygeneruje se následující nesprávný dotaz XPath.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-186">If the XPath query that retrieves the `CartId` is created using the correlation dialogs in the workflow designer, the following incorrect XPath query is generated.</span></span>

```
sm:body()/xg0:AddItemMessage/xg0:CartId
```

 <span data-ttu-id="8dcdc-187">Tento dotaz XPath by byl správný, pokud <xref:System.ServiceModel.Activities.Receive> aktivita použila parametry pro data, ale vzhledem k tomu, že používá kontrakt zprávy, není správný.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-187">This XPath query would be correct if the <xref:System.ServiceModel.Activities.Receive> activity used parameters for the data, but since it is using a message contract it is incorrect.</span></span> <span data-ttu-id="8dcdc-188">Následující dotaz XPath je správný dotaz XPath pro načtení `CartId` z hlavičky.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-188">The following XPath query is the correct XPath query to retrieve the `CartId` from the header.</span></span>

```
sm:header()/tempuri:CartId
```

<span data-ttu-id="8dcdc-189">To lze potvrdit kontrolou textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-189">This can be confirmed by examining the body of the message.</span></span>

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

<span data-ttu-id="8dcdc-190">Následující příklad ukazuje aktivitu <xref:System.ServiceModel.Activities.Receive> nakonfigurovanou pro operaci `AddItem`, která používá předchozí kontrakt zprávy pro příjem dat.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-190">The following example shows a <xref:System.ServiceModel.Activities.Receive> activity configured for an `AddItem` operation that uses the previous message contract to receive data.</span></span> <span data-ttu-id="8dcdc-191">Dotaz XPath je správně nakonfigurován.</span><span class="sxs-lookup"><span data-stu-id="8dcdc-191">The XPath query is correctly configured.</span></span>

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
