---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 6765259f290047a4199a422b4ad0cced2ffee9ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179826"
---
# <a name="peertransport"></a>\<peerTransport >
Definuje rovnocenný přenos pro vlastní vazbu.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<peerTransport >  
  
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
|listenIpAddress|Řetězec, který určuje IP adresu, na které bude partnerský uzel přijímat zprávy TCP. Výchozí hodnota je `null`.|  
|maxBufferPoolSize|Kladné celé číslo, které určuje maximální velikost fondu vyrovnávacích pamětí. Výchozí hodnota je 524288.<br /><br /> Mnoho částí WCF pomocí vyrovnávací paměti. Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné. S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi. Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.|  
|maxReceivedMessageSize|Kladné celé číslo, které definuje maximální velikost zprávy v bajtech, včetně záhlaví. Odesílatel zprávy obdrží chybu protokolu SOAP v případě, že zprávy je příliš velký pro příjemce. Příjemce zahodí a vytvoří záznam události v protokolu trasování. Výchozí hodnota je 65536.|  
|port|Celé číslo, které určuje portu síťového rozhraní, na které bude tato vazba zpracovávat zprávy TCP rovnocenného kanálu. Tato hodnota musí být mezi <xref:System.Net.IPEndPoint.MinPort> a <xref:System.Net.IPEndPoint.MaxPort>. Výchozí hodnota je 0.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|Definuje nastavení zabezpečení pro tento přenos. Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vázání pro vlastní vazbu.|  
  
## <a name="remarks"></a>Poznámky  
 Tento přenos nelze použít s smluv, které mají operace požadavku/odpovědi.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
