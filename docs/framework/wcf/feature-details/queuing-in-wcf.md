---
title: Fronty ve WCF
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: c390970d66e442eb413d238691896608dcf27e03
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643499"
---
# <a name="queuing-in-wcf"></a>Fronty ve WCF
Tato část popisuje způsob použití komunikaci ve frontě ve Windows Communication Foundation (WCF).  
  
## <a name="queues-as-a-wcf-transport-binding"></a>Vazby přenosu fronty jako WCF  
 Ve službě WCF kontrakty určit, co vyměňují. Kontrakty se výměny zpráv závislé na firmy nebo specifické pro aplikaci. Mechanismus, který se používá k výměně zpráv (nebo "o") je zadán v vazby. Vazby WCF zapouzdřit podrobnosti o výměně zpráv. Zveřejňovaly knoflíky konfigurace pro uživatele k řízení různých aspektů přenos nebo protokolu, které představují vazby. Fronty ve WCF se zachází stejně jako jakékoli jiné přenosu vázání, jež je velkým přínosem pro spoustu aplikací na zařazování do fronty. V současné době se mnoho aplikací služby Řízení front zapisují odlišně od jiných vzdálené volání procedur (RPC)-style distribuovaných aplikací, kvůli tomu je těžší sledovat a udržovat. S použitím technologie WCF styl psaní distribuované aplikace je skoro stejné, snadněji sledovat a udržovat. Ve které budou zohledňovat si mechanismus exchange nezávisle na obchodní logiku, je navíc jednodušší konfigurovat přenos nebo provést změny bez ovlivnění kódu konkrétní aplikace. Následující obrázek znázorňuje strukturu pomocí služby MSMQ jako přenosového mechanismu klienta a služby WCF.  
  
 ![Ve frontě diagramu aplikace](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "distribuované obrázek fronty")  
  
 Jak je vidět z předchozí obrázek, klient a služba musí definovat jenom aplikace sémantiku, to znamená, kontrakt a implementaci. Služba nakonfiguruje pomocí nastavení vazbu s frontou. Klient použije [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování klienta WCF na službu a vygenerovat konfigurační soubor, který popisuje vazby na použití pro odesílání zpráv do služby. Odeslat zprávu ve frontě, proto klient vytvoří instanci klienta WCF a vyvolá operaci na něj. To způsobí, že zpráva, která má být odeslána do fronty přenosu a přenést do cílové fronty. Všem složitosti komunikaci ve frontě jsou skryté aplikace, která je odeslání a příjem zpráv.  
  
 Upozornění o vazbách zařazených do fronty ve WCF patří:  
  
- Všechny služby, které operace musí být jednosměrné, protože výchozí vazby ve službě WCF zařazených do fronty nepodporuje duplexní komunikaci pomocí front. Ukázka obousměrnou komunikaci ([obousměrné komunikace](../../../../docs/framework/wcf/samples/two-way-communication.md)) ukazuje, jak můžete implementovat pomocí front duplexní komunikaci dva jednosměrné kontrakty.  
  
- Ke generování WCF klienta pomocí výměny metadat vyžaduje další koncový bod protokolu HTTP na službu, takže může být dotazována přímo k generování klienta WCF a získat informace o vazbě správně nakonfigurovat komunikaci ve frontě.  
  
- Podle vazbu s frontou, není nutná další konfigurace mimo WCF. Například <xref:System.ServiceModel.NetMsmqBinding> třídy, který je dodáván s použitím technologie WCF vyžaduje, abyste nakonfigurujte vazby také provedli minimální konfiguraci služby Řízení front zpráv (MSMQ).  
  
 Následující části popisují konkrétní zařazených do fronty vazby součástí WCF, které jsou založeny na služby MSMQ.  
  
### <a name="msmq"></a>MSMQ  
 Přenos zařazených do fronty ve WCF využívá služby MSMQ pro jeho komunikaci ve frontě.  
  
 Fronta MSMQ se dodává jako volitelnou komponentu s Windows a běží jako služba NT. Zachycení zpráv pro předávání v přenosové frontě a doručování do cílové fronty. Správci fronty MSMQ implementovat spolehlivé přenos zpráv protokolu, aby se zprávy nejsou ztraceno v přenosu. Protokol může být nativní nebo založený na protokolu SOAP, jako je například spolehlivé zprávy protokolu (SRMP) protokolu SOAP.  
  
 Služby MSMQ může být fronty transakcí nebo není transakční. Transakční fronta umožňuje zachytit a doručit v transakci a potom ukládají odolným způsobem ve frontě zpráv. Zprávy odeslané do transakční fronty přenosu právě jednou v pořadí. Netransakční fronta můžete použít k odesílání zpráv volatile a odolnost. Zpráva odeslaná do netransakční fronta neobsahuje žádnou záruku spolehlivé přenos; Proto může dojít ke ztrátě zpráv.  
  
 Fronty MSMQ zabezpečit je také možné pomocí Windows identity registraci ve službě Active Directory directory. Při instalaci služby MSMQ, můžete nainstalovat integrace služby Active Directory, která vyžaduje, aby počítač jako součást síťové domény Windows.  
  
 Další informace o MSMQ najdete v tématu [instalace řízení front zpráv (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 [ \<NetMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) je ve frontě vazby WCF poskytuje dva koncové body služby WCF pro komunikaci pomocí služby MSMQ. Vazba, proto zpřístupní vlastnosti, které jsou specifické pro službu MSMQ. Ale ne všechny funkce služby MSMQ a vlastnosti nejsou zveřejněné v žádném `NetMsmqBinding`. Komprese `NetMsmqBinding` je navržená s optimální sadu funkcí, které většina zákazníků byste najít dostatečná.  
  
 `NetMsmqBinding` Manifesty základní koncepty služby Řízení front doposud popsané ve formě vlastnosti na vazby. Tyto vlastnosti zase komunikaci služby MSMQ přenosu a doručovat zprávy. Diskuzi o vlastnosti kategorie je v následujících částech. Další informace najdete v tématu koncepční témata, které popisují konkrétní vlastnosti komplexněji.  
  
#### <a name="exactlyonce-and-durable-properties"></a>ExactlyOnce a trvalý vlastnosti  
 `ExactlyOnce` a `Durable` vlastnosti vliv na způsob přenosu zpráv mezi fronty:  
  
- `ExactlyOnce`: Pokud je nastavena na `true` (výchozí), kanálu ve frontě zajistí, že není duplicitní zprávy, pokud doručena. Také zajistí, že nedojde ke ztrátě zprávy. Pokud zprávu nelze doručit nebo zprávy čas – Chcete-li vyprší zprávu můžou doručit, neúspěšné zprávy spolu s doručování důvod selhání se zaznamená do fronty nedoručených zpráv. Pokud je nastavena na `false`, kanálu ve frontě nevyvine přenášet zprávy. V takovém případě můžete volitelně zvolit fronty nedoručených zpráv.  
  
- `Durable:` Pokud je nastavena na `true` (výchozí), kanálu ve frontě zajistí, že služba MSMQ ukládá zprávy trvale na disk. Proto šlo zastavit a restartovat službu MSMQ zprávy na disku je přenést do cílové fronty nebo odeslaná do služby. Pokud je nastavena na `false`, zprávy se ukládají v úložišti volatile a jsou ztraceny na zastavení a restartování služby MSMQ.  
  
 Pro `ExactlyOnce` spolehlivé přenosu služby MSMQ vyžaduje fronty využívat transakce. MSMQ také vyžaduje transakce čtení z transakční frontu. V důsledku toho při použití `NetMsmqBinding`, mějte na paměti, že transakce je nutný k odeslání nebo přijetí zprávy, když `ExactlyOnce` je nastavena na `true`. Obdobně vyžaduje MSMQ fronty bude netransakční pro záruky best effort, například kdy `ExactlyOnce` je `false` a pro těkavých zasílání zpráv. Proto při nastavování `ExactlyOnce` k `false` nebo trvalý k `false`, nelze odesílat ani přijímat pomocí transakce.  
  
> [!NOTE]
>  Ověřte, zda správné fronty (transakční či netransakční) je vytvořen na základě nastavení ve vazbách. Pokud `ExactlyOnce` je `true`, použít transakční frontu; v opačném případě použijte netransakční fronta.  
  
#### <a name="dead-letter-queue-properties"></a>Vlastnosti fronty nedoručených zpráv  
 Fronty nedoručených zpráv se používá k ukládání zpráv, které nesplní doručování. Uživatel můžete napsat kompenzační logiku, která čte zprávy z fronty nedoručených zpráv.  
  
 Mnoho systémů zařazování do fronty poskytuje fronty nedoručených zpráv celý systém. Služby MSMQ obsahuje systémová netransakční onta nedoručených zpráv fronty zpráv, které nesplní doručování transakční fronty a systémová Transakční nedoručené zprávy fronty zpráv, které nesplní doručování transakční fronty.  
  
 Pokud více klientů, které odesílání zpráv do fronty jiné cílové sdílené složky služby MSMQ, všechny zprávy od klientů použít stejné fronty nedoručených zpráv. To není vždy vhodnější. Pro lepší izolaci, WCF a služby MSMQ v [!INCLUDE[wv](../../../../includes/wv-md.md)] poskytnout vlastní frontu nedoručených zpráv (nebo frontu nedoručených zpráv specifické pro aplikaci), může uživatel zadat k ukládání zpráv, které nesplní doručování. Proto různých klientů Nesdílejte stejné fronty nedoručených zpráv.  
  
 Vazba má dvě vlastnosti, které vás zajímají:  
  
- `DeadLetterQueue`: Tato vlastnost je výčet, který označuje, zda je požadována fronty nedoručených zpráv. Výčet obsahuje také typ fronty nedoručených zpráv, pokud požadovaná. Hodnoty jsou `None`, `System`, a `Custom`. Další informace o interpretaci těchto vlastností najdete v tématu [pomocí fronty nedoručených zpráv pro zpracování selhání přenosu zpráv](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
- `CustomDeadLetterQueue`: Tato vlastnost je identifikátor URI (Uniform Resource) adresa fronty nedoručených zpráv specifické pro aplikaci. To je potřeba, pokud `DeadLetterQueue`.`Custom` je vybrán.  
  
#### <a name="poison-message-handling-properties"></a>Zacházení s nezpracovatelnými vlastnosti zpracování zpráv  
 Když služba načte zprávy z cílové fronty v rámci transakce, služba nemusí podařit zprávu zpracovat z různých důvodů. Zpráva se pak znovu umístěny do fronty se znovu přečíst. Se zprávy, které nesplní opakovaně, sadu zpracování zpráv poison vlastnosti mohou být konfigurovány ve vazbě. Existují čtyři vlastnosti: `ReceiveRetryCount`, `MaxRetryCycles`, `RetryCycleDelay`, a `ReceiveErrorHandling`. Další informace o těchto vlastnostech najdete v tématu [zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
#### <a name="security-properties"></a>Vlastnosti zabezpečení  
 MSMQ zpřístupňuje svůj vlastní model zabezpečení, jako jsou například seznamy řízení přístupu (ACL) ve frontě nebo odeslání ověřené zprávy. `NetMsmqBinding` Zpřístupní tyto vlastnosti zabezpečení jako součást jeho nastavení zabezpečení přenosu. Existují dvě vlastnosti ve vazbě pro zabezpečení přenosu: `MsmqAuthenticationMode` a `MsmqProtectionLevel`. Nastavení na tyto vlastnosti závisí na konfiguraci služby MSMQ. Další informace najdete v tématu [zabezpečení zabezpečení zprávy přenosu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
 Kromě zabezpečení přenosu je možné zabezpečit skutečné vlastní zprávě SOAP pomocí zabezpečení zpráv. Další informace najdete v tématu [zabezpečení zabezpečení zprávy zpráv](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md).  
  
 `MsmqTransportSecurity` také poskytuje dvě vlastnosti `MsmqEncryptionAlgorithm` a `MsmqHashAlgorithm`. Jedná se o výčty různých algoritmů pro výběr pro algoritmu hash podpisů a šifrování přenosu k frontě zpráv.  
  
#### <a name="other-properties"></a>Další vlastnosti  
 Kromě předchozích vlastností další vlastnosti specifické pro službu MSMQ v vazby zahrnout:  
  
- `UseSourceJournal`: Je povolena vlastnost umožňující označit, že záznamu do deníku zdroje. Záznamu do deníku zdroje je funkce služby MSMQ, která uchovává informace o zprávy, které byly úspěšně odeslány z fronty přenosu.  
  
- `UseMsmqTracing`: Vlastnost umožňující označit, že je zapnutá trasování služby MSMQ. Trasování služby MSMQ odešle zprávy do fronty hlášení pokaždé, když opustí zpráva nebo zpráva dorazí na počítače hostujícího správce fronty MSMQ.  
  
- `QueueTransferProtocol`: Výčet protokol bude použit pro přenos zpráv k frontě. MSMQ – implementuje nativní k frontě přenosový protokol a názvem protokol spolehlivého zasílání zpráv na SOAP (SRMP) protokol založený na protokolu SOAP. SRMP se používá při použití přenosového protokolu HTTP pro přenos k frontě. SRMP zabezpečení se používá při použití protokolu HTTPS pro přenosy na frontě.  
  
- `UseActiveDirectory`: Logická hodnota označující, zda služba Active Directory musí být použito pro rozpoznání adresy fronty. Ve výchozím nastavení toto je vypnuto. Další informace najdete v tématu [koncové body služby a adresování front](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 `MsmqIntegrationBinding` Se používá, když chcete, aby ke komunikaci s existující služby MSMQ aplikace napsané v jazyce C, C++, COM nebo rozhraní API System.Messaging koncového bodu WCF.  
  
 Vazby vlastnosti jsou stejné jako v případě `NetMsmqBinding`. Nicméně platí následující rozdíly:  
  
- Kontrakt pro `MsmqIntegrationBinding` je omezen na pořízení jeden parametr typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> kde parametr typu je typ těla zprávy.  
  
- Velká část vlastnosti nativních zpráv MSMQ jsou přístupné <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> pro použití.  
  
- Smyslem serializaci a deserializaci textu zprávy, jsou k dispozici serializátory, jako jsou XML a ActiveX.  
  
### <a name="sample-code"></a>Vzorový kód  
 Podrobné pokyny o tom, jak napsat WCF služby, které používají služby MSMQ naleznete v následujících tématech:  
  
- [Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací služby Řízení front zpráv](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
- [Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 Dokončený kód v ukázce použití služby MSMQ ve službě WCF najdete v následujících tématech:  
  
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
