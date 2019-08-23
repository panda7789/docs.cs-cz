---
title: Zpracování škodlivých zpráv
ms.date: 03/30/2017
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
ms.openlocfilehash: 4813629f5ceec1c1b50dfcebe901f4bc25392ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909842"
---
# <a name="poison-message-handling"></a>Zpracování škodlivých zpráv
Nezpracovatelná *zpráva* je zpráva, že překročila maximální počet pokusů o doručení do aplikace. K této situaci může dojít, když aplikace založená na frontě nemůže zpracovat zprávu z důvodu chyb. Pro splnění požadavků na spolehlivost přijímá aplikace zařazené do fronty zprávy v rámci transakce. Přerušení transakce, ve které byla přijata zpráva zařazená do fronty, opustí zprávu ve frontě, aby se zpráva opakovala v rámci nové transakce. Pokud se problém, který způsobil přerušování transakce, neopraví, přijímající aplikace může zablokovat ve smyčce příjem a přerušit stejnou zprávu, dokud nedosáhnete maximálního počtu pokusů o doručení a výsledků nepoškozených zpráv.  
  
 Zpráva může ze spousty důvodů způsobit nezpracovatelovou zprávu. Nejběžnějšími důvody jsou konkrétní aplikace. Například pokud aplikace přečte zprávu z fronty a provede nějaké zpracování databáze, aplikace může selhat, aby získala zámek pro databázi a způsobila přerušení transakce. Vzhledem k tomu, že transakce databáze byla přerušena, zpráva zůstane ve frontě, což způsobí, že aplikace znovu přečte zprávu podruhé a provede další pokus o získání zámku databáze. Zprávy mohou být také poškozené, pokud obsahují neplatné informace. Například objednávka nákupu může obsahovat neplatné číslo zákazníka. V těchto případech může aplikace dobrovolně transakci zrušit a vynutit, aby se zpráva stala nezpracovatelovou zprávou.  
  
 Ve výjimečných případech se zprávy nemůžou podařit odeslat do aplikace. Vrstva Windows Communication Foundation (WCF) může najít problém se zprávou, například pokud má zpráva špatný rámec, připojeny neplatné přihlašovací údaje k této zprávě nebo neplatnou hlavičku akce. V těchto případech aplikace zprávu nikdy neobdrží. zpráva se však stále může stát nezpracovatelnou zprávou a bude zpracována ručně.  
  
## <a name="handling-poison-messages"></a>Zpracování poškozených zpráv  
 V rámci služby WCF poskytuje manipulace s nezpracovatelovou zprávou mechanismus pro přijímající aplikaci, aby mohla řešit zprávy, které nelze odeslat do aplikace, nebo zprávy, které byly odeslány do aplikace, ale které nemohly být zpracovány z důvodu specifického pro aplikaci. hlediska. Zpracování nezpracovatelných zpráv je konfigurováno následujícími vlastnostmi v každé z dostupných vazeb zařazených do fronty:  
  
- `ReceiveRetryCount`. Celočíselná hodnota, která určuje maximální počet pokusů o doručení zprávy z fronty aplikace do aplikace. Výchozí hodnota je 5. To je dostačující v případech, kdy se problém okamžitě vyřeší, například s dočasným zablokování v databázi.  
  
- `MaxRetryCycles`. Celočíselná hodnota, která určuje maximální počet cyklů opakování. Cyklus opakování se skládá z přenosu zprávy z fronty aplikace do podfronty opakování a po nastavitelném zpoždění z podfronty opakování zpět do fronty aplikace pro opakované pokusy o doručení. Výchozí hodnota je 2. V [!INCLUDE[wv](../../../../includes/wv-md.md)]je zpráva vyzkoušena maximálně (`ReceiveRetryCount` + 1) * (`MaxRetryCycles` + 1) krát. `MaxRetryCycles`ignoruje se [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] v [!INCLUDE[wxp](../../../../includes/wxp-md.md)]a.  
  
- `RetryCycleDelay`. Časová prodleva mezi opakovanými cykly Výchozí hodnota je 30 minut. `MaxRetryCycles`a `RetryCycleDelay` společně poskytují mechanismus pro vyřešení problému, kdy se problém opakuje po pravidelném zpoždění. Například tato operace zpracovává uzamčenou sadu řádků v SQL Server čeká na potvrzení transakce.  
  
- `ReceiveErrorHandling`. Výčet, který označuje akci, která má být provedena pro zprávu s neúspěšným doručením po pokusu o maximální počet opakovaných pokusů. Hodnoty mohou být chyba, vyřazení, zamítnutí a přesunutí. Výchozí možnost je chyba.  
  
- Indikován. Tato možnost pošle chybu posluchači, která způsobila `ServiceHost` chybu. Před pokračováním zpracování zpráv z fronty musí být zpráva z fronty aplikace odebrána nějakým externím mechanismem.  
  
- Umístíte. Tato možnost zruší nezpracovatelovou zprávu a zpráva se do aplikace nikdy nedoručuje. Pokud v tomto okamžiku `TimeToLive` vypršela vlastnost zprávy, zpráva se může zobrazit ve frontě nedoručených zpráv odesilatele. V takovém případě se zpráva nezobrazí kdekoli. Tato možnost označuje, že uživatel neurčil, co dělat, když dojde ke ztrátě zprávy.  
  
- Schvalovatel. Tato možnost je k dispozici [!INCLUDE[wv](../../../../includes/wv-md.md)]pouze v systému. Tím se dá službě Řízení front zpráv (MSMQ) poslat negativní potvrzení zpátky do správce odesílající fronty, že aplikace nemůže zprávu přijmout. Zpráva se umístí do fronty nedoručených zpráv ve Správci fronty pro odesílání.  
  
- Pøesunout. Tato možnost je k dispozici [!INCLUDE[wv](../../../../includes/wv-md.md)]pouze v systému. Tím se tato nezpracovatelná zpráva přesune do fronty nezpracovatelných zpráv pro pozdější zpracování pomocí aplikace pro zpracování nepoškozené zprávy. Fronta nepoškozených zpráv je podfrontou fronty aplikace. Aplikace pro zpracování nepoškozených zpráv může být služba WCF, která čte zprávy z fronty nezpracovatelných zpráv. Nepoškozená fronta je podfrontou fronty aplikací a lze ji adresovat jako NET.\<MSMQ://*Machine-Name*>/*applicationQueue*;p oison, kde *název počítače* je název počítače, na kterém je fronta nachází se a *applicationQueue* je název fronty pro konkrétní aplikaci.  
  
 Níže jsou uvedené maximální počty pokusů o doručení, které se pro zprávu udělaly:  
  
- ((ReceiveRetryCount + 1) * (MaxRetryCycles + 1)) na [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
- (ReceiveRetryCount + 1) v [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] systémech [!INCLUDE[wxp](../../../../includes/wxp-md.md)]a.  
  
> [!NOTE]
> U zprávy, která byla úspěšně doručena, nejsou provedeny žádné opakované pokusy.  
  
 Aby bylo možné sledovat počet pokusů o přečtení zprávy, [!INCLUDE[wv](../../../../includes/wv-md.md)] aplikace udržuje vlastnost odolné zprávy, která počítá počet přerušení a vlastnost Count Move, která spočítá počet přesunutí zprávy mezi frontou aplikace a podfrontách. Kanál WCF je používá k výpočtu počtu opakování příjmu a počtu cyklů opakování. V [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] systémech [!INCLUDE[wxp](../../../../includes/wxp-md.md)]a se počet přerušení udržuje v paměti kanálu WCF a resetuje se, pokud se aplikace nezdařila. Kanál WCF také může uchovávat počty přerušení až 256 zpráv v paměti. Pokud je přečtena zpráva 257th, je počet přerušení nejstarší zprávy resetován.  
  
 Vlastnosti počet přerušení a přesunutí jsou k dispozici pro operaci služby prostřednictvím kontextu operace. Následující příklad kódu ukazuje, jak k nim přistupovat.  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 WCF poskytuje dvě standardní vazby ve frontě:  
  
- <xref:System.ServiceModel.NetMsmqBinding>. .NET Framework vazba vhodná pro komunikaci založenou na frontě s ostatními koncovými body WCF.  
  
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Vazba vhodná pro komunikaci se stávajícími aplikacemi služby Řízení front zpráv.  
  
> [!NOTE]
> Můžete změnit vlastnosti v těchto vazbách na základě požadavků vaší služby WCF. Celý mechanismus zpracování zpráv o nezpracovateli je místní pro přijímající aplikaci. Proces je neviditelná pro odesílající aplikaci, pokud přijímající aplikace se nakonec nezastaví a pošle negativní potvrzení zpět odesilateli. V takovém případě je zpráva přesunuta do fronty nedoručených zpráv odesilatele.  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>Osvědčené postupy: Zpracování MsmqPoisonMessageException –  
 Pokud služba zjistí, že je zpráva poškozená, přenos ve frontě vyvolá výjimku <xref:System.ServiceModel.MsmqPoisonMessageException> , která `LookupId` obsahuje zprávu o poškození.  
  
 Přijímající aplikace může implementovat <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní, aby zpracovávala všechny chyby, které aplikace vyžaduje. Další informace najdete v tématu [rozšíření kontroly nad zpracováním a vytvářením chyb](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md).  
  
 Aplikace může vyžadovat určitý druh automatizovaného zpracování nepoškozených zpráv, které přesouvají poškozené zprávy do fronty nezpracovatelných zpráv, aby služba mohla přistupovat ke zbytku zpráv ve frontě. Jediným scénářem použití mechanismu obslužné rutiny chyb pro naslouchání výjimkám nepoškozených zpráv je, <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> Pokud je nastavení nastaveno <xref:System.ServiceModel.ReceiveErrorHandling.Fault>na hodnotu. Ukázka nezpracovatelné zprávy pro službu Řízení front zpráv 3,0 ukazuje toto chování. Následující postup popisuje kroky, které je třeba provést pro zpracování nezpracovatelných zpráv, včetně osvědčených postupů:  
  
1. Ujistěte se, že vaše nastavení poškození odráží požadavky vaší aplikace. Při práci s nastavením se ujistěte, že rozumíte rozdílům mezi funkcemi služby Řízení front zpráv v systémech [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
2. V `IErrorHandler` případě potřeby implementujte pro zpracování chyb nepoškozených zpráv. Vzhledem k `ReceiveErrorHandling` tomu `Fault` , že nastavení pro vyžaduje ruční mechanismus pro přesunutí nepoškozené zprávy z fronty nebo pro nápravu externího závislého problému, je typické použití implementováno `ReceiveErrorHandling` `IErrorHandler` , když je `Fault`nastaveno na, jako viz následující kód.  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3. `PoisonBehaviorAttribute` Vytvořte, který může používat chování služby. Chování se nainstaluje `IErrorHandler` na dispečera. Podívejte se na následující příklad kódu.  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4. Zajistěte, aby byla služba opatřena poznámkou s atributem chování po nepoškození.  

 Kromě toho, pokud `ReceiveErrorHandling` je nastaven na `Fault`, `ServiceHost` chyby při zjištění nepoškozené zprávy. Můžete se připojit k chybové události a vypnout službu, provést nápravné akce a restartovat. Například `LookupId` `IErrorHandler` `System.Messaging` vpřípadě`LookupId` , že je možné je poznamenat a v případěchybhostiteleslužby,můžetepoužítrozhraníAPIkpřijetízprávyzfrontypomocínástrojekodebránízprávyz<xref:System.ServiceModel.MsmqPoisonMessageException> zařadí a uloží zprávu do fronty v některém externím úložišti nebo jiné frontě. Pak se můžete restartovat `ServiceHost` , aby se obnovilo normální zpracování. Toto chování ukazuje [zpracování nezpracovatelné zprávy v MSMQ 4,0](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md) .  
  
## <a name="transaction-time-out-and-poison-messages"></a>Časový limit transakce a nepoškozené zprávy  
 Mezi transportním kanálem fronty a uživatelským kódem může dojít ke třídy chyb. Tyto chyby mohou být zjištěny pomocí vrstev mezi, jako je například vrstva zabezpečení zprávy nebo služba pro odeslání logiky. Například chybějící certifikát X. 509 zjištěný ve vrstvě zabezpečení SOAP a chybějící akce jsou případy, kdy se zpráva odešle do aplikace. Pokud k tomu dojde, model služby tuto zprávu zruší. Vzhledem k tomu, že je zpráva čtena v transakci a nelze zadat výsledek pro tuto transakci, transakce je nakonec vyprší, dojde k přerušení a zpráva se vrátí do fronty. Jinými slovy, transakce není okamžitě přerušena, ale čeká do vypršení časového limitu transakce. Časový limit transakce pro službu můžete upravit pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute>.  
  
 Chcete-li změnit časový limit transakce v rámci jednotlivých počítačů, upravte soubor Machine. config a nastavte příslušný časový limit transakce. Je důležité si uvědomit, že v závislosti na časovém limitu nastaveném v transakci nakonec dojde k přerušení transakce a návratu do fronty a jejich počet přerušení je zvýšen. Nakonec se zpráva stane neškodou a správná dispozice se provede podle uživatelských nastavení.  
  
## <a name="sessions-and-poison-messages"></a>Relace a nepoškozené zprávy  
 Relace podchází stejným způsobem jako jedna zpráva a procedura pro zpracování pokusů o manipulaci s nepoškozenými zprávami. Výše uvedené vlastnosti pro nepoškozené zprávy se vztahují na celou relaci. To znamená, že se celá relace zopakuje a v případě odmítnutí zprávy přejde do konečné fronty nedoručitelné zprávy nebo do fronty nedoručených zpráv odesilatele.  
  
## <a name="batching-and-poison-messages"></a>Dávkování a nepoškozených zpráv  
 Pokud se zpráva stala nezpracovatelovou zprávou, která je součástí dávky, pak se celá dávka vrátí zpět a kanál se vrátí ke čtení jedné zprávy v jednom okamžiku. Další informace o dávkování najdete v tématu [dávkové zpracování zpráv v transakci](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md) .  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>Zpracování nezpracovatelných zpráv pro zprávy ve frontě otrav  
 Zpracování nezpracovatelných zpráv nekončí při umístění zprávy do fronty nezpracovatelných zpráv. Zprávy ve frontě nepoškozených zpráv musí být pořád přečtené a zpracovávané. Při čtení zpráv z konečné podfronty poškození lze použít podmnožinu nastavení zpracování nezpracovatelných zpráv. Příslušná nastavení jsou `ReceiveRetryCount` a `ReceiveErrorHandling`. Můžete nastavit `ReceiveErrorHandling` vyřazení, zamítnutí nebo selhání. `MaxRetryCycles`je ignorován a je vyvolána výjimka, pokud `ReceiveErrorHandling` je nastavena na hodnotu Move.  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Rozdíly v systémech Windows Vista, Windows Server 2003 a Windows XP  
 Jak bylo uvedeno dříve, ne všechna nastavení zpracování nezpracovatelných zpráv [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] platí [!INCLUDE[wxp](../../../../includes/wxp-md.md)]pro a. Následující klíčové rozdíly mezi službou Řízení front zpráv [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]v [!INCLUDE[wxp](../../../../includes/wxp-md.md)]systémech, [!INCLUDE[wv](../../../../includes/wv-md.md)] a jsou relevantní pro zpracování nezpracovatelných zpráv:  
  
- Služba Řízení front [!INCLUDE[wv](../../../../includes/wv-md.md)] zpráv v nástroji podporuje dílčí fronty [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] , [!INCLUDE[wxp](../../../../includes/wxp-md.md)] zatímco a nepodporují dílčí fronty. Podfronty se používají při zpracování nezpracovatelných zpráv. Fronty opakování a nepoškozená fronta jsou podfronty aplikací, které jsou vytvořeny na základě nastavení zpracování nezpracovatelných zpráv. Určuje `MaxRetryCycles` , kolik opakovaných podfront se má vytvořit. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] Proto při spuštění v [!INCLUDE[wxp](../../../../includes/wxp-md.md)] `MaxRetryCycles` nebo se ignorují a `ReceiveErrorHandling.Move` není povoleno.  
  
- Služba Řízení front [!INCLUDE[wv](../../../../includes/wv-md.md)] zpráv v nástroji podporuje negativní [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] potvrzení [!INCLUDE[wxp](../../../../includes/wxp-md.md)] a ne. Negativní potvrzení od přijímacího správce fronty způsobí, že odesílajícímu správci fronty umístí odmítnutou zprávu do fronty nedoručených zpráv. V takovém `ReceiveErrorHandling.Reject` případě není povolena v [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
- Služba Řízení front [!INCLUDE[wv](../../../../includes/wv-md.md)] zpráv v nástroji podporuje vlastnost zprávy, která udržuje počet pokusů o doručení zprávy. Tato vlastnost počet přerušení není k dispozici [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] v [!INCLUDE[wxp](../../../../includes/wxp-md.md)]systémech a. Služba WCF udržuje počet přerušení v paměti, takže je možné, že tato vlastnost nesmí obsahovat přesnou hodnotu, pokud je stejná zpráva čtena více než jednou službou WCF ve farmě.  
  
## <a name="see-also"></a>Viz také:

- [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Rozdíly ve funkcích zařazování do front ve Windows Vista, Windows Serveru 2003 a Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Určování a zpracování chyb v kontraktech a službách](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
