---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 95ce89aabb400c01002799fd8251383a2e5dd4c2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732706"
---
# <a name="udpbinding"></a>\<udpBinding >
Prvek konfigurace, který slouží ke konfiguraci vazby <xref:System.ServiceModel.UdpBinding>.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<udpBinding >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<udpBinding>
  <binding closeTimeout="TimeSpan"
           duplicateMessageHistoryLength="Integer"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxPendingMessagesTotalSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetransmitCount="Integer"
           multicastInterfaceId="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           timeToLive="TimeSpan">
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`closeTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`duplicateMessageHistoryLength`|Celočíselná hodnota, která určuje duplicitní délku historie zprávy.|  
|`maxBufferPoolSize`|Celočíselná hodnota, která určuje maximální velikost paměti, která je přidělena pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z kanálu. Výchozí hodnota je 524288 (0x80000) bajtů.|  
|`maxBufferSize`|Celočíselná hodnota, která určuje maximální velikost vyrovnávací paměti v bajtech, která ukládá zprávy, když jsou zpracovávány pro koncový bod nakonfigurovaný pomocí této vazby. Výchozí hodnota je 65 536 bajtů.|  
|`maxPendingMessagesTotalSize`|Celočíselná hodnota, která určuje maximální počet zpráv, které byly přijaty, ale nebyly dosud odebrány ze vstupní fronty pro jednotlivou instanci kanálu.|  
|`maxReceivedMessageSize`|Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně hlaviček, pro zprávu, která se dá přijmout na kanálu nakonfigurovaném pomocí této vazby. Odesilatel obdrží chybu protokolu SOAP, pokud je zpráva pro příjemce příliš velká. Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65 536 bajtů.|  
|`maxRetransmitCount`|Celočíselná hodnota, která určuje maximální počet znovu odeslaných zpráv.|  
|`multicastInterfaceId`|Celočíselná hodnota, která určuje ID rozhraní vícesměrového vysílání.|  
|`name`|Řetězec, který obsahuje název konfigurace vazby. Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby. Každá vazba má atribut `name` a `namespace`, který ji společně jednoznačně identifikuje v metadatech služby. Kromě toho je tento název jedinečný mezi vazbami stejného typu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]nejsou vazby a chování nutné mít název. Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`receiveTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|`sendTimeout`|Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání. Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`textEncoding`|Nastaví kódování znakové sady, které se má použít pro generování zpráv ve vazbě. Platné hodnoty jsou následující:<br /><br /> -BigEndianUnicode: kódování Unicode BigEndian.<br />-Unicode: 16 bitů kódování.<br />-UTF8:8bitové kódování<br /><br /> Výchozí hodnota je UTF8. Tento atribut je typu <xref:System.Text.Encoding>.|  
|`timeToLive`|Hodnota TimeSpan, která určuje dobu, po kterou má být tato vazba živá.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[vazby\<](bindings.md)|Tento prvek obsahuje kolekci standardních a vlastních vazeb.|  
  
## <a name="remarks"></a>Poznámky  
 UdpBinding umožňuje službám WCF komunikovat přes přenos UDP. Umožňuje výměnu zpráv typu "oheň a zapomenout", kde klient odesílá zprávu službě a neočekává zpětnou odezvu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat <xref:System.ServiceModel.UdpBinding> pomocí elementu <`udpBinding`>.  
  
```xml  
<udpBinding>
  <binding  closeTimeout="00:10:00"
            duplicateMessageHistoryLength="100"
            maxBufferPoolSize="100"
            maxPendingMessagesTotalSize="100000"
            maxReceivedMessageSize="65536"
            maxRetransmitCount="10"
            multicastInterfaceId="00000"
            name="myUdpBinding"
            openTimeout="00:10:00"
            receiveTimeout="00:10:00"
            sendTimeout="00:10:00"
            textEncoding="utf-8"
            timeToLive="00:10:00">
    <readerQuotas />
  </binding>
</udpBinding>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [vazba \<](bindings.md)
