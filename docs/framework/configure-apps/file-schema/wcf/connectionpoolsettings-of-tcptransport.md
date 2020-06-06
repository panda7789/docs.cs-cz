---
title: <connectionPoolSettings> z <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: f9b0fff741c32c1a3d6f9461f478e89acc18114e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398100"
---
# <a name="connectionpoolsettings-of-tcptransport"></a>\<connectionPoolSettings> z \<tcpTransport>
Určuje další nastavení fondu připojení pro přenos TCP.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tcpTransport>**](tcptransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`groupName`|Řetězec definující název fondu připojení, který se používá pro odchozí kanály. V režimu streamování nejsou připojení sdílená, což znamená, že sdružování připojení je zakázané. Výchozí hodnota je "výchozí" řetězec. Tuto hodnotu můžete upravit a izolovat připojení pro konkrétního klienta do samostatných skupin.|  
|`idleTimeout`|Kladná hodnota <xref:System.TimeSpan> , která určuje maximální dobu, po kterou může být připojení nečinné, než bude odpojeno. Výchozí hodnota je 00:02:00.|  
|`leaseTimeout`|A <xref:System.TimeSpan> Určuje dobu, po jejímž uplynutí je aktivní připojení ukončeno. Výchozí hodnota je 00:05:00.<br /><br /> Po návratu do mezipaměti připojení a při aktivním přenosu se připojení zavře. Mezipaměť připojení, kterou přenos TCP používá, vytvoří nová připojení podle požadavků pro každý koncový bod až do limitu mezipaměti, který nastaví.`maxOutboundConnectionsPerEndpoint.`|  
|`maxOutboundConnectionsPerEndpoint`|Celé kladné číslo určující maximální počet připojení ke vzdálenému koncovému bodu iniciované službou. Překročení limitu se zařadí do fronty, dokud nebude k dispozici mezera pod limitem. `idleTimeout`Omezuje dobu trvání, během které zůstanou připojení zařazená do fronty, než je vyvolána výjimka. Výchozí hodnota je 10.<br /><br /> Tento atribut omezuje počet současných aktivních připojení z klienta na konkrétní koncový bod služby. Pokud je tato hodnota překročena o více aktivních připojeních klienta, může se stát, že služba přestane reagovat na klienta. V takovém případě by tato hodnota měla být upravena tak, aby překročila maximální počet očekávaných současných připojení klientů ke konkrétnímu koncovému bodu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|Definuje přenos, který způsobuje, že kanál přenáší zprávy pomocí pojmenovaných kanálů.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Přenosy](../../../wcf/feature-details/transports.md)
- [Volba přenosu](../../../wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
