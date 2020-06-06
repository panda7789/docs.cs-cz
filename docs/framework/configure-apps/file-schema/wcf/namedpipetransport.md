---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 00631ad88d771ed8f45638f28c84df05917fd3a0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736582"
---
# \<namedPipeTransport>
Definuje přenos, který způsobuje, že kanál přenáší zprávy pomocí pojmenovaných kanálů, pokud je součástí vlastní vazby.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|ChannelInitializationTimeout|Získá nebo nastaví <xref:System.TimeSpan> , který určuje maximální dobu, po kterou může kanál ve stavu inicializace, než bude odpojen.|  
|ConnectionBufferSize|Získá nebo nastaví velikost vyrovnávací paměti, která se používá k přenosu bloku serializované zprávy na lince z klienta nebo služby.|  
|hostNameComparisonMode|Získává nebo nastavuje hodnotu, která indikuje, jestli se k dosažení služby při shodě s identifikátorem URI používá název hostitele.|  
|Jeho|Získává nebo nastavuje hodnotu, která indikuje, jestli se vyžaduje ruční adresování zprávy.|  
|maxBufferPoolSize|Získá nebo nastaví maximální velikost všech fondů vyrovnávací paměti používaných při přenosu (v bajtech).|  
|Třída|Získá nebo nastaví maximální velikost vyrovnávací paměti, která se má použít. U zpráv v datových proudech by tato hodnota měla být alespoň maximální možná velikost záhlaví zprávy, která je čtena v režimu vyrovnávací paměti.|  
|maxOutputDelay|Získá nebo nastaví maximální časový interval, po který může blok zprávy nebo úplná zpráva zůstat v paměti před odesláním do vyrovnávací paměti.|  
|maxPendingAccepts|Získá nebo nastaví maximální počet kanálů, které může služba čekat na naslouchací proces pro zpracování příchozích připojení ke službě.|  
|maxPendingConnections|Získá nebo nastaví maximální počet připojení čekajících na odeslání ve službě.|  
|maxReceivedMessageSize|Získá a nastaví maximální povolenou velikost zprávy (v bajtech), kterou lze přijmout.|  
|Třídy TransferMode|Získává nebo nastavuje hodnotu, která indikuje, jestli se zprávy ukládají do vyrovnávací paměti nebo streamují s přenosem orientovaným na připojení.|  
|[\<connectionPoolSettings>tohoto\<namedPipeTransport>](connectionpoolsettings.md)|Určuje další nastavení fondu připojení pro vazbu pojmenovaného kanálu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
Tento přenos používá identifikátory URI ve formátu "NET. pipe://hostname/Path". Jiné součásti identifikátoru URI jsou volitelné.  
  
`namedPipeTransport`Element je výchozím bodem pro vytvoření vlastní vazby, která implementuje transportní protokol pojmenovaných kanálů. Tento přenos se používá pro komunikaci mezi počítači Windows Communication Foundation (WCF) a WCF.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Přenosy](../../../wcf/feature-details/transports.md)
- [Volba přenosu](../../../wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
