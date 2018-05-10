---
title: Použití relací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: da877568d5444ed9cfcf041adc378f7fc95cb774
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="using-sessions"></a>Použití relací
V aplikacích Windows Communication Foundation (WCF) *relace* korelaci skupinu zpráv k konverzaci. WCF relací se liší od k dispozici v objektu session [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikace, podporují různé chování a jsou ovládaná různými způsoby. Toto téma popisuje funkce, které umožňují relací ve WCF aplikací a jejich použití.  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Relace v aplikacích Windows Communication Foundation  
 Při kontrakt služby specifikuje, že vyžaduje relaci, je této smlouvy určující, zda všechna volání (který je základní výměny zpráv podporující volání) musí být součástí stejné konverzaci. Pokud kontrakt Určuje, že umožňuje relace, ale nevyžaduje jeden, klienti mohou připojit a buď vytvořit relaci nebo není vytvořit relaci. Pokud relace skončí a je odeslána zpráva prostřednictvím stejného kanálu, který je vyvolána výjimka.  
  
 Relace WCF mají následující hlavní koncepční funkce:  
  
-   Jsou explicitně iniciované a ukončila příkazem volající aplikace (klienta WCF).  
  
-   Zpráv doručených během relace se zpracovávají v pořadí, ve kterém jsou přijaty.  
  
-   Relace korelovat skupinu zpráv k konverzaci. Různé typy korelace je možné. Jeden kanál na bázi relace, například mohou souviset zprávy založené na sdílené síťové připojení, zatímco jiné kanál na bázi relací, mohou souviset zprávy založené na značku sdílené v textu zprávy. Funkce, které může být odvozen z relace závisí na povaze korelaci.  
  
-   Neexistuje obecné datové úložiště přidružené k relaci WCF.  
  
 Pokud jste se seznámili s <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> třídy v [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikace a funkce, poskytuje, můžete si všimnout, následující rozdíly mezi tento druh relace a WCF relace:  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] relace jsou vždy iniciovaných serverem.  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] jsou implicitně neuspořádaný relace.  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] relace poskytují mechanismus obecné datové úložiště napříč požadavky.  
  
 Toto téma popisuje:  
  
-   Výchozí chování při spuštění při použití vazby na bázi relace v vrstva modelu služby.  
  
-   Typy funkcí, které poskytují vazby WCF na bázi relací, poskytované systémem.  
  
-   Postup vytvoření kontraktu, který deklaruje požadavek relace.  
  
-   Jak pochopit a řídí vytváření a ukončení relace a vztah relace v instanci služby.  
  
## <a name="default-execution-behavior-using-sessions"></a>Výchozí provádění chování pomocí relace  
 Je volána vazbu, která se pokusí o zahájení relace *na bázi relací* vazby. Kontrakty služeb uvést, že budou vyžadovat, povolit nebo odmítnout na bázi relací vazby nastavením <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnost u rozhraní kontraktu služby (nebo třída) do jednoho z <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> hodnot výčtu. Výchozí hodnota této vlastnosti je <xref:System.ServiceModel.SessionMode.Allowed>, což znamená, že pokud klient používá vazbu na bázi relace s implementaci služby WCF, služba vytváří a používá zadané relace.  
  
 Pokud služby WCF přijímá klientské relace, jsou ve výchozím nastavení povoleny tyto funkce:  
  
1.  Všechna volání mezi objekt klienta WCF jsou zpracovávány stejnou instanci služby.  
  
2.  Různé vazby na bázi relací poskytují další funkce.  
  
## <a name="system-provided-session-types"></a>Typy relace poskytované systémem  
 Vazba na bázi relací podporuje přidružení výchozí instanci služby s konkrétní relací. Různé vazby na bázi relací však podporují různé funkce kromě povolení na bázi relací zřizování instancí řízení popsaných výše.  
  
 WCF poskytuje následující typy chování na základě relace aplikace:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> Podporuje zabezpečení na základě relací, ve kterých obou konců komunikace uzavřeli na konkrétní zabezpečenou konverzaci. Další informace najdete v tématu [zabezpečení služby](../../../docs/framework/wcf/securing-services.md). Například <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> vazby, který obsahuje podporu pro zabezpečení relací a spolehlivé relace, ve výchozím nastavení používá jenom zabezpečené relace, který šifruje a digitálně podepíše zprávy.  
  
-   <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> Vazba podporuje založené na protokolu TCP relací zajistit, že jsou všechny zprávy korelační připojení na úrovni soketu.  
  
-   <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> Element, který implementuje specifikace protokolu WS-ReliableMessaging, poskytuje podporu pro spolehlivé relace, ve kterých je možné nakonfigurovat zprávy na doručit v pořadí a přesně po zajištění i v případě, že zprávy při přenosu jsou přijaty zprávy. mezi několika uzly během konverzace. Další informace najdete v tématu [spolehlivé relace](../../../docs/framework/wcf/feature-details/reliable-sessions.md).  
  
-   <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> Vazby poskytuje relací datagram MSMQ. Další informace najdete v tématu [fronty ve WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
 Nastavení <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> vlastnost neurčuje typ relace kontrakt vyžaduje, jen to vyžaduje jeden.  
  
## <a name="creating-a-contract-that-requires-a-session"></a>Vytvoření kontraktu, která vyžaduje relaci  
 Vytvoření kontraktu, která vyžaduje že relaci tvrdí, že skupině operací, které kontrakt služby deklaruje všechny se provedou v rámci stejné relace a že zprávy musí být dodávány v určitém pořadí. K vyhodnocení úroveň podpory relace, která vyžaduje kontraktu služby, nastavte <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> vlastnost na rozhraní kontraktu služby nebo třída na hodnotu <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> výčtu k určení zda kontrakt:  
  
-   Vyžaduje relaci.  
  
-   Umožňuje vytvořit relaci klienta.  
  
-   Zakáže relaci.  
  
 Nastavení <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> vlastnost však neurčuje typ chování na základě relace vyžaduje kontrakt. Se dá pokyn WCF potvrďte za běhu, nakonfigurované (která vytvoří komunikační kanál) pro službu nemá, neexistuje nebo můžete vytvořit relaci při implementaci služby. Znovu, vazba může stát odpovědí na tento požadavek s žádným typem relace na základě chování zvolí – zabezpečení, přenos, spolehlivé nebo jejich kombinaci. Přesný postup závisí na <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> hodnota vybraná. Pokud je nakonfigurovaná vazba služby neodpovídá hodnotě <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>, je vyvolána výjimka. Vazby a kanály vytvoří že relací podpory se říká, že na bázi relací.  
  
 Následující kontrakt služby určuje, že všechny operace v `ICalculatorSession` musí být vyměňují v rámci relace. Žádná z operací vrací hodnotu volajícího s výjimkou `Equals` metoda. Ale `Equals` metoda nepřijímá žádné parametry a proto může vrátit pouze nenulovou hodnotu v relaci, ve kterém data již byla předána dalších operací. Tato smlouva vyžaduje relaci fungovat správně. Bez relaci spojené s konkrétním klientovi instance služby nemá možnost nijak zjistit, jaká předchozí data odeslal tohoto klienta.  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 Pokud služba umožňuje relaci, pak relace je vytvořit a použít, pokud klient zahájí jeden; jinak není třeba vytvořit relaci.  
  
## <a name="sessions-and-service-instances"></a>Relace a instance služby  
 Pokud chcete použít výchozí chování v WCF vytváření instancí, všechna volání mezi objekt klienta WCF zpracovává stejnou instanci služby. Proto na úrovni aplikace, si můžete představit jako povolení chování aplikace, podobně jako místní volání chování relace. Když například vytvoříte místní objekt:  
  
-   Konstruktor je volána.  
  
-   Zpracovává všechny následné volání do odkaz na objekt klienta WCF na stejnou instanci objektu.  
  
-   Destruktor je volána, když je zničen odkaz na objekt.  
  
 Relace povolit podobné chování mezi klienty a služby, pokud se používá výchozí chování instance služby. Pokud kontraktu služby vyžaduje nebo podporuje relací, jednu nebo více operací kontrakt může být označen jako inicializaci nebo ukončení relace nastavením <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> a <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> vlastnosti.  
  
 *Spouštění operací* jsou ty, které musí být voláno jako první operace novou relaci. Inicializaci jiné operace lze volat pouze po nejméně jednu operaci Inicializace byla volána. Proto můžete vytvořit druh relace konstruktor pro vaši službu deklarováním inicializace operace, které jsou navržené tak, aby vstupní od klientů, které jsou vhodné pro začátek instance služby. (Stav je přidružené k této relaci, ale a není objekt služby).  
  
 *Ukončení operací*, naopak jsou ty, které musí být volána jako poslední zprávy v existující relaci. V případě výchozí WCF recykluje objektu služby a jeho kontextu po uzavření relace, ke kterému se vztahovaly službu. Proto můžete vytvořit druh – destruktor deklarováním ukončující operations navržený tak, aby vykonávat funkci odpovídající konci instance služby.  
  
> [!NOTE]
>  I když výchozí chování nenese podobný místní konstruktory a destruktory, je pouze podobají. Všechny operace služby WCF může být inicializaci nebo ukončování operace nebo oba ve stejnou dobu. Kromě toho v případě výchozí spouštění operací lze volat libovolný počet časy v libovolném pořadí; žádné další relace jsou vytvořeny po vytvoření a přidružené instance, pokud explicitně řídí životnost instance služby relace (manipulací <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> objekt). Nakonec stav je přidružena k relaci a není objektu služby.  
  
 Například `ICalculatorSession` smlouvy používat v předchozím příkladu vyžaduje, aby klienta WCF objektu první volání `Clear` operace před všechny ostatní operace a zda relace s tímto objektem klienta WCF by měl ukončí při volání `Equals` operaci. Následující příklad kódu ukazuje kontrakt, který vynucuje tyto požadavky. `Clear` musí být nejdříve volána k zahájení relace, a že ukončení relace při `Equals` je volána.  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 Služby nelze spustit relace s klienty. V klientských aplikací WCF existuje přímou relaci mezi životnost kanál na bázi relací a doba platnosti relace, sám sebe. Klienti jako takový vytvořit nové relace vytvářejí nové kanály na bázi relací a přerušit existující relace řádně ukončením relace na základě kanály. Klient spustí relaci s koncového bodu služby voláním jednu z těchto možností:  
  
-   <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> na kanálu vrácený volání <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> na objekt klienta WCF vygenerované [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
-   Operace inicializace na buď typ objektu klienta WCF (ve výchozím nastavení, jsou všechny operace inicializace). Při první operace je volána, objekt klienta WCF automaticky otevře kanál a inicializuje relaci.  
  
 Klient obvykle ukončí relaci s koncového bodu služby voláním jednu z těchto možností:  
  
-   <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> na kanálu vrácený volání <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> na objekt klienta WCF generované Svcutil.exe.  
  
-   Ukončování operace na buď typ objektu klienta WCF (ve výchozím nastavení, jsou žádné operace ukončení; kontrakt nutné explicitně zadat ukončování operace). Při první operace je volána, objekt klienta WCF automaticky otevře kanál a inicializuje relaci.  
  
 Příklady najdete v tématu [postupy: vytváření služby, vyžaduje relací](../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md) společně s [výchozí chování služby](../../../docs/framework/wcf/samples/default-service-behavior.md) a [Instancing](../../../docs/framework/wcf/samples/instancing.md) ukázky.  
  
 Další informace o klientech a relací najdete v tématu [přístup k službám pomocí klienta WCF](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Relace interakci s InstanceContext nastavení  
 Je interakci mezi <xref:System.ServiceModel.SessionMode> výčet ve kontraktu a <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnosti, která řídí přidružení mezi kanály a objekty konkrétní služby. Další informace najdete v tématu [relací, Instancing a souběžnost](../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md).  
  
### <a name="sharing-instancecontext-objects"></a>Sdílení InstanceContext objekty  
 Můžete taky řídit, které na bázi relací kanál nebo volání je přidružen který <xref:System.ServiceModel.InstanceContext> objektu tak, že provedete toto přidružení sami. Úplný příklad najdete v tématu [InstanceContextSharing](http://msdn.microsoft.com/library/4a6a46d7-b7d7-4bb5-a0dd-03ffa3cbc230).  
  
## <a name="sessions-and-streaming"></a>Relace a vysílání datového proudu  
 Když máte velké množství dat pro přenos, streamování režim přenosu ve WCF je to vhodné alternativa k výchozí chování ukládání do vyrovnávací paměti a zpracování zpráv v paměti jako celek. Při volání streamování s vazbou na bázi relací, může dojít k neočekávanému chování. Všechna volání streamování jsou provedeny prostřednictvím jednoho kanálu (kanál datagram), který nepodporuje relace, i v případě, že je vazba používá nakonfigurovaný na použití relací. Pokud více klientů volání streamování ke stejnému objektu služby přes vazbu na bázi relací a objektu služby souběžný režim je nastavena na jednou a jeho instance kontextu režim je nastaven `PerSession`, všechna volání musí procházet přes kanál datagram a tak najednou je zpracovat pouze jedno volání. Jeden nebo více klientů může pak vypršení časového limitu. Tento problém můžete vyřešit nastavením objektu služby `InstanceContextMode` k `PerCall` nebo souběžnosti násobek.  
  
> [!NOTE]
>  MaxConcurrentSessions mít žádný vliv v tomto případě, protože není k dispozici pouze jeden "relace".  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
