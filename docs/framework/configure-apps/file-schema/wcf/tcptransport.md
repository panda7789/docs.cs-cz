---
title: <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: f2c1335795ffd3cb395a7006bfaeb3cf7b39636b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77448618"
---
# \<tcpTransport>
Definuje přenos TCP, který může kanál použít k přenosu zpráv pro vlastní vazbu.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tcpTransport>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<tcpTransport channelInitializationTimeout="TimeSpan"
              connectionBufferSize="Integer"
              hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
              listenBacklog="Integer"
              manualAddressing="Boolean"
              maxBufferPoolSize="Integer"
              maxBufferSize="Integer"
              maxOutputDelay="TimeSpan"
              maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              maxReceivedMessageSize="Integer"
              portSharingEnabled="Boolean"
              teredoEnabled="Boolean"
              transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse" >
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          leaseTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</tcpTransport>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|channelInitializationTimeout|Získá nebo nastaví časový limit pro inicializaci kanálu, který se má přijmout.  Maximální doba, po kterou kanál může být ve stavu inicializace, než bude odpojen během několika sekund. Tato kvóta zahrnuje dobu, kterou může připojení TCP trvat při ověřování pomocí protokolu rámce zpráv .NET. Klient potřebuje odeslat některá počáteční data předtím, než server bude mít dostatek informací k provedení ověření. Výchozí hodnota je 30 sekund.|  
|connectionBufferSize|Získá nebo nastaví velikost vyrovnávací paměti, která se používá k přenosu bloku serializované zprávy na lince z klienta nebo služby.|  
|hostNameComparisonMode|Získává nebo nastavuje hodnotu, která indikuje, jestli se k dosažení služby při shodě s identifikátorem URI používá název hostitele.|  
|listenBacklog|Maximální počet požadavků na připojení zařazených do fronty, které mohou být vyřízeny u webové služby. `connectionLeaseTimeout`Atribut omezuje dobu, po kterou bude klient čekat na připojení, než dojde k výjimce připojení. Toto je vlastnost na úrovni soketu, která určuje maximální počet požadavků na připojení zařazených do fronty, které mohou být vyřízeny u webové služby. Pokud je ListenBacklog příliš nízké, WCF přestane přijímat požadavky, a proto vyřadí nová připojení, dokud server nepotvrdí některá existující připojení ve frontě. Výchozí hodnota je 16 * počet procesorů.|  
|Jeho|Získává nebo nastavuje hodnotu, která indikuje, jestli se vyžaduje ruční adresování zprávy.|  
|maxBufferPoolSize|Získá nebo nastaví maximální velikost všech fondů vyrovnávací paměti používaných pro přenos.|  
|Třída|Získá nebo nastaví maximální velikost vyrovnávací paměti, která se má použít. U zpráv v datových proudech by tato hodnota měla být alespoň maximální možná velikost záhlaví zprávy, která je čtena v režimu vyrovnávací paměti.|  
|maxOutputDelay|Získá nebo nastaví maximální časový interval, po který může blok zprávy nebo úplná zpráva zůstat v paměti před odesláním do vyrovnávací paměti.|  
|maxPendingAccepts|Získá nebo nastaví maximální počet nedokončených asynchronních operací přijetí, které jsou k dispozici pro zpracování příchozích připojení ke službě.|  
|maxPendingConnections|Získá nebo nastaví maximální počet připojení čekajících na odeslání ve službě.|  
|maxReceivedMessageSize|Získá a nastaví maximální povolenou velikost zprávy, kterou lze přijmout.|  
|portSharingEnabled|Logická hodnota, která určuje, zda je pro toto připojení povoleno sdílení portu TCP. V takovém případě `false` bude každá vazba používat vlastní výhradní port. Výchozí formát je `false`.<br /><br /> Toto nastavení je relevantní pouze pro služby. Klienti nejsou ovlivněni.<br /><br /> Použití tohoto nastavení vyžaduje povolení služby sdílení portů služby Windows Communication Foundation (WCF) TCP změnou typu spuštění na ruční nebo automatické.|  
|teredoEnabled|Logická hodnota určující, zda je povolena Teredo (technologie pro oslovování klientů, kteří jsou za branami firewall). Výchozí formát je `false`.<br /><br /> Tato vlastnost umožňuje technologii Teredo pro základní soket TCP. Další informace najdete v tématu [Přehled technologie Teredo](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-xp/bb457011(v=technet.10)).<br /><br /> Tato vlastnost se vztahuje pouze na systémy Windows XP SP2 a Windows Server 2003. Systém Windows Vista má pro Teredo možnost konfigurace na úrovni počítače, takže při spuštění systému Vista se tato vlastnost ignoruje. Teredo vyžaduje, aby v počítačích klientů a služeb byla nainstalovaná služba Microsoft IPv6 stack a správně nakonfigurovaná pro použití Teredo.|  
|Třídy TransferMode|Získává nebo nastavuje hodnotu, která indikuje, jestli se zprávy ukládají do vyrovnávací paměti nebo streamují s přenosem orientovaným na připojení.|  
|connectionPoolSettings|Určuje další nastavení fondu připojení pro vazbu pojmenovaného kanálu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Definuje všechny schopnosti vazby vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Tento přenos používá identifikátory URI ve formátu "NET. TCP://hostname: port/cesta". Jiné součásti identifikátoru URI jsou volitelné.  
  
 `tcpTransport`Element je výchozím bodem pro vytvoření vlastní vazby, která implementuje transportní protokol TCP. Tento přenos je optimalizovaný pro komunikaci WCF-to-WCF.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.TcpTransportElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Přenosy](../../../wcf/feature-details/transports.md)
- [Volba přenosu](../../../wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
