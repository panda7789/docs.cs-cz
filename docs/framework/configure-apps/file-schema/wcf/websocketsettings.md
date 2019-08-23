---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 5c9dbec13dd0d71ba1b92ea971d067540013b6f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940318"
---
# <a name="websocketsettings"></a>\<webSocketSettings>
Prvek konfigurace, který slouží k zadání nastavení webového soketu.  
  
\<system.ServiceModel>  
\<> vazeb  
\<netHttpBinding>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|createNotificationOnConnection|Určuje, zda je při připojení odesláno oznámení.|  
|disablePayloadMasking|Určuje, jestli je zakázané maskování webového soketu.|  
|keepAliveInterval|Určuje interval Keep Alive.|  
|maxPendingConnections|Určuje maximální počet připojení čekajících na odeslání ve službě.|  
|receiveBufferSize|Určuje velikost vyrovnávací paměti pro příjem.|  
|sendBufferSize|Určuje velikost vyrovnávací paměti pro odeslání.|  
|Dílčí protokol|Určuje dílčí protokol webového soketu.|  
|transportUsage|Určuje, kdy se mají používat webové sokety.|  
  
## <a name="transportusage-attribute"></a>transportUsage – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|WhenDuplex|Protokol webového soketu použijte v případě, že je kontrakt duplexní.|  
|Vždy|Vždy používejte protokol webového soketu bez ohledu na kontrakt.|  
|Nikdy|Nikdy nepoužívejte protokol webového soketu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|\<netHttpBinding>|Určuje NetHttpBinding|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití \<prvku webSocketSettings >.  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> vazby](../../../misc/binding.md)
