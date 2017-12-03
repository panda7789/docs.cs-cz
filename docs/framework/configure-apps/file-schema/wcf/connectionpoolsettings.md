---
title: '&lt;connectionPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f1980365da8514060290066a4e15e5f88e35f7f4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltconnectionpoolsettingsgt"></a>&lt;connectionPoolSettings&gt;
Určuje nastavení fondu další připojení pro vazbu s názvem kanálu.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<namePipeTransport >  
\<connectionPoolSettings >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<connectionPoolSettings  
        groupName="String"  
    idleTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`groupName`|Řetězec, který definuje název fondu připojení používané pro odchozí kanály. V přenášené datovými proudy režimu nejsou sdílené připojení – zakázáno sdružování připojení. Výchozí hodnota je řetězec "default". Tato hodnota izolovat připojení pro konkrétního klienta do samostatných skupin můžete upravit.|  
|`idleTimeout`|U kladné <xref:System.TimeSpan> , určuje maximální dobu může být připojení nečinnosti, než dojde k odpojení. Výchozí hodnota je 00:02:00.|  
|`maxOutboundConnectionsPerEndpoint`|Kladné celé číslo, které určuje maximální počet připojení, aby vzdálený koncový bod iniciovat službu. Připojení nad tento limit jsou zařazeny do fronty, dokud nebude k dispozici místo pod limit. `idleTimeout` Omezí doba trvání, ve kterém připojení zůstat ve frontě, než je vyvolána výjimka. Výchozí hodnota je 10.<br /><br /> Tento atribut omezuje počet souběžných aktivních připojení z klienta pro koncový bod konkrétní služby. Pokud se překročí tuto hodnotu tak, že více aktivních připojení klienta, se mohou objevit reagovat na klienta služby. V takovém případě je třeba upravit tuto hodnotu delší než maximální počet očekávané simultánních klientských připojení na konkrétní.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<namedPipeTransport >](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|Definuje přenos, který způsobuje, že kanálu pro přenos zpráv pomocí pojmenovaných kanálů.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
