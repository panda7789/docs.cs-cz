---
title: Použití relací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: a879e90aeab7b40529df1f1a60cd1f879c39720a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143171"
---
# <a name="using-sessions"></a>Použití relací
V aplikacích Windows Communication Foundation (WCF) *relace* koreluje skupinu zpráv do konverzace. WCF relace se liší od objektu relace k dispozici v ASP.NET aplikacích, podporují různé chování a jsou řízeny různými způsoby. Toto téma popisuje funkce, které relace povolit v aplikacích WCF a jak je používat.  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Relace v aplikacích Windows Communication Foundation  
 Pokud smlouva o poskytování služeb určuje, že vyžaduje relaci, tato smlouva určuje, že všechna volání (to znamená, že základní zprávy výměny, které podporují volání) musí být součástí stejné konverzace. Pokud smlouva určuje, že umožňuje relace, ale nevyžaduje ji, klienti se mohou připojit a buď vytvořit relaci nebo nenařídit relaci. Pokud relace skončí a zpráva je odeslána prostřednictvím stejného kanálu je vyvolána výjimka.  
  
 Relace WCF mají následující hlavní koncepční funkce:  
  
- Jsou explicitně iniciovány a ukončeny volající aplikací (klientwcf).  
  
- Zprávy doručené během relace jsou zpracovány v pořadí, ve kterém jsou přijímány.  
  
- Relace korelují skupinu zpráv do konverzace. Různé typy korelace jsou možné. Jeden kanál založený na relaci může například korelovat zprávy založené na sdíleném síťovém připojení, zatímco jiný kanál založený na relaci může korelovat zprávy na základě sdílené značky v textu zprávy. Funkce, které lze odvodit z relace závisí na povaze korelace.  
  
- Neexistuje žádné obecné úložiště dat přidružené k relaci WCF.  
  
 Pokud jste obeznámeni <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> s třídou v ASP.NET aplikacích a funkce, které poskytuje, můžete si všimnout následující rozdíly mezi tento druh relace a WCF relací:  
  
- ASP.NET relací jsou vždy inicializovány serverem.  
  
- ASP.NET relace jsou implicitně neuspořádané.  
  
- ASP.NET relace poskytují obecný mechanismus ukládání dat napříč požadavky.  
  
 Toto téma popisuje:  
  
- Výchozí chování spuštění při použití vazeb založených na relaci ve vrstvě modelu služby.  
  
- Typy funkcí, které poskytují vazby založené na relaci WCF, poskytované systémem.  
  
- Jak vytvořit smlouvu, která deklaruje požadavek relace.  
  
- Jak porozumět a řídit vytvoření a ukončení relace a vztah relace k instanci služby.  
  
## <a name="default-execution-behavior-using-sessions"></a>Výchozí chování spuštění pomocí relací  
 Vazba, která se pokouší zahájit relaci, se nazývá *vazba založená na relaci.* Servisní smlouvy určují, že vyžadují, povolují nebo <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> odmítají vazby založené na relaci nastavením <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> vlastnosti v rozhraní servisní smlouvy (nebo třídě) na jednu z hodnot výčtu. Ve výchozím nastavení je <xref:System.ServiceModel.SessionMode.Allowed>hodnota této vlastnosti , což znamená, že pokud klient používá vazbu založenou na relaci s implementací služby WCF, služba vytvoří a použije poskytnutou relaci.  
  
 Pokud služba WCF přijímá relaci klienta, jsou ve výchozím nastavení povoleny následující funkce:  
  
1. Všechna volání mezi objektem klienta WCF jsou zpracována stejnou instancí služby.  
  
2. Různé vazby založené na relaci poskytují další funkce.  
  
## <a name="system-provided-session-types"></a>Typy relací poskytované systémem  
 Vazba založená na relaci podporuje výchozí přidružení instance služby s určitou relací. Různé vazby založené na relaci však podporují různé funkce kromě povolení ovládacího prvku instance založenéna relace, který byl popsán dříve.  
  
 WCF poskytuje následující typy chování aplikací založených na relaci:  
  
- Podporuje <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> relace založené na zabezpečení, ve kterých se oba konce komunikace dohodly na konkrétní zabezpečené konverzaci. Další informace naleznete [v tématu Zabezpečení služeb](securing-services.md). Například vazba, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> která obsahuje podporu pro relace zabezpečení a spolehlivé relace, ve výchozím nastavení používá pouze zabezpečenou relaci, která šifruje a digitálně podepisuje zprávy.  
  
- Vazba <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> podporuje relace založené na protokolu TCP/IP, aby bylo zajištěno, že všechny zprávy jsou korelovány připojením na úrovni soketu.  
  
- Prvek, <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> který implementuje ws spolehlivé zasílání zpráv specifikace, poskytuje podporu pro spolehlivé relace, ve kterých zprávy lze nakonfigurovat tak, aby byly doručeny v pořadí a přesně jednou, zajištění zprávy jsou přijímány i v případě, že zprávy cestují přes více uzlů během konverzace. Další informace naleznete v [tématu Spolehlivé relace](./feature-details/reliable-sessions.md).  
  
- Vazba <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> poskytuje relace datagramu msmq. Další informace naleznete [v tématu Fronty v WCF](./feature-details/queues-in-wcf.md).  
  
 Nastavení <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> vlastnosti neurčuje typ relace, kterou smlouva vyžaduje, pouze to, že ji vyžaduje.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Vytvoření smlouvy, která vyžaduje relaci  
 Vytvoření smlouvy, která vyžaduje relace uvádí, že skupina operací, které smlouva o poskytování služeb deklaruje, musí být všechny provedeny v rámci stejné relace a že zprávy musí být doručeny v pořadí. Chcete-li uplatnit úroveň podpory relace, kterou <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> servisní smlouva vyžaduje, nastavte vlastnost rozhraní <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> servisní smlouvy nebo třídy na hodnotu výčtu a určete, zda je smlouva:  
  
- Vyžaduje relaci.  
  
- Umožňuje klientovi vytvořit relaci.  
  
- Zakazuje relaci.  
  
 Nastavení <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> vlastnosti však neurčuje typ chování založeného na relaci, které smlouva vyžaduje. Dává pokyn WCF potvrdit za běhu, že nakonfigurovaná vazba (která vytvoří komunikační kanál) pro službu nemá, není nebo může vytvořit relaci při implementaci služby. Opět vazba může splňovat tento požadavek s libovolným typem chování na základě relace, které zvolí – zabezpečení, přenos, spolehlivé nebo nějakou kombinaci. Přesné chování závisí <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> na vybrané hodnotě. Pokud nakonfigurovaná vazba služby <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>neodpovídá hodnotě aplikace , je vyvolána výjimka. Vazby a kanály, které vytvářejí, které podporují relace jsou řekl, aby relace založené.  
  
 Následující servisní smlouva určuje, že `ICalculatorSession` všechny operace v rámci musí být vyměněny v rámci relace. Žádná z operací vrátí hodnotu volajícímu s výjimkou `Equals` metody. `Equals` Metoda však nepřebírá žádné parametry a proto může vrátit pouze nenulovou hodnotu uvnitř relace, ve které již byla data předána ostatním operacím. Tato smlouva vyžaduje relaci správně fungovat. Bez relace přidružené k určitému klientovi nemá instance služby žádný způsob, jak zjistit, jaká předchozí data tento klient odeslal.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Pokud služba umožňuje relaci, je relace vytvořena a použita, pokud ji klient iniciuje; v opačném případě není vytvořena žádná relace.  
  
## <a name="sessions-and-service-instances"></a>Relací a instance služeb  
 Pokud použijete výchozí instance chování wcf, všechna volání mezi objektem klienta WCF jsou zpracovány stejnou instanci služby. Proto na úrovni aplikace si můžete myslet relace jako povolení chování aplikace podobné chování místní volání. Například při vytváření místního objektu:  
  
- Konstruktor se nazývá.  
  
- Všechna následná volání odkaz na objekt klienta WCF jsou zpracována stejnou instancí objektu.  
  
- Destruktor je volána při zničení odkazu na objekt.  
  
 Relace povolit podobné chování mezi klienty a službami tak dlouho, dokud je použito výchozí instance služby chování. Pokud servisní smlouva vyžaduje nebo podporuje relace, jeden nebo více operací smlouvy lze označit <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> jako zahájení nebo ukončení relace nastavením vlastnosti a.  
  
 *Zahajující operace* jsou ty, které musí být volány jako první operace nové relace. Nezahajující operace lze volat pouze po volání alespoň jedné zahajovací operace. Proto můžete vytvořit druh konstruktoru relace pro vaši službu deklarováním iniciačních operací navržených tak, aby přejíměly vstup od klientů odpovídajících začátku instance služby. (Stav je však přidružen k relaci a nikoli k objektu služby.)  
  
 *Ukončující operace*, naopak, jsou ty, které musí být volány jako poslední zprávy v existující relaci. Ve výchozím případě WCF recykluje objekt služby a jeho kontext po ukončení relace, ke které byla služba přidružena. Proto můžete vytvořit druh destruktoru deklarováním ukončujících operací určených k provedení funkce odpovídající konci instance služby.  
  
> [!NOTE]
> Přestože výchozí chování nese podobnost s místní konstruktory a destruktory, je to jen podobnost. Všechny operace služby WCF může být zahájení nebo ukončení operace nebo obojí současně. Kromě toho ve výchozím případě zahájení operace lze volat libovolný počet opakování v libovolném pořadí; žádné další relace jsou vytvořeny po vytvoření relace a přidružené k instanci, pokud explicitně řídit životnost instance služby (manipulací s objektem). <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> Nakonec je stav přidružen k relaci a nikoli k objektu služby.  
  
 Například `ICalculatorSession` smlouva použitá v předchozím příkladu vyžaduje, aby objekt `Clear` klienta WCF nejprve zavolal operaci před jakoukoli jinou operací `Equals` a že relace s tímto objektem klienta WCF by měla být ukončena při volání operace. Následující příklad kódu ukazuje smlouvu, která vynucuje tyto požadavky. `Clear`musí být volána jako první, aby `Equals` zahájila relaci a tato relace končí, když je volána.  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Služby nespouštějí relace s klienty. V klientských aplikacích WCF existuje přímý vztah mezi životností kanálu založeného na relaci a životností samotné relace. Jako takové klienti vytvořit nové relace vytvořením nové kanály založené na relacích a strhnout existující relace tím, že zavřekanály založené na relacích ladem. Klient spustí relaci s koncovým bodem služby voláním jedné z následujících:  
  
- <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType>na kanálu vráceném <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>voláním na .  
  
- <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>na objektu klienta WCF generované [servicemodel metadata utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
- Inicializační operace na obou typech objektu klienta WCF (ve výchozím nastavení jsou všechny operace inicializační). Při volání první operace objekt klienta WCF automaticky otevře kanál a zahájí relaci.  
  
 Klient obvykle ukončí relaci koncovým bodem služby voláním jedné z následujících akcí:  
  
- <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>na kanálu vráceném <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>voláním na .  
  
- <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>na objektu klienta WCF generovanésvcutil.exe.  
  
- Ukončující operace na obou typech objektu klienta WCF (ve výchozím nastavení žádné operace jsou ukončovány; smlouva musí explicitně určit ukončující operaci). Při volání první operace objekt klienta WCF automaticky otevře kanál a zahájí relaci.  
  
 Příklady naleznete v [tématu How to: Create a Service that Requires Sessions](./feature-details/how-to-create-a-service-that-requires-sessions.md) as the Default Service [Behavior](./samples/default-service-behavior.md) and [Instancing](./samples/instancing.md) samples.  
  
 Další informace o klientech a relacích naleznete [v tématu Přístup ke službám pomocí klienta WCF](./feature-details/accessing-services-using-a-client.md).  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Interakce relací s nastavením instancekontextu  
 Existuje interakce mezi <xref:System.ServiceModel.SessionMode> výčet ve smlouvě a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost, která řídí přidružení mezi kanály a konkrétní objekty služby. Další informace naleznete [v tématu Relace, Instance a Souběžnost](./feature-details/sessions-instancing-and-concurrency.md).  
  
### <a name="sharing-instancecontext-objects"></a>Sdílení objektů InstanceContext  
 Můžete také určit, který kanál nebo volání <xref:System.ServiceModel.InstanceContext> založené na relaci je přidruženo k jakému objektu, provedením tohoto přidružení sami.
  
## <a name="sessions-and-streaming"></a>Relace a streamování  
 Pokud máte velké množství dat k přenosu, režim přenosu datových proudů v WCF je proveditelnou alternativou k výchozí chování ukládání do vyrovnávací paměti a zpracování zpráv v paměti v plném rozsahu. Při streamování volání pomocí vazby založené na relaci může dojít k neočekávanému chování. Všechna volání streamování jsou prováděny prostřednictvím jednoho kanálu (kanál datagram), který nepodporuje relace i v případě, že se používá vazba je nakonfigurován pro použití relací. Pokud více klientů provádět volání streamování stejného objektu služby přes vazby založené na relaci a režim souběžnosti `PerSession`objektu služby je nastavena na jednu a jeho instance kontextový režim je nastavena na , všechna volání musí projít kanálem datagram a tak pouze jedno volání je zpracována současně. Jeden nebo více klientů pak může časový mzda. Tento problém můžete vyřešit nastavením objektu `InstanceContextMode` `PerCall` služby nebo souběžnosti na více.  
  
> [!NOTE]
> MaxConcurrentSessions nemají žádný vliv v tomto případě, protože je k dispozici pouze jedna "relace".  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
