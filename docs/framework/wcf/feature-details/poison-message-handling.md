---
title: Zpracování škodlivých zpráv
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6fa35209b2dafc088605848a0dc96a53a2813dfd
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="poison-message-handling"></a>Zpracování škodlivých zpráv
A *nezpracovatelná zpráva* je zprávu, která byla překročena maximální počet pokusů o doručení do aplikace. Tato situace mohou vzniknout, když aplikace založenou na fronty nemůže zpracovat zprávu z důvodu chyb. Splňovat požadavky na spolehlivost, aplikace přijímá zprávy v rámci transakce. Ruší se transakce, ve kterém byl přijat zprávu ve frontě zanechává zprávy ve frontě, zpráva se pokus o pod novou transakci. Pokud není problém, která způsobila zrušení vyřešen, může být zablokován má přijímající aplikace v smyčku přijímáním a přerušení stejná zpráva, dokud byl překročen maximální počet pokusů o doručení a výsledky poškozená zpráva.  
  
 Zpráva se může stát nezpracovatelná zpráva z mnoha důvodů. Nejčastější příčiny jsou specifické pro aplikaci. Například pokud aplikace přečte zprávu z fronty a provádí zpracování některé databáze, aplikace se pravděpodobně nepodaří získat zámek na databázi, způsobuje ho ji přerušit. Vzhledem k tomu, že databáze transakce byla přerušena, zůstane zprávy ve frontě, což způsobí, že aplikace znovu načíst zprávu podruhé a ujistěte se, další pokus o získání zámku v databázi. Zprávy se může stát také poškozených v případě, že obsahují neplatné informace. Nákupní objednávka může například obsahovat neplatný zákaznické číslo. V těchto případech může aplikace odpojit přerušení transakce a vynutit zpráva, která má být poškozená zpráva.  
  
 Ve výjimečných případech může selhat zprávy k získání odeslat do aplikace. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Vrstvy může být problém se zprávou, například pokud zpráva má nesprávný rámečku, přihlašovací údaje neplatná zpráva připojen nebo hlavičce neplatná akce. V těchto případech aplikace nikdy obdrží zprávu; zpráva však stále může stát nezpracovatelná zpráva a zpracovat ručně.  
  
## <a name="handling-poison-messages"></a>Zpracování poškozených zpráv  
 V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], poškozených zpracování zpráv poskytuje mechanismus pro přijímající aplikace k řešení zprávy, které nelze odeslat do aplikace nebo zprávy, které se odesílají do aplikace, ale které se nepodařilo zpracovat z důvodu důvody specifické pro aplikaci. Zpracování poškozených zpráv ke konfiguraci pomocí následující vlastnosti v každé vazeb k dispozici zařazených do fronty:  
  
-   `ReceiveRetryCount`. Celočíselná hodnota, která určuje maximální počet pokusů o opakování doručení zpráv z fronty aplikace do aplikace. Výchozí hodnota je 5. Toto je dostatečná v případech, kde okamžitou opakování odstraňuje problém, například s dočasné vzájemné zablokování v databázi.  
  
-   `MaxRetryCycles`. Celočíselná hodnota, která určuje maximální počet cyklů opakování. Opakování cyklus se skládá z přenosu zprávy z fronty aplikace na dílčí fronta opakování a konfigurovat zpožděním z dílčí fronta opakování zpět do fronty aplikace pro doručování pokuste se znovu spustit. Výchozí hodnota je 2. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], zkusí se zpráva nesmí být delší než (`ReceiveRetryCount` + 1) * (`MaxRetryCycles` + 1) časy. `MaxRetryCycles` je na ignorována [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   `RetryCycleDelay`. Prodlevu mezi cykly opakování. Výchozí hodnota je 30 minut. `MaxRetryCycles` a `RetryCycleDelay` společně poskytují mechanismus potíže, kde opakovat po pravidelné zpoždění odstraňuje problém vyřešit. Například zpracovává uzamčeném řádek nastavit v systému SQL Server čeká na potvrzení transakce.  
  
-   `ReceiveErrorHandling`. Výčet, který určuje akce pro zprávu, která se nezdařila doručení, po maximální počet opakovaných pokusů, se pokusilo. Hodnoty může být odmítněte odolnost, Drop a přesunout. Výchozí možnost je selhání.  
  
-   Selhání. Tato možnost odešle pro naslouchací proces, který způsobil chybu `ServiceHost` k selhání. Zpráva musí odebrána z fronty aplikace pomocí některé externího mechanismu, než aplikace může dál ke zpracování zpráv z fronty.  
  
-   Vyřaďte. Tato možnost zahodí nezpracovatelná zpráva a nikdy doručení zprávy do aplikace. Pokud zpráva `TimeToLive` vlastnost v tomto okamžiku vypršela a pak zpráva se může zobrazit do fronty nedoručených zpráv odesílatele. Pokud ne, zpráva nezobrazí odkudkoli. Tato možnost znamená, že uživatel není určeného co dělat, když dojde ke ztrátě zprávy.  
  
-   Odmítněte. Tato možnost je dostupná pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)]. To se dá pokyn řízení front zpráv (MSMQ) k odeslání záporné potvrzení zpět do odesílání správce front, že aplikace nemůže přijímat zprávy. Zpráva se umístí do fronty odesílání správce front nedoručených zpráv.  
  
-   Přesunete. Tato možnost je dostupná pouze na [!INCLUDE[wv](../../../../includes/wv-md.md)]. Tento krok přesune poškozených zpráv do fronty zpráv poison pro pozdější zpracování zpracování zpráv poison aplikace. Fronty zpráv poison je dílčí fronta fronty aplikace. Zpracování zpráv poison aplikace může být [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba, která čte zprávy z fronty poškozených. Poškozených fronta je dílčí fronta fronty aplikace a lze řešit jako net.msmq://\<*název počítače*>/*applicationQueue*; poškozených, kde  *název počítače* je název počítače, na kterém je fronta umístěna a *applicationQueue* je název fronty pro konkrétní aplikace.  
  
 Tady jsou maximální počet pokusů o doručení pro zprávu:  
  
-   ((ReceiveRetryCount+1) * (MaxRetryCycles + 1)) na [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
-   (ReceiveRetryCount + 1) na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
> [!NOTE]
>  Žádné opakování jsou vytvářeny pro zprávu, která je úspěšně doručeno.  
  
 Můžete sledovat počet pokusů, dojde k pokusu o čtení zprávy, [!INCLUDE[wv](../../../../includes/wv-md.md)] udržuje vlastnosti trvanlivý zprávy, která vrátí počet přerušení a přesunutí počet vlastnost, která udává počet, kolikrát zprávu přesune mezi frontě aplikace a Podfronty. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Kanál tyto používá k výpočtu receive počet opakování a počet cyklů opakování. Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)], počet přerušení se udržuje v paměti pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanálu a se vynuluje, pokud aplikace. Navíc [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel mohou být uloženy přerušení počty až 256 zprávy v paměti kdykoli. Pokud je pro čtení 257th zprávy, se resetuje počet přerušení nejstarší zpráv.  
  
 Přerušení počet a počet vlastnosti jsou k dispozici pro operace služby prostřednictvím kontext operaci přesunutí. Následující příklad kódu ukazuje, jak přistupovat k nim.  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje dvě vazby standardní zařazených do fronty:  
  
-   <xref:System.ServiceModel.NetMsmqBinding>. A [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] vazby, které jsou vhodné pro provedení komunikace na základě fronty s jinými [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncové body.  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Vazba, která je vhodná pro komunikaci se stávajícími aplikacemi služby Řízení front zpráv.  
  
> [!NOTE]
>  Můžete změnit vlastnosti v těchto vazeb podle požadavků vaší [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby. Celý nezpracovatelná zpráva mechanismu pro zpracování je místní pro přijímající aplikace. Proces je neviditelná pro odesílající aplikací, pokud má přijímající aplikace nakonec zastaví a odešle záporné potvrzení zpátky do odesílatele. V takovém případě zpráva bude přesunuta do fronty nedoručených zpráv odesílatele.  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>Doporučené postupy: Zpracování msmqpoisonmessageexception –  
 Když služba zjistí, že zprávu poškozených, vyvolá zařazených do fronty přenosu <xref:System.ServiceModel.MsmqPoisonMessageException> obsahující `LookupId` poškozených zprávy.  
  
 Můžete implementovat přijímající aplikace <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní pro zpracování chyby, ke kterým aplikace vyžaduje. Další informace najdete v tématu [rozšíření řízení přes zpracování chyb a generování sestav](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md).  
  
 Aplikace může vyžadovat nějaké automatizované zpracování poškozených zpráv, která přemísťuje poškozených zpráv do fronty nezpracovatelná zpráva, aby služba přístup zbytek zprávy ve frontě. Jediný scénář pro použití mechanismu obslužnou rutinu chyby naslouchat poison zpráva výjimky je, když <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> nastavení je <xref:System.ServiceModel.ReceiveErrorHandling.Fault>. Příklad zprávy poison 3.0 služby Řízení front zpráv znázorňuje toto chování. Následující část popisuje kroky pro zpracování poškozených zpráv, včetně osvědčených postupů:  
  
1.  Zkontrolujte, zda že nastavení poškozených odpovídají požadavkům aplikace. Při práci s nastavením, ujistěte se, budete znát rozdíly mezi funkce služby Řízení front zpráv na [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
2.  V případě potřeby implementace `IErrorHandler` se budou zpracovávat chyby poison zprávy. Vzhledem k tomu, že nastavení `ReceiveErrorHandling` k `Fault` vyžaduje ruční mechanismus pro přesun poškozených zpráv z fronty nebo externí závislé problém, typickému využití je implementace `IErrorHandler` při `ReceiveErrorHandling` je nastaven na `Fault`, jako vidět v následujícím kódu.  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3.  Vytvoření `PoisonBehaviorAttribute` , můžete použít chování služby. Chování nainstaluje `IErrorHandler` na dispečera. Podívejte se na následující příklad kódu.  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4.  Ujistěte se, že služby je označena atributem poškozených chování.  
  
  
  
 Kromě toho pokud `ReceiveErrorHandling` je nastaven na `Fault`, `ServiceHost` závady při zjištění poškozená zpráva. Můžete spojit s chybou událostí a vypnout službu, provést opravné akce a restartovat. Například `LookupId` v <xref:System.ServiceModel.MsmqPoisonMessageException> rozšíří do `IErrorHandler` může být uvedeno a když chyb hostitele služby, můžete použít `System.Messaging` rozhraní API pro příjem zprávy z fronty pomocí `LookupId` k odebrání zprávy z fronty a zprávy v některé externím obchodu nebo jiné fronty úložiště. Potom můžete restartovat `ServiceHost` obnovit normální zpracování. [Škodlivých zpracování zpráv v MSMQ 4.0](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md) ukazuje toto chování.  
  
## <a name="transaction-time-out-and-poison-messages"></a>Časový limit transakcí a poškozených zpráv  
 Třída chyb dochází mezi kanál zařazených do fronty přenosu a uživatelského kódu. Tyto chyby lze zjistit pomocí vrstev mezi, jako je například vrstva zabezpečení zprávy nebo odeslání logiky služby. Například chybějící certifikát X.509 zjistil v vrstva zabezpečení protokolu SOAP a chybějící akce jsou případech, kde získat zprávu odeslat do aplikace. V takovém případě modelu služby zahodí zprávy. Protože přečtena v transakci a výstupem u dané transakce nemůže být zadaný transakce nakonec vyprší, přerušení a zpráva je vrátit zpět do fronty. Jinými slovy některých tříd chyb, transakce není abort okamžitě, ale počká, až vyprší transakce. Můžete upravit transakce časový limit pro službu pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute>.  
  
 Chcete-li změnit časový limit transakcí v rámci celého počítače, upravte souboru machine.config a nastavení časového limitu pro příslušnou transakci. Je důležité si uvědomit, že, v závislosti na časový limit, nastavte v transakci, transakce nakonec zruší a přejde zpět do fronty, a se zvýší jeho počet přerušení. Nakonec se stává poškozených zprávy a správné dispozice přišla podle nastavení uživatele.  
  
## <a name="sessions-and-poison-messages"></a>Relace a poškozených zpráv  
 Relaci projde stejné opakování a postupy zpracování zpráv poison jako do jedné zprávy. Vlastnosti dříve uvedené pro poškozených zpráv se vztahují na celé relace. To znamená, že se pokus o celé relace a přejde na poslední poison zprávy fronty nebo fronty nedoručených zpráv odesílatele, pokud se odmítne zprávy.  
  
## <a name="batching-and-poison-messages"></a>Dávkování a poškozených zpráv  
 Pokud zpráva stane poškozených zpráv a je součástí dávky, celý batch je vrácena zpět a kanál vrátí do čtení jednu zprávu najednou. Další informace o dávkování najdete v tématu [dávkování zpráv v transakci](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>Zpracování zpráv ve frontě poškozených Poison zpráv  
 Zpracování zpráv Poison nemá na konci při umístění zprávu do fronty poison zpráv. Zprávy ve frontě poison zprávy musí být stále číst a zpracovávat. Při čtení zpráv z poslední poškozených dílčí fronta můžete podmnožinu nastavení zpracování poison zpráv. Použít nastavení `ReceiveRetryCount` a `ReceiveErrorHandling`. Můžete nastavit `ReceiveErrorHandling` vyřadit, odmítněte, nebo poruch. `MaxRetryCycles` je ignorován a je vyvolána výjimka, pokud `ReceiveErrorHandling` je nastaven na přesunutí.  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Windows Vista, Windows Server 2003 a Windows XP rozdíly  
 Jak již bylo uvedeno dříve, ne všechny zpracování zpráv poison nastavení se vztahují na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Následující klíčové rozdíly mezi služby Řízení front zpráv na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], [!INCLUDE[wxp](../../../../includes/wxp-md.md)], a [!INCLUDE[wv](../../../../includes/wv-md.md)] jsou relevantní pro zpracování poison zpráv:  
  
-   Zprávy služby Řízení front zpráv v [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje podfronty, zatímco [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nepodporují podfronty. Podfronty se používají při zpracování poison zpráv. Fronty opakování a poškozených fronty jsou podfronty do fronty aplikace, která je vytvořena na základě nastavení zpracování poison zpráv. `MaxRetryCycles` Určuje, kolik opakujte podfronty k vytvoření. Proto při spuštění [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` jsou ignorovány a `ReceiveErrorHandling.Move` není povolen.  
  
-   Zprávy služby Řízení front zpráv v [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje zápornou potvrzení, zatímco [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nepodporují. Záporné potvrzení z přijímající správce front způsobí, že odesílání správce front k umístit odmítnuté zprávy do fronty nedoručených zpráv. Jako takový `ReceiveErrorHandling.Reject` není povolen u [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   Zprávy služby Řízení front zpráv v [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje dojde k pokusu o vlastnosti zprávy, která udržuje počet Počet doručení zpráv. Tato vlastnost počet přerušení není k dispozici na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] udržuje počet přerušení v paměti, takže je možné, že tato vlastnost nesmí obsahovat přesné hodnoty přečtení stejné zprávy o více než jednu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] službu ve farmě.  
  
## <a name="see-also"></a>Viz také  
 [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Rozdíly ve funkcích zařazování do front ve Windows Vista, Windows Serveru 2003 a Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 [Určování a zpracování chyb v kontraktech a službách](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
