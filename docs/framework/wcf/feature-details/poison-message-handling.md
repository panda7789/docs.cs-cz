---
title: Zpracování škodlivých zpráv
ms.date: 03/30/2017
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
ms.openlocfilehash: 378849815617f6556a7d9cc7e89c6697bfdd895d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094992"
---
# <a name="poison-message-handling"></a>Zpracování škodlivých zpráv
*Nezpracovatelná zpráva* je zpráva, že překročila maximální počet pokusů o doručení do aplikace. K této situaci může dojít, když aplikace založená na frontě nemůže zpracovat zprávu z důvodu chyb. Pro splnění požadavků na spolehlivost přijímá aplikace zařazené do fronty zprávy v rámci transakce. Přerušení transakce, ve které byla přijata zpráva zařazená do fronty, opustí zprávu ve frontě, aby se zpráva opakovala v rámci nové transakce. Pokud se problém, který způsobil přerušování transakce, neopraví, přijímající aplikace může zablokovat ve smyčce příjem a přerušit stejnou zprávu, dokud nedosáhnete maximálního počtu pokusů o doručení a výsledků nepoškozených zpráv.  
  
 Zpráva může ze spousty důvodů způsobit nezpracovatelovou zprávu. Nejběžnějšími důvody jsou konkrétní aplikace. Například pokud aplikace přečte zprávu z fronty a provede nějaké zpracování databáze, aplikace může selhat, aby získala zámek pro databázi a způsobila přerušení transakce. Vzhledem k tomu, že transakce databáze byla přerušena, zpráva zůstane ve frontě, což způsobí, že aplikace znovu přečte zprávu podruhé a provede další pokus o získání zámku databáze. Zprávy mohou být také poškozené, pokud obsahují neplatné informace. Například objednávka nákupu může obsahovat neplatné číslo zákazníka. V těchto případech může aplikace dobrovolně transakci zrušit a vynutit, aby se zpráva stala nezpracovatelovou zprávou.  
  
 Ve výjimečných případech se zprávy nemůžou podařit odeslat do aplikace. Vrstva Windows Communication Foundation (WCF) může najít problém se zprávou, například pokud má zpráva špatný rámec, připojeny neplatné přihlašovací údaje k této zprávě nebo neplatnou hlavičku akce. V těchto případech aplikace zprávu nikdy neobdrží. zpráva se však stále může stát nezpracovatelnou zprávou a bude zpracována ručně.  
  
## <a name="handling-poison-messages"></a>Zpracování poškozených zpráv  
 V rámci WCF zajišťuje manipulace s nezpracovatelovou zprávou mechanismus pro přijímající aplikaci, aby mohla zabývat se zprávami, které nelze odeslat do aplikace nebo zpráv, které jsou odeslány do aplikace, ale jejichž zpracování se nezdařilo kvůli konkrétní aplikaci. hlediska. Nakonfigurujte zpracování nezpracovatelných zpráv s následujícími vlastnostmi v každé z dostupných vazeb zařazených do fronty:  
  
- `ReceiveRetryCount`. Celočíselná hodnota, která určuje maximální počet pokusů o doručení zprávy z fronty aplikace do aplikace. Výchozí hodnota je 5. To je dostačující v případech, kdy se problém okamžitě vyřeší, například s dočasným zablokování v databázi.  
  
- `MaxRetryCycles`. Celočíselná hodnota, která určuje maximální počet cyklů opakování. Cyklus opakování se skládá z přenosu zprávy z fronty aplikace do podfronty opakování a po nastavitelném zpoždění z podfronty opakování zpět do fronty aplikace pro opakované pokusy o doručení. Výchozí hodnota je 2. V systému Windows Vista se zpráva pokusí o maximum (`ReceiveRetryCount` + 1) * (`MaxRetryCycles` + 1) krát. `MaxRetryCycles` se ignoruje v systémech Windows Server 2003 a Windows XP.  
  
- `RetryCycleDelay`. Časová prodleva mezi opakovanými cykly Výchozí hodnota je 30 minut. `MaxRetryCycles` a `RetryCycleDelay` společně poskytují mechanismus, který řeší problém, kdy se problém opakuje po pravidelném zpoždění. Například tato operace zpracovává uzamčenou sadu řádků v SQL Server čeká na potvrzení transakce.  
  
- `ReceiveErrorHandling`. Výčet, který označuje akci, která má být provedena pro zprávu s neúspěšným doručením po pokusu o maximální počet opakovaných pokusů. Hodnoty mohou být chyba, vyřazení, zamítnutí a přesunutí. Výchozí možnost je chyba.  
  
- Indikován. Tato možnost pošle chybu naslouchacího procesu, který způsobil chybu `ServiceHost`. Před pokračováním zpracování zpráv z fronty musí být zpráva z fronty aplikace odebrána nějakým externím mechanismem.  
  
- Umístíte. Tato možnost zruší nezpracovatelovou zprávu a zpráva se do aplikace nikdy nedoručuje. Pokud v tomto okamžiku vypršela vlastnost `TimeToLive` zprávy, zpráva se může zobrazit ve frontě nedoručených zpráv odesilatele. V takovém případě se zpráva nezobrazí kdekoli. Tato možnost označuje, že uživatel neurčil, co dělat, když dojde ke ztrátě zprávy.  
  
- Schvalovatel. Tato možnost je k dispozici pouze v systému Windows Vista. Tím se dá službě Řízení front zpráv (MSMQ) poslat negativní potvrzení zpátky do správce odesílající fronty, že aplikace nemůže zprávu přijmout. Zpráva se umístí do fronty nedoručených zpráv ve Správci fronty pro odesílání.  
  
- Pøesunout. Tato možnost je k dispozici pouze v systému Windows Vista. Tím se tato nezpracovatelná zpráva přesune do fronty nezpracovatelných zpráv pro pozdější zpracování pomocí aplikace pro zpracování nepoškozené zprávy. Fronta nepoškozených zpráv je podfrontou fronty aplikace. Aplikace pro zpracování nepoškozených zpráv může být služba WCF, která čte zprávy z fronty nezpracovatelných zpráv. Fronta poškození je podfrontou fronty aplikací a lze ji adresovat jako NET. MSMQ://\<*název počítače*>/*applicationQueue*;p oison, kde *název počítače* je název počítače, na kterém je fronta uložena, a *applicationQueue* je název fronty pro konkrétní aplikaci.  
  
Níže jsou uvedené maximální počty pokusů o doručení, které se pro zprávu udělaly:  
  
- ((ReceiveRetryCount + 1) * (MaxRetryCycles + 1)) v systému Windows Vista.  
  
- (ReceiveRetryCount + 1) v systémech Windows Server 2003 a Windows XP.  
  
> [!NOTE]
> U zprávy, která byla úspěšně doručena, nejsou provedeny žádné opakované pokusy.  
  
 Aby bylo možné sledovat počet pokusů o přečtení zprávy, systém Windows Vista udržuje vlastnost odolné zprávy, která počítá počet přerušení a vlastnost Count Move, která spočítá počet pokusů o přesunutí zprávy mezi frontou a podfrontou aplikace. Kanál WCF je používá k výpočtu počtu opakování příjmu a počtu cyklů opakování. V systémech Windows Server 2003 a Windows XP je počet přerušování uchováván v paměti kanálu WCF a je obnoven, pokud aplikace nebude úspěšná. Kanál WCF také může uchovávat počty přerušení až 256 zpráv v paměti. Pokud je přečtena zpráva 257th, je počet přerušení nejstarší zprávy resetován.  
  
 Vlastnosti počet přerušení a přesunutí jsou k dispozici pro operaci služby prostřednictvím kontextu operace. Následující příklad kódu ukazuje, jak k nim přistupovat.  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 WCF poskytuje dvě standardní vazby ve frontě:  
  
- <xref:System.ServiceModel.NetMsmqBinding>. .NET Framework vazba vhodná pro komunikaci založenou na frontě s ostatními koncovými body WCF.  
  
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Vazba vhodná pro komunikaci se stávajícími aplikacemi služby Řízení front zpráv.  
  
> [!NOTE]
> Můžete změnit vlastnosti v těchto vazbách na základě požadavků vaší služby WCF. Celý mechanismus zpracování zpráv o nezpracovateli je místní pro přijímající aplikaci. Proces je neviditelná pro odesílající aplikaci, pokud přijímající aplikace se nakonec nezastaví a pošle negativní potvrzení zpět odesilateli. V takovém případě je zpráva přesunuta do fronty nedoručených zpráv odesilatele.  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>Osvědčený postup: zpracování MsmqPoisonMessageException –  
 Pokud služba zjistí, že je zpráva poškozená, přenos zařazený do fronty vyvolá <xref:System.ServiceModel.MsmqPoisonMessageException>, který obsahuje `LookupId` nepoškozené zprávy.  
  
 Přijímající aplikace může implementovat rozhraní <xref:System.ServiceModel.Dispatcher.IErrorHandler>, aby zpracovávala všechny chyby, které aplikace vyžaduje. Další informace najdete v tématu [rozšíření kontroly nad zpracováním a vytvářením chyb](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md).  
  
 Aplikace může vyžadovat určitý druh automatizovaného zpracování nepoškozených zpráv, které přesouvají poškozené zprávy do fronty nezpracovatelných zpráv, aby služba mohla přistupovat ke zbytku zpráv ve frontě. Jediným scénářem použití mechanismu obslužné rutiny chyb pro naslouchání výjimkám nepoškozených zpráv je, pokud je nastavení <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> nastaveno na hodnotu <xref:System.ServiceModel.ReceiveErrorHandling.Fault>. Ukázka nezpracovatelné zprávy pro službu Řízení front zpráv 3,0 ukazuje toto chování. Následující postup popisuje kroky, které je třeba provést pro zpracování nezpracovatelných zpráv, včetně osvědčených postupů:  
  
1. Ujistěte se, že vaše nastavení poškození odráží požadavky vaší aplikace. Při práci s nastavením se ujistěte, že rozumíte rozdílům mezi možnostmi služby Řízení front zpráv v systému Windows Vista, Windows Server 2003 a Windows XP.  
  
2. V případě potřeby implementujte `IErrorHandler` pro zpracování chyb nepoškozených zpráv. Vzhledem k tomu, že nastavení `ReceiveErrorHandling` na `Fault` vyžaduje ruční mechanismus k přesunutí nepoškozené zprávy z fronty nebo opravu externího závislého problému, je typické použití implementace `IErrorHandler`, pokud je `ReceiveErrorHandling` nastaveno na `Fault`, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3. Vytvořte `PoisonBehaviorAttribute`, kterou může chování služby využít. Chování nainstaluje `IErrorHandler` na dispečera. Podívejte se na následující příklad kódu.  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4. Zajistěte, aby byla služba opatřena poznámkou s atributem chování po nepoškození.  

 Kromě toho, pokud je `ReceiveErrorHandling` nastaveno na `Fault`, `ServiceHost` chyby při zjištění poškozené zprávy. Můžete se připojit k chybové události a vypnout službu, provést nápravné akce a restartovat. Například `LookupId` v <xref:System.ServiceModel.MsmqPoisonMessageException> šířené do `IErrorHandler` lze poznamenat a v případě selhání hostitele služby můžete pomocí rozhraní API `System.Messaging` získat zprávu z fronty pomocí `LookupId` k odebrání zprávy z fronty a uložení zprávy do některého externího úložiště nebo jiné fronty. Pak můžete restartovat `ServiceHost` pro obnovení normálního zpracování. Toto chování ukazuje [zpracování nezpracovatelné zprávy v MSMQ 4,0](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md) .  
  
## <a name="transaction-time-out-and-poison-messages"></a>Časový limit transakce a nepoškozené zprávy  
 Mezi transportním kanálem fronty a uživatelským kódem může dojít ke třídy chyb. Tyto chyby mohou být zjištěny pomocí vrstev mezi, jako je například vrstva zabezpečení zprávy nebo služba pro odeslání logiky. Například chybějící certifikát X. 509 zjištěný ve vrstvě zabezpečení SOAP a chybějící akce jsou případy, kdy se zpráva odešle do aplikace. Pokud k tomu dojde, model služby tuto zprávu zruší. Vzhledem k tomu, že je zpráva čtena v transakci a nelze zadat výsledek pro tuto transakci, transakce je nakonec vyprší, dojde k přerušení a zpráva se vrátí do fronty. Jinými slovy, transakce není okamžitě přerušena, ale čeká do vypršení časového limitu transakce. Časový limit transakce pro službu můžete upravit pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute>.  
  
 Chcete-li změnit časový limit transakce v rámci jednotlivých počítačů, upravte soubor Machine. config a nastavte příslušný časový limit transakce. Je důležité si uvědomit, že v závislosti na časovém limitu nastaveném v transakci nakonec dojde k přerušení transakce a návratu do fronty a jejich počet přerušení je zvýšen. Nakonec se zpráva stane neškodou a správná dispozice se provede podle uživatelských nastavení.  
  
## <a name="sessions-and-poison-messages"></a>Relace a nepoškozené zprávy  
 Relace podchází stejným způsobem jako jedna zpráva a procedura pro zpracování pokusů o manipulaci s nepoškozenými zprávami. Výše uvedené vlastnosti pro nepoškozené zprávy se vztahují na celou relaci. To znamená, že se celá relace zopakuje a v případě odmítnutí zprávy přejde do konečné fronty nedoručitelné zprávy nebo do fronty nedoručených zpráv odesilatele.  
  
## <a name="batching-and-poison-messages"></a>Dávkování a nepoškozených zpráv  
 Pokud se zpráva stala nezpracovatelovou zprávou, která je součástí dávky, pak se celá dávka vrátí zpět a kanál se vrátí ke čtení jedné zprávy v jednom okamžiku. Další informace o dávkování najdete v tématu [dávkové zpracování zpráv v transakci](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md) .  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>Zpracování nezpracovatelných zpráv pro zprávy ve frontě otrav  
 Zpracování nezpracovatelných zpráv nekončí při umístění zprávy do fronty nezpracovatelných zpráv. Zprávy ve frontě nepoškozených zpráv musí být pořád přečtené a zpracovávané. Při čtení zpráv z konečné podfronty poškození lze použít podmnožinu nastavení zpracování nezpracovatelných zpráv. Příslušná nastavení jsou `ReceiveRetryCount` a `ReceiveErrorHandling`. Můžete nastavit `ReceiveErrorHandling` pro vyřazení, zamítnutí nebo selhání. `MaxRetryCycles` je ignorováno a je vyvolána výjimka, pokud je `ReceiveErrorHandling` nastavena na hodnotu přesunout.  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Rozdíly v systémech Windows Vista, Windows Server 2003 a Windows XP  
 Jak bylo uvedeno dříve, ne všechna nastavení zpracování nezpracovatelných zpráv se vztahují na systémy Windows Server 2003 a Windows XP. Následující klíčové rozdíly mezi službou Řízení front zpráv v systému Windows Server 2003, Windows XP a Windows Vista jsou důležité pro zpracování nezpracovatelných zpráv:  
  
- Služba Řízení front zpráv v systému Windows Vista podporuje dílčí fronty, přičemž systémy Windows Server 2003 a Windows XP nepodporují dílčí fronty. Podfronty se používají při zpracování nezpracovatelných zpráv. Fronty opakování a nepoškozená fronta jsou podfronty aplikací, které jsou vytvořeny na základě nastavení zpracování nezpracovatelných zpráv. `MaxRetryCycles` určuje, kolik opakovaných podfront se má vytvořit. Proto při spuštění v systému Windows Server 2003 nebo Windows XP se `MaxRetryCycles` ignorují a `ReceiveErrorHandling.Move` není povolená.  
  
- Služba Řízení front zpráv v systému Windows Vista podporuje negativní potvrzení, ale systémy Windows Server 2003 a Windows XP ne. Negativní potvrzení od přijímacího správce fronty způsobí, že odesílajícímu správci fronty umístí odmítnutou zprávu do fronty nedoručených zpráv. V takovém případě není `ReceiveErrorHandling.Reject` u systémů Windows Server 2003 a Windows XP povolena.  
  
- Služba Řízení front zpráv v systému Windows Vista podporuje vlastnost zprávy, která udržuje počet pokusů o doručení zprávy. Tato vlastnost počet přerušení není k dispozici v systémech Windows Server 2003 a Windows XP. Služba WCF udržuje počet přerušení v paměti, takže je možné, že tato vlastnost nesmí obsahovat přesnou hodnotu, pokud je stejná zpráva čtena více než jednou službou WCF ve farmě.  
  
## <a name="see-also"></a>Viz také

- [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Rozdíly ve funkcích zařazování do front ve Windows Vista, Windows Serveru 2003 a Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Určování a zpracování chyb v kontraktech a službách](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
