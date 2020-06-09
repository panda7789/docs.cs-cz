---
title: Fronty – přehled
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], MSMQ integration
ms.assetid: b8757992-ffce-40ad-9e9b-3243f6d0fce1
ms.openlocfilehash: 3e75b6d5926b65a93204241eb7c71ca23a5694af
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596718"
---
# <a name="queues-overview"></a>Přehled front

V této části se seznámíte s obecnými a základními koncepty za komunikaci ve frontě. Následující části obsahují podrobné informace o tom, jak tady popsané koncepty služby Řízení front jsou v Windows Communication Foundation (WCF) uvedené v manifestu.  
  
## <a name="basic-queuing-concepts"></a>Základní koncepty řízení front  
 Při navrhování distribuované aplikace je důležité zvolit správný přenos pro komunikaci mezi službami a klienty. Typ přenosu, který se má použít, má vliv na několik faktorů. Jeden důležitý faktor – izolace mezi službou, klientem a přenosem – Určuje použití přenosu ve frontě nebo přímé přenosu, jako je například TCP nebo HTTP. Vzhledem k povaze přímých přenosů, jako jsou TCP a HTTP, se komunikace zcela zastaví, pokud služba nebo klient přestane fungovat nebo pokud síť selže. Aby aplikace fungovala, musí být služba, klient a síť spuštěná současně. Přenosy zařazené do fronty poskytují izolaci, což znamená, že pokud dojde k selhání služby nebo klienta nebo pokud komunikační propojení mezi nimi selže, může klient a služba dál fungovat.  
  
 Fronty poskytují spolehlivou komunikaci i s chybami v komunikujících stranách nebo v síti. Fronty zachycují a dodávají zprávy vyměňované mezi komunikujícími stranami. Fronty jsou obvykle zálohované nějakým druhem úložiště, která můžou být nestálá nebo trvalá. Fronty ukládají zprávy od klienta jménem služby a později tyto zprávy předá službě. Nepřímých front zajišťuje, aby kterákoli strana zajišťovala vzájemnou izolaci selhání, takže je upřednostňovaným komunikačním mechanismem pro systémy s vysokou dostupností a odpojené služby. Nepřímý odkaz je dodáván s náklady na vysokou latenci. *Latence* je časová prodleva mezi časem, kdy klient odesílá zprávu a čas, kdy ji služba přijme. To znamená, že jakmile se pošle zpráva, nevíte, kdy se tato zpráva může zpracovat. Většina aplikací zařazených do fronty se vypořádat s vysokou latencí. Následující ilustrace znázorňuje koncepční model komunikace ve frontě.  
  
 ![Model komunikace ve frontě](media/qconceptual-figure1c.gif "QConceptual-Figure1c")  
  
 Konceptuální model komunikace ve frontě  
  
 Ve skutečnosti je fronta distribuovaným konceptem. V takovém případě mohou být obě strany buď místní, nebo vzdálené. Obvykle je fronta pro službu místní. V této konfiguraci klient nemůže být závislý na připojení ke vzdálené frontě, aby byl neustále dostupný. Podobně musí být fronta dostupná nezávisle na dostupnosti služby čtené z fronty. Správce fronty spravuje kolekci front. Zodpovídá za příjem zpráv odeslaných do front z jiných správců fronty. Zodpovídá taky za správu připojení ke vzdáleným frontám a přenos zpráv do těchto vzdálených front. Správce fronty se obvykle spouští jako externí služba, aby se zajistila dostupnost front i přes selhání aplikací klienta nebo služby.  
  
 Když klient odešle zprávu do fronty, adresuje zprávu do cílové fronty, což je fronta spravovaná správcem fronty služby. Správce fronty klienta odesílá zprávu do fronty pro přenos (nebo odchozí). Fronta přenosu je frontou ve Správci front klienta, který ukládá zprávy pro přenos do cílové fronty. Správce fronty pak najde cestu ke Správci fronty, který vlastní cílovou frontu a přenáší do ní zprávu. Aby se zajistila spolehlivá komunikace, správci fronty implementují protokol spolehlivého přenosu, aby se zabránilo ztrátě dat. Cílový správce fronty přijímá zprávy adresované cílovým frontám, které vlastní, a ukládá zprávy. Služba dává žádosti o čtení z cílové fronty, kdy ji správce fronty pak doručí do cílové aplikace. Následující ilustrace znázorňuje komunikaci mezi čtyřmi stranami.  
  
 ![Diagram aplikace ve frontě](media/distributed-queue-figure.jpg "Distribuované – fronta – obrázek")  
  
 Komunikace ve frontě v typickém scénáři nasazení  
  
 Správce fronty proto poskytne požadovanou izolaci, aby odesílatel a přijímač mohli nezávisle selhat bez vlivu na skutečnou komunikaci. Výhodou dalšího dereference, kterou fronty poskytují, umožňuje také více instancí aplikace číst ze stejné fronty, aby výrobní prostředí mezi uzly dosáhlo vyšší propustnosti. Proto není běžné zobrazovat fronty používané k dosažení vyšších požadavků na škálování a propustnost.  
  
## <a name="queues-and-transactions"></a>Fronty a transakce  
 Transakce umožňují seskupit sadu operací dohromady, takže pokud selže jedna operace, všechny operace selžou. Příkladem použití transakcí je, že uživatel používá ATM k přenosu $1 000 z účtu úspory na svůj účet pro kontrolu. To zahrnuje následující operace:  
  
- Z účtu úspory se odeberou $1 000.  
  
- Do kontrolního účtu se uloží $1 000.  
  
 Pokud je první operace úspěšná a $1 000 z účtu úspory, ale druhá operace selže, bude $1 000 ztraceno, protože již bylo odebráno z účtu úspory. Chcete-li zachovat účty v platném stavu, v případě selhání jedné operace musí dojít k selhání obou operací.  
  
 V transakčních přenosech zpráv je možné zprávy odesílat do fronty a přijímat z fronty v rámci transakce. Proto pokud je zpráva odeslána v transakci a transakce je vrácena zpět, výsledek je, jako by zpráva nebyla nikdy odeslána do fronty. Podobně pokud je v transakci přijata zpráva a transakce je vrácena zpět, výsledek je, jako kdyby nebyla zpráva nikdy přijata. Zpráva zůstane ve frontě pro čtení.  
  
 Kvůli vysoké latenci vám při odeslání zprávy nezáleží na tom, jak dlouho trvá přístup k cílové frontě, ani nevíte, jak dlouho trvá, než služba zprávu zpracuje. Z tohoto důvodu nechcete pro odeslání zprávy použít jedinou transakci, přijmout zprávu a potom zprávu zpracovat. Tím se vytvoří transakce, která není potvrzena po neurčitou dobu. Když klient a služba komunikují prostřednictvím fronty pomocí transakce, jsou zapojeny dvě transakce: jeden na straně klienta a druhý ve službě. Následující ilustrace znázorňuje hranice transakce v typické komunikaci ve frontě.  
  
 ![Zařazení do fronty s transakcemi](media/qwithtransactions-figure3.gif "QWithTransactions-Figure3")  
  
 Komunikace ve frontě znázorňující samostatné transakce pro zachytávání a doručování  
  
 Transakce klienta zpracovává a odesílá zprávu. Když je transakce potvrzena, zpráva je ve frontě přenosu. Transakce ve službě načte zprávu z cílové fronty, zpracuje zprávu a pak transakci potvrdí. Pokud během zpracování dojde k chybě, zpráva se vrátí zpátky a umístí se do cílové fronty.  
  
## <a name="asynchronous-communication-using-queues"></a>Asynchronní komunikace pomocí front  
 Fronty poskytují asynchronní způsob komunikace. Aplikace odesílající zprávy pomocí front nečekají na příjem a zpracování zprávy příjemcem z důvodu vysoké latence zavedené správcem fronty. Zprávy mohou zůstat ve frontě delší dobu, než je aplikace určena. Aby k tomu nedocházelo, aplikace může pro zprávu zadat hodnotu TTL (Time to Live). Tato hodnota určuje, jak dlouho by zpráva měla zůstat ve frontě přenosu. Pokud je tato hodnota času překročena a zpráva ještě nebyla odeslána do cílové fronty, zpráva může být přenesena do fronty nedoručených zpráv.  
  
 Když odesílatel odešle zprávu, vrátí návrat z operace odeslání, že zpráva byla odeslána pouze do fronty přenosu v odesilateli. V takovém případě, pokud dojde k selhání při získávání zprávy do cílové fronty, nemůže odesílající aplikace o tom okamžitě získat informace. V takovém případě se zpráva o selhání přenese do fronty nedoručených zpráv.  
  
 Všechny chyby, jako je například zpráva o neúspěšném dosažení cílové fronty nebo vypršení doby do provozu, musí být zpracovány samostatně. Pro aplikace zařazené do fronty není neobvyklé, takže zapisují dvě sady logiky:  
  
- Normální logika klienta a služby pro odesílání a příjem zpráv.  
  
- Logika kompenzace pro zpracování zpráv z neúspěšného přenosu nebo doručování.  
  
 Následující části popisují tyto koncepce.  
  
## <a name="dead-letter-queue-programming"></a>Programování fronty nedoručených zpráv  
 Fronty nedoručených zpráv obsahují zprávy, které selhaly při dosažení cílové fronty z různých důvodů. Důvody mohou být v rozsahu od zpráv s vypršenou platností až po problémy s připojením zabraňující přenosu zprávy do cílové fronty.  
  
 Aplikace obvykle může číst zprávy z fronty nedoručených zpráv v rámci systému, zjistit, co se nepovedlo, a provést příslušné akce, třeba opravit chyby a znovu odeslat zprávu nebo si ji poznamenat.  
  
## <a name="poison-message-queue-programming"></a>Programování ve frontě zpráv o nepoškozeném řízení  
 Po vytvoření zprávy do cílové fronty může služba opakovaně selhat při zpracování zprávy. Například aplikace, která čte zprávu z fronty v rámci transakce a aktualizuje databázi, může databázi najít dočasně odpojenou. V tomto případě se transakce vrátí zpět, vytvoří se nová transakce a zpráva se znovu načte z fronty. Druhý pokus může být úspěšný nebo neúspěšný. V některých případech může v závislosti na příčině chyby dojít k opakovanému doručování zpráv do aplikace. V tomto případě se zpráva považuje za "jed". Tyto zprávy jsou přesunuty do fronty nepoškozeného, kterou lze číst aplikací pro zpracování poškození.  
  
## <a name="see-also"></a>Viz také

- [Fronty ve WCF](queuing-in-wcf.md)
- [Relace a fronty](../samples/sessions-and-queues.md)
- [Fronty nedoručených zpráv](../samples/dead-letter-queues.md)
- [Nestálá komunikace ve frontě](../samples/volatile-queued-communication.md)
- [Z WCF do Řízení front zpráv](../samples/wcf-to-message-queuing.md)
- [Instalace služby Řízení front zpráv (MSMQ)](../samples/installing-message-queuing-msmq.md)
- [Řízení front zpráv do WCF](../samples/message-queuing-to-wcf.md)
- [Zabezpečení zprávy pomocí služby Řízení front zpráv](../samples/message-security-over-message-queuing.md)
