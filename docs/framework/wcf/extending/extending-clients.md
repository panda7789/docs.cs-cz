---
title: Rozšíření klientů
ms.date: 03/30/2017
helpviewer_keywords:
- proxy extensions [WCF]
ms.assetid: 1328c61c-06e5-455f-9ebd-ceefb59d3867
ms.openlocfilehash: 91277e1a4d0a1d001d62d677dbd087bec5d875f0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797160"
---
# <a name="extending-clients"></a>Rozšíření klientů
V rámci volající aplikace je vrstva modelu služby odpovědná za překlad volání metod v kódu aplikace do odchozích zpráv, jejich vložení do základních kanálů a jejich posunutí zpět na vrácené hodnoty a výstupní parametry v kód aplikace a vrácení výsledků zpět volajícímu. Rozšíření modelu služby upraví nebo implementují chování nebo chování komunikace a funkce zahrnující funkce klienta nebo dispečera, vlastní chování, zachycení zprávy a parametry a další funkce rozšíření.  
  
 Toto téma popisuje, jak použít <xref:System.ServiceModel.Dispatcher.ClientRuntime> třídy a <xref:System.ServiceModel.Dispatcher.ClientOperation> v klientské aplikaci Windows Communication Foundation (WCF) k úpravě výchozího chování spuštění klienta WCF nebo k zachycení nebo úpravě zpráv, parametrů nebo vrácených hodnot. před odesláním nebo následným odesláním nebo po jeho načtení z vrstvy kanálu. Další informace o rozšíření modulu runtime služby najdete v tématu [rozšíření expedičních](extending-dispatchers.md)modulů. Další informace o chování při úpravách a vkládání objektů přizpůsobení do modulu runtime klienta najdete v tématu [Konfigurace a rozšíření modulu runtime s chováním](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="clients"></a>Klienti  
 V klientovi klientský objekt WCF nebo klientský kanál převede volání metod do odchozích zpráv a příchozí zprávy do výsledků operací, které se vrátí do volající aplikace. (Další informace o typech klientů najdete v tématu [Architektura klienta WCF](../feature-details/client-architecture.md).)  
  
 Typy klientů WCF mají běhové typy, které zpracovávají tuto funkci koncového bodu a na úrovni provozu. Když aplikace zavolá operaci, <xref:System.ServiceModel.Dispatcher.ClientOperation> přeloží odchozí objekty do zprávy, procesy procesů, potvrdí, že odchozí volání odpovídá cílové smlouvě, a předá odchozí zprávu <xref:System.ServiceModel.Dispatcher.ClientRuntime>na, což je zodpovídá za vytváření a správu odchozích kanálů (a příchozích kanálů v případě duplexních služeb), zpracovávání dalších odchozích zpráv (například úpravy hlaviček), zpracování zachycených zpráv v obou směrech a příchozí směrování. duplexní volání na příslušný objekt na straně <xref:System.ServiceModel.Dispatcher.DispatchRuntime> klienta. Jak a poskytují <xref:System.ServiceModel.Dispatcher.ClientRuntime> podobné služby, když jsou zprávy (včetně chyb) vraceny klientovi. <xref:System.ServiceModel.Dispatcher.ClientOperation>  
  
 Tyto dvě běhové třídy jsou hlavní rozšíření pro přizpůsobení zpracování objektů a kanálů klienta WCF. <xref:System.ServiceModel.Dispatcher.ClientRuntime> Třída umožňuje uživatelům zachytit a zvětšit spuštění klienta ve všech zprávách ve smlouvě. <xref:System.ServiceModel.Dispatcher.ClientOperation> Třída umožňuje uživatelům zachytit a zvětšit spuštění klienta pro všechny zprávy v dané operaci.  
  
 Úprava vlastností nebo vložení přizpůsobení se provádí pomocí chování kontraktu, koncového bodu a operace. Další informace o tom, jak použít tyto typy chování k provedení úprav modulu runtime klienta, najdete v tématu [Konfigurace a rozšíření modulu runtime s chováním](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="scenarios"></a>Scénáře  
 K dispozici je několik důvodů pro rozšiřování klientského systému, včetně:  
  
- Vlastní ověření zprávy Uživatel může chtít vyhovět, že je zpráva platná pro určité schéma. To lze provést implementací <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> rozhraní a přiřazením implementace <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A> do vlastnosti. Příklady naleznete v tématu [How to: Zkontrolujte nebo upravte zprávy na klientovi](how-to-inspect-or-modify-messages-on-the-client.md) a [postup: Zkontrolujte nebo upravte zprávy na klientovi](how-to-inspect-or-modify-messages-on-the-client.md).  
  
- Vlastní protokolování zpráv. Uživatel může chtít zkontrolovat a zaprotokolovat některé sady zpráv aplikace, které procházejí koncovým bodem. Můžete to také provést pomocí rozhraní pro zachycování zpráv.  
  
- Vlastní transformace zpráv Místo úprav kódu aplikace může uživatel chtít použít určité transformace na zprávu v modulu runtime (například pro správu verzí). To se dá provést znovu s rozhraními pro zachycování zpráv.  
  
- Vlastní datový model. Uživatel může chtít, aby model dat nebo serializace byl jiný než podporovaný standardně ve službě WCF (tj <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>., a <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> objekty). To lze provést implementací rozhraní formátovacích zpráv. Další informace naleznete v tématu <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType> a ve <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A?displayProperty=nameWithType> vlastnosti.  
  
- Ověřování vlastního parametru. Uživatel může chtít vyhovět tomu, že typové parametry jsou platné (na rozdíl od XML). To lze provést pomocí rozhraní Inspector pro parametry. Příklad naleznete v tématu [How to: Zkontrolujte nebo upravte parametry](how-to-inspect-or-modify-parameters.md) nebo [ověření klienta](../samples/client-validation.md).  
  
### <a name="using-the-clientruntime-class"></a>Použití třídy ClientRuntime  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime> Třída je bod rozšiřitelnosti, ke kterému můžete přidat objekty rozšíření, které zachycují zprávy, a rozšířit chování klienta. Objekty zachycení mohou zpracovávat všechny zprávy v konkrétní smlouvě, zpracovávat pouze zprávy pro konkrétní operace, provádět inicializaci vlastního kanálu a implementovat jiné vlastní chování klientské aplikace.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> Vlastnost vrací objekt run-time pro klienty zpětného volání iniciované službou.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.OperationSelector%2A> Vlastnost přijímá objekt výběru vlastní operace.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ChannelInitializers%2A> Vlastnost umožňuje přidání inicializátoru kanálu, který může kontrolovat nebo upravovat kanál klienta.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> Vlastnost získá<xref:System.ServiceModel.Dispatcher.ClientOperation> kolekci objektů, do kterých lze přidat vlastní zachycení zpráv, které poskytují funkce specifické pro zprávy této operace.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ManualAddressing%2A> Vlastnost umožňuje aplikaci vypnutí některých automatických hlaviček adresování, aby bylo možné přímo řídit adresování.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.Via%2A> Vlastnost nastavuje hodnotu cíle zprávy na úrovni přenosu pro podporu zprostředkovatelů a dalších scénářů.  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> Vlastnost získá<xref:System.ServiceModel.Dispatcher.IClientMessageInspector> kolekci objektů, do kterých můžete přidat vlastní zachycení zpráv pro všechny zprávy na cestách prostřednictvím klienta WCF.  
  
 Kromě toho existuje řada dalších vlastností, které načítají informace o kontraktu:  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractName%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractNamespace%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractClientType%2A>  
  
 Pokud je klient služby WCF duplexní klient služby WCF, následující vlastnosti také načtou informace o klientovi WCF zpětného volání:  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackClientType%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A>  
  
 Chcete-li rozšíření spustit klienta WCF v rámci celého klienta služby WCF, Projděte si <xref:System.ServiceModel.Dispatcher.ClientRuntime> vlastnosti, které jsou k dispozici ve třídě, abyste viděli, zda je změna vlastnosti nebo implementace rozhraní a přidání do vlastnosti vytvořena funkce, kterou hledáte. Po zvolení konkrétního rozšíření pro sestavení vložte rozšíření do příslušné <xref:System.ServiceModel.Dispatcher.ClientRuntime> vlastnosti implementací chování klienta, které poskytuje přístup <xref:System.ServiceModel.Dispatcher.ClientRuntime> ke třídě při vyvolání.  
  
 Můžete vložit vlastní objekty rozšíření do kolekce pomocí chování operace (objekt, který implementuje <xref:System.ServiceModel.Description.IOperationBehavior>), chování kontraktu (objekt, který implementuje <xref:System.ServiceModel.Description.IContractBehavior>) nebo chování koncového bodu (objekt, který implementuje <xref:System.ServiceModel.Description.IEndpointBehavior> ). Objekt chování při instalaci se přidá do příslušné kolekce chování programově, deklarativně (implementací vlastního atributu) nebo implementací vlastního <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> objektu, aby bylo možné chování vložit pomocí konfigurační soubor aplikace. Podrobnosti najdete v tématu [Konfigurace a rozšíření modulu runtime s chováním](configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Příklady, které ukazují zachycení napříč klientem WCF, naleznete v tématu [How to: Zkontrolujte nebo upravte zprávy na klientovi](how-to-inspect-or-modify-messages-on-the-client.md).  
  
### <a name="using-the-clientoperation-class"></a>Použití třídy třída ClientOperation  
 <xref:System.ServiceModel.Dispatcher.ClientOperation> Třída je umístěním pro změny v době běhu klienta a místo pro vložení vlastních rozšíření, která jsou vymezena pouze pro jednu operaci služby. (Chcete-li upravit chování klientského běhu pro všechny zprávy ve kontraktu, použijte <xref:System.ServiceModel.Dispatcher.ClientRuntime> třídu.)  
  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> Pomocí vlastnosti<xref:System.ServiceModel.Dispatcher.ClientOperation> vyhledejte objekt, který představuje konkrétní operaci služby. Následující vlastnosti umožňují vkládat vlastní objekty do systému klienta WCF:  
  
- Použijte vlastnost pro vložení vlastní <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementace pro operaci nebo změňte aktuální formátovací modul. <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A>  
  
- Tuto <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A> vlastnost použijte k vložení vlastní <xref:System.ServiceModel.Dispatcher.IParameterInspector> implementace nebo k úpravě aktuálního typu.  
  
 Následující vlastnosti umožňují změnit systém v interakci s formátovacími moduly a vlastními inspektory parametrů:  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.SerializeRequest%2A> Použijte vlastnost k řízení serializace odchozí zprávy.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.DeserializeReply%2A> Použijte vlastnost k řízení deserializace příchozí zprávy.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.Action%2A> Pomocí vlastnosti můžete řídit akci WS-Addressing zprávy s požadavkem.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.BeginMethod%2A> Pomocí a <xref:System.ServiceModel.Dispatcher.ClientOperation.EndMethod%2A> určete, které metody klienta WCF jsou přidruženy k asynchronní operaci.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.FaultContractInfos%2A> Vlastnost použijte k získání kolekce, která obsahuje typy, které se mohou objevit v chybách protokolu SOAP jako typ podrobností.  
  
- Pomocí vlastností <xref:System.ServiceModel.Dispatcher.ClientOperation.IsTerminating%2A> a můžete řídit, jestli je relace iniciovaná nebo je potrhané v uvedeném pořadí, když se zavolá operace. <xref:System.ServiceModel.Dispatcher.ClientOperation.IsInitiating%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.IsOneWay%2A> Pomocí vlastnosti můžete určit, zda je operace jednosměrnou operací.  
  
- Vlastnost použijte k získání objektu, který <xref:System.ServiceModel.Dispatcher.ClientRuntime> jej obsahuje. <xref:System.ServiceModel.Dispatcher.ClientOperation.Parent%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.Name%2A> Pomocí vlastnosti Získejte název operace.  
  
- <xref:System.ServiceModel.Dispatcher.ClientOperation.SyncMethod%2A> Použijte vlastnost k určení, která metoda je namapována na operaci.  
  
 Chcete-li rozšíření spouštění klienta služby WCF rozšíří pouze v rámci jedné operace služby, <xref:System.ServiceModel.Dispatcher.ClientOperation> zkontrolujte vlastnosti dostupné ve třídě, abyste viděli, zda upravujete vlastnost nebo implementujete rozhraní a přidáte ho do vlastnosti, která vytváří funkce, které hledáte. Po zvolení konkrétního rozšíření pro sestavení vložte rozšíření do příslušné <xref:System.ServiceModel.Dispatcher.ClientOperation> vlastnosti implementací chování klienta, které poskytuje přístup <xref:System.ServiceModel.Dispatcher.ClientOperation> ke třídě při vyvolání. V takovém případě <xref:System.ServiceModel.Dispatcher.ClientRuntime> můžete vlastnost upravit tak, aby vyhovovala vašim požadavkům.  
  
 Obvykle je implementováno chování operace (objekt, který implementuje <xref:System.ServiceModel.Description.IOperationBehavior> rozhraní), ale můžete také použít chování koncového bodu a chování kontraktu k tomu, abyste mohli dosáhnout stejného účelu <xref:System.ServiceModel.Description.OperationDescription> umístěním pro konkrétní operace a připojení chování. Podrobnosti najdete v tématu [Konfigurace a rozšíření modulu runtime s chováním](configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Chcete-li použít vlastní chování z konfigurace, nainstalujte své chování pomocí obslužné rutiny oddílu konfigurace vlastního chování. Chování můžete také nainstalovat vytvořením vlastního atributu.  
  
 Příklady, které ukazují zachycení napříč klientem WCF, naleznete v tématu [How to: Zkontrolujte nebo upravte parametry](how-to-inspect-or-modify-parameters.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Dispatcher.ClientRuntime>
- <xref:System.ServiceModel.Dispatcher.ClientOperation>
- [Postupy: Kontrola nebo úprava zpráv na klientovi](how-to-inspect-or-modify-messages-on-the-client.md)
- [Postupy: Kontrola nebo úprava parametrů](how-to-inspect-or-modify-parameters.md)
