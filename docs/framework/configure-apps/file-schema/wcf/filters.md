---
title: '&lt;filtry&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a91be2862f58994b4495f1fa1a5c4e692b5ff7b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltersgt"></a><span data-ttu-id="06063-102">&lt;filtry&gt;</span><span class="sxs-lookup"><span data-stu-id="06063-102">&lt;filters&gt;</span></span>

<span data-ttu-id="06063-103">`filters` Element obsahuje kolekci filtrů XPath použít k řízení, jaký typ zprávy přihlášen.</span><span class="sxs-lookup"><span data-stu-id="06063-103">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="06063-104">Filtry se použijí jenom v přenosové vrstvě určeného `logMessagesAtTransportLevel` je `true`.</span><span class="sxs-lookup"><span data-stu-id="06063-104">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="06063-105">Protokolování úrovně a poškozených zpráv služby nemá vliv filtry.</span><span class="sxs-lookup"><span data-stu-id="06063-105">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="06063-106">Chcete-li přidat filtr do kolekce, použijte `add` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="06063-106">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="06063-107">Když jsou definovány jeden nebo více filtrů, jsou protokolovány pouze zprávy, které odpovídají alespoň jeden z filtrů.</span><span class="sxs-lookup"><span data-stu-id="06063-107">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="06063-108">Pokud je definován žádný filtr, všechny zprávy předávat.</span><span class="sxs-lookup"><span data-stu-id="06063-108">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="06063-109">Filtry podporovat úplnou syntaxí XPath a aplikují v pořadí, ve kterém se zobrazují v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="06063-109">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="06063-110">Správnou syntaxi filtr výsledkem výjimka v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="06063-110">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="06063-111">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává jen zprávy, které máte oddíl hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="06063-111">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="06063-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="06063-112">See also</span></span>

 <span data-ttu-id="06063-113"><xref:System.ServiceModel.Configuration.DiagnosticSection><xref:System.ServiceModel.Diagnostics> <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> <xref:System.ServiceModel.Configuration.MessageLoggingElement> <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A> <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection> <xref:System.ServiceModel.Configuration.XPathMessageFilterElement> <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> [Konfigurace protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) [ \<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)</span><span class="sxs-lookup"><span data-stu-id="06063-113"><xref:System.ServiceModel.Configuration.DiagnosticSection> <xref:System.ServiceModel.Diagnostics> <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> <xref:System.ServiceModel.Configuration.MessageLoggingElement> <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A> <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection> <xref:System.ServiceModel.Configuration.XPathMessageFilterElement> <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> [Configuring Message Logging](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) [\<messageLogging>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)</span></span>
