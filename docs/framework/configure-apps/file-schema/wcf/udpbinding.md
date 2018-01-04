---
title: '&lt;udpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f43462ac42c59407ae90f2d342a445a688e1b26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltudpbindinggt"></a>&lt;udpBinding&gt;
Element konfigurace slouží ke konfiguraci <xref:System.ServiceModel.UdpBinding> vazby.  
  
 \<systém. ServiceModel >  
\<vazby >  
\<udpBinding >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<udpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       duplicateMessageHistoryLength="Integer"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"       maxPendingMessagesTotalSize="Integer"  
       maxReceivedMessageSize="Integer"       maxRetransmitCount="Integer"  
       multicastInterfaceId="Integer"  
              name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
       textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
       timeToLive="TimeSpan">  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"             maxNameTableCharCount="Integer"                maxStringContentLength="Integer" />  
   </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`closeTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`duplicateMessageHistoryLength`|Celočíselná hodnota, která určuje, jak dlouho historie duplicitní zpráva.|  
|`maxBufferPoolSize`|Celočíselná hodnota, která určuje maximální množství paměti přidělené pro použití správcem vyrovnávacích pamětí zpráv, které přijímají zprávy z tohoto kanálu. Výchozí hodnota je 524288 (0x80000) bajtů.|  
|`maxBufferSize`|Celočíselná hodnota, která určuje maximální velikost v bajtech vyrovnávací paměti, která ukládá zprávy, když jsou zpracovávány pro koncovým bodem nakonfigurovaným s touto vazbou. Výchozí hodnota je 65 536 bajtů.|  
|`maxPendingMessagesTotalSize`|Celočíselná hodnota, která určuje maximální počet zpráv, které byly přijaty, ale ještě nebyla odebrána z vstupní fronty pro instance jednotlivých kanálu.|  
|`maxReceivedMessageSize`|Kladné celé číslo, které definuje maximální velikost zprávy, v bajtech, včetně záhlaví zprávy, která lze přijímat pomocí kanálu nakonfigurovaným s touto vazbou. Odesílatel obdrží chybu protokolu SOAP, pokud zpráva je příliš velké vzhledem k příjemce. Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování. Výchozí hodnota je 65 536 bajtů.|  
|`maxRetransmitCount`|Celočíselná hodnota, která určuje maximální počet opakování přenosu zpráv.|  
|`multicastInterfaceId`|Celočíselná hodnota, která určuje ID rozhraní vícesměrového vysílání.|  
|`name`|Řetězec, který obsahuje název konfigurace vazby. Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu. Má každou vazbu `name` a `namespace` atributů, které společně jednoznačně identifikovat v metadatech služby. Kromě toho je tento název jedinečný mezi vazby stejného typu. Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název. Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`receiveTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:10:00.|  
|`sendTimeout`|A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání. Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>. Výchozí hodnota je 00:01:00.|  
|`textEncoding`|Nastaví znak, nastavení kódování, který se má použít pro vysílání zpráv v vazby. Platné hodnoty patří:<br /><br /> -BigEndianUnicode: Unicode BigEndian kódování.<br />-Unicode: 16bitové kódování.<br />-UTF8: kódování 8bitové<br /><br /> Výchozí hodnota je UTF8. Tento atribut je typu <xref:System.Text.Encoding>.|  
|`timeToLive`|Hodnota časového rozpětí určující TTL pro vazbu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby. Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<vazby >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Tento prvek obsahuje kolekci standardní a vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 UdpBinding umožňuje službám WCF pro komunikaci pomocí přenosu UDP. To umožňuje používat pro "fire a zapomněli" výměny zpráv kde klient odešle zprávu do služby a očekává žádná odpověď zpět.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat <xref:System.ServiceModel.UdpBinding> pomocí <`udpBinding`> elementu.  
  
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
                   timeToLive="00:10:00"  
          <readerQuotas/>   
        </binding>  
      </udpBinding>  
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
