---
title: <udpTransportSettings> z <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: a7ddff1a-5eed-4bbc-8580-b95ef8890e1f
ms.openlocfilehash: b67bdf825948dffe18aabe91b0de236eb929bccc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854845"
---
# <a name="udptransportsettings-of-udpannouncementendpoint"></a>\<udpTransportSettings > \<udpAnnouncementEndpoint >
Tento prvek konfigurace zveřejňuje nastavení přenosu UDP pro [ \<udpAnnouncementEndpoint >](udpannouncementendpoint.md).  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<udpAnnouncementEndpoint >** ](udpannouncementendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<updTransportSettings >**  

## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpAnnouncementEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer"
                              maxBufferPoolSize="Integer"
                              maxMulticastRetransmitCount="Integer"
                              maxPendingMessageCount="Integer"
                              maxReceivedMessageSize="Integer"
                              maxUnicastRetransmitCount="Integer"
                              multicastInterfaceId="String"
                              socketReceiveBufferSize="Integer"
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpAnnouncementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|duplicateMessageHistoryLength|Celé číslo, které určuje maximální počet hodnot hash zpráv používaných při přenosu pro identifikaci duplicitních zpráv.  Vyhledávání duplicit bude provedeno na úrovni správce TransportManager. Nastavením této vlastnosti na hodnotu 0 zakážete detekci duplicit.<br /><br /> Tento atribut umožňuje správcům systému nebo vývojářům vypnout algoritmy pro detekci duplicitních zpráv. To může být žádoucí, pokud chcete implementovat vlastní algoritmus zjišťování duplicit.<br /><br /> Výchozí hodnota je 4112.|  
|maxBufferPoolSize|Celé číslo, které určuje maximální velikost všech fondů vyrovnávacích pamětí používaných při přenosu.|  
|maxMulticastRetransmitCount|Celé číslo, které určuje maximální počet, kolikrát se má zpráva znovu přenést (kromě prvního odeslání).<br /><br /> Výchozí hodnota je 2.|  
|maxPendingMessageCount|Celé číslo, které určuje maximální počet zpráv, které byly přijaty, ale nebyly odebrány z InputQueue pro jednotlivé instance kanálu.  Pokud InputQueue dosáhlo limitu počtu nedokončených zpráv, zpráva se vynechá.<br /><br /> Výchozí hodnota je 32.|  
|maxReceivedMessageSize|Celé číslo, které určuje maximální velikost zprávy, která může být zpracována vazbou.<br /><br /> Výchozí hodnota je 65507.|  
|maxUnicastRetransmitCount|Celé číslo, které určuje maximální počet, kolikrát se má zpráva znovu přenést (kromě prvního odeslání).  Pokud se zpráva pošle na adresu jednosměrového vysílání a přijata zpráva odpovědi s odpovídající hlavičkou RelatesTo, může se opakovaný přenos ukončit včas (před opakovaným odesláním konfigurovaného počtu).<br /><br /> Výchozí hodnota je 1.|  
|multicastInterfaceId|Řetězec, který jednoznačně identifikuje síťový adaptér, který se má použít při odesílání a přijímání vícesměrového přenosu na více domácích počítačích. Za běhu bude přenos používat tuto hodnotu atributu pro vyhledání indexu rozhraní, který se pak použije k nastavení `IP_MULTICAST_IF` možnosti soketu a. `IPV6_MULTICAST_IF`  Stejný index rozhraní se použije při připojení ke skupině vícesměrového vysílání (Pokud je k dispozici).<br /><br /> Výchozí hodnota je `null`.|  
|socketReceiveBufferSize|Celé číslo, které určuje velikost vyrovnávací paměti pro příjem na základním soketu WinSock.<br /><br /> Uživatel přijímacího kanálu může tento atribut u vazby použít k řízení toho, jak se systém chová při přijímání dat.  Například vzhledem k tomu, že aplikace, která spotřebovává příchozí zprávy WCF s maximální prahovou hodnotou, bude pomocí vyšší hodnoty pro tento atribut umožňovat, aby se zprávy navrstveny ve vyrovnávací paměti rozhraní WinSock při čekání, až aplikace bude schopna je zpracovat.  Použití nižší hodnoty ve stejné situaci způsobí, že se zprávy vynechává. Tento atribut zpřístupňuje základní možnost `SO_RCVBUF` soketu rozhraní Winsock. Hodnota tohoto atributu musí být alespoň velikost `maxReceivedMessageSize`.   Jeho nastavení na hodnotu menší, než `maxReceivedMessageSize` výsledkem bude výjimka za běhu.<br /><br /> Výchozí hodnota je 65536.|  
|timeToLive|Celé číslo, které určuje počet segmentů směrování sítě, které může procházet paket vícesměrového vysílání.  Tento atribut zpřístupňuje funkce přidružené `IP_MULTICAST_TTL` k možnostem soketu a. `IP_TTL`<br /><br /> Výchozí hodnota je 1.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<udpAnnouncementEndpoint>](udpannouncementendpoint.md)|Standardní koncový bod, který má pevně daný kontrakt oznámení a přenosovou vazbu UDP.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
