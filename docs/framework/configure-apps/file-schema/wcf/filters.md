---
title: <filters>
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: e4ce0452cc46a8f29334fa67f51f14b83290b1c8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "69918877"
---
# \<filters>

<span data-ttu-id="1d896-101">`filters`Element obsahuje kolekci filtrů XPath používaných k řízení toho, jaký druh zprávy je protokolován.</span><span class="sxs-lookup"><span data-stu-id="1d896-101">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="1d896-102">Filtry se aplikují jenom na transportní vrstvě, kterou Určuje `logMessagesAtTransportLevel` `true` .</span><span class="sxs-lookup"><span data-stu-id="1d896-102">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="1d896-103">Filtry neovlivní úroveň služeb a nesprávně přihlašování zpráv.</span><span class="sxs-lookup"><span data-stu-id="1d896-103">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="1d896-104">Chcete-li přidat filtr do kolekce, použijte `add` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="1d896-104">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="1d896-105">Při definování jednoho nebo více filtrů jsou protokolovány pouze zprávy, které odpovídají alespoň jednomu z filtrů.</span><span class="sxs-lookup"><span data-stu-id="1d896-105">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="1d896-106">Pokud není definován žádný filtr, všechny zprávy procházejí.</span><span class="sxs-lookup"><span data-stu-id="1d896-106">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="1d896-107">Filtry podporují úplnou syntaxi XPath a jsou aplikovány v pořadí, v jakém jsou uvedeny v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="1d896-107">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="1d896-108">Syntakticky nesprávný filtr má za následek výjimku konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1d896-108">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="1d896-109">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají hlavičku SOAP.</span><span class="sxs-lookup"><span data-stu-id="1d896-109">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="1d896-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d896-110">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="1d896-111">Konfigurace protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="1d896-111">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
