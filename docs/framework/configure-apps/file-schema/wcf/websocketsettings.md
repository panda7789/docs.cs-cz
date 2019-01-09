---
title: '&lt;webSocketSettings&gt;'
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 134a233a337c40d21f7547fe385ec788cef2165b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150055"
---
# <a name="ltwebsocketsettingsgt"></a>&lt;webSocketSettings&gt;
Prvek konfigurace určuje nastavení Websocket.  
  
\<system.ServiceModel>  
\<vazby >  
\<netHttpBinding >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|createNotificationOnConnection|Určuje, zda jsou oznámení odesílána při připojení.|  
|disablePayloadMasking|Určuje, zda je zakázaný maskování Websocket.|  
|nastavení KeepAliveInterval protokolu|Určuje keep alive interval.|  
|maxPendingConnections|Určuje maximální počet připojení čeká na odeslání ve službě.|  
|receiveBufferSize|Určuje velikost vyrovnávací paměti pro příjem.|  
|sendBufferSize|Určuje velikost vyrovnávací paměti pro odesílání.|  
|dílčí protokol|Určuje dílčí protokol Websocket.|  
|transportUsage|Určuje, kdy se má použít objekty Websocket.|  
  
## <a name="transportusage-attribute"></a>transportUsage atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|WhenDuplex|Protokol Websocket po duplexní kontrakt.|  
|Vždy|Vždy používejte protokol Websocket bez ohledu na to, kontrakt.|  
|Nikdy|Nikdy nepoužívejte protokolu Websocket.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|\<netHttpBinding >|Určuje vazeb NetHttpBinding|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití \<webSocketSettings > element.  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
