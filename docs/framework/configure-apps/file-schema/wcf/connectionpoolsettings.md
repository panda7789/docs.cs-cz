---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 3c8d905a04f8f6d7ecff9b0ef9e7d3c8afa727e3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925965"
---
# <a name="connectionpoolsettings"></a>\<connectionPoolSettings>
Určuje další nastavení fondu připojení pro vazbu pojmenovaného kanálu.  
  
 \<system.serviceModel>  
\<> vazeb  
\<customBinding >  
\<> vazby  
\<namePipeTransport >  
\<connectionPoolSettings>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`groupName`|Řetězec definující název fondu připojení, který se používá pro odchozí kanály. V režimu streamování nejsou připojení sdílená, což znamená, že sdružování připojení je zakázané. Výchozí hodnota je "výchozí" řetězec. Tuto hodnotu můžete upravit a izolovat připojení pro konkrétního klienta do samostatných skupin.|  
|`idleTimeout`|Kladná <xref:System.TimeSpan> hodnota, která určuje maximální dobu, po kterou může být připojení nečinné, než bude odpojeno. Výchozí hodnota je 00:02:00.|  
|`maxOutboundConnectionsPerEndpoint`|Celé kladné číslo určující maximální počet připojení ke vzdálenému koncovému bodu iniciované službou. Překročení limitu se zařadí do fronty, dokud nebude k dispozici mezera pod limitem. `idleTimeout` Omezuje dobu trvání, během které zůstanou připojení zařazená do fronty, než je vyvolána výjimka. Výchozí hodnota je 10.<br /><br /> Tento atribut omezuje počet současných aktivních připojení z klienta na konkrétní koncový bod služby. Pokud je tato hodnota překročena o více aktivních připojeních klienta, může se stát, že služba přestane reagovat na klienta. V takovém případě by tato hodnota měla být upravena tak, aby překročila maximální počet očekávaných současných připojení klientů ke konkrétnímu koncovému bodu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|Definuje přenos, který způsobuje, že kanál přenáší zprávy pomocí pojmenovaných kanálů.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Přenosy](../../../wcf/feature-details/transports.md)
- [Volba přenosu](../../../wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
