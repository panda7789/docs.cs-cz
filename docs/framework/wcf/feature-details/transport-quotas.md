---
title: Přenosové kvóty
ms.date: 03/30/2017
helpviewer_keywords:
- transport quotas [WCF]
ms.assetid: 3e71dd3d-f981-4d9c-9c06-ff8abb61b717
ms.openlocfilehash: fca5fbeffb560f848edda6421301785f02547d2c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585698"
---
# <a name="transport-quotas"></a>Přenosové kvóty
Přenosové kvóty představují mechanismus zásad pro rozhodování, kdy připojení spotřebovává nadměrné prostředky. Kvóta je pevný limit, který brání použití dalších prostředků, jakmile je překročena hodnota kvóty. Přenosové kvóty zabraňují útokům prostřednictvím škodlivého nebo neúmyslného útoku na dostupnost služeb.  
  
 Přenosy Windows Communication Foundation (WCF) mají výchozí hodnoty kvóty, které jsou založené na konzervativním přidělení prostředků. Tyto výchozí hodnoty jsou vhodné ve vývojových prostředích a malých scénářích instalace. Správci služeb by měli projít transportními kvótami a vyladit jednotlivé hodnoty kvót v případě, že dojde k instalaci z prostředků nebo pokud se spojení omezí i bez ohledu na dostupnost dalších prostředků.  
  
## <a name="types-of-transport-quotas"></a>Typy přenosových kvót  
 Přenosy WCF mají tři typy kvót:  
  
- *Vypršení časových limitů* zmírnění útoků při odepření služeb, které spoléhají na provázání prostředků po delší dobu.  
  
- *Omezení přidělení paměti* brání jednomu připojení z vyčerpání systémové paměti a odepření služby jiným připojením.  
  
- *Limity velikosti kolekce* , které jsou vázány na spotřebu prostředků, které nepřímo přidělují paměť nebo jsou v omezeném dodávce.  
  
## <a name="transport-quota-descriptions"></a>Popis kvóty přenosu  
 Tato část popisuje přenosové kvóty dostupné pro standardní přenosy WCF: HTTP (S), TCP/IP a pojmenované kanály. Vlastní přenosy můžou vystavovat vlastní konfigurovatelné kvóty, které nejsou zahrnuté v tomto seznamu. Informace o kvótách najdete v dokumentaci k vlastnímu přenosu.  
  
 Každé nastavení kvóty má typ, minimální hodnotu a výchozí hodnotu. Maximální hodnota kvóty je omezená podle typu. Kvůli omezením počítače není vždy možné nastavit kvótu na maximální hodnotu.  
  
|Name|Typ|Dlouhé.<br /><br /> hodnota|Výchozí<br /><br /> hodnota|Popis|  
|----------|----------|--------------------|-----------------------|-----------------|  
|`ChannelInitializationTimeout`|TimeSpan|1 takt|5 sekund|Maximální doba, po kterou se má čekat na připojení k odeslání preambule během počátečního čtení. Tato data se obdrží před tím, než dojde k ověření. Toto nastavení je všeobecně mnohem menší než `ReceiveTimeout` hodnota kvóty.|  
|`CloseTimeout`|TimeSpan|0|1 min|Maximální doba, po kterou se má čekat na ukončení připojení, než přenos vyvolá výjimku.|  
|`ConnectionBufferSize`|Integer|1|8 kB|Velikost přenosových a přijímacích vyrovnávacích pamětí podkladového přenosu (v bajtech). Zvýšení velikosti vyrovnávací paměti může zlepšit propustnost při posílání velkých zpráv.|  
|`IdleTimeout`|TimeSpan|0|2 min|Maximální doba, po kterou může připojení ve fondu zůstat nečinné, než bude zavřeno.<br /><br /> Toto nastavení platí jenom pro připojení ve fondu.|  
|`LeaseTimeout`|TimeSpan|0|5 min|Maximální doba života aktivního připojení ve fondu. Po uplynutí zadané doby se připojení zavře, jakmile se aktuální žádost dojedná o službu.<br /><br /> Toto nastavení platí jenom pro připojení ve fondu.|  
|`ListenBacklog`|Integer|1|10|Maximální počet připojení, která naslouchací proces mohl zrušit před odepřením dalších připojení k tomuto koncovému bodu.|  
|`MaxBufferPoolSize`|Dlouhou|0|512 kB|Maximální velikost paměti (v bajtech), která se přenese do sdružování opakovaně použitelných vyrovnávacích pamětí zpráv. Pokud fond nemůže dodat vyrovnávací paměť zpráv, je pro dočasné použití přidělena nová vyrovnávací paměť.<br /><br /> Instalace, které vytvářejí mnoho továrn a posluchačů kanálů, můžou přidělit velké množství paměti pro fondy vyrovnávacích pamětí. Zmenšení této velikosti vyrovnávací paměti může výrazně snížit využití paměti v tomto scénáři.|  
|`MaxBufferSize`|Integer|1|64 kB|Maximální velikost vyrovnávací paměti, která se používá pro streamovaná data, v bajtech. Pokud tato kvóta přenosu není nastavená nebo přenos nepoužívá streamování, pak je hodnota kvóty stejná jako u menší `MaxReceivedMessageSize` hodnoty kvóty a <xref:System.Int32.MaxValue> .|  
|`MaxOutboundConnectionsPerEndpoint`|Integer|1|10|Maximální počet odchozích připojení, která se dají přidružit ke konkrétnímu koncovému bodu<br /><br /> Toto nastavení platí jenom pro připojení ve fondu.|  
|`MaxOutputDelay`|TimeSpan|0|200 MS|Maximální doba, po kterou se má čekat po operaci odeslání pro dávkování dalších zpráv v rámci jedné operace. Zprávy se odešlou dříve, pokud se vyrovnávací paměť podkladového přenosu zaplní. Odeslání dalších zpráv neresetuje dobu zpoždění.|  
|`MaxPendingAccepts`|Integer|1|1|Maximální počet přijetí pro kanály, které naslouchací proces mohl čekat.<br /><br /> Doba mezi přijetím a novým přijetím je v intervalu. Zvětšení této velikosti kolekce může zabránit tomu, aby se klienti, kteří se připojili během tohoto intervalu, vynechali.|  
|`MaxPendingConnections`|Integer|1|10|Maximální počet připojení, která naslouchací proces mohl čekat na přijetí aplikací. Pokud je tato hodnota kvóty překročena, jsou nová příchozí připojení vynechána, ale čekají na přijetí.<br /><br /> Funkce připojení, jako je například zabezpečení zprávy, mohou způsobit, že klient může otevřít více než jedno připojení. Správci služeb by měli při nastavení této kvóty brát v úvahu tato další připojení.|  
|`MaxReceivedMessageSize`|Dlouhou|1|64 kB|Maximální velikost přijaté zprávy v bajtech, včetně hlaviček, před přenosem vyvolá výjimku.|  
|`OpenTimeout`|TimeSpan|0|1 min|Maximální doba, po kterou se má čekat na navázání spojení, než přenos vyvolá výjimku.|  
|`ReceiveTimeout`|TimeSpan|0|10 min|Maximální doba, po kterou se má čekat na dokončení operace čtení, než přenos vyvolá výjimku.|  
|`SendTimeout`|Časový interval|0|1 min|Maximální doba, po kterou se má čekat na dokončení operace zápisu, než přenos vyvolá výjimku.|  
  
 Přenosové kvóty `MaxPendingConnections` a `MaxOutboundConnectionsPerEndpoint` jsou zkombinovány do jedné dopravní kvóty, která je volána `MaxConnections` při nastavení prostřednictvím vazby nebo konfigurace. Pouze element Binding umožňuje nastavit tyto hodnoty kvóty jednotlivě. `MaxConnections`Kvóta přenosu má stejné minimální a výchozí hodnoty.  
  
## <a name="setting-transport-quotas"></a>Nastavení přenosových kvót  
 Přenosové kvóty se nastavují prostřednictvím elementu Transport Binding, vazby přenosu, konfigurace aplikace nebo zásad hostitele. Tento dokument nepokrývá nastavení přenosů prostřednictvím zásad hostitele. Pokud chcete zjistit nastavení kvót zásad hostitele, Projděte si dokumentaci k příslušnému přenosu. Téma [Konfigurace protokolu HTTP a HTTPS](configuring-http-and-https.md) popisuje nastavení kvót pro ovladač HTTP. sys. V článku znalostní báze Microsoft Knowledge Base najdete další informace o konfiguraci omezení Windows pro připojení HTTP, TCP/IP a pojmenované kanály.  
  
 Jiné typy kvót platí pro přenos nepřímo. Kodér zprávy, který přenos používá k transformaci zprávy na bajty, může mít vlastní nastavení kvót. Tyto kvóty jsou ale nezávislé na typu používaného přenosu.  
  
### <a name="controlling-transport-quotas-from-the-binding-element"></a>Řízení přenosových kvót z elementu vazby  
 Nastavení přenosových kvót prostřednictvím elementu vazby nabízí největší flexibilitu při řízení chování přenosu. Výchozí časové limity pro operace zavření, otevření, přijetí a odeslání jsou z vazby provedeny při sestavení kanálu.  
  
|Name|HTTP|TCP/IP|Pojmenovaný kanál|  
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
  
### <a name="controlling-transport-quotas-from-the-binding"></a>Řízení přenosových kvót z vazby  
 Nastavení přenosových kvót prostřednictvím vazby nabízí zjednodušenou sadu kvót, ze kterých si můžete vybrat, a zároveň přitom udělíte přístup k nejběžnějším hodnotám kvót.  
  
|Name|HTTP|TCP/IP|Pojmenovaný kanál|  
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
  
1. `MaxBufferSize`Kvóta přenosu je k dispozici pouze pro `BasicHttp` vazbu. `WSHttp`Vazby jsou pro scénáře, které nepodporují streamované transportní režimy.  
  
2. Přenosové kvóty `MaxPendingConnections` a `MaxOutboundConnectionsPerEndpoint` jsou zkombinovány do jedné dopravní kvóty s názvem `MaxConnections` .  
  
### <a name="controlling-transport-quotas-from-configuration"></a>Řízení přenosových kvót z konfigurace  
 Konfigurace aplikace může nastavit stejnou přenosovou kvótu jako přímý přístup k vlastnostem vazby. V konfiguračních souborech má název pro přenosovou kvótu vždycky začínat malým písmenem. Například `CloseTimeout` vlastnost u vazby odpovídá `closeTimeout` nastavení v konfiguraci a `MaxConnections` vlastnost u vazby odpovídá `maxConnections` nastavení v konfiguraci.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
