---
title: '&lt;webSocketSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ee0f555fc1e3412032e0a7dda3a747bbfef6f4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebsocketsettingsgt"></a>&lt;webSocketSettings&gt;
Element konfigurace slouží k zadání nastavení Websocket.  
  
\<systém. ServiceModel >  
\<vazby >  
\<netHttpBinding >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netHttpBinding>  
  <binding>   
    <webSocketSettings createNotificationOnConnection="boolean" 
                       disablePayloadMasking="boolean" 
                       keepAliveInterval="TimeSpan" 
                       maxPendingConnections="Integer" 
                       receiveBufferSize="Integer" 
                       sendBufferSize="Integer" 
                       subProtocol="String" 
                       transportUsage="WhenDuplex/Always/Never"/>
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|createNotificationOnConnection|Určuje, zda jsou oznámení odesílána při připojení.|  
|disablePayloadMasking|Určuje, zda je zakázána Websocket maskování.|  
|keepAliveInterval|Určuje interval zachovat zachování připojení.|  
|maxPendingConnections|Určuje maximální počet připojení, které čekají na odeslání ve službě.|  
|receiveBufferSize|Určuje velikost vyrovnávací paměti pro příjem.|  
|sendBufferSize|Určuje velikost vyrovnávací paměti pro odesílání.|  
|subProtocol|Určuje subprotocol Websocket.|  
|transportUsage|Určuje, kdy se mají použít objekty Websocket.|  
  
## <a name="transportusage-attribute"></a>transportUsage atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|WhenDuplex|Po duplexní kontrakt používejte protokol Websocket.|  
|Vždy|Vždy používejte protokol Websocket bez ohledu na to, kontrakt.|  
|Nikdy|Nikdy používat protokol Websocket.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|\<netHttpBinding >|Určuje vazeb NetHttpBinding|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat \<webSocketSettings > elementu.  
  
```xml  
<netHttpBinding>  
        <binding>  
          <webSocketSettings createNotificationOnConnection="true"  
                              disablePayloadMasking="false  
                              keepAliveInterval="00:10:00"  
                              maxPendingConnections="100"  
                              receiveBufferSize="1000"  
                              sendBufferSize="1000"  
                              subProtocol="Soap"  
                              transportUsage="WhenDuplex/Always/Never"/>  
  
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
 [Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Vazba >](../../../../../docs/framework/misc/binding.md)
