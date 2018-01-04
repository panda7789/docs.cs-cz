---
title: "Přenosové kvóty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transport quotas [WCF]
ms.assetid: 3e71dd3d-f981-4d9c-9c06-ff8abb61b717
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e9d7fbf42f2ed9b8f68b1faf2e2425050b62eaa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="transport-quotas"></a>Přenosové kvóty
Přenosové kvóty jsou mechanismus zásad rozhodování, kdy připojení spotřebovává nadměrné prostředky. Kvótu je pevný limit, který brání použití další prostředky, jakmile dojde k překročení kvóty hodnota. Přenosové kvóty zabránit škodlivý nebo neúmyslnému útoku DOS.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]přenosy mají výchozí hodnoty kvóty, které jsou založeny na konzervativní přidělení prostředků. Tyto výchozí hodnoty jsou vhodné pro vývojové prostředí a scénáře malé instalace. Správci služeb zkontrolujte přenosové kvóty a ladit jednotlivé hodnoty kvót, pokud instalace může být nedostatek prostředků, nebo pokud jsou právě připojení omezený navzdory dostupnost další prostředky.  
  
## <a name="types-of-transport-quotas"></a>Typy přenosové kvóty  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]přenosy mít tři typy kvót:  
  
-   *Časové limity* zmírnit útok na dostupnost služby útoků, které jsou závislé na příkazů systémové prostředky pro delší dobu.  
  
-   *Omezení přidělení paměti* zabránit jednoho připojení z vyčerpáním systémové paměti a odepření služby do jiné připojení.  
  
-   *Limity velikosti kolekce* vázaný spotřeby prostředků, které nepřímo přidělit paměť nebo jsou v omezenou nabídkou.  
  
## <a name="transport-quota-descriptions"></a>Popisy kvóty přenosu  
 Tato část popisuje přenosové kvóty, které jsou k dispozici pro standardní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přenosy: HTTP (S), protokolu TCP/IP a pojmenované kanály. Vlastní přenosy můžou zpřístupnit vlastní konfigurovat kvóty, které nejsou uvedené v tomto seznamu. Najdete v dokumentaci pro vlastní přenos informace o jeho kvóty.  
  
 Každé nastavení kvót má typ, minimální hodnota a výchozí hodnota. Maximální hodnota, která kvótu je omezena její typ. Vzhledem k omezením počítače není vždy možné nastavit kvótu na maximální hodnotu.  
  
|Název|Typ|Min.<br /><br /> value|Výchozí<br /><br /> value|Popis|  
|----------|----------|--------------------|-----------------------|-----------------|  
|`ChannelInitializationTimeout`|Časový interval|1 značek|5 s|Maximální doba čekání na připojení k odeslání preambule během počáteční čtení. Tato data byl přijat, než dojde k ověřování. Toto nastavení je obvykle mnohem menší, než `ReceiveTimeout` hodnota kvóty.|  
|`CloseTimeout`|Časový interval|0|1 min|Maximální doba čekání na připojení k zavřete před přenos vyvolá výjimku.|  
|`ConnectionBufferSize`|Integer|1|8 KB|Velikost v bajtech odesílání a příjmu vyrovnávací paměti základní přenosu. Zvýšení velikosti vyrovnávací paměti může zvýšit propustnost při odesílání zpráv velké.|  
|`IdleTimeout`|Časový interval|0|2 min.|Maximální doba ve fondu připojení zůstat v nečinnosti před dochází k uzavření.<br /><br /> Toto nastavení platí pouze pro ve fondu připojení.|  
|`LeaseTimeout`|Časový interval|0|5 minut|Maximální doba života aktivního připojení ve fondu. Po uplynutí určité doby, připojení zavře, jakmile je servis aktuální požadavek.<br /><br /> Toto nastavení platí pouze pro ve fondu připojení.|  
|`ListenBacklog`|Integer|1|10|Maximální počet připojení, která může mít unserviced naslouchací proces před další připojení do tohoto koncového bodu je odepřen.|  
|`MaxBufferPoolSize`|dlouhá|0|512 KB|Maximální velikost paměti v bajtech, které přenos věnoval sdružování opakovaně použitelné zpráva vyrovnávací paměti. Když fondu nelze zadat zprávu vyrovnávací paměť, vyrovnávací paměť nového je přidělen pro dočasné použití.<br /><br /> Instalace vytvořit mnoho objektů factory kanálu nebo naslouchací procesy, které můžete přidělit velké množství paměti pro fondy vyrovnávací paměti. Zmenšení velikosti této vyrovnávací paměti může výrazně snížit využití paměti v tomto scénáři.|  
|`MaxBufferSize`|Integer|1|64 KB|Maximální velikost v bajtech vyrovnávací paměť pro datový proud. Pokud není nastavena tato kvóta přenosu, nebo není přenosu pomocí vysílání datového proudu, pak hodnota kvóty je stejný jako menší z `MaxReceivedMessageSize` hodnota kvóty a <xref:System.Int32.MaxValue>.|  
|`MaxOutboundConnectionsPerEndpoint`|Integer|1|10|Maximální počet odchozí připojení, které může být spojeno s konkrétní koncový bod.<br /><br /> Toto nastavení platí pouze pro ve fondu připojení.|  
|`MaxOutputDelay`|Časový interval|0|200 ms|Maximální doba čekání po operaci odeslání pro dávkování další zprávy v rámci jedné operace. Zprávy jsou odesílány dříve, pokud vyrovnávací paměť základní přenos plný. Doba zpoždění neprovádí vynulování odesláním další zprávy.|  
|`MaxPendingAccepts`|Integer|1|1|Maximální počet přijme pro kanály, naslouchací proces můžou mít čekání.<br /><br /> Je interval mezi dokončení přijmout a nové spuštění přijmout. Zvýšit velikost této kolekce můžete zabránit klienti, kteří připojují během tohoto intervalu z probíhá vyřazování.|  
|`MaxPendingConnections`|Integer|1|10|Maximální počet připojení, která naslouchací proces může mít čeká se na aplikace akceptovat. Při překročení této hodnoty kvóty na nový příchozí připojení zahozených místo čekání na přijmout.<br /><br /> Funkce připojení jako zabezpečení zpráv může způsobit klienta otevřít víc než jedno připojení. Správci služeb by měl účet pro tyto další připojení při nastavování této hodnoty kvóty.|  
|`MaxReceivedMessageSize`|dlouhá|1|64 KB|Maximální velikost v bajtech přijaté zprávy, včetně hlavičky, než se přenos vyvolá výjimku.|  
|`OpenTimeout`|Časový interval|0|1 min|Maximální doba čekání připojení lze navázat před přenos vyvolá výjimku.|  
|`ReceiveTimeout`|Časový interval|0|10 min.|Maximální doba čekání na dokončení před přenos čtení operace vyvolá výjimku.|  
|`SendTimeout`|Časový interval|0|1 min|Maximální doba čekání na dokončení před přenos operace zápisu vyvolá výjimku.|  
  
 Přenosové kvóty `MaxPendingConnections` a `MaxOutboundConnectionsPerEndpoint` jsou sloučeny do jednoho přenosu kvóty s názvem `MaxConnections` Pokud nastavíte prostřednictvím vazby nebo konfigurace. Pouze prvku vazby umožňuje nastavení tyto hodnoty kvóty jednotlivě. `MaxConnections` Kvóty přenosu má stejné minimální a výchozí hodnoty.  
  
## <a name="setting-transport-quotas"></a>Nastavení přenosové kvóty  
 Přenosové kvóty se konfigurují pomocí prvku vazby přenosu, přenos vazby, konfigurace aplikace nebo zásad. Tento dokument nepopisuje nastavení přenosy prostřednictvím zásad. Naleznete v dokumentaci k základní přenos ke zjištění nastavení zásad kvót hostitele. [Konfigurace HTTP a HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md) téma popisuje nastavení kvót pro ovladač Http.sys. Vyhledejte další informace o konfiguraci omezení systému Windows na protokolu HTTP, protokolu TCP/IP a pojmenovaný kanál připojení ve znalostní bázi Microsoft Knowledge Base.  
  
 Jiné typy kvót nepřímo týkají přenosy. Kodér zpráv, který přenos používá k transformaci zprávu do bajtů může mít svůj vlastní nastavení kvót. Ale tyto kvóty jsou nezávislé na typ přenosu, které používá.  
  
### <a name="controlling-transport-quotas-from-the-binding-element"></a>Řízení přenosové kvóty z prvku vazby  
 Nastavení přenosové kvóty prostřednictvím prvku vazby nabízí nejvyšší flexibilitu při řízení chování je přenos. Výchozí vypršení časových limitů pro zavřít, otevřete, Receive a odešlete operations jsou převzaty z vazby, když je sestavena kanál.  
  
|Název|HTTP|TCP/IP|Pojmenovaný kanál|  
|----------|----------|-------------|----------------|  
|`ChannelInitializationTimeout`||X|X|  
|`CloseTimeout`||||  
|`ConnectionBufferSize`||X|X|  
|`IdleTimeout`||X|X|  
|`LeaseTimeout`||X||  
|`ListenBacklog`||X||  
|`MaxBufferPoolSize`|X|X|X|  
|`MaxBufferSize`|X|X|X|  
|`MaxOutboundConnectionsPerEndpoint`||X|X|  
|`MaxOutputDelay`||X|X|  
|`MaxPendingAccepts`||X|X|  
|`MaxPendingConnections`||X|X|  
|`MaxReceivedMessageSize`|X|X|X|  
|`OpenTimeout`||||  
|`ReceiveTimeout`||||  
|`SendTimeout`||||  
  
### <a name="controlling-transport-quotas-from-the-binding"></a>Řízení přenosové kvóty z vazby  
 Nastavení přenosové kvóty prostřednictvím vazby nabízí zjednodušené sadu kvóty, které se vybírat a přitom dál udělíte přístup k nejběžnější hodnoty kvóty.  
  
|Název|HTTP|TCP/IP|Pojmenovaný kanál|  
|----------|----------|-------------|----------------|  
|`ChannelInitializationTimeout`||||  
|`CloseTimeout`|X|X|X|  
|`ConnectionBufferSize`||||  
|`IdleTimeout`||||  
|`LeaseTimeout`||||  
|`ListenBacklog`||X||  
|`MaxBufferPoolSize`|X|X|X|  
|`MaxBufferSize`|1|X|X|  
|`MaxOutboundConnectionsPerEndpoint`||2|2|  
|`MaxOutputDelay`||||  
|`MaxPendingAccepts`||||  
|`MaxPendingConnections`||2|2|  
|`MaxReceivedMessageSize`|X|X|X|  
|`OpenTimeout`|X|X|X|  
|`ReceiveTimeout`|X|X|X|  
|`SendTimeout`|X|X|X|  
  
1.  `MaxBufferSize` Kvóty přenosu je dostupná pouze na `BasicHttp` vazby. `WSHttp` Vazby jsou pro scénáře, které nepodporují režimy přenášené datovými proudy přenosu.  
  
2.  Přenosové kvóty `MaxPendingConnections` a `MaxOutboundConnectionsPerEndpoint` jsou sloučeny do jednoho přenosu kvóty s názvem `MaxConnections`.  
  
### <a name="controlling-transport-quotas-from-configuration"></a>Řízení přenosové kvóty z konfigurace  
 Konfigurace aplikace můžete nastavit stejné přenosové kvóty jako přímý přístup k vlastnosti u vazby. V konfiguračních souborech název kvóty přenosu vždy začíná malým písmenem. Například `CloseTimeout` vlastnost u vazby odpovídá `closeTimeout` nastavení v konfiguraci a `MaxConnections` vlastnost u vazby odpovídá `maxConnections` nastavení v konfiguraci.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
