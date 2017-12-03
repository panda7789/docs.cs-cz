---
title: "&lt;connectionPoolSettings&gt; – &lt;tcpTransport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b0bd7303f714847228bcd8bfed7134fe9942c1a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltconnectionpoolsettingsgt-of-lttcptransportgt"></a>&lt;connectionPoolSettings&gt; – &lt;tcpTransport&gt;
Určuje nastavení fondu další připojení pro přenos TCP.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<tcpTransport >  
\<connectionPoolSettings >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<connectionPoolSettings  
    groupName="String"  
    idleTimeout"TimeSpan"  
        leaseTimeout="TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`groupName`|Řetězec, který definuje název fondu připojení používané pro odchozí kanály. V přenášené datovými proudy režimu nejsou sdílené připojení – zakázáno sdružování připojení. Výchozí hodnota je řetězec "default". Tato hodnota izolovat připojení pro konkrétního klienta do samostatných skupin můžete upravit.|  
|`idleTimeout`|U kladné <xref:System.TimeSpan> , určuje maximální dobu může být připojení nečinnosti, než dojde k odpojení. Výchozí hodnota je 00:02:00.|  
|`leaseTimeout`|A <xref:System.TimeSpan> určující dobu, po jejímž uplynutí je uzavřený aktivní připojení. Výchozí hodnota je 00:05:00.<br /><br /> Poté, co se vrátí do mezipaměti připojení a ne během aktivní přenos, je připojení ukončeno. Mezipaměť připojení používá přenos TCP vytvoří nové připojení podle potřeby pro každý koncový bod, až do limitu mezipaměti, kterou je nastavit`maxOutboundConnectionsPerEndpoint.`|  
|`maxOutboundConnectionsPerEndpoint`|Kladné celé číslo, které určuje maximální počet připojení, aby vzdálený koncový bod iniciovat službu. Připojení nad tento limit jsou zařazeny do fronty, dokud nebude k dispozici místo pod limit. `idleTimeout` Omezí doba trvání, ve kterém připojení zůstat ve frontě, než je vyvolána výjimka. Výchozí hodnota je 10.<br /><br /> Tento atribut omezuje počet souběžných aktivních připojení z klienta pro koncový bod konkrétní služby. Pokud se překročí tuto hodnotu tak, že více aktivních připojení klienta, se mohou objevit reagovat na klienta služby. V takovém případě je třeba upravit tuto hodnotu delší než maximální počet očekávané simultánních klientských připojení na konkrétní.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<namedPipeTransport >](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|Definuje přenos, který způsobuje, že kanálu pro přenos zpráv pomocí pojmenovaných kanálů.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
