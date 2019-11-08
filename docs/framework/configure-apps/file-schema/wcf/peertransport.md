---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 99fb013e052329ae4b99c4db89565ace8935c456
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736507"
---
# <a name="peertransport"></a>\<peerTransport >
Definuje partnerský přenos pro vlastní vazbu.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<peerTransport >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Třída ListenIPAddress|Řetězec, který určuje IP adresu, na které bude partnerský uzel naslouchat zprávám TCP. Výchozí hodnota je `null`.|  
|maxBufferPoolSize|Kladné celé číslo, které určuje maximální velikost fondu vyrovnávací paměti. Výchozí hodnota je 524288.<br /><br /> Mnoho částí služby WCF používá vyrovnávací paměti. Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné. Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu. Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.|  
|maxReceivedMessageSize|Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně záhlaví. Odesílatel zprávy obdrží chybu protokolu SOAP, pokud je zpráva pro příjemce příliš velká. Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65536.|  
|port|Celé číslo určující, na kterém portu síťového rozhraní bude tato vazba zpracovávat zprávy TCP rovnocenného kanálu. Tato hodnota musí být mezi <xref:System.Net.IPEndPoint.MinPort> a <xref:System.Net.IPEndPoint.MaxPort>. Výchozí hodnota je 0.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[> zabezpečení \<](security-of-peertransport.md)|Definuje nastavení zabezpečení pro tento přenos. Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[vazba \<](bindings.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Tento přenos nelze použít u kontraktů, které mají operace požadavku a odpovědi.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Přenosy](../../../wcf/feature-details/transports.md)
- [Volba přenosu](../../../wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
