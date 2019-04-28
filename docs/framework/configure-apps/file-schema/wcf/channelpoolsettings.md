---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: ca1f680e2de67984dfcec49b3d262799000a2625
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673326"
---
# <a name="channelpoolsettings"></a>\<channelPoolSettings>
Určuje nastavení fondu kanálu pro vlastní vazbu.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<oneWay>  
\<channelPoolSettings>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`idleTimeout`|Pozitivní <xref:System.TimeSpan> , která určuje maximální dobu kanály ve fondu může být neaktivní, než je odpojeno. Výchozí hodnota je 00:02:00.|  
|`leaseTimeout`|A <xref:System.TimeSpan> , který určuje dobu, po jejímž uplynutí je kanál, když je vrácen do fondu, uzavřen. Výchozí hodnota je 00:10:00.|  
|`maxOutboundChannelsPerEndpoint`|Kladné celé číslo, určující maximální počet kanálů, které mohou být uloženy ve fondu pro každý vzdálený koncový bod. Výchozí hodnota je 10.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<oneWay>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|Umožňuje směrování paketů pro vlastní vazbu.|  
  
## <a name="remarks"></a>Poznámky  
 Kvóty slouží jako vhodný mechanismus zásady zabránit spotřebu nadměrné prostředků. Brání tomu, aby útoků s cílem odepření služby (DOS), které jsou škodlivých aktivit nebo neúmyslným. Při nastavování kvóty kanál ve vlastním kanálu pomocí tohoto prvku.  
  
 `ChannelPoolSettings` Určuje tři kvót:  
  
- `idleTimeout` Kvóty slouží ke zmírnění útoků s cílem odepření služby (DOS) na serveru, které využívají obsadit prostředků delší dobu. Na straně klienta můžete nastavení správnou hodnotu zvýšit spolehlivost připojení ke službě. Výchozí hodnota je založena na konzervativní zvýšení přidělení prostředků. Je vhodný pro vývojové prostředí a scénářů malé instalace. Správci služeb by měl zkontrolujte hodnotu, pokud instalace může být nedostatek prostředků, nebo pokud připojení jsou omezeno bez ohledu na dostupnost další prostředky.  
  
- `leaseTimeout` Kvóty slouží k integraci s nástroji pro vyrovnávání zatížení a zlepšení spolehlivosti. Výchozí hodnota je založena na konzervativní přidělení prostředků. Je vhodný pro vývojové prostředí a scénářů malé instalace. Správci služeb by měl zkontrolujte hodnotu, pokud instalace může být nedostatek prostředků, nebo pokud připojení jsou omezeno bez ohledu na dostupnost další prostředky.  
  
- `maxOutboundChannelsPerEndpoint` Kvóta nastavuje omezení mezipaměti na serveru a klienta a slouží ke zlepšení spolehlivosti. Výchozí hodnota je založena na konzervativní zvýšení přidělení prostředků, která je vhodná pro malé instalace scénáře a vývojové prostředí. Správci služeb by měl zkontrolujte hodnotu, pokud instalace může být nedostatek prostředků, nebo pokud připojení jsou omezeno bez ohledu na dostupnost další prostředky.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
