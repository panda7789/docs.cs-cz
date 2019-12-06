---
title: Fronty ve WCF
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: 6656ab0b2db88297e6ac9a28bb2ea18c0056d18c
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837321"
---
# <a name="queuing-in-wcf"></a>Fronty ve WCF
Tato část popisuje, jak používat komunikaci ve frontě v Windows Communication Foundation (WCF).  
  
## <a name="queues-as-a-wcf-transport-binding"></a>Fronty jako transportní vazba WCF  
 Ve službě WCF smlouvy určují, co se má vyměňovat. Kontrakty jsou v závislosti na podnikovém nebo specifickém výměnou zpráv. Mechanismus použitý k výměně zpráv (nebo "How") je zadán ve vazbách. Vazby v WCF zapouzdřují podrobnosti výměny zpráv. Zpřístupňují konfigurační ovladače pro uživatele k řízení různých aspektů přenosu nebo protokolu, který vazby představují. Zařazení do fronty ve službě WCF se považuje za jakoukoliv jinou přenosovou vazbu, což je velkou výhodou pro mnoho aplikací služby Řízení front. V současné době se mnoho aplikací služby Řízení front zapisuje odlišně od jiných distribuovaných aplikací ve stylu vzdáleného volání procedur (RPC), což usnadňuje sledování a údržbu. Pomocí služby WCF je styl psaní distribuované aplikace mnohem stejný, což usnadňuje sledování a údržbu. Kromě toho tím, že se mechanizmus výměny nezávisle na obchodní logice nakonfiguruje, je snazší nakonfigurovat přenos nebo provádět změny, aniž by to ovlivnilo kód specifický pro aplikaci. Následující obrázek znázorňuje strukturu služby WCF a klienta pomocí služby MSMQ jako přenosu.  
  
 ![Diagram aplikace ve frontě](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Distribuované – fronta – obrázek")  
  
 Jak vidíte předchozí obrázek, klient a služba musí definovat pouze sémantiku aplikace, to znamená kontrakt a implementaci. Služba konfiguruje vazbu ve frontě s preferovaným nastavením. Klient nástroje používá nástroj pro dokládání [metadat (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování klienta WCF pro službu a k vygenerování konfiguračního souboru, který popisuje vazby, které se mají použít k posílání zpráv do služby. Proto klient pro odeslání zprávy ve frontě vytvoří instanci klienta WCF a vyvolá na něm operaci. Tím dojde k odeslání zprávy do fronty přenosů a přenos do cílové fronty. Všechny složitosti komunikace ve frontě jsou skryté od aplikace, která odesílá a přijímá zprávy.  
  
 Mezi upozornění týkající se vazby ve frontě ve službě WCF patří:  
  
- Všechny operace služby musí být jednosměrné, protože výchozí vazba zařazená do fronty ve službě WCF nepodporuje duplexní komunikaci pomocí front. Obousměrný způsob komunikace ([Obousměrná komunikace](../../../../docs/framework/wcf/samples/two-way-communication.md)) ukazuje, jak používat 2 1 kontrakty k implementaci duplexní komunikace pomocí front.  
  
- Generování klienta WCF pomocí výměny metadat vyžaduje pro službu další koncový bod HTTP, aby se mohla dotazovat přímo za účelem generování klienta WCF a získání informací o vazbě ke správné konfiguraci komunikace zařazené do fronty.  
  
- V závislosti na vazbě zařazené do fronty je vyžadována další konfigurace mimo WCF. Například třída <xref:System.ServiceModel.NetMsmqBinding>, která je dodávána s WCF, vyžaduje, abyste nakonfigurovali vazby a nakonfigurovali také minimální konfiguraci služby Řízení front zpráv (MSMQ).  
  
 Následující části popisují konkrétní vazby zařazené do fronty dodávané se službou WCF založené na službě MSMQ.  
  
### <a name="msmq"></a>MSMQ  
 Přenos ve frontě ve službě WCF používá ke své komunikaci ve frontě službu MSMQ.  
  
 Služba MSMQ je dodávána jako volitelná součást se systémem Windows a spouští se jako služba NT. Zachycuje zprávy pro přenos ve frontě přenosu a pro doručení do cílové fronty. Správci fronty MSMQ implementují spolehlivý protokol pro přenos zpráv, aby se zprávy během přenosu neztratily. Protokol může být buď nativní, nebo založený na protokolu SOAP, jako je protokol SRMP (SOAP Reliable Message Protocol).  
  
 Ve službě MSMQ můžou být fronty transakční nebo netransakční. Transakční fronta umožňuje zaznamenávat a doručovat zprávy v transakci a následně ukládat trvale ve frontě. Zprávy odeslané do transakční fronty jsou přenášeny právě jednou v daném pořadí. K posílání stálých i trvalých zpráv můžete použít netransakční frontu. Zpráva odeslaná do netransakční fronty neprovádí žádné spolehlivé záruky přenosu. zprávy proto mohou být ztraceny.  
  
 Fronty MSMQ je taky možné zabezpečit pomocí identity Windows registrované v adresářové službě Active Directory. Při instalaci služby MSMQ můžete nainstalovat integraci služby Active Directory, která vyžaduje, aby počítač byl součástí doménové sítě systému Windows.  
  
 Další informace o službě MSMQ najdete v tématu [instalace služby Řízení front zpráv (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 [\<NetMsmqBinding](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) je vazba WCF ve frontě, která umožňuje komunikaci dvou koncových bodů WCF pomocí služby MSMQ. Vazba proto zpřístupňuje vlastnosti, které jsou specifické pro službu MSMQ. Ne všechny funkce a vlastnosti služby MSMQ ale nejsou přístupné v `NetMsmqBinding`. Kompaktní `NetMsmqBinding` je navržený s optimální sadou funkcí, které by většina zákazníků měla najít dostatečná.  
  
 `NetMsmqBinding` manifesty základních konceptů zařazených do fronty, které jsou doposud popsané, ve formě vlastností vazeb. Tyto vlastnosti zase komunikují se službou MSMQ při přenosu a doručování zpráv. Diskuze o kategoriích vlastností je v následujících oddílech. Další informace najdete v koncepčních tématech s úplným popisem specifických vlastností.  
  
#### <a name="exactlyonce-and-durable-properties"></a>ExactlyOnce a trvalé vlastnosti  
 Vlastnosti `ExactlyOnce` a `Durable` ovlivňují přenos zpráv mezi frontami:  
  
- `ExactlyOnce`: když se nastaví na `true` (výchozí nastavení), kanál zařazený do fronty zajistí, že se zpráva, pokud je dodána, nebude duplikována. Také zajišťuje, že nedojde ke ztrátě zprávy. Pokud zprávu nelze doručit nebo pokud doba platnosti zprávy vypršela před doručením zprávy, chybová zpráva spolu s důvodem selhání doručení je zaznamenána ve frontě nedoručených zpráv. Když nastavíte `false`, kanál ve frontě vytvoří úsilí k přenosu zprávy. V takovém případě můžete volitelně zvolit frontu nedoručených zpráv.  
  
- `Durable:` Pokud je nastavená na `true` (výchozí nastavení), kanál zařazený do fronty zajistí, že služba MSMQ ukládá zprávu trvale na disk. Pokud se tedy služba MSMQ zastavila a restartuje, zprávy na disku se přenesou do cílové fronty nebo se doručí službě. Když nastavíte `false`, zprávy se uloží do stálého úložiště a při zastavení a restartování služby MSMQ se ztratí.  
  
 Pro `ExactlyOnce` Reliable Transfer vyžaduje fronta MSMQ transakční službu. Služba MSMQ také vyžaduje transakci pro čtení z transakční fronty. Když použijete `NetMsmqBinding`, pamatujte na to, že při posílání nebo přijímání zpráv je nutné zadat transakci, když `ExactlyOnce` nastavena na `true`. Podobně služba MSMQ vyžaduje, aby fronta byla netransakční pro zajištění co nejlepšího úsilí, například když `ExactlyOnce` `false` a pro nestálé zasílání zpráv. Proto když nakonfigurujete `ExactlyOnce`, aby `false` nebo trvalá `false`, nelze odeslat ani přijmout pomocí transakce.  
  
> [!NOTE]
> Zajistěte, aby byla na základě nastavení v vazbách vytvořena správná fronta (transakční nebo netransakční). Pokud je `ExactlyOnce` `true`, použijte transakční frontu. v opačném případě použijte netransakční frontu.  
  
#### <a name="dead-letter-queue-properties"></a>Vlastnosti fronty nedoručených zpráv  
 Fronta nedoručených zpráv se používá k ukládání zpráv, které nedoručení doplní. Uživatel může napsat kompenzační logiku, která čte zprávy z fronty nedoručených zpráv.  
  
 Řada systémů řízení front poskytuje pro frontu nedoručených zpráv pro celé systémy. Služba MSMQ poskytuje frontu netransakčních netransakčních zpráv pro zprávy, které selžou doručení do netransakčních front a frontu nedoručených transakčních zpráv v rámci systému pro zprávy, které selžou doručení do transakčních front.  
  
 Pokud více klientů odesílajících zprávy do různých cílových front sdílí službu MSMQ, všechny zprávy odesílané klienty přejdou do stejné fronty nedoručených zpráv. To není vždy vhodnější. Pro lepší izolaci WCF a MSMQ v systému Windows Vista poskytují vlastní frontu nedoručených zpráv (nebo frontu nedoručených zpráv specifickou pro aplikaci), kterou může uživatel zadat pro ukládání zpráv, u kterých dojde k selhání doručení. Proto Různí klienti nesdílejí stejnou frontu nedoručených zpráv.  
  
 Vazba má dvě vlastnosti zájmu:  
  
- `DeadLetterQueue`: Tato vlastnost je výčet, který označuje, jestli je požadovaná fronta nedoručených zpráv. Výčet také obsahuje druh fronty nedoručených zpráv, pokud je požadován. Hodnoty jsou `None`, `System`a `Custom`. Další informace o interpretaci těchto vlastností najdete v tématu [použití front nedoručených zpráv pro zpracování selhání přenosu zpráv](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md) .  
  
- `CustomDeadLetterQueue`: Tato vlastnost je adresa identifikátoru URI (Uniform Resource Identifier) fronty nedoručených zpráv pro konkrétní aplikaci. To je vyžadováno, pokud `DeadLetterQueue`.`Custom` je zvolena.  
  
#### <a name="poison-message-handling-properties"></a>Vlastnosti zpracování nezpracovatelných zpráv  
 Když služba přečte zprávy z cílové fronty v transakci, služba se nemusí podařit zpracovat zprávu z různých důvodů. Zpráva se pak vrátí zpátky do fronty pro opětovné čtení. Chcete-li se zabývat se zprávami, které se opakují opakovaně, lze ve vazbě nakonfigurovat sadu vlastností zpracování nefunkčních zpráv. Existují čtyři vlastnosti: `ReceiveRetryCount`, `MaxRetryCycles`, `RetryCycleDelay`a `ReceiveErrorHandling`. Další informace o těchto vlastnostech naleznete v tématu [manipulace s Nezpracovatelovou zprávou](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
#### <a name="security-properties"></a>Vlastnosti zabezpečení  
 Služba MSMQ zpřístupňuje svůj vlastní model zabezpečení, například seznamy řízení přístupu (ACL) ve frontě nebo odesílání ověřených zpráv. `NetMsmqBinding` zpřístupňuje tyto vlastnosti zabezpečení jako součást nastavení zabezpečení přenosu. Existují dvě vlastnosti ve vazbě pro zabezpečení přenosu: `MsmqAuthenticationMode` a `MsmqProtectionLevel`. Nastavení v těchto vlastnostech závisí na konfiguraci služby MSMQ. Další informace najdete v tématu [zabezpečení zpráv pomocí zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
 Kromě zabezpečení přenosu je možné samotnou vlastní zprávu SOAP zabezpečit pomocí zabezpečení zpráv. Další informace najdete v tématu [zabezpečení zpráv pomocí zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md).  
  
 `MsmqTransportSecurity` také zpřístupňuje dvě vlastnosti, `MsmqEncryptionAlgorithm` a `MsmqHashAlgorithm`. Jedná se o výčty různých algoritmů pro výběr přenosu zpráv z fronty do fronty a jejich hashování u podpisů.  
  
#### <a name="other-properties"></a>Další vlastnosti  
 Kromě předchozích vlastností jsou k dispozici i další vlastnosti specifické pro službu MSMQ uvedené ve vazbě:  
  
- `UseSourceJournal`: vlastnost, která označuje, že je zapnuté ukládání zdrojů do deníku. Deníkování zdrojů je funkce služby MSMQ, která sleduje zprávy, které byly úspěšně přeneseny z fronty přenosu.  
  
- `UseMsmqTracing`: vlastnost, která označuje, že trasování služby MSMQ je zapnuté. Trasování služby MSMQ odesílá zprávy sestavy do fronty sestav pokaždé, když se zpráva opustí nebo dorazí na počítač, který je hostitelem správce fronty MSMQ.  
  
- `QueueTransferProtocol`: výčet protokolu, který se má použít pro přenosy zpráv z fronty do fronty. Služba MSMQ implementuje nativní přenosovou protokol front-Queue a protokol SOAP nazvaný protokolu SOAP Reliable Messaging Protocol (SRMP). Protokol SRMP se používá při přenosu protokolu HTTP pro přenosy front-Queue. Protokol SRMP se používá při použití protokolu HTTPS k přenosům front-Queue.  
  
- `UseActiveDirectory`: logická hodnota určující, zda se má služba Active Directory používat k překladu adres fronty. Ve výchozím nastavení je to vypnuté. Další informace najdete v tématu [koncové body služby a adresování front](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 `MsmqIntegrationBinding` se používá v případě, že chcete, aby koncový bod WCF komunikoval s existující aplikací služby MSMQ napsanou C++v rozhraních API jazyka C,, com nebo System. Messaging.  
  
 Vlastnosti vazby jsou stejné jako u `NetMsmqBinding`. Platí ale následující rozdíly:  
  
- Kontrakt operace pro `MsmqIntegrationBinding` je omezen na použití jednoho parametru typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, kde parametr typu je typ těla.  
  
- Většina vlastností nativní zprávy služby MSMQ je dostupná v <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> pro použití.  
  
- Pro usnadnění serializace a deserializace těla zprávy je k dispozici serializátory, jako je XML a ActiveX.  
  
### <a name="sample-code"></a>Vzorový kód  
 Podrobné pokyny k psaní služeb WCF, které používají službu MSMQ, najdete v následujících tématech:  
  
- [Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
- [Postupy: Výměna zpráv zařazených do fronty s koncovými body WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 Kompletní vzorek kódu, který ilustruje použití služby MSMQ ve službě WCF, najdete v následujících tématech:  
  
- [Zpracované vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
- [Nestálá komunikace ve frontě](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
- [Fronty nedoručených zpráv](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
- [Relace a fronty](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
- [Obousměrná komunikace](../../../../docs/framework/wcf/samples/two-way-communication.md) 
  
- [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
- [Zabezpečení zprávy pomocí služby Řízení front zpráv](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>Viz také:

- [Koncové body služby a adresování front](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
- [Webhosting frontové aplikace](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
