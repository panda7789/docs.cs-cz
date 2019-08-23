---
title: Prohlížení protokolů zpráv
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: c926833a48331f191b6dcc3323f0dfda329b7014
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968673"
---
# <a name="viewing-message-logs"></a><span data-ttu-id="ed531-102">Prohlížení protokolů zpráv</span><span class="sxs-lookup"><span data-stu-id="ed531-102">Viewing Message Logs</span></span>
<span data-ttu-id="ed531-103">Toto téma popisuje, jak můžete zobrazit protokoly zpráv.</span><span class="sxs-lookup"><span data-stu-id="ed531-103">This topic describes how you can view message logs.</span></span>  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a><span data-ttu-id="ed531-104">Zobrazení protokolů zpráv v prohlížeči trasování služby</span><span class="sxs-lookup"><span data-stu-id="ed531-104">Viewing Message Logs in the Service Trace Viewer</span></span>  
 <span data-ttu-id="ed531-105">Zpráva bude transformovaná tak, jak je zpracována službou WCF.</span><span class="sxs-lookup"><span data-stu-id="ed531-105">A message will be transformed as it is processed by WCF.</span></span> <span data-ttu-id="ed531-106">Proto se zaprotokolovaná zpráva odrážejí pouze obsah zprávy v okamžiku, kdy byl protokol, nikoli obsah na drátě.</span><span class="sxs-lookup"><span data-stu-id="ed531-106">Therefore, a message being logged reflects only the message's content at the point it was logged, not the content on the wire.</span></span>  
  
 <span data-ttu-id="ed531-107">Vzhledem k tomu, že výstup protokolování zpráv nemá žádný vztah k formátu přenosu zprávy, bude protokolování zpráv vždy výstupem dekódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="ed531-107">Since the output of message logging has no relationship to the transfer format of the message, message logging always outputs the decoded message.</span></span> <span data-ttu-id="ed531-108">Pokud jste správně nakonfigurovali protokolování zpráv, všechny protokolované zprávy by měly být v prostém textu.</span><span class="sxs-lookup"><span data-stu-id="ed531-108">If you have configured message logging properly, any logged message should be in plain text.</span></span> <span data-ttu-id="ed531-109">Například formát (prostý text) protokolovaných zpráv není ovlivněn využitím binárního kodéru zpráv.</span><span class="sxs-lookup"><span data-stu-id="ed531-109">For example, the format (plain text) of the logged messages is not affected by the usage of a binary message encoder.</span></span>  
  
 <span data-ttu-id="ed531-110">Výstupem XmlWriterTraceListener je soubor, který obsahuje sekvenci fragmentů XML.</span><span class="sxs-lookup"><span data-stu-id="ed531-110">The output of the XmlWriterTraceListener is a file that contains a sequence of XML fragments.</span></span> <span data-ttu-id="ed531-111">Měli byste si uvědomit, že soubor není platný soubor XML.</span><span class="sxs-lookup"><span data-stu-id="ed531-111">You should be aware that the file is not a valid XML file.</span></span> <span data-ttu-id="ed531-112">Pro zobrazení souborů protokolu zpráv se doporučuje použít [Nástroj pro prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="ed531-112">It is recommended that you use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) to view the message log files.</span></span> <span data-ttu-id="ed531-113">Další informace o použití tohoto nástroje najdete v tématu [použití prohlížeče trasování služby pro zobrazení korelačních trasování a odstraňování potíží](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="ed531-113">For more information on how to use this tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="ed531-114">V prohlížeči trasování služby jsou zprávy uvedeny na kartě **zpráva** . Zprávy, které způsobily nebo souvisejí s, se chyba zpracování zvýrazní žlutě (úroveň upozornění) nebo červenou (úroveň chyby) v závislosti na závažnosti chyby.</span><span class="sxs-lookup"><span data-stu-id="ed531-114">In the Service Trace Viewer, messages are listed in the **Message** tab. Messages that have caused, or are related to, a processing error are highlighted in yellow (warning level) or red (error level), depending on the severity of the error.</span></span> <span data-ttu-id="ed531-115">Dvojím kliknutím na zprávu se zobrazí trasování zprávy v kontextu žádosti o zpracování.</span><span class="sxs-lookup"><span data-stu-id="ed531-115">Double-clicking on the message brings up the message trace in the context of the processing request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed531-116">Pokud zpráva neobsahuje hlavičku, není protokolována `<header/>` žádná značka.</span><span class="sxs-lookup"><span data-stu-id="ed531-116">If a message has no header, no `<header/>` tag is logged.</span></span>  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a><span data-ttu-id="ed531-117">Zobrazení zpráv protokolovaných klientem, přenosem a službou</span><span class="sxs-lookup"><span data-stu-id="ed531-117">Viewing Messages Logged by a Client, a Relay, and a Service</span></span>  
 <span data-ttu-id="ed531-118">Vaše prostředí může obsahovat klienta, který pošle zprávu do přenosu, který následně přepošle zprávu službě.</span><span class="sxs-lookup"><span data-stu-id="ed531-118">Your environment may contain a client, which sends a message to a relay, that subsequently forwards the message to the service.</span></span> <span data-ttu-id="ed531-119">Pokud je povoleno protokolování zpráv na všech třech místech a všechny tři protokoly zpráv se zobrazují současně v [nástroji Service Trace Viewer (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) současně, budou se zprávy o výměně protokolu zpráv nesprávně vykreslovat.</span><span class="sxs-lookup"><span data-stu-id="ed531-119">When message logging is enabled on all three locations, and all three message logs are viewed in [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) simultaneously, the message log exchanges will be incorrectly rendered.</span></span> <span data-ttu-id="ed531-120">Důvodem je, že `CorrelationId` a `ActivityId` v záhlaví zprávy nejsou jedinečné pro každou dvojici Send-Receive.</span><span class="sxs-lookup"><span data-stu-id="ed531-120">This is because the `CorrelationId` and `ActivityId` in the Message header are not unique for every send-receive pair.</span></span>  
  
 <span data-ttu-id="ed531-121">K vyřešení tohoto problému můžete použít některou z následujících metod.</span><span class="sxs-lookup"><span data-stu-id="ed531-121">You can use either one of the following methods to resolve this problem.</span></span>  
  
- <span data-ttu-id="ed531-122">V [nástroji Prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) si kdykoli zobrazit jenom dva ze tří protokolů zpráv.</span><span class="sxs-lookup"><span data-stu-id="ed531-122">Only view two of the three message logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at any time.</span></span>  
  
- <span data-ttu-id="ed531-123">Pokud je nutné zobrazit všechny tři protokoly v [nástroji Prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) současně, můžete službu Relay změnit vytvořením nové <xref:System.ServiceModel.Channels.Message> instance.</span><span class="sxs-lookup"><span data-stu-id="ed531-123">If you must view all three logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at the same time, you can modify the relay service by creating a new <xref:System.ServiceModel.Channels.Message> instance.</span></span> <span data-ttu-id="ed531-124">Tato instance by měla být kopií textu příchozí zprávy a všech hlaviček kromě `ActivityId` hlaviček a. `Action`</span><span class="sxs-lookup"><span data-stu-id="ed531-124">This instance should be a copy of the body of the incoming message, plus all the headers except for the `ActivityId` and `Action` headers.</span></span> <span data-ttu-id="ed531-125">Následující příklad kódu ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="ed531-125">The following example code demonstrates how to do this.</span></span>  
  
```csharp
Message outgoingMessage = Message.CreateMessage(incomingMessage.Version, incomingMessage.Headers.Action, incomingMessage.GetReaderAtBodyContents());  
  
for (int i = 0; i < incomingMessage.Headers.Count; i++)  
{  
   if (incomingMessage.Headers[i].Name.Equals("ActivityId", StringComparison.InvariantCultureIgnoreCase) ||  
incomingMessage.Headers[i].Name.Equals("Action", StringComparison.InvariantCultureIgnoreCase))  
   {  
      continue;  
    }  
    outgoingMessage.Headers.CopyHeaderFrom(incomingMessage, i);  
}  
```  
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a><span data-ttu-id="ed531-126">Výjimečné případy pro nepřesný obsah protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="ed531-126">Exceptional Cases for Inaccurate Message Logging Content</span></span>  
 <span data-ttu-id="ed531-127">V následujících podmínkách nemusí být protokolovaná zpráva přesným znázorněním oktetu přítomného na lince.</span><span class="sxs-lookup"><span data-stu-id="ed531-127">Under the following conditions, messages being logged might not be the exact representation of the octet stream present on the wire.</span></span>  
  
- <span data-ttu-id="ed531-128">Pro BasicHttpBinding se pro příchozí zprávy v oboru názvů/Addressing/None protokolují hlavičky obálek.</span><span class="sxs-lookup"><span data-stu-id="ed531-128">For BasicHttpBinding, envelope headers are logged for the incoming messages in the /addressing/none namespace.</span></span>  
  
- <span data-ttu-id="ed531-129">Nelze neshodovat prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="ed531-129">White spaces can be mismatched.</span></span>  
  
- <span data-ttu-id="ed531-130">Pro příchozí zprávy mohou být prázdné prvky reprezentovány jinak.</span><span class="sxs-lookup"><span data-stu-id="ed531-130">For incoming messages, empty elements can be represented differently.</span></span> <span data-ttu-id="ed531-131">Například \<Tag >\</Tag > namísto \<Tag/></span><span class="sxs-lookup"><span data-stu-id="ed531-131">For example, \<tag>\</tag> instead of  \<tag/></span></span>  
  
- <span data-ttu-id="ed531-132">Je-li známé protokolování PII zakázáno buď ve výchozím nastavení, nebo explicitním nastavením enableLoggingKnownPii = "true".</span><span class="sxs-lookup"><span data-stu-id="ed531-132">When known PII logging is disabled either by default or explicit setting enableLoggingKnownPii="true".</span></span>  
  
- <span data-ttu-id="ed531-133">Kódování je povoleno pro transformaci do UTF-8.</span><span class="sxs-lookup"><span data-stu-id="ed531-133">Encoding is enabled for transforming to UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed531-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed531-134">See also</span></span>

- [<span data-ttu-id="ed531-135">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="ed531-135">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [<span data-ttu-id="ed531-136">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů</span><span class="sxs-lookup"><span data-stu-id="ed531-136">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="ed531-137">Protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="ed531-137">Message Logging</span></span>](../../../../docs/framework/wcf/diagnostics/message-logging.md)
