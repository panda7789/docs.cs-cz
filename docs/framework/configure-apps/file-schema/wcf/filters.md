---
title: '&lt;Filtry&gt;'
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: aae70fbe873eee10fcf95dcdd443dfa9ae6efb57
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148965"
---
# <a name="ltfiltersgt"></a><span data-ttu-id="c5e19-102">&lt;Filtry&gt;</span><span class="sxs-lookup"><span data-stu-id="c5e19-102">&lt;filters&gt;</span></span>

<span data-ttu-id="c5e19-103">`filters` Element obsahuje kolekci filtrů XPath umožňují určit, jaký druh zprávy se protokoluje.</span><span class="sxs-lookup"><span data-stu-id="c5e19-103">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="c5e19-104">Filtry se použijí pouze na transportní vrstvě, určené `logMessagesAtTransportLevel` je `true`.</span><span class="sxs-lookup"><span data-stu-id="c5e19-104">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="c5e19-105">Protokolování úrovně a poškozené zprávy služby nejsou ovlivněny filtry.</span><span class="sxs-lookup"><span data-stu-id="c5e19-105">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="c5e19-106">Chcete-li přidat filtr do kolekce, použijte `add` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c5e19-106">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="c5e19-107">Když jsou definovány jeden nebo více filtrů, jsou protokolovány jen zprávy, které odpovídají alespoň jeden z filtrů.</span><span class="sxs-lookup"><span data-stu-id="c5e19-107">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="c5e19-108">Pokud není definován žádný filtr, všechny zprávy předávání.</span><span class="sxs-lookup"><span data-stu-id="c5e19-108">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="c5e19-109">Filtry podporuje úplnou syntaxi XPath a nastavení se použijí v pořadí, ve kterém se zobrazují v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="c5e19-109">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="c5e19-110">Filtr syntakticky nesprávný výsledkem výjimka v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="c5e19-110">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="c5e19-111">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají oddíl hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="c5e19-111">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
```xml  
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="420">
  <filters>
    <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">
      /soap:Envelope/soap:Headers
    </add>
  </filters>
</messageLogging>
```  
  
## <a name="see-also"></a><span data-ttu-id="c5e19-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5e19-112">See also</span></span>

 <span data-ttu-id="c5e19-113"><xref:System.ServiceModel.Configuration.DiagnosticSection><xref:System.ServiceModel.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="c5e19-113"><xref:System.ServiceModel.Configuration.DiagnosticSection> <xref:System.ServiceModel.Diagnostics></span></span>
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
 <span data-ttu-id="c5e19-114">[Konfigurace protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) [ \<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)</span><span class="sxs-lookup"><span data-stu-id="c5e19-114">[Configuring Message Logging](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) [\<messageLogging>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)</span></span>
