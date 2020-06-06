---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: fa87a1b0961425d6a9bc84769bef6e87cbc2ce96
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732551"
---
# \<webSocketSettings>
Prvek konfigurace, který slouží k zadání nastavení webového soketu.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
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
|createNotificationOnConnection|Určuje, zda je při připojení odesláno oznámení.|  
|disablePayloadMasking|Určuje, jestli je zakázané maskování webového soketu.|  
|keepAliveInterval|Určuje interval Keep Alive.|  
|maxPendingConnections|Určuje maximální počet připojení čekajících na odeslání ve službě.|  
|receiveBufferSize|Určuje velikost vyrovnávací paměti pro příjem.|  
|sendBufferSize|Určuje velikost vyrovnávací paměti pro odeslání.|  
|Dílčí protokol|Určuje dílčí protokol webového soketu.|  
|transportUsage|Určuje, kdy se mají používat webové sokety.|  
  
## <a name="transportusage-attribute"></a>transportUsage – atribut  
  
|Hodnota|Description|  
|-----------|-----------------|  
|WhenDuplex|Protokol webového soketu použijte v případě, že je kontrakt duplexní.|  
|Vždy|Vždy používejte protokol webového soketu bez ohledu na kontrakt.|  
|Nikdy|Nikdy nepoužívejte protokol webového soketu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|\<netHttpBinding>|Určuje NetHttpBinding|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít \<webSocketSettings> element.  
  
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

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
