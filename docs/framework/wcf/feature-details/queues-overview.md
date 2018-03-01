---
title: "Fronty – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queues [WCF], MSMQ integration
ms.assetid: b8757992-ffce-40ad-9e9b-3243f6d0fce1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eb5d0f51fbbb6c8bad9bfbbfd9977368fdbd0666
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="queues-overview"></a>Fronty – přehled
Tato část představuje obecné a základní koncepty za komunikace ve frontě. Následující části přejděte do podrobnosti o tom, jak jsou služby Řízení front konceptů popsaných v tomto poli označované v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="basic-queuing-concepts"></a>Základní koncepty služby Řízení front  
 Při návrhu distribuované aplikace se při výběru že správné přenosu pro komunikaci mezi služeb a klientů je důležité. Několika různými faktory ovlivňují druh přenosu použita. Důležitým faktorem – izolace mezi službou, klient a přenos – Určuje použití zařazených do fronty přenosu nebo přímý přenos, jako je například protokol TCP nebo HTTP. Vzhledem k povaze přímé přenosy, jako je například TCP a HTTP komunikace zcela zastaví pokud služba nebo klienta přestane fungovat nebo selhání sítě. Tato služba, klienta a sítě musí používat stejnou dobu pro aplikace pro práci. Ve frontě přenosů poskytují izolaci, což znamená, že pokud se služba nebo klienta selže nebo pokud komunikační propojení mezi nimi selže, klient a služba můžete nadále fungovat.  
  
 Fronty poskytují spolehlivé komunikace i s chybami v komunikující strany nebo sítě. Fronty zachycení a doručování zpráv, na které se vyměňují mezi komunikujícími stranami. Fronty jsou obvykle zálohován nějaký druh úložiště, který může být volatile nebo trvanlivý. Fronty ukládat zprávy z klienta jménem služby a později předávat tyto zprávy do služby. Indirection, které poskytují front zajištěn izolace selhání druhé strany, a tím upřednostňované komunikační mechanizmus pro systémů s vysokou dostupností a odpojí služby. Indirection se dodává s náklady na vysokou latencí. *Latence* je prodlevu mezi časem klient odešle zprávu a čas přijetí služby. To znamená, že jakmile je odeslána zpráva, si nejste jisti, kdy může tuto zprávu zpracovat. Většina zařazených do fronty aplikace zvládnout s vysokou latencí. Následující obrázek znázorňuje Koncepční model komunikace ve frontě.  
  
 ![Modelu komunikace ve frontě](../../../../docs/framework/wcf/feature-details/media/qconceptual-figure1c.gif "QConceptual Figure1c")  
  
 Konceptuální model komunikace ve frontě  
  
 Ve skutečnosti je fronty distribuované koncept. Může se jednat jako takový buď strany místního nebo vzdáleného pro obě strany. Fronta je obvykle místní ke službě. V této konfiguraci klienta nemůže záviset na připojení k vzdálené fronty být neustále k dispozici. Podobně fronty musí být k dispozici bez ohledu na dostupnost služby čtení z fronty. Správce front spravuje kolekce front. Je zodpovědná za příjem zpráv odeslaných do jeho front z jiným správcům fronty. Je také zodpovědná za správu připojení k vzdálené fronty a přenosu zpráv do těchto vzdálených front. K zajištění dostupnosti front i v případě selhání klienta služby nebo aplikace, je obvykle správce front spustit jako externí služby.  
  
 Když klient odešle zprávu do fronty, řeší zprávy do cílové fronty, který se spravuje správce front služby fronty. Správce front v klientovi odešle zprávu do přenosu (nebo odchozí) fronty. Fronty přenosu je do fronty v fronty správce klienta, která ukládá zprávy pro přenos do cílové fronty. Správce front potom vyhledá cestu manažera fronty, který vlastní cílové fronty a přenáší zprávy do něj. Aby se zajistilo spolehlivé komunikace, správci fronty implementovat protokol spolehlivého přenosu předchází se tak ztrátě dat. Správce front cílový přijímá zprávy adresované do cílové fronty je vlastní a ukládá zprávy. Služba umožňuje žádostí o čtení z cílové fronty, které během správce front pak doručení zprávy do cílové aplikaci. Následující obrázek znázorňuje komunikaci mezi čtyři strany.  
  
 ![Diagram aplikace ve frontě](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "distribuované obrázek fronty")  
  
 Komunikace ve frontě v případě typické nasazení  
  
 Proto správce front zajišťuje požadovanou izolaci tak, aby odesílatele a příjemce může selhat nezávisle bez ovlivnění skutečné komunikace. Výhodou navíc indirection, které poskytují front taky umožňuje číst ze stejné fronty více instancí aplikace tak, aby zaměření pracovních mezi uzly lze dosáhnout vyšší propustnost. Proto neobvyklé zobrazíte fronty používají k dosažení vyšší škálování a požadavky na propustnost.  
  
## <a name="queues-and-transactions"></a>Fronty a transakce  
 Transakce umožňují seskupit sadu operací, takže pokud jeden operace selže, všechny operace nezdaří. Příklad použití transakcí je, když uživatel používá k přenosu 1 000 USD ze svého účtu úspory k jeho účtu kontroluje ATM. To zahrnuje následující operace:  
  
-   Stažení 1 000 USD z účtu úspory.  
  
-   1 000 USD uloží do běžného účtu.  
  
 Pokud je první operace úspěšná a 1 000 USD stažení z účtu úspory, ale druhá operace selže, je 1 000 USD ztraceny, protože již byly staženy z účtu úspory. Zachovat účty v platném stavu, pokud jedna operace selže, musí oba operace nezdaří.  
  
 Zprávy můžete v transakční zasílání zpráv odeslaných do fronty a přijaté z fronty v rámci transakce. Proto pokud je zprávu odeslanou v transakci a transakce je vrácena zpět, pak výsledek je jako, pokud zpráva měli nikdy byla odeslána do fronty. Podobně pokud příjmu zprávy v transakci a transakce je vrácena zpět, pak výsledek je jako, pokud zpráva měli nikdy byla přijata. Zpráva zůstává ve frontě číst.  
  
 Z důvodu vysokou latencí při odeslání zprávy, že máte žádný způsob, jak zjistit, jak dlouho trvá kontaktovat příslušné cílové fronty ani udělat víte, jak dlouho trvá pro službu ke zpracování zprávy. Z toho důvodu nechcete použít jen jednu transakci odeslat zprávu, zobrazí se zpráva, a pak zpracovat zprávu. Tím se vytvoří transakci, která není potvrzena neurčitou dobu. Pokud klient a služba komunikují prostřednictvím fronty pomocí transakce, se jedná o dvě transakce: jeden na klientovi a jeden ve službě. Následující obrázek znázorňuje hranice transakce v typické komunikace ve frontě.  
  
 ![Fronty s transakcemi](../../../../docs/framework/wcf/feature-details/media/qwithtransactions-figure3.gif "QWithTransactions Figure3")  
  
 Komunikace ve frontě zobrazující samostatné transakce pro zachycení a doručení  
  
 Klientská transakce zpracovává a odešle zprávu. Po potvrzení transakce zpráva je v přenosové frontě. Ve službě transakce přečte zprávu z cílové fronty, zprávu zpracuje a potom provede transakce. Pokud dojde k chybě během zpracování, je vrácena zpět zpráva a umístit do cílové fronty.  
  
## <a name="asynchronous-communication-using-queues"></a>Asynchronní komunikaci pomocí front  
 Fronty asynchronní prostředkem komunikace. Aplikace, které odesílání zpráv pomocí front nemůže čekat na zprávu, která se přijímají a zpracovávají příjemce z důvodu vysoké latenci zaváděné správce front. Zprávy může zůstat ve frontě daleko delší dobu než určená aplikace. Abyste tomu předešli, aplikace, můžete zadat hodnotu Time To Live na zprávu. Tato hodnota určuje, jak dlouho zpráva by měla zůstat v přenosové frontě. Pokud dojde k překročení tuto hodnotu času, a zpráva nebyla odeslána stále do cílové fronty, zprávy lze přesunout do fronty nedoručených zpráv.  
  
 Pokud odesílatel odešle zprávu, návratový z operaci odeslání znamená, že zprávy pouze dostal fronty přenosu na odesílatele. Jako takový Pokud dojde k selhání při získávání zprávy do cílové fronty, odesílající aplikací nemůže vědět o ji okamžitě. K poznamenejte si tyto chyby, se přenáší neúspěšné zprávy do fronty nedoručených zpráv.  
  
 Všechny chyby, jako je například zprávu selhání dosáhne cílová fronta nebo Time To Live vypršení platnosti, je nutné zpracovat samostatně. Není, proto pro zařazených do fronty aplikace k zápisu dvě sady logiku:  
  
-   Normální klient a služba logiku odesílání a přijímání zpráv.  
  
-   Kompenzace logiku pro zpracování zprávy ze chybný přenos nebo doručení.  
  
 Následující části popisují tyto koncepty.  
  
## <a name="dead-letter-queue-programming"></a>Programování frontu nedoručených zpráv  
 Fronty nedoručených zpráv obsahují zprávy, které se nepodařilo dosáhnout cílová fronta z různých důvodů. Důvodů, proč může být v rozsahu od zprávy s vypršenou platností na problémy s připojením k zabránění přenosu zprávy do cílové fronty.  
  
 Obvykle se aplikace může číst zprávy z fronty nedoručených zpráv systémové, určete, kde došlo k chybě a proveďte příslušné akce, jako je například oprava chyby a odešlete zprávu nebo pořízení poznamenejte si ho.  
  
## <a name="poison-message-queue-programming"></a>Nezpracovatelná zpráva fronty programování  
 Po zprávu umožňuje do cílové fronty, služba může opakovaně nepodaří zprávu zpracovat. Například aplikace čtení zprávy z fronty pod transakce a aktualizace databáze může najít databázi dočasně odpojen. V takovém případě transakce je vrácena zpět, je-li vytvořit novou transakci a zpráva se znovu načíst z fronty. Druhý pokus o může úspěch nebo neúspěch. V některých případech, v závislosti na příčinu chyby zpráva opakované selhání doručení do aplikace. V takovém případě se považuje zprávu jako "poison." Takové zprávy se přesouvají do poškozených fronty, který může číst poison zpracování aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Relace a fronty](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [Fronty nedoručených zpráv](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
 [Nestálá komunikace ve frontě](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
 [Z Windows Communication Foundation do služby Řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Instalace služby Řízení front zpráv (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Ukázky vazby integrace služby Řízení front zpráv](http://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [Ze služby Řízení front zpráv do Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Zabezpečení zprávy pomocí služby Řízení front zpráv](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
