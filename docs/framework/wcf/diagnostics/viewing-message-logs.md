---
title: Prohlížení protokolů zpráv
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: 5d007efc9667ee5380b69349d6a960554ab0d4fe
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2018
ms.locfileid: "50047498"
---
# <a name="viewing-message-logs"></a><span data-ttu-id="18463-102">Prohlížení protokolů zpráv</span><span class="sxs-lookup"><span data-stu-id="18463-102">Viewing Message Logs</span></span>
<span data-ttu-id="18463-103">Toto téma popisuje, jak můžete zobrazit protokoly zpráv.</span><span class="sxs-lookup"><span data-stu-id="18463-103">This topic describes how you can view message logs.</span></span>  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a><span data-ttu-id="18463-104">Při zobrazení zprávy přihlásí prohlížeče trasování služeb</span><span class="sxs-lookup"><span data-stu-id="18463-104">Viewing Message Logs in the Service Trace Viewer</span></span>  
 <span data-ttu-id="18463-105">Zpráva se bude transformovat, jako je zpracován programovacím modelem WCF.</span><span class="sxs-lookup"><span data-stu-id="18463-105">A message will be transformed as it is processed by WCF.</span></span> <span data-ttu-id="18463-106">Proto zprávu přihlašováno odráží jenom obsah zprávy v okamžiku, kdy byla zapsána, není obsah na lince.</span><span class="sxs-lookup"><span data-stu-id="18463-106">Therefore, a message being logged reflects only the message's content at the point it was logged, not the content on the wire.</span></span>  
  
 <span data-ttu-id="18463-107">Protože výstup protokolování zpráv nemá žádný vztah k přenosu formát zprávy, vždy protokolování zpráv výstupy dekódovanou zprávu.</span><span class="sxs-lookup"><span data-stu-id="18463-107">Since the output of message logging has no relationship to the transfer format of the message, message logging always outputs the decoded message.</span></span> <span data-ttu-id="18463-108">Pokud jste nakonfigurovali správně protokolování zpráv, všechny Protokolovaná zpráva musí být ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="18463-108">If you have configured message logging properly, any logged message should be in plain text.</span></span> <span data-ttu-id="18463-109">Například formát (prostý text) zaznamenaných zpráv nemá vliv využití kodér binárních zpráv.</span><span class="sxs-lookup"><span data-stu-id="18463-109">For example, the format (plain text) of the logged messages is not affected by the usage of a binary message encoder.</span></span>  
  
 <span data-ttu-id="18463-110">Výstup XmlWriterTraceListener je soubor, který obsahuje posloupnost fragmentů XML.</span><span class="sxs-lookup"><span data-stu-id="18463-110">The output of the XmlWriterTraceListener is a file that contains a sequence of XML fragments.</span></span> <span data-ttu-id="18463-111">Byste měli vědět, že soubor není platný soubor XML.</span><span class="sxs-lookup"><span data-stu-id="18463-111">You should be aware that the file is not a valid XML file.</span></span> <span data-ttu-id="18463-112">Doporučuje se, že používáte [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) Chcete-li zobrazit soubory protokolu zpráv.</span><span class="sxs-lookup"><span data-stu-id="18463-112">It is recommended that you use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) to view the message log files.</span></span> <span data-ttu-id="18463-113">Další informace o tom, jak pomocí tohoto nástroje naleznete v tématu [pomocí prohlížeče trasování služeb k zobrazení korelovaných trasování a řešení potíží](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="18463-113">For more information on how to use this tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="18463-114">Zprávy jsou v prohlížeče trasování služeb uvedené v **zpráva** kartu. Zprávy, které způsobily, nebo jsou související s, Chyba při zpracování jsou zvýrazněné žlutou barvou (úroveň upozornění) nebo červený (úroveň chyb), v závislosti na závažnosti chyby.</span><span class="sxs-lookup"><span data-stu-id="18463-114">In the Service Trace Viewer, messages are listed in the **Message** tab. Messages that have caused, or are related to, a processing error are highlighted in yellow (warning level) or red (error level), depending on the severity of the error.</span></span> <span data-ttu-id="18463-115">Dvojitým kliknutím na zprávu zobrazí trasování zpráv v rámci zpracování požadavku.</span><span class="sxs-lookup"><span data-stu-id="18463-115">Double-clicking on the message brings up the message trace in the context of the processing request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18463-116">Pokud zpráva neobsahuje žádné záhlaví `<header/>` značka je zaznamenána.</span><span class="sxs-lookup"><span data-stu-id="18463-116">If a message has no header, no `<header/>` tag is logged.</span></span>  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a><span data-ttu-id="18463-117">Zobrazení zprávy zaprotokolované pomocí klienta, se při předávání a služby</span><span class="sxs-lookup"><span data-stu-id="18463-117">Viewing Messages Logged by a Client, a Relay, and a Service</span></span>  
 <span data-ttu-id="18463-118">Vaše prostředí může obsahovat klienta, který odešle zprávu do přenos, který následně předá zprávu do služby.</span><span class="sxs-lookup"><span data-stu-id="18463-118">Your environment may contain a client, which sends a message to a relay, that subsequently forwards the message to the service.</span></span> <span data-ttu-id="18463-119">Při protokolování zpráv je povolená na všech třech umístěních, a všechny tři protokoly zpráv jsou zobrazeny v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) současně, bude nesprávně vykreslit výměny zpráv protokolu.</span><span class="sxs-lookup"><span data-stu-id="18463-119">When message logging is enabled on all three locations, and all three message logs are viewed in [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) simultaneously, the message log exchanges will be incorrectly rendered.</span></span> <span data-ttu-id="18463-120">Je to proto, `CorrelationId` a `ActivityId` v záhlaví zprávy nejsou jedinečné pro každý pár send-receive.</span><span class="sxs-lookup"><span data-stu-id="18463-120">This is because the `CorrelationId` and `ActivityId` in the Message header are not unique for every send-receive pair.</span></span>  
  
 <span data-ttu-id="18463-121">Chcete-li vyřešit tento problém můžete použít jednu z následujících metod.</span><span class="sxs-lookup"><span data-stu-id="18463-121">You can use either one of the following methods to resolve this problem.</span></span>  
  
-   <span data-ttu-id="18463-122">Zobrazit pouze dvě ze tří protokolů zpráv v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) kdykoli.</span><span class="sxs-lookup"><span data-stu-id="18463-122">Only view two of the three message logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at any time.</span></span>  
  
-   <span data-ttu-id="18463-123">Pokud si musí zobrazit všechny tři protokoly v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ve stejnou dobu, můžete upravit se službou Relay vytvoříte tak, že vytvoříte nový <xref:System.ServiceModel.Channels.Message> instance.</span><span class="sxs-lookup"><span data-stu-id="18463-123">If you must view all three logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at the same time, you can modify the relay service by creating a new <xref:System.ServiceModel.Channels.Message> instance.</span></span> <span data-ttu-id="18463-124">Tato instance musí být kopie tělo z příchozí zprávy a navíc všechny hlavičky s výjimkou `ActivityId` a `Action` záhlaví.</span><span class="sxs-lookup"><span data-stu-id="18463-124">This instance should be a copy of the body of the incoming message, plus all the headers except for the `ActivityId` and `Action` headers.</span></span> <span data-ttu-id="18463-125">Následující příklad kódu ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="18463-125">The following example code demonstrates how to do this.</span></span>  
  
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
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a><span data-ttu-id="18463-126">Výjimečných případech nesprávné zpráva protokolování obsahu</span><span class="sxs-lookup"><span data-stu-id="18463-126">Exceptional Cases for Inaccurate Message Logging Content</span></span>  
 <span data-ttu-id="18463-127">Za následujících podmínek nemusí být právě protokolované zprávy přesnou reprezentací octet stream k dispozici na lince.</span><span class="sxs-lookup"><span data-stu-id="18463-127">Under the following conditions, messages being logged might not be the exact representation of the octet stream present on the wire.</span></span>  
  
-   <span data-ttu-id="18463-128">BasicHttpBinding, hlavičky obálky se protokolují pro příchozí zprávy v / adresování/žádný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="18463-128">For BasicHttpBinding, envelope headers are logged for the incoming messages in the /addressing/none namespace.</span></span>  
  
-   <span data-ttu-id="18463-129">Prázdné znaky může lišit.</span><span class="sxs-lookup"><span data-stu-id="18463-129">White spaces can be mismatched.</span></span>  
  
-   <span data-ttu-id="18463-130">Pro příchozí zprávy může být jinak reprezentována prázdné prvky.</span><span class="sxs-lookup"><span data-stu-id="18463-130">For incoming messages, empty elements can be represented differently.</span></span> <span data-ttu-id="18463-131">Například \<značka >\</označit > namísto \<značky / ></span><span class="sxs-lookup"><span data-stu-id="18463-131">For example, \<tag>\</tag> instead of  \<tag/></span></span>  
  
-   <span data-ttu-id="18463-132">Když je zakázáno přihlášení známého PII, buď ve výchozím nastavení nebo explicitní nastavení enableLoggingKnownPii = "true".</span><span class="sxs-lookup"><span data-stu-id="18463-132">When known PII logging is disabled either by default or explicit setting enableLoggingKnownPii="true".</span></span>  
  
-   <span data-ttu-id="18463-133">Kódování je povolená pro transformaci na UTF-8.</span><span class="sxs-lookup"><span data-stu-id="18463-133">Encoding is enabled for transforming to UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18463-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="18463-134">See Also</span></span>  
 [<span data-ttu-id="18463-135">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="18463-135">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [<span data-ttu-id="18463-136">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů</span><span class="sxs-lookup"><span data-stu-id="18463-136">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="18463-137">Protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="18463-137">Message Logging</span></span>](../../../../docs/framework/wcf/diagnostics/message-logging.md)
