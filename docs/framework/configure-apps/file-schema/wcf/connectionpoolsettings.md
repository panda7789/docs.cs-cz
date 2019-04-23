---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: b1ff302a46605cb78fe567a63f66723ed757f147
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169985"
---
# <a name="connectionpoolsettings"></a>\<connectionPoolSettings>
Určuje další nastavení fondu připojení pro vazbu pojmenovaného kanálu.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<namePipeTransport >  
\<connectionPoolSettings>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`groupName`|Řetězec, který definuje název fondu připojení používaný pro odchozí kanály. V proudu režimu nejsou sdíleny připojení, což znamená, že je zakázána sdružování připojení. Výchozí hodnota je řetězec "Výchozí". Tato hodnota k izolaci připojení pro konkrétního klienta do samostatných skupin můžete upravit.|  
|`idleTimeout`|Pozitivní <xref:System.TimeSpan> , která určuje maximální dobu, může být připojení nečinné, než je odpojeno. Výchozí hodnota je 00:02:00.|  
|`maxOutboundConnectionsPerEndpoint`|Kladné celé číslo, které určuje maximální počet připojení na vzdálený koncový bod iniciovaných službou. Připojení nad tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit. `idleTimeout` Omezení doby trvání, ve kterém připojení zůstat ve frontě, než dojde k výjimce. Výchozí hodnota je 10.<br /><br /> Tento atribut omezuje počet souběžných aktivních připojení z klienta do koncového bodu konkrétní služby. Pokud se překročí tuto hodnotu tak, že více aktivních připojení klienta, se můžou objevit reagovat na klienta služby. V takovém případě by měla být přizpůsobena tuto hodnotu delší než maximální počet očekávaných simultánních klientských připojení do určitého koncového bodu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<namedPipeTransport>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|Definuje přenos, který způsobí přenos zpráv pomocí pojmenovaných kanálů.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
