---
title: '&lt;tcpTransport&gt;'
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: 7f38d0c0ff42e75067b06835e7e6613f8fa4adcf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660648"
---
# <a name="lttcptransportgt"></a>&lt;tcpTransport&gt;
Definuje přenos TCP, který mohou využívat pro vlastní vazbu kanálu pro přenos zpráv.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<tcpTransport>  
  
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
                          maxOutboundConnectionsPerEndpopint="Integer" />
</tcpTransport>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|třídě channelInitializationTimeout|Získá nebo nastaví časový limit pro inicializaci kanálu na přijetí.  Maximální doba kanálu může být ve stavu inicializace před jeho odpojením během několika sekund. Tato kvóta obsahuje dobu připojení protokolu TCP může trvat až ke své autentizaci pomocí .net Framing zprávu protokolu. Klient potřebuje k odesílání nějaká počáteční data předtím, než má server dostatek informací k provedení ověřování. Výchozí hodnota je 30 sekund.|  
|connectionBufferSize|Získá nebo nastaví velikost vyrovnávací paměti použité k přenosu bloku serializovaných zpráv od klienta nebo služby.|  
|hostNameComparisonMode|Získá nebo nastaví hodnotu určující, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.|  
|listenBacklog|Maximální počet připojení zařazených do fronty požadavků, které mohou být nevyřízeny pro webovou službu. `connectionLeaseTimeout` Atribut omezuje doby trvání, klient bude čekat před vyvolání výjimky připojení připojený k Internetu. Toto je vlastnost úrovni soketu, která určuje maximální počet připojení zařazených do fronty požadavků, které mohou být nevyřízeny pro webovou službu. Když ListenBacklog je příliš nízké, WCF zastaví přijímá žádosti a proto vyřadit nová připojení, dokud server potvrdí některé z existujících připojení zařazených do fronty. Výchozí hodnota je 16 * počet procesorů.|  
|Vlastnost manualAddressing|Získá nebo nastaví hodnotu určující, jestli je potřeba ruční adresování zprávy.|  
|maxBufferPoolSize|Získá nebo nastaví maximální velikost všechny fondy vyrovnávací paměti používané přenos.|  
|maxBufferSize|Získá nebo nastaví maximální velikost vyrovnávací paměti pro použití. Pro proudu zpráv tato hodnota by měla být aspoň maximální možná velikost záhlaví zpráv, které jsou v režimu vyrovnávací paměti pro čtení.|  
|maxOutputDelay|Získá nebo nastaví maximální interval času, který blok zprávy, nebo celá zpráva může zůstat ve vyrovnávací paměti v paměti před odesláním navýšení kapacity.|  
|maxPendingAccepts|Získá nebo nastaví maximální počet nevyřízených asynchronních přijmout operace, které jsou k dispozici pro zpracování příchozích připojení ke službě.|  
|maxPendingConnections|Získá nebo nastaví maximální počet připojení čeká na odeslání ve službě.|  
|maxReceivedMessageSize|Získá nebo nastaví maximální povolenou velikost zprávy, která může být přijata.|  
|portSharingEnabled|Logická hodnota určující, zda je pro toto připojení povoleno sdílení portu TCP. Pokud je to `false`, každá vazba bude používat výhradně portu. Výchozí hodnota je `false`.<br /><br /> Toto nastavení je relevantní pouze pro služby. Klienti nejsou ovlivněny.<br /><br /> Použití tohoto nastavení vyžaduje povolení službu Windows Communication Foundation (WCF) protokolu TCP Port Sharing tak, že změníte její typ spouštění na ruční nebo automatické|  
|teredoEnabled|Logická hodnota určující, zda je povolena Teredo (technologie pro oslovování klientů, kteří jsou za firewally). Výchozí hodnota je `false`.<br /><br /> Tato vlastnost umožňuje Teredo pro základní soket TCP. Další informace najdete v tématu [Teredo přehled](https://go.microsoft.com/fwlink/?LinkId=95339).<br /><br /> Tato vlastnost se vztahuje pouze na [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] a [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)]. [!INCLUDE[wv](../../../../../includes/wv-md.md)] nabízí možnost konfiguraci celého počítače Teredo, takže při spuštění Vista, tato vlastnost se ignoruje. Teredo vyžaduje počítače klienta a služby Microsoftu IPv6 zásobníku nainstalované a správně nakonfigurován pro použití Teredo. Další informace o konfiguraci Teredo, naleznete v tématu [Teredo přehled](https://go.microsoft.com/fwlink/?LinkId=95339). Další informace najdete v tématu [systému Windows Server 2003 technologie centra](https://go.microsoft.com/fwlink/?LinkId=49888).|  
|transferMode|Získá nebo nastaví hodnotu určující, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány připojením řízenou přepravou.|  
|connectionPoolSettings|Určuje další nastavení fondu připojení pro vazbu pojmenovaného kanálu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vázání pro vlastní vazbu.|  
  
## <a name="remarks"></a>Poznámky  
 Tento přenos používá identifikátory URI ve tvaru "net.tcp://hostname: port/cesty". Ostatní součásti URI jsou volitelné.  
  
 `tcpTransport` Element je výchozí bod pro vytvoření vlastní vazby, který implementuje přenosový protokol TCP. Tento přenos je optimalizovaná pro komunikaci WCF WCF.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.TcpTransportElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
