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

`filters`Element obsahuje kolekci filtrů XPath používaných k řízení toho, jaký druh zprávy je protokolován.

Filtry se aplikují jenom na transportní vrstvě, kterou Určuje `logMessagesAtTransportLevel` `true` . Filtry neovlivní úroveň služeb a nesprávně přihlašování zpráv.

Chcete-li přidat filtr do kolekce, použijte `add` klíčové slovo. Při definování jednoho nebo více filtrů jsou protokolovány pouze zprávy, které odpovídají alespoň jednomu z filtrů. Pokud není definován žádný filtr, všechny zprávy procházejí.

Filtry podporují úplnou syntaxi XPath a jsou aplikovány v pořadí, v jakém jsou uvedeny v konfiguračním souboru. Syntakticky nesprávný filtr má za následek výjimku konfigurace.

Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají hlavičku SOAP.
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [Konfigurace protokolování zpráv](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](messagelogging.md)
