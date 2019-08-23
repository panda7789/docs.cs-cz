---
title: <filters>
ms.date: 03/30/2017
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
ms.openlocfilehash: e4ce0452cc46a8f29334fa67f51f14b83290b1c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918877"
---
# <a name="filters"></a><span data-ttu-id="8b784-101">\<> filtrů</span><span class="sxs-lookup"><span data-stu-id="8b784-101">\<filters></span></span>

<span data-ttu-id="8b784-102">`filters` Element obsahuje kolekci filtrů XPath používaných k řízení toho, jaký druh zprávy je protokolován.</span><span class="sxs-lookup"><span data-stu-id="8b784-102">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="8b784-103">Filtry se aplikují jenom na transportní vrstvě, kterou `logMessagesAtTransportLevel` `true`určuje.</span><span class="sxs-lookup"><span data-stu-id="8b784-103">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="8b784-104">Filtry neovlivní úroveň služeb a nesprávně přihlašování zpráv.</span><span class="sxs-lookup"><span data-stu-id="8b784-104">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="8b784-105">Chcete-li přidat filtr do kolekce, použijte `add` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="8b784-105">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="8b784-106">Při definování jednoho nebo více filtrů jsou protokolovány pouze zprávy, které odpovídají alespoň jednomu z filtrů.</span><span class="sxs-lookup"><span data-stu-id="8b784-106">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="8b784-107">Pokud není definován žádný filtr, všechny zprávy procházejí.</span><span class="sxs-lookup"><span data-stu-id="8b784-107">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="8b784-108">Filtry podporují úplnou syntaxi XPath a jsou aplikovány v pořadí, v jakém jsou uvedeny v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="8b784-108">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="8b784-109">Syntakticky nesprávný filtr má za následek výjimku konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8b784-109">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="8b784-110">Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají hlavičku SOAP.</span><span class="sxs-lookup"><span data-stu-id="8b784-110">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="8b784-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b784-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [<span data-ttu-id="8b784-112">Konfigurace protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="8b784-112">Configuring Message Logging</span></span>](../../../wcf/diagnostics/configuring-message-logging.md)
- [<span data-ttu-id="8b784-113">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="8b784-113">\<messageLogging></span></span>](messagelogging.md)
