---
title: Použití relací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: aea26c3a814a34c9d2985bb1bf02dbb80d32ef12
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320290"
---
# <a name="using-sessions"></a>Použití relací
V aplikacích Windows Communication Foundation (WCF) *relace* koreluje skupinu zpráv do konverzace. Relace WCF se liší od objektu relace, který je k dispozici v aplikacích ASP.NET, podporují různá chování a jsou ovládány různými způsoby. Toto téma popisuje funkce, které relace povolují v aplikacích WCF a jejich použití.  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Relace v Windows Communication Foundationch aplikacích  
 Pokud kontrakt služby určí, že vyžaduje relaci, je nutné, aby tato smlouva určila, že všechna volání (tj. základní výměny zpráv podporující volání) musí být součástí stejné konverzace. Pokud kontrakt určí, že umožňuje relace, ale nevyžaduje jednu, klienti se mohou připojit a vytvořit relaci nebo nevytvořit relaci. Pokud dojde k ukončení relace a zpráva se pošle prostřednictvím stejného kanálu, vyvolá se výjimka.  
  
 Relace WCF mají následující hlavní koncepční funkce:  
  
- Jsou explicitně iniciovány a ukončeny volající aplikací (klient služby WCF).  
  
- Zprávy dodávané během relace jsou zpracovávány v pořadí, ve kterém byly přijaty.  
  
- Relace korelují skupinu zpráv do konverzace. Je možné použít různé typy korelace. Jeden kanál založený na relaci může například korelovat zprávy na základě sdíleného síťového připojení, zatímco jiný kanál založený na relaci může korelovat zprávy na základě sdílené značky v těle zprávy. Funkce, které mohou být odvozeny z relace závisí na povaze korelace.  
  
- K relaci WCF není přidruženo žádné obecné úložiště dat.  
  
 Pokud znáte třídu <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> v aplikacích ASP.NET a funkcích, které poskytuje, můžete si všimnout následujících rozdílů mezi tímto druhem relace a relacemi WCF:  
  
- ASP.NET relace jsou vždy iniciovány serverem.  
  
- ASP.NET relace jsou implicitně neuspořádané.  
  
- ASP.NET relace poskytují obecný mechanismus pro ukládání dat napříč požadavky.  
  
 Toto téma popisuje:  
  
- Výchozí chování při spouštění při použití vazeb založených na relacích ve vrstvě modelu služby.  
  
- Typy funkcí, které poskytují vazby založené na relaci WCF.  
  
- Vytvoření kontraktu, který deklaruje požadavek relace.  
  
- Pochopení a řízení vytvoření a ukončení relace a relace relace k instanci služby.  
  
## <a name="default-execution-behavior-using-sessions"></a>Výchozí chování při provádění pomocí relací  
 Vazba, která se pokusí iniciovat relaci, se nazývá vazba *založená na relaci* . Kontrakty služby určují, že vyžadují, povolují nebo odmítnou vazby založené na relacích nastavením vlastnosti <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> v rozhraní kontraktu služby (nebo třídě) na jednu z hodnot <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> výčtu. Ve výchozím nastavení je hodnota této vlastnosti <xref:System.ServiceModel.SessionMode.Allowed>, což znamená, že pokud klient používá vazbu založenou na relaci s implementací služby WCF, služba vytvoří a použije poskytnutou relaci.  
  
 Když služba WCF akceptuje relaci klienta, jsou ve výchozím nastavení povoleny následující funkce:  
  
1. Všechna volání mezi objektem klienta WCF jsou zpracovávána stejnou instancí služby.  
  
2. Různé vazby založené na relacích poskytují další funkce.  
  
## <a name="system-provided-session-types"></a>Typy relací poskytovaných systémem  
 Vazba založená na relaci podporuje výchozí přidružení instance služby k určité relaci. Jiné vazby založené na relaci však podporují různé funkce kromě povolení výše popsaného řízení vytváření instancí založeného na relacích.  
  
 WCF nabízí následující typy chování aplikace založené na relacích:  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> podporuje relace založené na zabezpečení, ve kterých se na konkrétní zabezpečenou konverzaci dohodla obě konce komunikace. Další informace najdete v tématu [zabezpečení služeb](securing-services.md). Například vazba <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>, která obsahuje podporu pro relace zabezpečení i spolehlivé relace, ve výchozím nastavení používá jenom zabezpečenou relaci, která šifruje a digitálně podepisuje zprávy.  
  
- Vazba <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> podporuje relace založené na protokolu TCP/IP, aby se zajistilo, že se všechny zprávy budou korelovat připojením na úrovni soketu.  
  
- Element <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>, který implementuje specifikaci WS-ReliableMessaging, poskytuje podporu pro spolehlivé relace, ve kterých je možné nakonfigurovat zprávy tak, aby byly doručeny v daném pořadí a právě jednou, aby bylo zajištěno, že zprávy jsou přijímány i v případě, že se zprávy během konverzace cestují mezi více uzly. Další informace najdete v tématu [spolehlivé relace](./feature-details/reliable-sessions.md).  
  
- Vazba <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> poskytuje relace datagramů MSMQ. Další informace najdete v tématu [fronty ve službě WCF](./feature-details/queues-in-wcf.md).  
  
 Nastavením vlastnosti <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> neurčíte typ relace, kterou kontrakt vyžaduje, jenom to, že vyžaduje jeden.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Vytvoření kontraktu, který vyžaduje relaci  
 Vytvoření kontraktu, který vyžaduje relaci, má za následek, že skupina operací, které kontrakt služby deklaruje, musí být spuštěná v rámci stejné relace a zprávy musí být doručeny v daném pořadí. Pokud chcete vyhodnotit úroveň podpory relací, kterou kontrakt služby vyžaduje, nastavte vlastnost <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> v rozhraní nebo třídě kontraktu služby na hodnotu <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> výčtu, abyste určili, jestli kontrakt:  
  
- Vyžaduje relaci.  
  
- Umožňuje klientovi vytvořit relaci.  
  
- Zakáže relaci.  
  
 Nastavení vlastnosti <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> ale neurčuje typ chování založeného na relacích, které kontrakt vyžaduje. Instruuje službu WCF, aby ověřila za běhu, že nakonfigurovaná vazba (která vytvoří komunikační kanál) pro službu, není nebo může vytvořit relaci při implementaci služby. Vazba pak může tento požadavek splnit s jakýmkoli typem chování založeného na relacích, který zvolí – zabezpečení, přenos, spolehlivý nebo několik kombinací. Přesné chování závisí na vybrané hodnotě <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>. Pokud konfigurovaná vazba služby není v souladu s hodnotou <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>, je vyvolána výjimka. Vazby a kanály, které vytvoří, jsou označeny jako založené na relacích.  
  
 Následující kontrakt služby určuje, že všechny operace v `ICalculatorSession` musí být vyměňovány v rámci relace. Žádná operace nevrátí hodnotu volajícímu s výjimkou metody `Equals`. Metoda `Equals` však nepřebírá žádné parametry a proto může vrátit nenulovou hodnotu v rámci relace, ve které již byla data předána do ostatních operací. Tato smlouva vyžaduje, aby relace fungovala správně. Bez relace přidružené ke konkrétnímu klientovi nemá instance služby žádný způsob, jak poznáte předchozí data, která klient odeslal.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Pokud služba umožňuje relaci, pak se vytvoří relace, která se použije, pokud klient jednu z nich zahájí. v opačném případě se nevytvoří žádná relace.  
  
## <a name="sessions-and-service-instances"></a>Relace a instance služby  
 Použijete-li výchozí chování vytváření instancí v technologii WCF, všechna volání mezi objektem klienta WCF jsou zpracovávána stejnou instancí služby. Proto můžete na úrovni aplikace představit relaci jako povolení chování aplikace podobně jako chování místního volání. Například při vytváření místního objektu:  
  
- Je volán konstruktor.  
  
- Všechna následná volání odkaz na objekt klienta služby WCF jsou zpracována stejnou instancí objektu.  
  
- Destruktor se volá, když je zničen odkaz na objekt.  
  
 Relace umožňují podobné chování mezi klienty a službami, pokud se použije výchozí chování instance služby. Pokud kontrakt služby vyžaduje nebo podporuje relace, může být jedna nebo víc operací kontraktu označená jako iniciovaná nebo koncová relace nastavením vlastností <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> a <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>.  
  
 *Operace inicializace* jsou ty, které se musí volat jako první operace nové relace. Operace, které nelze iniciovat, lze volat pouze po volání nejméně jedné operace zahájení. Proto můžete vytvořit druh konstruktoru relace pro vaši službu tím, že deklarujete inicializační operace navržené k převzetí vstupu od klientů odpovídajících začátku instance služby. (Stav je přidružen k relaci, ale nikoli k objektu služby.)  
  
 *Koncové operace*, naopak, jsou ty, které se musí volat jako poslední zpráva v existující relaci. Ve výchozím případu služba WCF recykluje objekt služby a jeho kontext po ukončení relace, ke které byla služba přidružena. Můžete tedy vytvořit druh destruktoru deklarováním ukončovacích operací navržených k provedení funkce vhodné na konci instance služby.  
  
> [!NOTE]
> I když je výchozí chování rovno lokálním konstruktorům a destruktorům, je to pouze podobné. Jakoukoli operací služby WCF může být operace iniciování nebo ukončení, nebo obojí. Kromě toho ve výchozím případu se iniciované operace můžou v libovolném pořadí volat libovolným počtem časů; Po navázání relace a přidružení s instancí se nevytvoří žádné další relace, pokud explicitně neurčíte dobu života instance služby (při manipulaci s objektem <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>). Nakonec je tento stav přidružen k relaci, nikoli k objektu služby.  
  
 Například kontrakt `ICalculatorSession` použitý v předchozím příkladu vyžaduje, aby objekt klienta WCF nejprve volal operaci `Clear` před jakoukoliv jinou operací a aby relace s tímto objektem klienta WCF při volání operace `Equals` ukončila činnost. Následující příklad kódu ukazuje kontrakt, který tyto požadavky vynutil. aby bylo možné inicializovat relaci, musí být nejprve volána `Clear` a relace končí při volání `Equals`.  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Služby nespouštějí relace s klienty. V klientských aplikacích WCF existuje přímá relace mezi životností kanálu založeného na relaci a životností samotné relace. V takovém případě klienti vytvářejí nové relace vytvořením nových kanálů založených na relacích a odcházejí stávající relace tím, že budou kanály založené na relacích řádně uzavírat. Klient spustí relaci s koncovým bodem služby voláním jedné z následujících možností:  
  
- <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> na kanálu vráceném voláním <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
- <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> objektu klienta WCF generovaného [nástrojem Svcutil. exe (Nástroj pro metadata ServiceModel)](servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
- Operace iniciování na jednom typu objektu klienta WCF (ve výchozím nastavení se spouští všechny operace). Když je volána první operace, objekt klienta WCF automaticky otevře kanál a zahájí relaci.  
  
 Klient obvykle ukončí relaci s koncovým bodem služby voláním jedné z následujících možností:  
  
- <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> na kanálu vráceném voláním <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
- <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> objektu klienta WCF generovaného nástrojem Svcutil. exe.  
  
- Ukončující operace na jednom typu objektu klienta WCF (ve výchozím nastavení se neukončí žádné operace; kontrakt musí explicitně zadat ukončující operaci). Když je volána první operace, objekt klienta WCF automaticky otevře kanál a zahájí relaci.  
  
 Příklady najdete v tématu [Postupy: vytvoření služby, která vyžaduje relace,](./feature-details/how-to-create-a-service-that-requires-sessions.md) a také [výchozí chování služby](./samples/default-service-behavior.md) a ukázky vytváření [instancí](./samples/instancing.md) .  
  
 Další informace o klientech a relacích najdete v tématu [přístup ke službám pomocí klienta WCF](./feature-details/accessing-services-using-a-client.md).  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Relace pracují s nastavením InstanceContext  
 Existuje interakce mezi výčtem <xref:System.ServiceModel.SessionMode> ve kontraktu a vlastností <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType>, která řídí přidružení mezi kanály a konkrétními objekty služby. Další informace najdete v tématu [relace, vytváření instancí a souběžnost](./feature-details/sessions-instancing-and-concurrency.md).  
  
### <a name="sharing-instancecontext-objects"></a>Sdílení objektů InstanceContext  
 Můžete také určit, ke kterému kanálu nebo volání založenému na relaci je přidruženo, které <xref:System.ServiceModel.InstanceContext> objekt provádí přidružení sami. 
  
## <a name="sessions-and-streaming"></a>Relace a streamování  
 Pokud máte velké množství dat, která se mají přenést, je režim přenosu streamování ve službě WCF vhodná alternativa k výchozímu chování ukládání zpráv do vyrovnávací paměti a jejich zpracování v celé paměti. Může dojít k neočekávanému chování při volání streamování s vazbou založenou na relacích. Všechna volání streamování se provádějí pomocí jednoho kanálu (kanálu Datagram), který nepodporuje relace ani v případě, že použitá vazba je nakonfigurovaná tak, aby používala relace. Pokud více klientů provede volání do stejného objektu služby přes vazbu založenou na relaci a režim souběžnosti objektu služby je nastaven na hodnotu Single a kontextový režim instance je nastaven na `PerSession`, všechna volání musí projít kanálem datagramu a takže pouze jedno volání je zpracováváno v jednom okamžiku. Jeden nebo více klientů může vyprší časový limit. Tento problém můžete obejít tak, že nastavíte `InstanceContextMode` objektu služby na hodnotu `PerCall` nebo souběžnost na násobek.  
  
> [!NOTE]
> MaxConcurrentSessions se v tomto případě nijak neprojeví, protože je k dispozici pouze jedna relace.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
