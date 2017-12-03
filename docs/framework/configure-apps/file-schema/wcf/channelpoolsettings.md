---
title: '&lt;channelPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d48f3b304b337ba61f53bbd81cac8601bc68cb0a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltchannelpoolsettingsgt"></a>&lt;channelPoolSettings&gt;
Určuje nastavení fondu kanálu pro vlastní vazby.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<Typ oneWay >  
\<channelPoolSettings >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<channelPoolSettings  
    idleTimeout"TimeSpan"  
        leaseTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`idleTimeout`|U kladné <xref:System.TimeSpan> , určuje maximální dobu může být kanály ve fondu nečinnosti, než dojde k odpojení. Výchozí hodnota je 00:02:00.|  
|`leaseTimeout`|A <xref:System.TimeSpan> který určuje, po jejímž uplynutí je uzavřený kanál, pokud vrátí do fondu, časový interval. Výchozí hodnota je 00:10:00.|  
|`maxOutboundChannelsPerEndpoint`|Kladné celé číslo, které určuje maximální počet kanálů, které mohou být uloženy ve fondu pro každý vzdálený koncový bod. Výchozí hodnota je 10.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Typ oneWay >](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|Umožňuje směrování paketů pro vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Kvóty slouží jako mechanismus zásad aby spotřeba nadměrné zdrojů. Brání tomu, aby útok na dostupnost služby (DOS) útoků, které jsou škodlivý nebo nežádoucí. Při nastavení kvót kanál ve vlastním kanálu pomocí tohoto prvku.  
  
 `ChannelPoolSettings`Určuje tři kvót:  
  
-   `idleTimeout` Kvóty se používá k zmírnit útok na dostupnost služby (DOS) útoky na serveru, které jsou závislé na příkazů systémové prostředky pro delší dobu. Na straně klienta správnou hodnotu nastavení zvýšit spolehlivost připojení ke službě. Výchozí hodnota je založena na můžete mírné přidělení prostředků. Je vhodná pro prostředí pro vývoj a scénáře malé instalace. Správci služeb, zkontrolujte hodnotu, pokud instalace může být nedostatek prostředků, nebo pokud jsou právě připojení omezený navzdory dostupnost další prostředky.  
  
-   `leaseTimeout` Kvóty slouží k integraci s nástroje pro vyrovnávání zatížení a pro zlepšení spolehlivosti. Výchozí hodnota je založena na konzervativní přidělení prostředků. Je vhodná pro prostředí pro vývoj a scénáře malé instalace. Správci služeb, zkontrolujte hodnotu, pokud instalace může být nedostatek prostředků, nebo pokud jsou právě připojení omezený navzdory dostupnost další prostředky.  
  
-   `maxOutboundChannelsPerEndpoint` Kvóty nastaví limity mezipaměti na serveru a klienta a slouží k vylepšení spolehlivosti. Výchozí hodnota je založená na můžete mírné přidělení prostředků, který je vhodný pro malé instalace scénáře a vývojové prostředí. Správci služeb, zkontrolujte hodnotu, pokud instalace může být nedostatek prostředků, nebo pokud jsou právě připojení omezený navzdory dostupnost další prostředky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>  
 <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [\<Typ oneWay >](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
