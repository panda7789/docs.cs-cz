---
title: Použití relací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: 898e5688ae08a59415c8b3116665eec6cb4cf904
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877372"
---
# <a name="using-sessions"></a>Použití relací
V aplikacích Windows Communication Foundation (WCF) *relace* koreluje skupinu zpráv do konverzace. Relace WCF se liší od objekt relace, která je k dispozici v [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikace podporují různé chování a se řídí různými způsoby. Toto téma popisuje funkce, které umožňují relace ve službě WCF aplikací a jejich použití.  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Relace v aplikacích Windows Communication Foundation  
 Pokud kontrakt služby specifikuje, že vyžaduje relaci, zda kontrakt je určení, že všechna volání (to znamená, základní výměny zpráv, které podporují volání) musí být součástí stejné konverzaci. Pokud kontrakt Určuje, že umožňuje relace, ale nevyžaduje, aby jeden, klienti můžou připojit a buď vytvořit relaci nebo nelze navázat relaci. Pokud relace skončí a zpráva se odesílá prostřednictvím stejné kanál, který je vyvolána výjimka.  
  
 Relace WCF mají koncepční následující hlavní funkce:  
  
-   Jsou explicitně zahájeno a ukončeno volající aplikace (klient WCF).  
  
-   Zprávy doručí během relace se zpracovávají v pořadí, ve kterém jsou přijímány.  
  
-   Relace je možné korelovat skupinu zpráv do konverzace. Různé druhy korelace jsou možné. Například jeden kanál na základě relace mohou souviset zprávy založen na sdílených síťových připojení jiného kanálu založeného na relacích mohou souviset zprávy na základě sdílené značky v textu zprávy. Funkce, které mohou být odvozeny z relace závisí na povaze korelace.  
  
-   Neexistuje žádné úložiště obecná data související s relací WCF.  
  
 Pokud jste se seznámili s <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> třídy v [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] poskytuje aplikace a funkce, můžete si všimnout následující rozdíly mezi tento druh relace a relace WCF:  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] relace jsou vždy zahajované serverem.  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] relace jsou implicitně Neseřazený.  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] relace poskytují mechanismus pro ukládání obecná data napříč požadavky.  
  
 Toto téma popisuje:  
  
-   Výchozí spuštění chování při používání vazeb na základě relace v vrstva modelu služby.  
  
-   Typy funkcí, které poskytují vazby WCF na základě relace, poskytované systémem.  
  
-   Postup vytvoření kontrakt, který deklaruje požadavek relace.  
  
-   Jak pochopit a řídit vytváření a ukončení relace a relace relace v instanci služby.  
  
## <a name="default-execution-behavior-using-sessions"></a>Výchozí spuštění chování pomocí relace  
 Je volána vazbu, která se pokusí o zahájení relace *založeného na relacích* vazby. Kontrakty služeb zadat, že se vyžadují, povolit nebo odmítnout založeného na relacích vazby tak, že nastavíte <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnosti rozhraní kontraktu služby (nebo třídy) do jednoho z <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> hodnot výčtu. Výchozí hodnota této vlastnosti je <xref:System.ServiceModel.SessionMode.Allowed>, což znamená, že pokud klient používá vazbu na základě relace s implementací služby WCF, služba vytvoří a používá poskytnutou relaci.  
  
 Když služba WCF přijímá klientské relace, jsou ve výchozím nastavení povoleny následující funkce:  
  
1.  Všechna volání mezi objekt klienta WCF jsou zpracovávány stejné instance služby.  
  
2.  Různé na základě relace vazby poskytují další funkce.  
  
## <a name="system-provided-session-types"></a>Typy poskytované systémem relace  
 Vazba na základě relace podporuje výchozí přidružení instance služby s konkrétní relací. Různé na základě relace vazby však podporují různé funkce kromě povolení založeného na relacích vytvoření instance ovládacího prvku popsaných výše.  
  
 WCF poskytuje následující typy chování na základě relace aplikace:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> Podporuje zabezpečení na základě relací, ve kterých oba konce komunikace dohodnutých konkrétní zabezpečené konverzace. Další informace najdete v tématu [zabezpečení služby](../../../docs/framework/wcf/securing-services.md). Například <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> vazby, který obsahuje podporu pro relace zabezpečení a spolehlivé relace, ve výchozím nastavení používá pouze zabezpečenou relaci, která šifruje a digitálně podepisuje zprávy.  
  
-   <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> Vazba podporuje relace založené na TCP/IP k zajištění, že všechny zprávy se korelují připojení na úrovni soketu.  
  
-   <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> Element, který implementuje specifikaci WS-ReliableMessaging, poskytuje podporu pro spolehlivé relace, ve kterých lze nakonfigurovat zprávy pro doručeny v pořadí a přesně jednou, zajištění jsou zprávy přijímány i v případě, že zprávy mezi více uzlů během konverzace. Další informace najdete v tématu [spolehlivé relace](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
-   <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> Vazby poskytuje relace datagramem MSMQ. Další informace najdete v tématu [fronty ve WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
 Nastavení <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> vlastnost neurčuje typ relace kontrakt vyžaduje, jenom se vyžaduje jednu.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Vytvoření smlouvy, která vyžaduje relaci  
 Vytvoření smlouvy, která vyžaduje že relaci hlásí, že skupiny operací, které deklaruje kontraktu služby se musí všechny provádět v rámci stejné relace se, že zprávy musí být dodávány v určitém pořadí. K vyhodnocení úrovně podporu relací, která vyžaduje kontraktu služby, nastavte <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnosti rozhraní kontraktu služby nebo třídy do hodnoty vlastnosti <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> výčet k určení, zda kontrakt:  
  
-   Vyžaduje relaci.  
  
-   Umožňuje klientům navázat relaci.  
  
-   Zakazuje relace.  
  
 Nastavení <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> vlastnosti však neurčuje typu založeného na relacích chování kontrakt vyžaduje. Nastaví WCF potvrďte za běhu, která nakonfigurovaná vazba (která vytvoří komunikační kanál) pro službu nemá, nikoli nebo můžete vytvořit relaci při implementaci služby. Znovu, lze vazbu splňují tento požadavek s žádným typem chování na základě relace zvolí – zabezpečení, přenosu, spolehlivým nebo jejich kombinaci. Přesné chování závisí <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> vybraná hodnota. Pokud nakonfigurovanou vazbu služby není v souladu s hodnotu <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>, je vyvolána výjimka. Vazby a kanály, které vytvářejí, že podpora relací se označují jako založeného na relacích.  
  
 Následující kontrakt služby specifikuje, že všechny operace `ICalculatorSession` musí bude vyměněn v rámci relace. Žádná z operací vrací hodnotu volajícímu s výjimkou `Equals` metody. Ale `Equals` metoda nepřijímá žádné parametry a proto může vrátit pouze nenulové hodnoty uvnitř relace, ve kterém datového již byl předán jiné operace. Tato smlouva vyžaduje relaci fungovat správně. Bez relace spojené s konkrétního klienta instance služby nemá možnost nijak zjistit, co předchozí data tohoto klienta odeslal.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Pokud služba umožňuje relaci, pak relace je vytvořeno a použít iniciuje-li klienta. v opačném případě není třeba vytvořit relaci.  
  
## <a name="sessions-and-service-instances"></a>Relace a instance služby  
 Pokud používáte výchozí chování ve službě WCF vytváření instancí, jsou všechna volání mezi objekt klienta WCF zpracovat stejné instance služby. Proto na úrovni aplikace si můžete představit jako povolení chování aplikace, podobně jako na místní volání chování relace. Když například vytvoříte místní objekt:  
  
-   Je volána konstruktor.  
  
-   Všechny následné volání odkaz na objekt klienta WCF jsou zpracovány stejná instance objektu.  
  
-   Destruktor se volá, když odkaz na objekt je zničen.  
  
 Relace povolit podobné chování mezi klienty a služby, tak dlouho, dokud se použije výchozí chování instance služby. Pokud kontrakt služby požaduje nebo podporuje relací, jednu nebo více operací smlouvy může být označený jako inicializace nebo ukončení relace tak, že nastavíte <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> a <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> vlastnosti.  
  
 *Zahajuje se operace* jsou ty, které musí být volána jako první operace novou relaci. Bez zahájení operace lze volat pouze po zavolání alespoň jednu operaci zahájil. Proto můžete vytvořit typ konstruktoru relace pro vaši službu deklarováním zahájení operace, které jsou navržené tak, aby vstupní od klientů, třeba na začátek instance služby. (Stav je přiřazený k této relaci, ale a nikoli objekt služby).  
  
 *Operace se ukončuje*, a naopak, jsou ty, které musí být volána jako poslední zprávy v existující relaci. Ve výchozím nastavení recykluje WCF objektu služby a její kontext po zavření relace, pomocí kterého byl k službě. Druh destruktor můžete vytvořit proto deklarováním ukončující operace lze provádět na konec instance služby příslušné funkce.  
  
> [!NOTE]
>  I když výchozí chování je velmi podobný místní konstruktory a destruktory, je pouze velmi podobný. Inicializaci ukončující operaci nebo obojí ve stejnou dobu může být žádné operaci služby WCF. Kromě toho ve výchozím nastavení, zahajuje se operace lze volat libovolný počet v libovolném pořadí; Vytvoří se žádné další relace, jakmile je vytvořeno a přidružené instance, pokud explicitně řídit dobu života instance služby relace (manipulací <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> objekt). A konečně stav je přidružená relace a nikoli objekt služby.  
  
 Například `ICalculatorSession` smlouva použitých v předchozím příkladu vyžaduje, že klient WCF objektu první volání `Clear` operaci před žádné jiné operace a že relace s tímto objektem klienta WCF by měla ukončit při volání `Equals` operace. Následující příklad kódu ukazuje kontrakt, který vynucuje tyto požadavky. `Clear` musí být nejdříve volána k zahájení relace, a že ukončení relace při `Equals` je volána.  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Služba spuštěna relace s klienty. V klientských aplikací WCF přímý vztah existuje mezi dobu platnosti kanálu založeného na relacích a životnost relace samotný. V důsledku toho klienti vytvoření nové relace tak, že vytvoříte nové kanály na základě relace a odstraňovat existující relace ukončením založeného na relacích kanály bez výpadku. Klient spustí relaci s koncovým bodem služby voláním jedné z následujících akcí:  
  
-   <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> na kanálu vrácené voláním <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> u objektu klienta WCF generovaných [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
-   Zahájení operace na buď typ objektu klienta WCF (ve výchozím nastavení, všechny operace iniciují). Při první operace je volána, objekt klienta WCF se automaticky otevře kanál a spustí relaci.  
  
 Obvykle klient ukončí relaci s koncovým bodem služby voláním jedné z následujících akcí:  
  
-   <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> na kanálu vrácené voláním <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> u objektu klienta WCF generovaných Svcutil.exe.  
  
-   Ukončující operace na buď typ objektu klienta WCF (ve výchozím nastavení, se ukončuje žádné operace, kontrakt musíte explicitně zadat ukončující operace). Při první operace je volána, objekt klienta WCF se automaticky otevře kanál a spustí relaci.  
  
 Příklady najdete v tématu [postupy: vytváření služba, vyžaduje relací](../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md) také [výchozí chování služby](../../../docs/framework/wcf/samples/default-service-behavior.md) a [Instancing](../../../docs/framework/wcf/samples/instancing.md) ukázky.  
  
 Další informace o klientech a relace najdete v tématu [přístup ke službám pomocí klienta WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Relace interakci s InstanceContext nastavení  
 Je interakce mezi <xref:System.ServiceModel.SessionMode> výčtu v kontraktu a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost, která řídí přidružení mezi kanály a konkrétní objekty. Další informace najdete v tématu [relací, Instancing a souběžnosti](../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md).  
  
### <a name="sharing-instancecontext-objects"></a>Třída InstanceContext objekty pro sdílení obsahu  
 Můžete taky řídit, které využívají relace kanálu nebo volání je přidružený k který <xref:System.ServiceModel.InstanceContext> objektu pomocí provádí toto přidružení se sami. Kompletní příklad naleznete v tématu [InstanceContextSharing](https://msdn.microsoft.com/library/4a6a46d7-b7d7-4bb5-a0dd-03ffa3cbc230).  
  
## <a name="sessions-and-streaming"></a>Relace a streamování  
 Pokud máte velký objem přenášených dat, je režim tvorby datového proudu přenosu ve službě WCF proveditelné alternativou k výchozí chování ukládání do vyrovnávací paměti a zpracování zpráv v paměti jako celek. Můžete obdržet neočekávané chování při streamování volání s vazbou na základě relace. Všechna volání streamování se provádějí přes jeden kanál (kanálu datagramu), který nepodporuje relace, i v případě, že vazba používá je nakonfigurována pro použití relací. Pokud více klientů volání datových proudů na stejný objekt služby přes vazbu na základě relace, a objekt služby souběžný režim je nastavena na jednou a jeho režimu instance kontextu je nastavena na `PerSession`, kanálu datagramu a proto musí projít všechna volání současně je zpracována pouze jedno volání. Jeden nebo více klientů může potom vypršení časového limitu. Tento problém můžete obejít tak, že nastavíte objekt služby `InstanceContextMode` k `PerCall` nebo souběžnost více.  
  
> [!NOTE]
>  MaxConcurrentSessions nemají žádný vliv v tomto případě, protože není k dispozici pouze jeden "relace".  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
