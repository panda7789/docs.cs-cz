---
title: '&lt;tcpTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2cbc0fc790ce6ed9de2a920c851ee6656fa3abaa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="lttcptransportgt"></a>&lt;tcpTransport&gt;
Definuje přenos TCP, který lze použít pro vlastní vazby pomocí kanálu pro přenos zpráv.  
  
 \<system.serviceModel >  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<tcpTransport >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<tcpTransport   
      channelInitializationTimeout="TimeSpan"   
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
      <connectionPoolSettings  
            groupName="String"  
            idleTimeout"TimeSpan"  
            leaseTimeout="TimeSpan"  
            maxOutboundConnectionsPerEndpopint="Integer" />  
</tcpTransport>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|ChannelInitializationTimeout|Získá nebo nastaví časový limit pro inicializaci kanálu třeba přijmout.  Maximální doba kanál, který může být ve stavu inicializace uplynutí dojde k odpojení v sekundách. Tato kvóta obsahuje dobu připojení protokolu TCP může trvat, kterými se ověří pomocí .net rámců zprávu protokolu. Klient musí poslat některé počáteční data předtím, než má server dostatek informací k provedení ověřování. Výchozí hodnota je 30 sekund.|  
|ConnectionBufferSize|Získá nebo nastaví velikost vyrovnávací paměti používané k přenosu bloku serializovaných zprávu od klienta nebo služby.|  
|hostNameComparisonMode|Získá nebo nastaví hodnotu, která určuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.|  
|listenBacklog|Maximální počet požadavků ve frontě připojení, které mohou být čekající na vyřízení pro webovou službu. `connectionLeaseTimeout` Atribut omezuje trvání klient čekat, než se připojený. teprve potom vyvolání k výjimce připojení. Toto je soketu úrovně vlastnost, která určuje maximální počet požadavků ve frontě připojení, které mohou být čekající na vyřízení pro webovou službu. Když ListenBacklog příliš nízké, WCF zastaví přijímá žádosti a proto vyřadit nová připojení, dokud nebude server uznává některé z existujících připojení ve frontě. Výchozí hodnota je 16 * počet procesorů.|  
|manualAddressing|Získá nebo nastaví hodnotu, která určuje, zda je vyžadováno ruční adresování zprávy.|  
|maxBufferPoolSize|Získá nebo nastaví maximální velikost všechny fondy vyrovnávací paměti používané přenosu.|  
|maxBufferSize|Získá nebo nastaví maximální velikost vyrovnávací paměti pro použití. Pro proudu zpráv tato hodnota by měla být alespoň maximální možná velikost záhlaví zprávy, které jsou přečíst v režim s vyrovnávací pamětí.|  
|maxOutputDelay|Získá nebo nastaví maximální dobu, po kterou bloku zprávu nebo zprávu úplné může zůstat ve vyrovnávací paměti v paměti před odesláním interval.|  
|maxPendingAccepts|Získá nebo nastaví maximální počet čekající asynchronní přijmout operace, které jsou k dispozici pro zpracování příchozí připojení ke službě.|  
|maxPendingConnections|Získá nebo nastaví maximální počet připojení, které čekají na odeslání ve službě.|  
|MaxReceivedMessageSize|Získá nebo nastaví maximální povolenou velikost zprávy, může být přijata.|  
|PortSharingEnabled|Logická hodnota, která určuje, zda je sdílení portů TCP povolený pro toto připojení. Pokud je to `false`, každou vazbu budou používat svůj vlastní výhradní port. Výchozí hodnota je `false`.<br /><br /> Toto nastavení platí pouze pro služby. Ovlivněné nejsou klienty.<br /><br /> Použití tohoto nastavení vyžaduje povolení změnou její typ spuštění ručně nebo automaticky pomocí technologie Windows Communication Foundation (WCF) TCP Port sdílení služby|  
|TeredoEnabled|Logická hodnota, která určuje, zda je povoleno Teredo (technologie pro adresování klienty, kteří jsou za bránami firewall). Výchozí hodnota je `false`.<br /><br /> Tato vlastnost umožňuje Teredo základní soketu TCP. Další informace najdete v tématu [Teredo přehled](http://go.microsoft.com/fwlink/?LinkId=95339).<br /><br /> Tato vlastnost se vztahuje pouze na [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] a [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)]. [!INCLUDE[wv](../../../../../includes/wv-md.md)]má možnost konfigurace celého systému pro Teredo, takže když systém Vista, tato vlastnost je ignorována. Teredo vyžaduje, aby měl počítače klienta a služby Microsoft IPv6 zásobníku nainstalovaná a správně nakonfigurovaná pro použití Teredo. Další informace o konfiguraci Teredo najdete v tématu [Teredo přehled](http://go.microsoft.com/fwlink/?LinkId=95339). Další informace najdete v tématu [Windows Server 2003 technologie centrech](http://go.microsoft.com/fwlink/?LinkId=49888).|  
|transferMode|Získá nebo nastaví hodnotu, která určuje, zda jsou zprávy do vyrovnávací paměti nebo vysílání pomocí přenosu orientovaná na připojení.|  
|connectionPoolSettings|Určuje nastavení fondu další připojení pro vazbu s názvem kanálu.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vazba >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vazba vlastní vazby.|  
  
## <a name="remarks"></a>Poznámky  
 Tento přenos používá identifikátory URI ve tvaru "net.tcp://hostname: port či cestu". Ostatní součásti URI jsou volitelné.  
  
 `tcpTransport` Element je výchozím bodem pro vytvoření vlastní vazby, který implementuje přenosový protokol TCP. Tento přenos je optimalizovaná pro komunikaci WCF WCF.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.TcpTransportElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Přenosy](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Volba přenosu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšiřování vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
