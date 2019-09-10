---
title: <add> z <filters>
ms.date: 03/30/2017
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
ms.openlocfilehash: 280c516b17a133930bc4b6621a8c9bc7f4781085
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850560"
---
# <a name="add-of-filters"></a>\<Přidat > \<filtrů >
Filtr XPath určující druh zprávy, která má být zaznamenána.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> diagnostiky**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<messageLogging >** ](messagelogging.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> filtrů**](filters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**  
  
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
|filtrování|Řetězec, který určuje dotaz na dokumentu XML, který je definován výrazem XPath 1,0. Další informace naleznete v tématu <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Filtry>](filters.md)|Obsahuje kolekci filtrů XPath používaných k řízení toho, jaký druh zprávy je protokolován.|  
  
## <a name="remarks"></a>Poznámky  
 Filtry se aplikují jenom na transportní vrstvě, kterou `logMessagesAtTransportLevel` `true`určuje. Filtry neovlivní úroveň služeb a nesprávně přihlašování zpráv.  
  
 Chcete-li přidat filtr do kolekce, použijte `add` klíčové slovo. Při definování jednoho nebo více filtrů jsou protokolovány pouze zprávy, které odpovídají alespoň jednomu z filtrů. Pokud není definován žádný filtr, všechny zprávy procházejí.  
  
 Filtry podporují úplnou syntaxi XPath a jsou aplikovány v pořadí, v jakém jsou uvedeny v konfiguračním souboru. Syntakticky nesprávný filtr má za následek výjimku konfigurace.  
  
 Následuje příklad, jak nakonfigurovat filtr, který zaznamenává pouze zprávy, které mají hlavičku SOAP.  
  
## <a name="example"></a>Příklad  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement>
- <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>
- <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>
- <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>
- [Konfigurace protokolování zpráv](../../../wcf/diagnostics/configuring-message-logging.md)
- [\<messageLogging >](messagelogging.md)
