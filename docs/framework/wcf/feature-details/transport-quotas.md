---
title: Přenosové kvóty
ms.date: 03/30/2017
helpviewer_keywords:
- transport quotas [WCF]
ms.assetid: 3e71dd3d-f981-4d9c-9c06-ff8abb61b717
ms.openlocfilehash: 0664dbb70df61c0f68d34c4ab364db6623805bfa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542766"
---
# <a name="transport-quotas"></a>Přenosové kvóty
Přenosové kvóty slouží jako mechanismus pro zásady pro rozhodování o tom, kdy připojení spotřebovává přemíru prostředků. Kvóta je pevný limit, který brání použití další zdroje informací po překročení hodnoty kvóty. Přenosové kvóty zabránit škodlivým nebo neúmyslným útoky s cílem odepření služby.  
  
 Přenosy Windows Communication Foundation (WCF) mají výchozí kvótu hodnoty, které jsou založeny na konzervativní přidělení prostředků. Tyto výchozí hodnoty jsou vhodné pro vývojové prostředí a scénářů malé instalace. Správci služeb by měl přenosové kvóty ověřit a odladit hodnoty individuální diskových kvót, pokud instalace může být nedostatek prostředků, nebo pokud připojení jsou omezeno bez ohledu na dostupnost další prostředky.  
  
## <a name="types-of-transport-quotas"></a>Typy přenosové kvóty  
 Přenosy WCF mají tři typy kvót:  
  
-   *Vypršení časových limitů* zmírnit útoky na dostupnost služby, které využívají obsadit prostředků delší dobu.  
  
-   *Omezení přidělení paměti* zabránit jediné připojení z vyčerpáním systémové paměti a odepření služby do jiné připojení.  
  
-   *Limity velikosti kolekce* vázán spotřebu prostředků, která nepřímo alokovat paměť nebo jsou v nějak omezený.  
  
## <a name="transport-quota-descriptions"></a>Přenosové kvóty popisy  
 Tato část popisuje, k dispozici pro standardní přenosy WCF přenosové kvóty: HTTP (S), protokolu TCP/IP a pojmenovaných kanálů. Vlastní přenosy můžete zveřejnit své vlastní konfigurovatelné kvóty nejsou zahrnuty v tomto seznamu. V dokumentaci pro vlastní přenos najdete informace o jeho kvóty.  
  
 Každé nastavení kvóty má typ, minimální hodnota a výchozí hodnota. Jeho typ je omezená maximální hodnota kvóty. Vzhledem k omezením počítač není vždy možné nastavit kvótu pro maximální hodnota.  
  
|Název|Typ|Min.<br /><br /> value|Výchozí<br /><br /> value|Popis|  
|----------|----------|--------------------|-----------------------|-----------------|  
|`ChannelInitializationTimeout`|Časový interval|1 značek|5 s|Maximální doba čekání na připojení k odesílání preambule během počáteční pro čtení. Přijetí tato data předtím, než dojde k ověření. Toto nastavení je obvykle mnohem menší, než `ReceiveTimeout` hodnota kvóty.|  
|`CloseTimeout`|Časový interval|0|1 min.|Maximální doba čekání na připojení k zavřete, než přenos vyvolá výjimku.|  
|`ConnectionBufferSize`|Integer|1|VELIKOSTI 8 KB|Velikost v bajtech, odesílání a příjem základní přenos. Zvýšení velikosti vyrovnávací paměti může zvýšit propustnost, při odesílání velkých zpráv.|  
|`IdleTimeout`|Časový interval|0|2 min|Maximální doba připojení z fondu může zůstat nečinné, než jeho uzavírání.<br /><br /> Toto nastavení platí jenom pro připojení ve fondu.|  
|`LeaseTimeout`|Časový interval|0|5 min|Maximální doba života aktivní ve fondu připojení. Po uplynutí určité doby, zavře po Údržba aktuálního požadavku.<br /><br /> Toto nastavení platí jenom pro připojení ve fondu.|  
|`ListenBacklog`|Integer|1|10|Maximální počet připojení, které můžou mít unserviced naslouchací proces před další připojení do tohoto koncového bodu byl odepřen.|  
|`MaxBufferPoolSize`|Dlouhé|0|512 KB|Maximální velikost paměti v bajtech, která se věnuje přenos sdružování vyrovnávací paměti zpráv opakovaně použitelné. Pokud vyrovnávací paměť zpráv nelze zadat fond, nové vyrovnávací paměti přidělené dočasné.<br /><br /> Zařízení, které vytvoří velký počet objektů pro vytváření kanálů nebo naslouchacích procesů můžete přidělit velké množství paměti pro fondy vyrovnávací paměti. Zmenšení velikosti této vyrovnávací paměti může výrazně snížit využití paměti v tomto scénáři.|  
|`MaxBufferSize`|Integer|1|64 KB|Maximální velikost v bajtech pro datový proud vyrovnávací paměti. Tato kvóta přenos není nastavená, nebo přenos nepoužívá, streamování a potom hodnoty kvóty je stejné jako menší z `MaxReceivedMessageSize` hodnoty kvóty na a <xref:System.Int32.MaxValue>.|  
|`MaxOutboundConnectionsPerEndpoint`|Integer|1|10|Maximální počet odchozích připojení, které mohou být spojeny s konkrétní koncový bod.<br /><br /> Toto nastavení platí jenom pro připojení ve fondu.|  
|`MaxOutputDelay`|Časový interval|0|200 ms|Maximální doba čekání, po operaci odeslání pro dávkové zpracování dalších zpráv v rámci jedné operace. Zprávy se odešlou dříve, pokud vyrovnávací paměť základní přenos zaplní. Odesláním další zprávy není resetovaný dobu zpoždění.|  
|`MaxPendingAccepts`|Integer|1|1|Maximální počet kanálů přijme, mohou v naslouchacím čekání.<br /><br /> Je interval mezi dokončení přijmout a nové počáteční přijmout. Zvýšit velikost této kolekce mohou zabránit klientům, které během tohoto intervalu z probíhá vyřazování připojit.|  
|`MaxPendingConnections`|Integer|1|10|Maximální počet připojení, která mohou v naslouchacím čekat na přijetí aplikací. Při překročení této kvóty hodnoty nové příchozí připojení jsou vynechány místo čekat na přijetí.<br /><br /> Připojení funkce, jako je zabezpečení zpráv můžete donutit klienta k otevření více než jedno připojení. Správci služeb by měl účet pro tyto další připojení při nastavování této hodnoty kvóty.|  
|`MaxReceivedMessageSize`|Dlouhé|1|64 KB|Maximální velikost v bajtech přijaté zprávy, včetně záhlaví, než přenos vyvolá výjimku.|  
|`OpenTimeout`|Časový interval|0|1 min.|Maximální doba čekání na připojení k navázat před přenos vyvolá výjimku.|  
|`ReceiveTimeout`|Časový interval|0|10 minut|Maximální doba čekání na operaci čtení až po dokončení přenosu vyvolá výjimku.|  
|`SendTimeout`|Časový interval|0|1 min.|Maximální doba čekání na operaci zápisu až po dokončení přenosu vyvolá výjimku.|  
  
 Přenosové kvóty `MaxPendingConnections` a `MaxOutboundConnectionsPerEndpoint` jsou sloučeny do jednoho přenosové kvóty s názvem `MaxConnections` při nastavení prostřednictvím vazby nebo konfigurace. Pouze prvek vazby umožňuje nastavení tyto hodnoty kvóty zvlášť. `MaxConnections` Kvóty přenosu má stejné minimální a výchozí hodnoty.  
  
## <a name="setting-transport-quotas"></a>Nastavení přenosové kvóty  
 Přenosové kvóty jsou nastavené přes element vazby přenosu, vazby přenosu, konfiguraci aplikací nebo zásad. Tento dokument nepopisuje nastavení přenosy prostřednictvím zásad. V dokumentaci pro základní přenos zjistit nastavení pro hostitele zásady kvót. [Konfigurace HTTP a HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md) téma popisuje nastavení kvót pro ovladač Http.sys. Vyhledejte další informace o konfiguraci Windows omezení na HTTP, protokolu TCP/IP a pojmenovaných rour ve znalostní bázi Microsoft Knowledge Base.  
  
 Jiné typy kvót nepřímo platí pro přenosy. Kodér zprávy, která používá přenos pro transformaci zprávy do bajtů může mít svůj vlastní nastavení kvót. Tyto kvóty jsou však nezávisle na typ přenosu, které se používají.  
  
### <a name="controlling-transport-quotas-from-the-binding-element"></a>Přenosové kvóty z elementu vazby řízení  
 Nastavení přenosové kvóty prostřednictvím element vazby nabízí nejvyšší flexibilitu při řízení chování přenosu. Výchozí časové limity pro zavřít, otevřít, přijetí a odešlete operace pocházejí z vazby při vytváření kanálu.  
  
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
  
### <a name="controlling-transport-quotas-from-the-binding"></a>Přenosové kvóty z vazby řízení  
 Nastavení přenosové kvóty prostřednictvím vazby nabízí zjednodušené sadu kvót vybírat a přitom stále poskytují přístup k nejběžnějších hodnot kvóty.  
  
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
  
1.  `MaxBufferSize` Kvóty přenosu je dostupný jenom u `BasicHttp` vazby. `WSHttp` Vazby jsou určené pro scénáře, které nepodporují streamovaná dopravy.  
  
2.  Přenosové kvóty `MaxPendingConnections` a `MaxOutboundConnectionsPerEndpoint` jsou sloučeny do jednoho přenosové kvóty s názvem `MaxConnections`.  
  
### <a name="controlling-transport-quotas-from-configuration"></a>Přenosové kvóty z konfigurace řízení  
 Konfigurace aplikace můžete nastavit stejnou přenosové kvóty na přímo přístup k vlastnostem na vazbu. V konfiguračních souborech název kvóty přenosu vždy začíná malým písmenem. Například `CloseTimeout` odpovídá vlastnosti u vazby `closeTimeout` nastavení v konfiguraci a `MaxConnections` odpovídá vlastnosti u vazby `maxConnections` nastavení v konfiguraci.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
