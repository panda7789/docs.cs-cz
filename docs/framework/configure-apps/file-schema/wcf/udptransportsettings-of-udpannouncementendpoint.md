---
title: <udpTransportSettings> z <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: a7ddff1a-5eed-4bbc-8580-b95ef8890e1f
ms.openlocfilehash: 901b7e1429c3afc19e9b609026dc632730c35024
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148327"
---
# <a name="udptransportsettings-of-udpannouncementendpoint"></a>\<udpTransportSettings > z \<udpAnnouncementEndpoint >
Tento prvek konfigurace zpřístupňuje nastavení přenosu UDP pro [ \<udpAnnouncementEndpoint >](udpannouncementendpoint.md).  
  
\<system.ServiceModel>  
\<standardEndpoints>  
\<udpAnnouncementEndpoint>  
  
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
|duplicateMessageHistoryLength|Celé číslo určující maximální počet Transport používá k identifikaci duplicitních zpráv o hodnotách hash zpráv.  Zjišťování duplicit se provádí na úrovni Správce TransportManager. Nastavení této vlastnosti na hodnotu 0 zakáže vyhledávání duplicit.<br /><br /> Tento atribut umožňuje správcům systému a vývojáři, chcete-li vypnout algoritmy detekce duplicitních zpráv. To může být žádoucí, pokud chcete implementovat vlastní vyhledávání duplicit algoritmus.<br /><br /> Výchozí hodnota je 4112.|  
|maxBufferPoolSize|Celé číslo, které určuje maximální velikost všechny fondy vyrovnávací paměti používané přenos.|  
|maxMulticastRetransmitCount|Celé číslo, které určuje maximální počet pokusů, které se zpráva by měl být přenášena (kromě poslat prvním).<br /><br /> Výchozí hodnota je 2.|  
|maxPendingMessageCount|Celé číslo určující maximální počet zpráv, které bylo přijato, ale ještě nebyla odebrána z InputQueue instance jednotlivých kanálů.  Pokud InputQueue dosáhl svého limitu počtu zpráv, zpráva se zahodí.<br /><br /> Výchozí hodnota je 32.|  
|maxReceivedMessageSize|Celé číslo, které určuje maximální velikost zprávy, která může být zpracována vazbou.<br /><br /> Výchozí hodnota je 65507.|  
|maxUnicastRetransmitCount|Celé číslo, které určuje maximální počet pokusů, které se zpráva by měl být přenášena (kromě poslat prvním).  Pokud je zpráva odeslána na adresu jednosměrového vysílání a obdrží zprávu odpovědi s odpovídající záhlavím RelatesTo, může ukončit opakovaný přenos zpráv již v rané fázi (před opětovným odesláním nakonfigurovaný počet, kolikrát).<br /><br /> Výchozí hodnota je 1.|  
|multicastInterfaceId|Řetězec, který jednoznačně identifikuje síťový adaptér, který se má použít při odesílání a přijímání dat na počítačích s více adresami vícesměrového vysílání. Za běhu, použije přenos hodnota tohoto atributu pro vyhledání rozhraní index, který potom slouží k nastavení `IP_MULTICAST_IF` a `IPV6_MULTICAST_IF` soketu možnosti.  Stejný index rozhraní se použijí při připojení ke skupině vícesměrového vysílání, pokud je k dispozici.<br /><br /> Výchozí hodnota je `null`.|  
|socketReceiveBufferSize|Celé číslo, které určuje velikost vyrovnávací paměti příjmu na základní soketu rozhraní WinSock.<br /><br /> Uživatel přijímající kanálu můžete použít tento atribut ve vazbě řídit, jak se systém chová, když přijme data.  Například aplikace, která je přijímat příchozí zprávy WCF při dosažení maximálního povoleného počtu směru, použitím vyšší hodnoty pro tento atribut by umožnilo zprávy ukládány do vyrovnávací paměti rozhraní WinSock při čekání na aplikaci, která bude moct zpracovat.  Použití nižší hodnotu ve stejné situaci by mít za následek získávání počet ztracených zpráv. Tento atribut zpřístupňuje základní rozhraní WinSock `SO_RCVBUF` možnost soketu. Hodnota tohoto atributu musí být dlouhý aspoň velikost `maxReceivedMessageSize`.   Nastavení na hodnotu menší, než `maxReceivedMessageSize` způsobí výjimku při běhu.<br /><br /> Výchozí hodnota je 65536.|  
|timeToLive|Celé číslo určující počet segmentů směrování segmentu, které můžete procházet paketů vícesměrového vysílání.  Tento atribut zpřístupňuje funkce související s `IP_MULTICAST_TTL` a `IP_TTL` soketu možnosti.<br /><br /> Výchozí hodnota je 1.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<udpAnnouncementEndpoint>](udpannouncementendpoint.md)|Je standardní koncový bod, který se má vyřešit oznámení, že vazby přenosu kontrakt a UDP.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
