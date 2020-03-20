---
title: Fronty – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], MSMQ integration
ms.assetid: b8757992-ffce-40ad-9e9b-3243f6d0fce1
ms.openlocfilehash: 78d80a88153ee15f7ab152da44801c77900f874d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184603"
---
# <a name="queues-overview"></a>Přehled front

Tato část představuje obecné a základní koncepty komunikace ve frontě. Následující části naleznete podrobnosti o tom, jak se zde popsané koncepty fronty projevují v nadaci WCF (Windows Communication Foundation).  
  
## <a name="basic-queuing-concepts"></a>Základní koncepty řazení do fronty  
 Při návrhu distribuované aplikace je důležitá volba správného přenosu pro komunikaci mezi službami a klienty. Několik faktorů ovlivňuje druh dopravy k použití. Jeden důležitý faktor – izolace mezi službou, klientem a přenosem – určuje použití přenosu ve frontě nebo přímého přenosu, například TCP nebo HTTP. Vzhledem k povaze přímých přenosů, jako je tcp a HTTP, komunikace zastaví úplně, pokud služba nebo klient přestane fungovat nebo pokud dojde k selhání sítě. Služba, klient a síť musí být spuštěny současně, aby aplikace fungovala. Přenosy ve frontě poskytují izolaci, což znamená, že pokud služba nebo klient selže nebo pokud dojde k selhání komunikačních spojení mezi nimi, může klient a služba nadále fungovat.  
  
 Fronty poskytují spolehlivou komunikaci i při selhání v komunikujících stranách nebo v síti. Fronty zachycují a doručují zprávy vyměňované mezi komunikujícími stranami. Fronty jsou obvykle zálohovány nějakým druhem úložiště, které může být nestálé nebo trvanlivé. Fronty ukládají zprávy od klienta jménem služby a později předávají tyto zprávy službě. Fronty dereference poskytují zajištění izolace selhání ze strany kterékoli strany, čímž se jedná o upřednostňovaný komunikační mechanismus pro systémy s vysokou dostupností a odpojené služby. Dereference přichází s náklady na vysokou latenci. *Latence* je časová prodleva mezi časem, kdy klient odešle zprávu, a časem, kdy ji služba obdrží. To znamená, že po odeslání zprávy nevíte, kdy může být tato zpráva zpracována. Většina aplikací ve frontě se vyrovná s vysokou latencí. Následující obrázek znázorňuje koncepční model komunikace ve frontě.  
  
 ![Model komunikace ve frontě](../../../../docs/framework/wcf/feature-details/media/qconceptual-figure1c.gif "QKonceptuální obrázek1c")  
  
 Koncepční model komunikace ve frontě  
  
 Ve skutečnosti je fronta distribuovaný koncept. Jako takové mohou být místní pro jednu ze stran nebo vzdálené pro obě strany. Obvykle je fronta místní ke službě. V této konfiguraci klient nemůže záviset na připojení ke vzdálené frontě, aby byl neustále k dispozici. Podobně fronta musí být k dispozici nezávisle na dostupnosti služby čtení z fronty. Správce front spravuje kolekci front. Je zodpovědný za přijímání zpráv odeslaných do front od jiných správců front. Je také zodpovědný za správu připojení ke vzdáleným frontám a přenos zpráv do těchto vzdálených front. Chcete-li zajistit dostupnost front i přes selhání klienta nebo služby aplikace, správce front je obvykle spuštěn jako externí služba.  
  
 Když klient odešle zprávu do fronty, adresuje zprávu do cílové fronty, což je fronta spravovaná správcem front služby. Správce front v klientovi odešle zprávu do fronty přenosu (nebo odchozí). Fronta přenosu je fronta ve správci front klienta, která ukládá zprávy pro přenos do cílové fronty. Správce front pak najde cestu ke správci front, který vlastní cílovou frontu a přenese do ní zprávu. Aby byla zajištěna spolehlivá komunikace, správci front implementují spolehlivý přenosový protokol, aby zabránili ztrátě dat. Správce cílové fronty přijímá zprávy adresované cílovým frontám, které vlastní, a ukládá je. Služba provádí požadavky na čtení z cílové fronty, kdy správce front pak doručí zprávu cílové aplikaci. Následující obrázek znázorňuje komunikaci mezi čtyřmi stranami.  
  
 ![Diagram aplikace ve frontě](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Obrázek distribuované fronty")  
  
 Komunikace ve frontě v typickém scénáři nasazení  
  
 Správce front tedy poskytuje požadovanou izolaci tak, aby odesílatel a příjemce může nezávisle selhat bez ovlivnění skutečné komunikace. Výhoda extra dereference, které fronty poskytují také umožňuje více instancí aplikace číst ze stejné fronty, tak, aby zemědělské práce mezi uzly dosáhne vyšší propustnost. Proto není neobvyklé zobrazit fronty, které se používají k dosažení vyšší škálování a propustnosti požadavky.  
  
## <a name="queues-and-transactions"></a>Fronty a transakce  
 Transakce umožňují seskupit sadu operací dohromady, takže pokud jedna operace selže, všechny operace se nezdaří. Příkladem použití transakcí je, když osoba používá bankomat k převodu 1 000 USD ze svého spořicího účtu na běžný účet. To zahrnuje následující operace:  
  
- Výběr 1.000 dolarů ze spořicího účtu.  
  
- Na běžný účet jsem vložil 1000 dolarů.  
  
 Pokud první operace uspěje a 1.000 dolarů je stažen ze spořicího účtu, ale druhá operace selže, 1.000 dolarů je ztracena, protože již byla stažena ze spořicího účtu. Chcete-li zachovat účty v platném stavu, pokud jedna operace selže, musí selhat obě operace.  
  
 V transakčnízasílání zpráv zprávy mohou být odeslány do fronty a přijata z fronty v rámci transakce. Proto pokud je zpráva odeslána v transakci a transakce je vrácena zpět, pak výsledek je, jako kdyby zpráva nebyla nikdy odeslána do fronty. Podobně pokud je zpráva přijata v transakci a transakce je vrácena zpět, pak výsledek je, jako by zpráva nebyla nikdy přijata. Zpráva zůstane ve frontě ke čtení.  
  
 Z důvodu vysoké latence, při odeslání zprávy nemáte žádný způsob, jak zjistit, jak dlouho trvá dosažení cílové fronty, ani nevíte, jak dlouho trvá, než služba zpracovat zprávu. Z tohoto důvodu nechcete použít jednu transakci k odeslání zprávy, přijetí zprávy a následnému zpracování zprávy. Tím se vytvoří transakce, která není potvrzena na neurčitou dobu. Když klient a služba komunikují prostřednictvím fronty pomocí transakce, jsou zapojeny dvě transakce: jedna na straně klienta a jedna ve službě. Následující obrázek znázorňuje hranice transakcí v typické komunikaci ve frontě.  
  
 ![Fronta s transakcemi](../../../../docs/framework/wcf/feature-details/media/qwithtransactions-figure3.gif "QWithTransactions-Obrázek3")  
  
 Komunikace ve frontě zobrazující samostatné transakce pro zachycení a doručení  
  
 Transakce klienta zpracovává a odešle zprávu. Když je transakce potvrzena, zpráva je ve frontě přenosu. Ve službě transakce přečte zprávu z cílové fronty, zpracuje zprávu a potom potvrdí transakci. Pokud dojde k chybě během zpracování, zpráva je vrácena zpět a umístěna do cílové fronty.  
  
## <a name="asynchronous-communication-using-queues"></a>Asynchronní komunikace pomocí front  
 Fronty poskytují asynchronní komunikační prostředky. Aplikace, které odesílají zprávy pomocí front, nemohou čekat na přijetí a zpracování zprávy příjemcem z důvodu vysoké latence zavedené správcem front. Zprávy mohou zůstat ve frontě mnohem déle, než aplikace zamýšlela. Chcete-li tomu zabránit, aplikace může zadat hodnotu Time-To-Live ve zprávě. Tato hodnota určuje, jak dlouho by měla zpráva zůstat ve frontě přenosu. Pokud je tato hodnota času překročena a zpráva stále nebyla odeslána do cílové fronty, může být zpráva přenesena do fronty nedoručených zpráv.  
  
 Když odesílatel odešle zprávu, návrat z operace odeslání znamená, že zpráva pouze dělal to do fronty přenosu na odesílatele. V důsledku toho pokud dojde k chybě při získávání zprávy do cílové fronty, odesílající aplikace nemůže vědět o tom okamžitě. Chcete-li vzít na vědomí takové chyby, je zpráva se nezdařilo převedena do fronty nedoručených zpráv.  
  
 Každá chyba, jako je například zpráva, která nedosáhla cílové fronty nebo vypršení platnosti time-to-live, musí být zpracována samostatně. Není neobvyklé, proto pro aplikace ve frontě psát dvě sady logiky:  
  
- Normální logika klienta a služby odesílání a přijímání zpráv.  
  
- Logika kompenzace pro zpracování zpráv z neúspěšného přenosu nebo doručení.  
  
 Následující části popisují tyto pojmy.  
  
## <a name="dead-letter-queue-programming"></a>Programování fronty nedoručených zpráv  
 Fronty nedoručených zpráv obsahují zprávy, které se z různých důvodů nepodařilo dosáhnout cílové fronty. Důvody mohou být v rozsahu od zpráv s prošlou platností až po problémy s připojením, které brání přenosu zprávy do cílové fronty.  
  
 Aplikace může obvykle číst zprávy z fronty nedoručených zpráv v celém systému, určit, co se stalo, a provést příslušnou akci, například opravit chyby a znovu odeslat zprávu nebo ji vzít na vědomí.  
  
## <a name="poison-message-queue-programming"></a>Programování fronty poškozená zpráva  
 Po oznámení přejde do cílové fronty, služba může opakovaně nepodaří zpracovat zprávu. Například aplikace, která čte zprávu z fronty v rámci transakce a aktualizuje databázi, může dočasně odpojit databázi. V tomto případě je transakce vrácena zpět, je vytvořena nová transakce a zpráva je znovu přečtena z fronty. Druhý pokus může být úspěšný nebo úspěšný. V některých případech v závislosti na příčině chyby může zpráva opakovaně selhání doručení do aplikace. V tomto případě je zpráva považována za "jed". Tyto zprávy jsou přesunuty do fronty poison, které lze číst pomocí aplikace zpracování poison.  
  
## <a name="see-also"></a>Viz také

- [Fronty ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Relace a fronty](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Fronty nedoručených zpráv](../../../../docs/framework/wcf/samples/dead-letter-queues.md)
- [Nestálá komunikace ve frontě](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)
- [Z Windows Communication Foundation do služby Řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [Instalace služby Řízení front zpráv (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [Ze služby Řízení front zpráv do Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [Zabezpečení zprávy pomocí služby Řízení front zpráv](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
