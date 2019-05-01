---
title: Fronty – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], MSMQ integration
ms.assetid: b8757992-ffce-40ad-9e9b-3243f6d0fce1
ms.openlocfilehash: e34f2033ec0f7dac784634d06712d65786503299
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991249"
---
# <a name="queues-overview"></a>Fronty – přehled
Tato část představuje obecné a základní koncepty za komunikace ve frontě. Dalších částech podrobnější informace o zařazování do fronty koncepty je zde popsáno, jak jsou označované ve Windows Communication Foundation (WCF).  
  
## <a name="basic-queuing-concepts"></a>Základní koncepty služby Řízení front  
 Když navrhujete distribuované aplikace, když zvolíte že správné přenosu pro komunikaci mezi službami a klienty je důležité. Několik faktorů vliv druh přenosu použít. Důležitým faktorem – izolace mezi službou, klienta a přenos – Určuje použití zařazených do fronty přenosu nebo přímého přenosu, například protokol TCP nebo HTTP. Vzhledem k povaze přímé přenosy, jako je například TCP nebo HTTP, komunikace úplně zastaví Pokud službu nebo klienta přestane fungovat nebo selhání sítě. Služba klienta a sítě, musí běžet ve stejnou dobu pro aplikace pro spolupráci. Ve frontě přenosů zajišťují izolaci, což znamená, že pokud selžou i služba nebo klient nebo komunikační propojení mezi nimi selže, klient a služba může dál fungovat.  
  
 Fronty poskytují spolehlivé komunikaci i při selhání v komunikujících stran nebo síti. Fronty zachycení a doručení zprávy se vyměňují mezi komunikujícími stranami. Fronty jsou obvykle zajištěná určitého druhu úložiště, který může být přechodné nebo trvalé. Fronty ukládat zprávy z klienta jménem služby a později předávání těchto zpráv ve službě. Dereference, které poskytují front zajistit izolaci selhání druhé strany, a tím upřednostňované komunikační mechanizmus pro systémů s vysokou dostupností a odpojí služby. Dereference se dodává s náklady na vysokou latenci. *Latence* je časovou prodlevu mezi časem klient odešle zprávu a čas přijetí služby. To znamená, že jakmile je odeslána zpráva, si nejste jisti při může tuto zprávu zpracovat. Většina aplikací ve frontě se vypořádat s vysokou latencí. Následující obrázek znázorňuje Koncepční model komunikaci ve frontě.  
  
 ![Vzor komunikaci ve frontě](../../../../docs/framework/wcf/feature-details/media/qconceptual-figure1c.gif "QConceptual Figure1c")  
  
 Konceptuální model komunikaci ve frontě  
  
 Fronta je ve skutečnosti koncept distribuované. V důsledku toho může být buď strany místního nebo vzdáleného pro obě strany. Obvykle je místní služba fronty. V této konfiguraci klienta nemůže záviset na připojení ke vzdálené fronty neustále dostupná. Obdobně fronty musí být k dispozici bez ohledu na dostupnost služby čtení z fronty. Správce fronty spravuje kolekci front. Zodpovídá za příjem zpráv odeslaných z jiných správci fronty frontách. Je také zodpovědní za správu připojení ke vzdálené fronty a přenos zpráv do těchto vzdálených front. K zajištění dostupnosti fronty bez ohledu na selhání klienta nebo služby aplikace, správce fronty obvykle běží jako externí služby.  
  
 Když klient odešle zprávu do fronty, zaměřuje se na zprávy do cílové fronty, což je fronty spravuje správce fronty služby. Správce fronty v klientském počítači odešle zprávu do přenosu (nebo odchozí) fronty. Fronty přenosu je do fronty ve frontě správce klienta, který ukládá zprávy pro přenos do cílové fronty. Správce fronty následně vyhledá cestu k správce fronty, který vlastní cílové fronty a převede zprávu do něj. Chcete-li zajistit spolehlivou komunikaci, implementovat správci fronty spolehlivý přenosový protokol se tak ztrátě dat. Správce fronty cílové přijímá zprávy adresované do cílové fronty vlastní a ukládá zprávy. Služba umožňuje žádostí o čtení z cílové fronty, po kterém správce fronty pak doručí do cílové aplikace. Následující obrázek znázorňuje komunikace mezi čtyři strany.  
  
 ![Ve frontě diagramu aplikace](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "distribuované obrázek fronty")  
  
 Komunikaci ve frontě ve scénáři typické nasazení  
  
 Proto správce fronty zajišťuje požadovanou izolaci tak, aby odesílatel a příjemce může nezávisle na sobě selhat aniž by to ovlivnilo skutečné komunikace. Výhodou navíc dereference, které poskytují front taky umožňuje číst ze stejné fronty i několik instancí aplikace tak, aby zaměření práci mezi uzly dosahuje vyšší propustnost. Proto není nic neobvyklého, najdete v článku fronty se využívají k dosažení škálování ve větším měřítku a požadavkům na propustnost.  
  
## <a name="queues-and-transactions"></a>Fronty a transakce  
 Transakce umožňují seskupit sadu operací, takže pokud jedna operace selže, všechny operace selžou. Příklad použití transakce je při osoba používá k přenosu 1 000 USD z jeho úspory účtu do svého účtu kontroluje ATM. To zahrnuje následující operace:  
  
- Odebrání z účtu úspory 1 000 USD.  
  
- Uložení 1 000 USD v úvahu kontrola.  
  
 Pokud první operace úspěšná a 1 000 USD stažení z účtu úspory, ale selže druhou operaci, dojde ke ztrátě 1 000 USD, protože již byla stažena z účtu úspory. Zachovat účty v platném stavu, pokud jedna operace selže, musí selhat operace.  
  
 V transakční zasílání zpráv, můžete zprávy odeslané do fronty a přijatá z fronty v rámci transakce. Proto pokud je zprávu odeslanou v transakci a transakce je vrácena zpět, pak výsledek je jako by zpráva měla nikdy byla odeslána do fronty. Podobně pokud zprávu neobdrží v rámci transakce a transakce je vrácena zpět, pak výsledek je jako by zpráva měla nikdy byla přijata. Zpráva zůstane ve frontě ke čtení.  
  
 Z důvodu vysoké latenci při odeslání zprávy, že abyste měli vědět, jak dlouho trvá kontaktovat příslušné cílové fronty ani provést víte, jak dlouho trvá, službu ke zpracování zprávy. Z tohoto důvodu nechcete odeslat zprávu, zobrazí se zpráva a následně zpracovat zprávu pomocí jedné transakce. Tím se vytvoří transakce, která není zapsaná neurčitou dobu. Pokud klient a služba komunikují prostřednictvím fronty pomocí transakcí, se podílejí dvě transakce: jeden na klienta a jeden pro službu. Následující obrázek znázorňuje hranice transakce v typické komunikaci ve frontě.  
  
 ![Frontu s transakcí](../../../../docs/framework/wcf/feature-details/media/qwithtransactions-figure3.gif "QWithTransactions Figure3")  
  
 Komunikaci ve frontě znázorňující samostatný transakce pro zachycení a doručování  
  
 Klientská transakce zpracuje a odešle zprávu. Když je transakce potvrzeny, je zprávy v přenosové frontě. Ve službě transakce přečte zprávu z cílové fronty, zpracovává zprávu a pak potvrzení transakce. Pokud dojde k chybě během zpracování, je vrácena zpět zprávu a je umístěn v cílové fronty.  
  
## <a name="asynchronous-communication-using-queues"></a>Asynchronní komunikace pomocí front  
 Fronty představují asynchronní znamená, že komunikace. Aplikace, které odesílání zpráv s použitím front nemůže čekat zprávu přijme a zpracuje příjemce z důvodu vysoké latenci správcem fronty. Zprávy mohou zůstat ve frontě mnohem delší dobu než určená aplikace. Abyste tomu předešli, může aplikace ve zprávě určit hodnotu Time-To-Live. Tato hodnota určuje, jak dlouho zpráva by měla zůstat v přenosové frontě. Pokud je překročena této hodnoty času a zpráva nebyla odeslána stále do cílové fronty, zprávy lze přenést do fronty nedoručených zpráv.  
  
 Pokud odesílatel odešle zprávu, návrat z operace odeslání znamená, že zprávy pouze dostal přenosové frontě v odesílatele. V důsledku toho pokud dojde k chybě při získávání zprávy do cílové fronty, odeslání aplikace nejde o tom okamžitě dozvědět. K poznamenejte si tyto chyby, neúspěšné zprávy se přenesou do fronty nedoručených zpráv.  
  
 Všechny chyby, jako je například zpráva nedaří kontaktovat cílové fronty nebo do Time-To-Live vypršení platnosti, musí být zpracovány samostatně. Není, proto pro aplikace zařazených do fronty pro zápis dvě sady logik:  
  
- Normální klient a služba logiku odesílání a příjem zpráv.  
  
- Kompenzační logika zpracování zprávy ze chybný přenos nebo doručení.  
  
 Následující části popisují tyto koncepty.  
  
## <a name="dead-letter-queue-programming"></a>Programování fronty nedoručených zpráv  
 Obsahují fronty nedoručených zpráv, které se nepodařilo dosáhnout cílová fronta z různých důvodů. Důvody musí být v rozsahu zprávy s vypršenou platností do problémy s připojením, které brání přenos zprávy do cílové fronty.  
  
 Obvykle aplikace může číst zprávy z fronty nedoručených zpráv systémová zjistit, co se nepovedlo a přijmout vhodná opatření, jako jsou opravy chyb a odeslání zprávy nebo pořízení poznamenejte si ho.  
  
## <a name="poison-message-queue-programming"></a>Nezpracovatelná zpráva fronty programování  
 Po zprávu umožňuje do cílové fronty, služba nemusí opakovaně zprávu zpracovat. Například aplikace čtení zprávy z fronty pod transakcí a aktualizaci databáze může najít databázi dočasně odpojeny. V takovém případě transakce je vrácena zpět, se vytvoří novou transakci a zpráva se znova načíst z fronty. Druhý pokus může úspěch nebo neúspěch. V některých případech může v závislosti na příčinu chyby zpráva nemusí opakovaně doručování do aplikace. V takovém případě se zpráva bude považovat za jako "poison." Tyto zprávy se přesouvají na poškozené fronty, který může číst aplikace poison zpracování.  
  
## <a name="see-also"></a>Viz také:

- [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Relace a fronty](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Fronty nedoručených zpráv](../../../../docs/framework/wcf/samples/dead-letter-queues.md)
- [Nestálá komunikace ve frontě](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)
- [Z Windows Communication Foundation do služby Řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [Instalace služby Řízení front zpráv (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [Ze služby Řízení front zpráv do Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [Zabezpečení zprávy pomocí služby Řízení front zpráv](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
