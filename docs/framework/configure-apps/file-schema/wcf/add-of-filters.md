---
title: <add> z <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 0e42766cd94b58562bc5728d517e65e80f558cda
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288792"
---
# <a name="add-of-filters"></a>\<Přidat > z \<filtry >
Filtr XPath určující druh zaznamenávané zprávy.  
  
 \<system.ServiceModel>  
\<diagnostic>  
\<messageLogging>  
\<Filtry >  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<filters>
  <add filter="String" />
</filters>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|filtrování|Řetězec určující dotaz na dokument jazyka XML, definován výrazem jazyka XPath 1.0. Další informace naleznete v tématu <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Filtry>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|Obsahuje kolekci filtrů XPath umožňují určit, jaký druh zprávy se protokoluje.|  
  
## <a name="remarks"></a>Poznámky  
 Filtry se použijí pouze na transportní vrstvě, určené `logMessagesAtTransportLevel` je `true`. Protokolování úrovně a poškozené zprávy služby nejsou ovlivněny filtry.  
  
 Chcete-li přidat filtr do kolekce, použijte `add` – klíčové slovo. Když jsou definovány jeden nebo více filtrů, jsou protokolovány jen zprávy, které odpovídají alespoň jeden z filtrů. Pokud není definován žádný filtr, všechny zprávy předávání.  
  
 Filtry podporuje úplnou syntaxi XPath a nastavení se použijí v pořadí, ve kterém se zobrazují v konfiguračním souboru. Filtr syntakticky nesprávný výsledkem výjimka v konfiguraci.  
  
 Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají oddíl hlavičky SOAP.  
  
## <a name="example"></a>Příklad  
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
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [Konfigurace protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
- [Konfigurace protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
