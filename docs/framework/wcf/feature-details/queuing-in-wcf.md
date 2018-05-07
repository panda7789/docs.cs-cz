---
title: Fronty ve WCF
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: 7f0a6700dba8eb844cc471704095b29c2a2c7937
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="queuing-in-wcf"></a>Fronty ve WCF
Tato část popisuje postup použití komunikace ve frontě v systému Windows Communication Foundation (WCF).  
  
## <a name="queues-as-a-wcf-transport-binding"></a>Vazba přenosu fronty jako službou WCF  
 Ve službě WCF smluv zadejte, co je během výměny. Kontrakty jsou výměny zpráv závislé na obchodní nebo specifické pro aplikaci. Používáno pro výměnu zpráv (nebo "jak") je zadána v vazby. Vazby ve WCF zapouzdřovat podrobnosti výměny zpráv. Vystavují knoflíky konfigurace pro uživatele k řízení různé aspekty přenos nebo protokolu, které představují vazby. Fronty ve WCF je zpracovaná jako všechny ostatní přenosu vazby, což je velký využít pro mnoho aplikací služby Řízení front. V současné době se řada aplikací pro řazení do fronty zapisují jinak z jiných vzdáleného volání procedur (RPC)-styl distribuovaných aplikací, což těžší postupujte podle a údržbu. S použitím technologie WCF styl psaní distribuované aplikace je podobný, usnadnit postupujte podle a údržbu. Kromě toho řešení se tento mechanismus exchange nezávisle na obchodní logiku, se snadno konfigurovat přenos nebo provést změny bez ovlivnění konkrétního kódu aplikace. Následující obrázek ukazuje strukturu pomocí služby MSMQ přenos klienta a služby WCF.  
  
 ![Diagram aplikace ve frontě](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "distribuované obrázek fronty")  
  
 Jak je vidět na předchozím obrázku, klient a služba musí definovat pouze aplikace sémantiky, to znamená, kontrakt a implementaci. Služba nakonfiguruje vazbu zařazených do fronty se požadovaná nastavení. Klient použije [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování klienta WCF na službu a ke generování konfiguračního souboru, který popisuje vazby používat k odesílání zpráv do služby. Odeslat zprávu ve frontě, proto klient vytvoří klienta WCF a vyvolá operace na něm. To způsobí, že zpráva, která má být odeslána do fronty přenosu a přenést do cílové fronty. Aplikace, která odesílá a přijímá zprávy jsou skryta všechny složitosti komunikace ve frontě.  
  
 Upozornění o vazbě zařazených do fronty ve WCF patří:  
  
-   Všechny služby, které musí být operace jednosměrné, protože výchozí vazby ve WCF zařazených do fronty nepodporuje duplexní komunikace pomocí front. Ukázka obousměrné komunikace ([obousměrné komunikace](../../../../docs/framework/wcf/samples/two-way-communication.md)) ukazuje, jak používat dvě jednosměrné kontrakty implementovat duplexní komunikace pomocí front.  
  
-   Ke generování službou WCF klienta pomocí metadat exchange vyžaduje další koncový bod HTTP ve službě, takže může být dotazován přímo ke generování klienta WCF a získat informace o vazbě správně nakonfigurovat komunikace ve frontě.  
  
-   Podle toho, zařazených do fronty vazby, není nutná další konfigurace mimo WCF. Například <xref:System.ServiceModel.NetMsmqBinding> třídu, která je dodávána s použitím technologie WCF vyžaduje, abyste nakonfigurujte vazby a také minimálně konfigurovat služby Řízení front zpráv (MSMQ).  
  
 Následující části popisují konkrétní zařazených do fronty vazeb dodávané s použitím technologie WCF, které jsou založeny na služby MSMQ.  
  
### <a name="msmq"></a>MSMQ  
 Přenos zařazených do fronty ve WCF používá služby MSMQ pro jeho komunikaci ve frontě.  
  
 MSMQ dodává jako volitelná komponenta s Windows a spustí jako služba NT. Zachycení zprávy k přenosu v přenosové frontě pro doručení v cílové fronty. Správci frontu MSMQ implementovat protokol spolehlivého přenos zpráv tak, aby zprávy nejsou ztrátě při přenosu. Protokol může být nativní nebo založený na protokolu SOAP, jako je například protokolu SOAP spolehlivé zpráva SRMP (Protocol).  
  
 Služby MSMQ může být fronty transakcí nebo netransakční. Transakční fronta umožňuje zprávy a pokuste se zachytit a dodat v transakci a pak bezpečně uložené ve frontě. Zprávy odeslané do fronty transakcí se přenesou právě jednou v pořadí. Netransakční frontu můžete použít k odeslání zprávy volatile a trvanlivé. Zprávy odeslané do fronty netransakční neobsahuje žádné záruky, spolehlivé přenos; Proto může dojít ke ztrátě zpráv.  
  
 Fronty služby MSMQ lze také zabezpečit pomocí zaregistrována adresářové služby Active Directory identitu systému Windows. Při instalaci služby MSMQ, můžete nainstalovat integrace služby Active Directory, který vyžaduje počítač součástí domény sítě systému Windows.  
  
 Další informace o MSMQ najdete v tématu [instalaci řízení front zpráv (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>– NetMsmqBinding  
 [ \<– NetMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) je ve frontě vazby WCF poskytuje dva koncové body WCF na komunikaci pomocí služby MSMQ. Vazba, tedy zpřístupní vlastnosti, které jsou specifické pro služby MSMQ. Ale ne všechny funkce služby MSMQ a vlastnosti jsou přístupné `NetMsmqBinding`. Compact `NetMsmqBinding` slouží optimální sadou funkcí, které by měl zjistit dostatečná většina zákazníků.  
  
 `NetMsmqBinding` Manifesty základní koncepty služby Řízení front doposud popsané ve formě vlastnosti na vazby. Tyto vlastnosti se pak komunikovat s MSMQ postup přenosu a doručení zprávy. Popis kategorie vlastnost je v následujících částech. Další informace najdete v tématu koncepční témata, která popisují specifické vlastnosti více úplně.  
  
#### <a name="exactlyonce-and-durable-properties"></a>ExactlyOnce a trvanlivé vlastnosti  
 `ExactlyOnce` a `Durable` vlastnosti vliv na způsob přenosu zpráv mezi fronty:  
  
-   `ExactlyOnce`: Pokud nastavíte hodnotu `true` (výchozí), ve frontě kanál zajistí, že není duplikovaná zprávu, pokud doručit,. Také zajistí, že zpráva není ztraceny. Pokud zprávu nelze doručit, nebo před zprávy mohou být zajišťovány vyprší platnost zprávy čas k za provozu, neúspěšné zpráva spolu s důvodem selhání doručení se zaznamená do fronty nedoručených zpráv. Pokud nastavíte hodnotu `false`, díky snaze přenosu zprávy ve frontě kanál. V takovém případě můžete volitelně vybrat frontu nedoručených zpráv.  
  
-   `Durable:` Pokud nastavíte hodnotu `true` (výchozí), ve frontě kanál zajistí, že služby MSMQ ukládá zprávy spolehlivě na disk. Proto pokud služby MSMQ zastavit a restartovat, zprávy na disku je přenést do cílové fronty nebo doručit do služby. Pokud nastavíte hodnotu `false`, zprávy jsou uloženy v úložišti volatile a jsou v zastavením a restartováním služby MSMQ ztraceny.  
  
 Pro `ExactlyOnce` spolehlivé přenos MSMQ vyžaduje fronty využívat transakce. Také MSMQ vyžaduje transakce čtení z fronty transakcí. Jako takový, když použijete `NetMsmqBinding`, mějte na paměti, že transakce je potřeba odesílat nebo přijímat zprávy při `ExactlyOnce` je nastaven na `true`. Podobně MSMQ vyžaduje fronty být netransakční pro záruky best effort, například kdy `ExactlyOnce` je `false` a volatile zasílání zpráv. Proto při nastavování `ExactlyOnce` k `false` nebo trvanlivý k `false`, nelze odesílat a přijímat pomocí transakce.  
  
> [!NOTE]
>  Ověřte, zda správné fronty (transakční nebo netransakční) je vytvořen na základě nastavení v vazby. Pokud `ExactlyOnce` je `true`, použijte transakční fronty, jinak použijte netransakční fronty.  
  
#### <a name="dead-letter-queue-properties"></a>Vlastnosti fronty nedoručených zpráv  
 Frontu nedoručených zpráv se používá k ukládání zpráv, které nesplní doručení. Uživatel může zapisovat zušlechtěných logiky, která čte zprávy z fronty nedoručených zpráv.  
  
 Mnoho front systémy zadejte systémové fronty nedoručených zpráv. MSMQ poskytuje systémové netransakční frontu nedoručených zpráv pro zprávy, které nesplní doručení netransakční fronty a systémové transakční nedoručených zpráv fronty pro zprávy, které nesplní doručení transakcí fronty.  
  
 Pokud více klientů zasílání zpráv na jiné cílové fronty sdílet služby MSMQ, všechny zprávy od klientů přejděte do stejné fronty nedoručených zpráv. Toto není vždy vhodnější. Pro lepší izolaci, WCF a služby MSMQ v [!INCLUDE[wv](../../../../includes/wv-md.md)] zadejte vlastní frontu nedoručených zpráv (nebo frontu nedoručených zpráv specifické pro aplikaci), může uživatel zadat pro ukládání zpráv, které nesplní doručení. Proto různých klientů nesdílejí stejný frontu nedoručených zpráv.  
  
 Vazba má dvě vlastnosti, které vás zajímají:  
  
-   `DeadLetterQueue`: Tato vlastnost je výčet, který označuje, zda je fronta nedoručených zpráv. Pokud požadovaná, výčtu obsahuje také druh frontu nedoručených zpráv. Hodnoty jsou `None`, `System`, a `Custom`. Další informace o interpretaci těchto vlastností najdete v tématu [pomocí fronty nedoručených zpráv pro zpracování chyb přenosu zpráv](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
-   `CustomDeadLetterQueue`: Tato vlastnost je identifikátor URI (Uniform Resource) adresa fronty nedoručených zpráv specifické pro aplikaci. To je potřeba, pokud `DeadLetterQueue`.`Custom` je vybrán.  
  
#### <a name="poison-message-handling-properties"></a>Zacházení s nezpracovatelnými vlastnosti zpracování zpráv  
 Při službu čte zprávy z cílové fronty v rámci transakce, službu může dojít k selhání zpracování zprávy z různých důvodů. Zpráva je pak vrátit zpět do fronty se znovu načíst. Jak nakládat s zprávy, které nesplní opakovaného sadu zpracování zpráv poison vlastnosti mohou být konfigurovány vazba. Existují čtyři vlastnosti: `ReceiveRetryCount`, `MaxRetryCycles`, `RetryCycleDelay`, a `ReceiveErrorHandling`. Další informace o těchto vlastnostech najdete v tématu [zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
#### <a name="security-properties"></a>Vlastnosti zabezpečení  
 MSMQ zpřístupňuje vlastní model zabezpečení, jako je seznamy řízení přístupu (ACL) ve frontě nebo odesílání zprávy ověřený. `NetMsmqBinding` Zpřístupní tyto vlastnosti zabezpečení jako součást nastavení zabezpečení přenosu. Existují dvě vlastnosti ve vazbě pro zabezpečení přenosu: `MsmqAuthenticationMode` a `MsmqProtectionLevel`. Nastavení v těchto vlastností závisí na konfiguraci služby MSMQ. Další informace najdete v tématu [zabezpečení zabezpečení zprávy přenosu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
 Kromě zabezpečení přenosu skutečné samotnou zprávu protokolu SOAP se dají zabezpečit zabezpečení zpráv. Další informace najdete v tématu [zabezpečení zabezpečení zprávy zpráv](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md).  
  
 `MsmqTransportSecurity` také poskytuje dvě vlastnosti `MsmqEncryptionAlgorithm` a `MsmqHashAlgorithm`. Jedná se o výčty různé algoritmy zvolit pro algoritmu hash podpisů a šifrování fronty fronty přenosu zpráv.  
  
#### <a name="other-properties"></a>Ostatní vlastnosti  
 Kromě předchozích vlastnosti další vlastnosti specifické pro službu MSMQ v zahrnout vazby:  
  
-   `UseSourceJournal`: Je zapnutý vlastnost označující, že zdroj deníku. Zdroj deníku je funkce služby MSMQ, která uchovává informace o zprávy, které byly úspěšně odeslány z fronty přenosu.  
  
-   `UseMsmqTracing`: Vlastnost označující, jestli je zapnutá trasování služby MSMQ. MSMQ trasování odešle zprávy hlášení do fronty hlášení pokaždé, když opustí zpráva nebo zpráva dorazí na počítači hostování správce front služby MSMQ.  
  
-   `QueueTransferProtocol`: Výčet protokolu používaných pro přenosy mezi zprávu fronty fronty. MSMQ implementuje protokol nativní fronty fronty přenosu a protokol založený na protokolu SOAP názvem protokol spolehlivého zasílání zpráv na protokolu SOAP (SRMP). SRMP se používá při použití přenos HTTP pro přenosy fronty fronty. SRMP zabezpečení se používá při použití protokolu HTTPS pro přenosy fronty fronty.  
  
-   `UseActiveDirectory`: Logická hodnota označující, zda služby Active Directory musí být použit pro překlad adres fronty. Ve výchozím nastavení to je vypnuto. Další informace najdete v tématu [koncové body služby a adresování front](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 `MsmqIntegrationBinding` Se používá, pokud chcete, aby koncový bod WCF ke komunikaci s existující služby MSMQ aplikace napsané v C, C++, COM nebo System.Messaging rozhraní API.  
  
 Vlastnosti vazby jsou stejné jako u `NetMsmqBinding`. Však platí následující rozdíly:  
  
-   Operace kontrakt `MsmqIntegrationBinding` je omezen na pořízení jeden parametr typu <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> kde parametr typu je typ textu.  
  
-   Velká část vlastnosti služby MSMQ nativní zprávy jsou přístupné <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> pro použití.  
  
-   Pomoci při serializaci a deserializaci textu zprávy, jsou uvedeny serializátorů například XML a ActiveX.  
  
### <a name="sample-code"></a>Ukázkový kód  
 Pokyny krok za krokem na tom, jak psát WCF služby, které používají služby MSMQ naleznete v následujících tématech:  
  
-   [Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
-   [Postupy: Výměna zpráv zařazených do fronty s koncovými body WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 Dokončený kód ukázka ilustrující použití služby MSMQ ve službě WCF najdete v následujících tématech:  
  
-   [Zpracované vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
-   [Nestálá komunikace ve frontě](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
-   [Fronty nedoručených zpráv](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
-   [Relace a fronty](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
-   [Obousměrná komunikace](../../../../docs/framework/wcf/samples/two-way-communication.md)  
  
-   [Transakční dávkování](../../../../docs/framework/wcf/samples/transacted-batching.md)  
  
-   [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
-   [Zabezpečení zprávy pomocí služby Řízení front zpráv](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>Viz také  
 [Koncové body služby a adresování front](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)  
 [Webhosting frontové aplikace](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
