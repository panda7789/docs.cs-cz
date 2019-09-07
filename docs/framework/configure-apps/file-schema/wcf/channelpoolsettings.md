---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 26537980a6be5c0fe12661d93a6ba5fe862ceb4e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398162"
---
# <a name="channelpoolsettings"></a>\<channelPoolSettings>
Určuje nastavení fondu kanálu pro vlastní vazbu.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> oneWay**](oneway.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<channelPoolSettings >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`idleTimeout`|Kladná <xref:System.TimeSpan> hodnota, která určuje maximální dobu, po kterou můžou být kanály ve fondu nečinné, než se odpojí. Výchozí hodnota je 00:02:00.|  
|`leaseTimeout`|A <xref:System.TimeSpan> určuje časový interval, po jehož uplynutí je kanál, který byl vrácen do fondu, uzavřen. Výchozí hodnota je 00:10:00.|  
|`maxOutboundChannelsPerEndpoint`|Celé kladné číslo určující maximální počet kanálů, které mohou být uloženy ve fondu pro každý vzdálený koncový bod. Výchozí hodnota je 10.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<oneWay>](oneway.md)|Povolí směrování paketů pro vlastní vazbu.|  
  
## <a name="remarks"></a>Poznámky  
 Kvóty se používají jako mechanismus zásad, aby se zabránilo vyčerpání nadměrných prostředků. Zabraňují útokům DOS (Denial of Service), které jsou buď škodlivé, nebo neúmyslné. Tento prvek použijte při nastavování kvót kanálů na vlastním kanálu.  
  
 `ChannelPoolSettings`Určuje tři kvóty:  
  
- `idleTimeout` Kvóta se používá ke zmírnění útoků DOS (Denial of Service) na serveru, které se spoléhají na provázání prostředků po delší dobu. Nastavení správné hodnoty na klientovi může zvýšit spolehlivost připojení ke službě. Výchozí hodnota vychází z konzervativního mírného přidělení prostředků. Je vhodný pro vývojové prostředí a malé scénáře instalace. Správci služeb by měli tuto hodnotu zkontrolovat, pokud dojde k nějakému nedostatku prostředků nebo pokud je připojení omezené bez ohledu na dostupnost dalších prostředků.  
  
- `leaseTimeout` Kvóta se používá pro integraci s nástroji pro vyrovnávání zatížení a za účelem zlepšení spolehlivosti. Výchozí hodnota je založena na konzervativním přidělení prostředků. Je vhodný pro vývojové prostředí a malé scénáře instalace. Správci služeb by měli tuto hodnotu zkontrolovat, pokud dojde k nějakému nedostatku prostředků nebo pokud je připojení omezené bez ohledu na dostupnost dalších prostředků.  
  
- Omezení mezipaměti sad kvót nastavuje na serveru i v klientovi a slouží ke zvýšení spolehlivosti. `maxOutboundChannelsPerEndpoint` Výchozí hodnota vychází z konzervativního mírného přidělení prostředků, které jsou vhodné pro vývojové prostředí a malé instalace. Správci služeb by měli tuto hodnotu zkontrolovat, pokud dojde k nějakému nedostatku prostředků nebo pokud je připojení omezené bez ohledu na dostupnost dalších prostředků.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](oneway.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
