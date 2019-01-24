---
title: Zpracování škodlivých zpráv
ms.date: 03/30/2017
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
ms.openlocfilehash: ec7603e547c065b4b86f2c81650c6e8a2ce09e6f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745802"
---
# <a name="poison-message-handling"></a>Zpracování škodlivých zpráv
A *nezpracovatelná zpráva byla* je zpráva, která byla překročena maximální počet pokusů o doručení do aplikace. Tato situace může nastat, když aplikace na základě fronty nemůže zpracovat zprávu z důvodu chyby. Abyste splnili požadavky na spolehlivost, frontové aplikace přijímá zprávy v rámci transakce. Zrušená transakce, ve kterém byla přijata zpráva ve frontě opustí zprávu ve frontě, tak, aby zprávy se zopakuje za novou transakci. Pokud není opraven problém, která způsobila zrušení, přijímající aplikace můžete uvízne ve smyčce přijímáním a přerušení stejné zprávy, dokud byl překročen maximální počet pokusů o doručení a výsledky nezpracovatelná zpráva byla.  
  
 Zpráva se může stát nezpracovatelná zpráva z mnoha důvodů. Mezi nejběžnější důvody jsou specifické pro aplikaci. Například pokud aplikace čte zprávy z fronty a provede zpracování databáze, aplikace nemusí získat zámek na databázi, vyvolá přerušení transakce. Protože databázové transakce byla přerušena, zpráva zůstane ve frontě, což způsobí, že aplikace znovu načíst zprávu podruhé a udělat další pokus o získání zámku v databázi. Zprávy se může stát také nezpracovatelných v případě, že obsahují neplatné informace. Nákupní objednávky může například obsahovat neplatný zákaznické číslo. V těchto případech může aplikace dobrovolně přerušení transakce a vynutit zprávu, která se stane nezpracovatelných zpráv.  
  
 Ve výjimečných případech může selhat zprávy k získání odeslaných do aplikace. Vrstvě Windows Communication Foundation (WCF) možná zjistíte problém se zprávou, například pokud má zpráva nesprávné rámce, přihlašovací údaje neplatná zpráva připojené k nebo hlavičce akce je neplatná. V těchto případech se nikdy aplikace obdrží zprávy. zpráva však může být stále nezpracovatelná zpráva a zpracovat ručně.  
  
## <a name="handling-poison-messages"></a>Počet Nezpracovatelných zpráv zpracování  
 Ve službě WCF manipulaci s nezpracovatelnými zprávami poskytuje mechanismus pro přijímající aplikace k řešení zprávy, které aplikace se nedají odbavovat nebo zprávy, které se odesílají do aplikace, ale které nepovedlo se zpracovat z důvodu specifické pro aplikaci z důvodů. Následující vlastnosti ve všech dostupných ve frontě vazby je nakonfiguroval manipulaci s nezpracovatelnými zprávami:  
  
-   `ReceiveRetryCount`. Celočíselná hodnota, která určuje maximální počet pokusů o zopakování doručení zprávy z fronty aplikace do aplikace. Výchozí hodnota je 5. To stačí v případech, kdy okamžité opakování vyřeší daný problém, například s dočasné zablokování v databázi.  
  
-   `MaxRetryCycles`. Celočíselná hodnota, která určuje maximální počet cyklů opakování. Opakovat cyklus se skládá z přenosu zprávy z fronty aplikace do podfronty opakování a konfigurovat zpožděním z podfronty opakování zpět do fronty, aplikace pro doručování pokuste se znovu spustit. Výchozí hodnota je 2. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], zkusí se zprávy nesmí být delší (`ReceiveRetryCount` + 1) * (`MaxRetryCycles` + 1) časy. `MaxRetryCycles` se ignoruje u [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   `RetryCycleDelay`. Časovou prodlevu mezi cyklů opakování. Výchozí hodnota je 30 minut. `MaxRetryCycles` a `RetryCycleDelay` společně poskytují mechanismus pro řešení potíží, kde zkuste to znovu za pravidelné zpoždění vyřeší daný problém. Například zpracovává uzamčené řádek nastavení v systému SQL Server čekající potvrzení transakce.  
  
-   `ReceiveErrorHandling`. Výčet, který označuje akce má být provedena, který selhal po pokusil maximální počet pokusů o doručení zprávy. Hodnotami může být selhání, Drop odmítnout a přesunout. Výchozí možnost je odolná.  
  
-   Selhání. Tato možnost odešle naslouchací proces, který způsobil chybu `ServiceHost` selhání. Zpráva musí odebrána z fronty aplikace některé externí mechanismem předtím, než může aplikace dál zpracovávat zprávy z fronty.  
  
-   Vyřaďte. Tato možnost sníží počet nezpracovatelných zpráv a zpráva se doručí nikdy k aplikaci. Pokud zpráva `TimeToLive` vlastnost vypršela platnost v tuto chvíli a pak zpráva se může zobrazit ve frontě nedoručených zpráv odesílatele. Pokud ne, zpráva se nezobrazí kdekoli. Tato možnost označuje, že uživatel není určený co dělat, když dojde ke ztrátě zprávy.  
  
-   Odmítnout. Tato možnost je dostupná jenom na [!INCLUDE[wv](../../../../includes/wv-md.md)]. Toto dá pokyn řízení front zpráv (MSMQ) do posílat negativní potvrzení zpět k odesílání správce fronty, že aplikace nemůže přijímat zprávy. Zprávu je umístěn do fronty odesílání správce fronty nedoručených zpráv.  
  
-   Přesuňte. Tato možnost je dostupná jenom na [!INCLUDE[wv](../../../../includes/wv-md.md)]. Nezpracovatelná zpráva to přesune do fronty zpráv poison k dalšímu zpracování zpracování zpráv poison aplikací. Fronta zpráv poison je dílčí fronty aplikace. Zpracování zpráv poison aplikací může být služby WCF, který čte z fronty nezpracovatelných zpráv. Nezpracovatelná fronty je dílčí fronty aplikace, můžete řešit jako net.msmq://\<*název počítače*>/*applicationQueue*; poškozené, kde  *název počítače* je název počítače, na kterém je fronta umístěna a *applicationQueue* je název fronty, specifické pro aplikaci.  
  
 Následují maximální počet pokusů o doručení zprávy:  
  
-   ((ReceiveRetryCount+1) * (MaxRetryCycles + 1)) na [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
-   (ReceiveRetryCount + 1) na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
> [!NOTE]
>  Žádné opakování probíhají zprávy, která je úspěšně doručeno.  
  
 Můžete sledovat počet, kolikrát dojde k pokusu o čtení zprávy, [!INCLUDE[wv](../../../../includes/wv-md.md)] udržuje zpráv trvalý vlastnost, která vrátí počet přerušení a přesunutí vlastnost počet, který počítá počet, kolikrát se zpráva přesune mezi fronty aplikace a podfrontách. Kanál WCF používá tato vypočítat počet opakování přijetí a počet cyklů opakování. Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)], počet přerušení kanál WCF udržuje v paměti a je obnovení v případě selhání aplikace. Navíc kanál WCF mohou být uloženy že Abort počty až 256 zprávy v paměti v čase. Pokud je pro čtení 257th zprávy, se resetuje počet přerušení nejstarší zpráv.  
  
 Přerušení počet a počet vlastnosti jsou k dispozici pro operace služby prostřednictvím kontext operace přesunutí. Následující příklad kódu ukazuje, jak přistupovat k nim.  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 WCF poskytuje dvě vazby standardní zařazených do fronty:  
  
-   <xref:System.ServiceModel.NetMsmqBinding>. A [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] vazby vhodné pro provádění komunikace pomocí dalších koncových bodů WCF na základě fronty.  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Vazba, která je vhodná pro komunikaci se stávajícími aplikacemi služby Řízení front zpráv.  
  
> [!NOTE]
>  Můžete změnit vlastnosti v těchto vazeb na základě požadavků vaší služby WCF. Celý nezpracovatelná zpráva mechanismu pro zpracování je místní pro přijímající aplikace. Proces je neviditelné u odesílací aplikace, pokud přijímající aplikace nakonec zastaví a odesílateli pošle negativní potvrzení. V takovém případě zpráva bude přesunuta do fronty nedoručených zpráv odesílatele.  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>Osvědčený postup: Msmqpoisonmessageexception – zpracování  
 Když službu shledá, že je zpráva poškozená, vyvolá zařazených do fronty přenosu <xref:System.ServiceModel.MsmqPoisonMessageException> , která obsahuje `LookupId` nezpracovatelných zpráv.  
  
 Můžete implementovat přijímající aplikace <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní pro zpracování chyby, ke kterým aplikace vyžaduje. Další informace najdete v tématu [rozšíří ovládací prvek průběhu zpracování chyb a vytváření sestav](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md).  
  
 Aplikace může vyžadovat, aby nějaký druh automatizované zpracování nezpracovatelných zpráv, který přesouvá nezpracovatelných zpráv ve frontě nezpracovatelných zpráv tak, aby službě můžete získat přístup k zbytek zprávy ve frontě. Jediným případem použití mechanismu obslužná rutina chyb pro naslouchání poison zpráva výjimky je, když <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> nastavená na <xref:System.ServiceModel.ReceiveErrorHandling.Fault>. Ukázková zpráva poison 3.0 služby Řízení front zpráv ukazuje toto chování. Následující část popisuje kroky pro zpracování nezpracovatelných zpráv, včetně osvědčených postupů:  
  
1.  Zkontrolujte, že počet poškozených nastavení odpovídají požadavkům vaší aplikace. Při práci s nastavením, ujistěte se, znát rozdíly mezi funkce služby Řízení front zpráv na [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
2.  V případě potřeby implementovat `IErrorHandler` zpracování chyb poison zprávy. Protože nastavení `ReceiveErrorHandling` k `Fault` vyžaduje ruční mechanismus pro přesun nezpracovatelná zpráva z fronty nebo externí závislé opravena, typickému využití je implementace `IErrorHandler` při `ReceiveErrorHandling` je nastavena na `Fault`, jako je znázorněno v následujícím kódu.  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3.  Vytvoření `PoisonBehaviorAttribute` , můžete použít chování služby. Chování nainstaluje `IErrorHandler` na dispečer. Podívejte se na následující příklad kódu.  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4.  Ujistěte se, že vaše služba je opatřen poznámkou atributu nezpracovatelných chování.  
  
  
  
 Kromě toho pokud `ReceiveErrorHandling` je nastavena na `Fault`, `ServiceHost` chyb při zjištění nezpracovatelných zpráv. Můžete připojit k chybnou událost a vypnutí služby, provést opravné akce a restartovat. Například `LookupId` v <xref:System.ServiceModel.MsmqPoisonMessageException> rozšíří na `IErrorHandler` můžete třeba poznamenat, a když chyby hostitele služby, můžete použít `System.Messaging` přijímat zprávy z fronty pomocí rozhraní API `LookupId` odebrání zprávy z Fronta a zpráva v některé externí úložiště nebo jinou frontu úložiště. Potom můžete restartovat `ServiceHost` obnovit normální zpracování. [Zacházení s Nezpracovatelnými zpracování zpráv v MSMQ 4.0](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md) ukazuje toto chování.  
  
## <a name="transaction-time-out-and-poison-messages"></a>Časový limit transakce a Nezpracovatelných zpráv  
 Třída chyb mohla probíhat ve frontě přenosový kanál a kód uživatele. Tyto chyby můžete zjistit pomocí vrstev mezi, jako je například vrstva zabezpečení zprávy nebo odeslání logiky služby. Například ve vrstvě zabezpečení SOAP zjistil chybějícího certifikátu X.509 a chybějící akce jsou případy, kde získat zpráva odeslána do aplikace. Pokud k tomu dojde, model služby zahodí. Protože je pro čtení zprávy v transakci a jako výsledek pro dané transakce nemůže být zadaný transakce časem i vypršení časového, přerušení a zpráva je znovu umístěny do fronty. Jinými slovy v případě určité třídy chyb transakce není přerušit okamžitě, ale počká, dokud nebudou transakce vyprší časový limit. Můžete upravit časový limit transakce pro službu pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute>.  
  
 Chcete-li změnit časový limit transakce na základě celý počítač, upravte soubor machine.config a nastavení časového limitu pro příslušnou transakci. Je důležité si uvědomit, že, v závislosti na časový limit, nastavte v rámci transakce, transakce nakonec přeruší a přejde zpět do fronty, a je zvýšen počet jeho přerušení. Nakonec bude nezpracovatelná zpráva a správné disposition je k podle nastavení uživatele.  
  
## <a name="sessions-and-poison-messages"></a>Relace a Nezpracovatelných zpráv  
 Relace projde stejné opakování a postupy zpracování zpráv poison jako jedna zpráva. Vlastnosti výše uvedených nezpracovatelných zpráv platí pro celou relaci. To znamená, že celá relace je pokus o získání a přejde na poslední poison zprávu fronty nebo fronty nedoručených zpráv odesílatele, pokud se zpráva.  
  
## <a name="batching-and-poison-messages"></a>Dávkování a Nezpracovatelných zpráv  
 Pokud zpráva stane nezpracovatelných zpráv a je součástí dávky, celý batch se vrátí zpět a kanál se vrátí v čase pro čtení zpráv. Další informace o dávkové zpracování, naleznete v tématu [dávkování zpráv v transakci](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>Zpracování zpráv ve frontě Nezpracovatelných Poison zprávy  
 Zpracování zpráv Poison nekončí při umístění zprávu do fronty zpráv poison. Zprávy ve frontě zpráv poison musí nadále číst a zpracovat. Při čtení z poslední podfronty nezpracovatelných zpráv, můžete použít podmnožinu nastavení zpracování poison zpráv. Použít nastavení, musí být `ReceiveRetryCount` a `ReceiveErrorHandling`. Můžete nastavit `ReceiveErrorHandling` vyřadit, odmítnout, nebo selhání. `MaxRetryCycles` je ignorována a pokud je vyvolána výjimka `ReceiveErrorHandling` je nastavena na přesunutí.  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Windows Vista, Windows Server 2003 a Windows XP rozdíly  
 Jak bylo uvedeno dříve, ne všechna nastavení zpracování zpráv poison platí pro [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Následující klíče rozdíly mezi služby Řízení front zpráv na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], [!INCLUDE[wxp](../../../../includes/wxp-md.md)], a [!INCLUDE[wv](../../../../includes/wv-md.md)] jsou relevantní pro zpracování zpráv poison:  
  
-   Zprávy služby Řízení front zpráv v [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje podfrontách, zatímco [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nepodporují podfrontách. Podfrontách se používají při zpracování poison zpráv. Fronty opakovaných a nezpracovatelných fronty jsou podfronty do aplikace fronty, který je vytvořen na základě nastavení zpracování poison zpráv. `MaxRetryCycles` Určuje, kolik opakování podfrontách vytvořit. Proto při spuštění na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nebo [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` jsou ignorovány a `ReceiveErrorHandling.Move` není povolený.  
  
-   Zprávy služby Řízení front zpráv v [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje negativní potvrzení, zatímco [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nepodporují. Negativní potvrzení z využívá správce fronty způsobí, že odesílání správce front k umístění odmítnuté zprávy do fronty nedoručených zpráv. V důsledku toho `ReceiveErrorHandling.Reject` není povolen u [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   Zprávy služby Řízení front zpráv v [!INCLUDE[wv](../../../../includes/wv-md.md)] podporuje dojde k pokusu o vlastnost zprávy, který udržuje počet určený počet pokusů o doručení zpráv. Tato vlastnost počet přerušení není k dispozici na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. WCF udržuje počet přerušení v paměti, takže je možné, že tato vlastnost nesmí obsahovat přesné hodnoty, když přečte stejné zprávy více než jedné služby WCF ve farmě.  
  
## <a name="see-also"></a>Viz také:
- [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Rozdíly ve funkcích zařazování do front ve Windows Vista, Windows Serveru 2003 a Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Určování a zpracování chyb v kontraktech a službách](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
