---
title: <connectionPoolSettings> z <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 93363c5ff1753ff02956404da7697780078c9839
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129971"
---
# <a name="connectionpoolsettings-of-tcptransport"></a>\<connectionPoolSettings> of \<tcpTransport>
Určuje další nastavení fondu připojení přenosu protokolu TCP.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<tcpTransport>  
\<connectionPoolSettings>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`groupName`|Řetězec, který definuje název fondu připojení používaný pro odchozí kanály. V proudu režimu nejsou sdíleny připojení, což znamená, že je zakázána sdružování připojení. Výchozí hodnota je řetězec "Výchozí". Tato hodnota k izolaci připojení pro konkrétního klienta do samostatných skupin můžete upravit.|  
|`idleTimeout`|Pozitivní <xref:System.TimeSpan> , která určuje maximální dobu, může být připojení nečinné, než je odpojeno. Výchozí hodnota je 00:02:00.|  
|`leaseTimeout`|A <xref:System.TimeSpan> , který určuje dobu, po jejímž uplynutí aktivní připojení ukončeno. Výchozí hodnota je 00:05:00.<br /><br /> Poté, co se vrátí do mezipaměti připojení a ne během aktivní přenos, je připojení ukončeno. Mezipaměť připojení přenosu protokolu TCP používané vytvoří nové připojení pro každý koncový bod, až po limit mezipaměti, který je nastaven podle potřeby `maxOutboundConnectionsPerEndpoint.`|  
|`maxOutboundConnectionsPerEndpoint`|Kladné celé číslo, které určuje maximální počet připojení na vzdálený koncový bod iniciovaných službou. Připojení nad tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit. `idleTimeout` Omezení doby trvání, ve kterém připojení zůstat ve frontě, než dojde k výjimce. Výchozí hodnota je 10.<br /><br /> Tento atribut omezuje počet souběžných aktivních připojení z klienta do koncového bodu konkrétní služby. Pokud se překročí tuto hodnotu tak, že více aktivních připojení klienta, se můžou objevit reagovat na klienta služby. V takovém případě by měla být přizpůsobena tuto hodnotu delší než maximální počet očekávaných simultánních klientských připojení do určitého koncového bodu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<namedPipeTransport>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|Definuje přenos, který způsobí přenos zpráv pomocí pojmenovaných kanálů.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
