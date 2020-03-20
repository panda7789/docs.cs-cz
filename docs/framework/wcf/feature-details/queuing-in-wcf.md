---
title: Fronty ve WCF
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: e6608a3d556b546660be904eb8c853243e833d2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184566"
---
# <a name="queuing-in-wcf"></a>Fronty ve WCF
Tato část popisuje použití komunikace ve frontě v systému Windows Communication Foundation (WCF).  
  
## <a name="queues-as-a-wcf-transport-binding"></a>Fronty jako vazby přenosu WCF  
 V WCF smlouvy určují, co se vyměňuje. Smlouvy jsou obchodní nebo aplikace specifické výměny zpráv. Mechanismus používaný k výměně zpráv (nebo "jak") je určen ve vazbách. Vazby v WCF zapouzdřit podrobnosti výměny zpráv. Zveřejňují konfigurační knoflíky pro uživatele k ovládání různých aspektů přenosu nebo protokolu, který představují vazby. Řazení do fronty v wcf je zacházeno jako všechny ostatní transportní vazby, což je velká výhoda pro mnoho aplikací řazení do fronty. V současné době mnoho aplikací ve frontách jsou zapsány odlišně od jiných vzdálených procedur volání (RPC) styl distribuovaných aplikací, takže je těžší sledovat a udržovat. S WCF styl psaní distribuované aplikace je téměř stejný, což usnadňuje sledování a údržbu. Navíc tím, že faktoring z mechanismu směny odděleně od obchodní logiky, je snazší konfigurovat přenos nebo provádět změny, aniž by to ovlivnilo kód specifický pro aplikaci. Následující obrázek znázorňuje strukturu služby WCF a klienta pomocí služby MSMQ jako přenos.  
  
 ![Diagram aplikace ve frontě](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Obrázek distribuované fronty")  
  
 Jak můžete vidět z předchozího obrázku, klient a služba musí definovat pouze sémantiku aplikace, to znamená smlouvu a implementaci. Služba konfiguruje vazbu ve frontě s upřednostňovaným nastavením. Klient používá [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování WCF klienta ke službě a ke generování konfiguračního souboru, který popisuje vazby použít k odesílání zpráv do služby. Proto chcete-li odeslat zprávu ve frontě, klient instancije wcf klienta a vyvolá operaci na něm. To způsobí, že zpráva má být odeslána do fronty přenosu a převedeny do cílové fronty. Všechny složitosti komunikace ve frontě jsou skryty z aplikace, která odesílá a přijímá zprávy.  
  
 Upozornění týkající se vazby ve frontě v WCF zahrnují:  
  
- Všechny operace služby musí být jednosměrné, protože výchozí vazby ve frontě v WCF nepodporuje duplexní komunikaci pomocí front. Ukázka obousměrné komunikace[(Obousměrná komunikace](../../../../docs/framework/wcf/samples/two-way-communication.md)) ukazuje, jak používat dvě jednosměrné smlouvy k implementaci duplexní komunikace pomocí front.  
  
- Chcete-li generovat wcf klienta pomocí výměny metadat vyžaduje další koncový bod HTTP ve službě tak, aby jej lze dotazovat přímo generovat wcf klienta a získat informace o vazbě vhodně konfigurovat komunikaci ve frontě.  
  
- Na základě ve frontě vazby je vyžadována další konfigurace mimo WCF. Například <xref:System.ServiceModel.NetMsmqBinding> třída, která je dodávána s WCF vyžaduje konfiguraci vazby, jakož i minimálně konfigurovat službu Řízení front zpráv (MSMQ).  
  
 Následující části popisují konkrétní vazby ve frontě dodávané s WCF, které jsou založeny na službě MSMQ.  
  
### <a name="msmq"></a>MSMQ  
 Přenos ve frontě v wcf používá službu MSMQ pro komunikaci ve frontě.  
  
 Služba MSMQ je dodávána jako volitelná součást systému Windows a spuštěna jako služba NT. Zachycuje zprávy pro přenos v přenosové frontě a pro doručení v cílové frontě. Správci front služby MSMQ implementují spolehlivý protokol přenosu zpráv, aby nedošlo ke ztrátě zpráv při přenosu. Protokol může být nativní nebo na základě SOAP, například SOAP Reliable Message Protocol (SRMP).  
  
 V msmq fronty mohou být transakční nebo netransakční. Transakční fronta umožňuje zprávy, které mají být zachyceny a doručeny v transakci a pak trvale uloženy ve frontě. Zprávy odeslané do transakční fronty jsou přenášeny přesně jednou v pořadí. Netransakční frontu můžete použít k odesílání nestálých a trvalých zpráv. Zpráva odeslaná do netransakční fronty neobsahuje žádné spolehlivé záruky převodu. zprávy tedy mohou být ztraceny.  
  
 Fronty služby MSMQ lze také zabezpečit pomocí identity systému Windows registrované v adresářové službě Active Directory. Při instalaci služby MSMQ můžete nainstalovat integraci služby Active Directory, která vyžaduje, aby byl počítač součástí domény systému Windows.  
  
 Další informace o službě MSMQ naleznete [v tématu Instalace služby Řízení front zpráv (MSMQ).](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
  
### <a name="netmsmqbinding"></a>Netmsmqbinding  
 [ \<NetMsmqBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) je ve frontě vazba WCF poskytuje pro dva koncové body WCF pro komunikaci pomocí služby MSMQ. Vazba proto zpřístupňuje vlastnosti, které jsou specifické pro službu MSMQ. Ne všechny funkce a vlastnosti služby MSMQ jsou však vystaveny v rozhraní `NetMsmqBinding`. Kompaktní `NetMsmqBinding` je navržen s optimální sadou funkcí, které by většina zákazníků měla najít dostatečné.  
  
 Manifesty `NetMsmqBinding` základní fronty pojmy diskutovány tak daleko ve formě vlastností na vazby. Tyto vlastnosti zase komunikovat službu MSMQ, jak přenášet a doručovat zprávy. Diskuse o kategoriích vlastností je v následujících částech. Další informace naleznete v koncepčních tématech, která popisují konkrétní vlastnosti úplněji.  
  
#### <a name="exactlyonce-and-durable-properties"></a>ExactlyOnce a trvalé vlastnosti  
 `ExactlyOnce` Vlastnosti `Durable` a ovlivňují způsob přenosu zpráv mezi frontami:  
  
- `ExactlyOnce`: Pokud `true` je nastavena na (výchozí), kanál ve frontě zajistí, že zpráva, pokud je doručena, není duplikována. Také zajišťuje, že zpráva není ztracena. Pokud zprávu nelze doručit nebo vyprší platnost zprávy Time-To Live před doručením zprávy, je zpráva, která selhala, spolu s důvodem selhání doručení zaznamenána do fronty nedoručených zpráv. Pokud je `false`nastavena na , kanál ve frontě se snaží zprávu přenést. V takovém případě můžete volitelně zvolit frontu nedoručených zpráv.  
  
- `Durable:`Pokud je `true` nastavena na (výchozí), kanál zařazený do fronty zajišťuje, že služba MSMQ trvale ukládá zprávu na disk. Pokud by tedy služba MSMQ byla zastavit a restartovat, zprávy na disku je převedena do cílové fronty nebo doručena do služby. Pokud je `false`nastavena na , zprávy jsou uloženy v nestálém úložišti a jsou ztraceny při zastavení a restartování služby MSMQ.  
  
 Pro `ExactlyOnce` spolehlivý přenos vyžaduje služba MSMQ, aby byla fronta transakční. Služba MSMQ také vyžaduje transakci ke čtení z transakční fronty. V důsledku toho při `NetMsmqBinding`použití , nezapomeňte, že transakce je `ExactlyOnce` nutné `true`odesílat nebo přijímat zprávy, pokud je nastavena na . Podobně služba MSMQ vyžaduje, aby fronta byla netransakční pro zajištění `ExactlyOnce` nejlepšíintenzity, například kdy je `false` a pro nestálé zasílání zpráv. Proto při `ExactlyOnce` nastavení `false` nebo `false`trvanlivé na , nelze odesílat nebo přijímat pomocí transakce.  
  
> [!NOTE]
> Ujistěte se, že je vytvořena správná fronta (transakční nebo netransakční) na základě nastavení ve vazbách. Pokud `ExactlyOnce` `true`je , použijte transakční fronty; v opačném případě použijte netransakční frontu.  
  
#### <a name="dead-letter-queue-properties"></a>Vlastnosti fronty nedoručených zpráv  
 Fronta nedoručených zpráv se používá k ukládání zpráv, které se nezdaří doručení. Uživatel může napsat kompenzační logiku, která čte zprávy z fronty nedoručených zpráv.  
  
 Mnoho systémů řazení do fronty zajišťuje frontu nedoručených zpráv v celém systému. Služba MSMQ poskytuje celosystémovou netransakční frontu nedoručených zpráv pro zprávy, které nedoručení neposkytují netransakční mši, a celosystémovou transakční frontu nedoručených zpráv pro zprávy, které se nezdaří doručení transakčním frontám.  
  
 Pokud službu MSMQ sdílí více klientů odesílajících zprávy do různých cílových front, všechny zprávy odeslané klienty přejdou do stejné fronty nedoručených zpráv. To není vždy lepší. Pro lepší izolaci WCF a MSMQ v systému Windows Vista poskytují vlastní fronty nedoručených zpráv (nebo fronty nedoručených zpráv specifické pro aplikaci), které může uživatel zadat pro ukládání zpráv, které se nezdaří doručení. Proto různí klienti nesdílejí stejnou frontu nedoručených zpráv.  
  
 Vazba má dvě vlastnosti zájmu:  
  
- `DeadLetterQueue`: Tato vlastnost je výčet, který označuje, zda je požadována fronta nedoručených zpráv. Výčet také obsahuje druh fronty nedoručených zpráv, pokud je požadována. Hodnoty jsou `None` `System`, `Custom`a . Další informace o interpretaci těchto vlastností naleznete [v tématu Použití front nedoručených zpráv ke zpracování chyb přenosu zpráv](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
- `CustomDeadLetterQueue`: Tato vlastnost je adresa URI identifikátoru jednotného prostředku (URI) fronty nedoručených zpráv specifických pro aplikaci. To je `DeadLetterQueue`nutné, pokud .`Custom` je zvolena.  
  
#### <a name="poison-message-handling-properties"></a>Vlastnosti zpracování poškozená zpráva  
 Když služba čte zprávy z cílové fronty v rámci transakce, služba může selhat ke zpracování zprávy z různých důvodů. Zpráva je pak vrátit zpět do fronty číst znovu. Chcete-li řešit zprávy, které opakovaně selhávají, lze ve vazbě nakonfigurovat sadu vlastností zpracování poškozenou zprávou. Existují čtyři `ReceiveRetryCount`vlastnosti: , `MaxRetryCycles`, `RetryCycleDelay`a `ReceiveErrorHandling`. Další informace o těchto vlastnostech naleznete v [tématu Poison Message Handling](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
#### <a name="security-properties"></a>Vlastnosti zabezpečení  
 Služba MSMQ zveřejňuje vlastní model zabezpečení, například seznamy řízení přístupu (ACL) ve frontě nebo odesílání ověřených zpráv. Zpřístupňuje `NetMsmqBinding` tyto vlastnosti zabezpečení jako součást nastavení zabezpečení přenosu. Ve vazbě jsou dvě vlastnosti `MsmqAuthenticationMode` `MsmqProtectionLevel`pro zabezpečení přenosu: a . Nastavení v těchto vlastnostech závisí na konfiguraci služby MSMQ. Další informace naleznete [v tématu Zabezpečení zpráv pomocí zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
 Kromě zabezpečení přenosu může být skutečná zpráva SOAP sama zabezpečena pomocí zabezpečení zpráv. Další informace naleznete [v tématu Zabezpečení zpráv pomocí zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md).  
  
 `MsmqTransportSecurity`také zpřístupňuje `MsmqEncryptionAlgorithm` dvě `MsmqHashAlgorithm`vlastnosti a . Jedná se o výčty různých algoritmů, které chcete zvolit pro šifrování zpráv a hašování podpisů ve frontě.  
  
#### <a name="other-properties"></a>Další vlastnosti  
 Kromě předchozích vlastností zahrnují další vlastnosti specifické pro službu MSMQ, které jsou ve vazbě vystaveny:  
  
- `UseSourceJournal`: Vlastnost označující, že je zapnuto ukládání zdroje do deníku. Ukládání zdrojů do deníku je funkce msmq, která sleduje zprávy, které byly úspěšně přeneseny z fronty přenosu.  
  
- `UseMsmqTracing`: Vlastnost označující, že je zapnuto trasování msmq. Trasování služby MSMQ odesílá zprávy sestav do fronty sestav pokaždé, když zpráva opustí nebo dorazí do počítače hostujícího správce front služby MSMQ.  
  
- `QueueTransferProtocol`: Výčet protokolu, který se má použít pro přenosy zpráv frontami do fronty. Služba MSMQ implementuje nativní protokol přenosu fronty do fronty a protokol založený na protokolu SOAP s názvem SOAP Reliable Messaging Protocol (SRMP). SRMP se používá při použití přenosu HTTP pro přenosy front-front. SRMP secure se používá při použití protokolu HTTPS pro přenosy do fronty.  
  
- `UseActiveDirectory`: Logická hodnota označující, zda je nutné použít službu Active Directory pro rozlišení adresy fronty. Ve výchozím nastavení je to to vypnout. Další informace naleznete v [tématu Koncové body služby a Adresování front](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>Msmqintegrationbinding  
 Používá `MsmqIntegrationBinding` se, když chcete, aby koncový bod WCF komunikoval s existující aplikací msmq napsanou v jazycích C, C++, COM nebo System.Messaging.  
  
 Vlastnosti vazby jsou `NetMsmqBinding`stejné jako pro . Platí však následující rozdíly:  
  
- Provozní smlouva `MsmqIntegrationBinding` pro je omezena na převzetí <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> jednoho parametru typu, kde parametr typu je typ typu typ.  
  
- Většina vlastností nativní zprávy služby <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> MSMQ je vystavena pro použití.  
  
- Chcete-li pomoci s serializací a rekonstrukcí textu zprávy, jsou k dispozici serializátory jako XML a ActiveX.  
  
### <a name="sample-code"></a>Příklad kódu  
 Podrobné pokyny k zápisu služeb WCF, které používají službu MSMQ, naleznete v následujících tématech:  
  
- [Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
- [Postupy: Výměna zpráv zařazených do fronty s koncovými body WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 Ukázka dokončeného kódu ilustrující použití technologie MSMQ v wcf naleznete v následujících tématech:  
  
- [Zpracované vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
- [Nestálá komunikace ve frontě](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
- [Fronty nedoručených zpráv](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
- [Relace a fronty](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
- [Obousměrná komunikace](../../../../docs/framework/wcf/samples/two-way-communication.md)
  
- [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
- [Zabezpečení zprávy pomocí služby Řízení front zpráv](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>Viz také

- [Koncové body služby a adresování front](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
- [Webhosting frontové aplikace](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
