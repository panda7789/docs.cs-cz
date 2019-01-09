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
# <a name="ltfiltersgt"></a>&lt;Filtry&gt;

`filters` Element obsahuje kolekci filtrů XPath umožňují určit, jaký druh zprávy se protokoluje.

Filtry se použijí pouze na transportní vrstvě, určené `logMessagesAtTransportLevel` je `true`. Protokolování úrovně a poškozené zprávy služby nejsou ovlivněny filtry.

Chcete-li přidat filtr do kolekce, použijte `add` – klíčové slovo. Když jsou definovány jeden nebo více filtrů, jsou protokolovány jen zprávy, které odpovídají alespoň jeden z filtrů. Pokud není definován žádný filtr, všechny zprávy předávání.

Filtry podporuje úplnou syntaxi XPath a nastavení se použijí v pořadí, ve kterém se zobrazují v konfiguračním souboru. Filtr syntakticky nesprávný výsledkem výjimka v konfiguraci.

Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají oddíl hlavičky SOAP.
  
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
  
## <a name="see-also"></a>Viz také:

 <xref:System.ServiceModel.Configuration.DiagnosticSection><xref:System.ServiceModel.Diagnostics>
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection>
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
 [Konfigurace protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) [ \<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
