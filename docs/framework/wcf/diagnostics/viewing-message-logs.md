---
title: "Prohlížení protokolů zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09a26d3580b37ea92bf4ef5708a238396f22eb4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="viewing-message-logs"></a><span data-ttu-id="81af7-102">Prohlížení protokolů zpráv</span><span class="sxs-lookup"><span data-stu-id="81af7-102">Viewing Message Logs</span></span>
<span data-ttu-id="81af7-103">Toto téma popisuje, jak můžete zobrazit protokoly zpráv.</span><span class="sxs-lookup"><span data-stu-id="81af7-103">This topic describes how you can view message logs.</span></span>  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a><span data-ttu-id="81af7-104">Při zobrazení zprávy přihlásí prohlížeče trasování služeb</span><span class="sxs-lookup"><span data-stu-id="81af7-104">Viewing Message Logs in the Service Trace Viewer</span></span>  
 <span data-ttu-id="81af7-105">Zpráva bude transformovat, jako je zpracován [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81af7-105">A message will be transformed as it is processed by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="81af7-106">Proto zprávu protokolována odráží jenom obsah zprávy v místě, které ho protokolu byla zaznamenána, není obsah v drátové síti.</span><span class="sxs-lookup"><span data-stu-id="81af7-106">Therefore, a message being logged reflects only the message's content at the point it was logged, not the content on the wire.</span></span>  
  
 <span data-ttu-id="81af7-107">Vzhledem k tomu, že výstup protokolování zpráv nemá žádný vztah k přenosu formát zprávy, vždy protokolování zpráv výstupy dekódované zprávy.</span><span class="sxs-lookup"><span data-stu-id="81af7-107">Since the output of message logging has no relationship to the transfer format of the message, message logging always outputs the decoded message.</span></span> <span data-ttu-id="81af7-108">Pokud jste nakonfigurovali protokolování správně zpráv, jakékoli zaznamenané zprávy musí být ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="81af7-108">If you have configured message logging properly, any logged message should be in plain text.</span></span> <span data-ttu-id="81af7-109">Formát zprávy zaznamenané (prostý text) není například vliv použití kodéru zprávy v binární.</span><span class="sxs-lookup"><span data-stu-id="81af7-109">For example, the format (plain text) of the logged messages is not affected by the usage of a binary message encoder.</span></span>  
  
 <span data-ttu-id="81af7-110">Výstup XmlWriterTraceListener je soubor, který obsahuje posloupnost fragmenty kódu XML.</span><span class="sxs-lookup"><span data-stu-id="81af7-110">The output of the XmlWriterTraceListener is a file that contains a sequence of XML fragments.</span></span> <span data-ttu-id="81af7-111">Byste měli vědět, že soubor není platný soubor XML.</span><span class="sxs-lookup"><span data-stu-id="81af7-111">You should be aware that the file is not a valid XML file.</span></span> <span data-ttu-id="81af7-112">Je doporučeno používat [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) k zobrazení souborů protokolů zpráv.</span><span class="sxs-lookup"><span data-stu-id="81af7-112">It is recommended that you use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) to view the message log files.</span></span> <span data-ttu-id="81af7-113">Další informace o tom, jak pomocí tohoto nástroje najdete v tématu [pomocí prohlížeče trasování služeb pro zobrazení korelační trasování a Poradce při potížích s](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="81af7-113">For more information on how to use this tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="81af7-114">V prohlížeči trasování služby, zprávy jsou uvedeny v **zpráva** kartě. Zprávy, které způsobily, nebo jsou související s, chyba zpracování jsou vyznačené na žlutý (varování úroveň) nebo červený (úroveň chyb), v závislosti na závažnosti chyby.</span><span class="sxs-lookup"><span data-stu-id="81af7-114">In the Service Trace Viewer, messages are listed in the **Message** tab. Messages that have caused, or are related to, a processing error are highlighted in yellow (warning level) or red (error level), depending on the severity of the error.</span></span> <span data-ttu-id="81af7-115">Dvojitým kliknutím na zprávu, na které se vyvolá trasování zpráv v kontextu požadavku na zpracování.</span><span class="sxs-lookup"><span data-stu-id="81af7-115">Double-clicking on the message brings up the message trace in the context of the processing request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81af7-116">Pokud zpráva není hlavička, ne `<header/>` značky přihlášen.</span><span class="sxs-lookup"><span data-stu-id="81af7-116">If a message has no header, no `<header/>` tag is logged.</span></span>  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a><span data-ttu-id="81af7-117">Zobrazení zprávy zaznamenané klienta, předávání a služby</span><span class="sxs-lookup"><span data-stu-id="81af7-117">Viewing Messages Logged by a Client, a Relay, and a Service</span></span>  
 <span data-ttu-id="81af7-118">Klient, který odešle zprávu do předávání, které následně předá zprávu do služby může obsahovat vaše prostředí.</span><span class="sxs-lookup"><span data-stu-id="81af7-118">Your environment may contain a client, which sends a message to a relay, that subsequently forwards the message to the service.</span></span> <span data-ttu-id="81af7-119">Pokud je povoleno protokolování zpráv na všech tří umístění, a jsou všechny tři protokoly zprávy zobrazit v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) současně, bude nesprávně vykreslen výměny zpráv protokolu.</span><span class="sxs-lookup"><span data-stu-id="81af7-119">When message logging is enabled on all three locations, and all three message logs are viewed in [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) simultaneously, the message log exchanges will be incorrectly rendered.</span></span> <span data-ttu-id="81af7-120">Důvodem je, že `CorrelationId` a `ActivityId` v záhlaví zprávy nejsou pro každý pár send-receive jedinečné.</span><span class="sxs-lookup"><span data-stu-id="81af7-120">This is because the `CorrelationId` and `ActivityId` in the Message header are not unique for every send-receive pair.</span></span>  
  
 <span data-ttu-id="81af7-121">Chcete-li vyřešit tento problém můžete jednu z následujících metod.</span><span class="sxs-lookup"><span data-stu-id="81af7-121">You can use either one of the following methods to resolve this problem.</span></span>  
  
-   <span data-ttu-id="81af7-122">Zobrazit pouze dvě ze tří protokolů zpráv v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) kdykoli.</span><span class="sxs-lookup"><span data-stu-id="81af7-122">Only view two of the three message logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at any time.</span></span>  
  
-   <span data-ttu-id="81af7-123">Pokud musíte zobrazit všechny tři protokoly v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ve stejnou dobu, můžete upravit tak, že vytvoříte novou službu předávání přes <xref:System.ServiceModel.Channels.Message> instance.</span><span class="sxs-lookup"><span data-stu-id="81af7-123">If you must view all three logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at the same time, you can modify the relay service by creating a new <xref:System.ServiceModel.Channels.Message> instance.</span></span> <span data-ttu-id="81af7-124">Tato instance musí být kopie obsahu příchozí zprávy, včetně všech záhlaví s výjimkou `ActivityId` a `Action` hlavičky.</span><span class="sxs-lookup"><span data-stu-id="81af7-124">This instance should be a copy of the body of the incoming message, plus all the headers except for the `ActivityId` and `Action` headers.</span></span> <span data-ttu-id="81af7-125">Následující příklad kódu ukazuje, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="81af7-125">The following example code demonstrates how to do this.</span></span>  
  
```  
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
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a><span data-ttu-id="81af7-126">Výjimečných případech pro obsah protokolování nesprávné zprávy</span><span class="sxs-lookup"><span data-stu-id="81af7-126">Exceptional Cases for Inaccurate Message Logging Content</span></span>  
 <span data-ttu-id="81af7-127">Za těchto podmínek zprávy protokolována nemusí být přesné reprezentace datového proudu octet přítomen v drátové síti.</span><span class="sxs-lookup"><span data-stu-id="81af7-127">Under the following conditions, messages being logged might not be the exact representation of the octet stream present on the wire.</span></span>  
  
-   <span data-ttu-id="81af7-128">Pro BasicHttpBinding, se zaznamenávají obálky hlavičky pro příchozí zprávy v / adresování/žádný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="81af7-128">For BasicHttpBinding, envelope headers are logged for the incoming messages in the /addressing/none namespace.</span></span>  
  
-   <span data-ttu-id="81af7-129">Může být neshoda prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="81af7-129">Whitespaces can be mismatched.</span></span>  
  
-   <span data-ttu-id="81af7-130">Pro příchozí zprávy může být reprezentován prázdné prvky jinak.</span><span class="sxs-lookup"><span data-stu-id="81af7-130">For incoming messages, empty elements can be represented differently.</span></span> <span data-ttu-id="81af7-131">Například \<značka >\</značka > místo \<značka / ></span><span class="sxs-lookup"><span data-stu-id="81af7-131">For example, \<tag>\</tag> instead of  \<tag/></span></span>  
  
-   <span data-ttu-id="81af7-132">Když je zakázáno známé PII protokolování buď ve výchozím nastavení nebo explicitní nastavení enableLoggingKnownPii = "true".</span><span class="sxs-lookup"><span data-stu-id="81af7-132">When known PII logging is disabled either by default or explicit setting enableLoggingKnownPii="true".</span></span>  
  
-   <span data-ttu-id="81af7-133">Kódování je povolený pro převod na UTF-8.</span><span class="sxs-lookup"><span data-stu-id="81af7-133">Encoding is enabled for transforming to UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81af7-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="81af7-134">See Also</span></span>  
 [<span data-ttu-id="81af7-135">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="81af7-135">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [<span data-ttu-id="81af7-136">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů</span><span class="sxs-lookup"><span data-stu-id="81af7-136">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="81af7-137">Protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="81af7-137">Message Logging</span></span>](../../../../docs/framework/wcf/diagnostics/message-logging.md)
