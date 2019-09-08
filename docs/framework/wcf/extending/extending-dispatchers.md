---
title: Rozšíření dispečerů
ms.date: 03/30/2017
helpviewer_keywords:
- dispatcher extensions [WCF]
ms.assetid: d0ad15ac-fa12-4f27-80e8-7ac2271e5985
ms.openlocfilehash: 9250ca09fb5e28655e39f8d91d991fdb3bffcdbd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795744"
---
# <a name="extending-dispatchers"></a>Rozšíření dispečerů
Odesílatelé jsou odpovědni za příjem příchozích zpráv ze základních kanálů, jejich překlad na vyvolání metod v kódu aplikace a odeslání výsledků zpět volajícímu. Rozšíření dispečera umožňují upravit toto zpracování.  Můžete implementovat zprávy nebo inspektory parametrů, které kontrolují nebo mění obsah zpráv nebo parametrů.  Můžete změnit způsob, jakým jsou zprávy směrovány na operace, nebo poskytovat jiné funkce.

Toto téma popisuje, jak použít <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy a <xref:System.ServiceModel.Dispatcher.DispatchOperation> v aplikaci služby Windows Communication Foundation (WCF) pro úpravu výchozího chování dispečera nebo zachycení nebo změny zpráv, parametrů nebo vrácení. hodnoty před nebo po odeslání nebo jejich načtení z vrstvy kanálu. Další informace o ekvivalentním zpracování zpráv modulu runtime klienta najdete v tématu [rozšíření klientů](extending-clients.md). Pro pochopení role, kterou <xref:System.ServiceModel.IExtensibleObject%601> typy hrají při přístupu ke sdílenému stavu mezi různými objekty vlastního nastavení modulu runtime, se podívejte na téma [rozšiřitelné objekty](extensible-objects.md).

## <a name="dispatchers"></a>Dispečery

Vrstva modelu služby provádí převod mezi programovacím modelem vývojáře a základní výměnou zpráv, která se běžně označuje jako vrstva kanálu. V rámci WCF jsou odeslané kanály kanálu a koncového<xref:System.ServiceModel.Dispatcher.ChannelDispatcher> bodu <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>(a v uvedeném pořadí) komponenty služby zodpovědné za příjem nových kanálů, přijímání zpráv, odesílání a volání operací a zpracování odpovědí. Objekty dispečera jsou objekty přijímače, ale implementace kontraktu zpětného volání v duplexních službách také zveřejňují své objekty dispečera pro kontrolu, úpravy nebo rozšíření.

Dispečer kanálu (a doprovodný <xref:System.ServiceModel.Channels.IChannelListener>nástroj) vyžádá zprávy z kanálu identifikátor a předá zprávy příslušnému odesilateli koncových bodů. Každý dispečer koncového bodu <xref:System.ServiceModel.Dispatcher.DispatchRuntime> má a směruje zprávy na příslušné <xref:System.ServiceModel.Dispatcher.DispatchOperation>, což zodpovídá za volání metody, která implementuje operaci. Různé volitelné a požadované třídy rozšíření jsou vyvolány způsobem. V tomto tématu se dozvíte, jak se tyto části vejdou dohromady, a jak můžete upravit vlastnosti a zapojit vlastní kód v nástroji, aby se rozšířily základní funkce.

Vlastnosti dispečera a upravené objekty přizpůsobení jsou vloženy pomocí objektů služby, koncového bodu, kontraktu nebo chování operací. Toto téma nepopisuje použití chování. Další informace o typech použitých pro vložení úprav dispečera najdete v tématu [Konfigurace a rozšíření modulu runtime s chováním](configuring-and-extending-the-runtime-with-behaviors.md).

Následující obrázek poskytuje podrobný pohled na položky architektury v rámci služby.

![Běhová architektura Dispatch](./media/wcfc-dispatchruntimearchc.gif "wcfc_DispatchRuntimeArchc")

### <a name="channel-dispatchers"></a>Odesílání kanálů

<xref:System.ServiceModel.Channels.IChannelListener> Vytvoří se <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> objekt pro přidružení k konkrétnímu identifikátoru URI (označovanému jako identifikátor URI naslouchání) s instancí služby. Každý <xref:System.ServiceModel.ServiceHost> objekt může mít mnoho <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> objektů, z nichž každý je přidružen pouze k jednomu identifikátoru URI naslouchacího procesu a naslouchání. Když se přijme zpráva, <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> dotazuje každý z přidružených <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objektů na to, jestli koncový bod může zprávu přijmout, a pošle zprávu na tu, kterou může.

Všechny vlastnosti, které řídí dobu života a chování relace kanálu, jsou k dispozici pro kontrolu a úpravy <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> objektu. Patří sem vlastní Inicializátory kanálů, naslouchací proces kanálu, hostitel, přidružený <xref:System.ServiceModel.InstanceContext>a tak dále.

### <a name="endpoint-dispatchers"></a>Expedice koncových bodů

Objekt je zodpovědný za zpracování zpráv <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> z a v případě, že cílová adresa zprávy odpovídá <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> vlastnosti a akce zprávy se shoduje s vlastností. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Pokud dva <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objekty mohou přijmout zprávu <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.FilterPriority%2A> , hodnota vlastnosti Určuje koncový bod s vyšší prioritou.

Použijte k získání dvou hlavních bodů rozšíření modelu služby <xref:System.ServiceModel.Dispatcher.DispatchRuntime> – třídy a <xref:System.ServiceModel.Dispatcher.DispatchOperation> –, které lze použít k přizpůsobení zpracování dispečera. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Třída umožňuje uživatelům zachytit a rozšíření dispečera v oboru kontraktu (tj. pro všechny zprávy ve smlouvě). <xref:System.ServiceModel.Dispatcher.DispatchOperation> Třída umožňuje uživatelům zachytit a rozšíření dispečera v oboru operace (tj. pro všechny zprávy v operaci).

## <a name="scenarios"></a>Scénáře

K dispozici je několik důvodů pro rozšiřování dispečera:

- Vlastní ověření zprávy Uživatelé mohou vyhovět, že je zpráva platná pro určité schéma. To se dá udělat implementací rozhraní pro zachycování zpráv. Příklad naleznete v tématu [inspektoři zpráv](../samples/message-inspectors.md).

- Vlastní protokolování zpráv. Uživatelé mohou kontrolovat a protokolovat některé sady zpráv aplikace, které jsou spouštěny prostřednictvím koncového bodu. Můžete to také provést pomocí rozhraní pro zachycování zpráv.

- Vlastní transformace zpráv Uživatelé mohou použít určité transformace na zprávu v modulu runtime (například pro správu verzí). To se dá provést znovu s rozhraními pro zachycování zpráv.

- Vlastní datový model. Uživatelé mohou mít model serializace dat jiný než podporované ve výchozím nastavení ve službě WCF (konkrétně <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>, a nezpracované zprávy). To lze provést implementací rozhraní formátovacích zpráv. Příklad naleznete v tématu [formátovací modul operací a selektor operací](../samples/operation-formatter-and-operation-selector.md).

- Ověřování vlastního parametru. Uživatelé můžou vyhovět tomu, že typové parametry jsou platné (na rozdíl od XML). To lze provést pomocí rozhraní Inspector pro parametry.

- Odesílání vlastních operací. Uživatelé mohou implementovat odesílání na něco jiného než akce – například u prvku tělo nebo na vlastní vlastnost zprávy. To lze provést pomocí <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> rozhraní. Příklad naleznete v tématu [formátovací modul operací a selektor operací](../samples/operation-formatter-and-operation-selector.md).

- Sdružování objektů. Uživatelé můžou místo přidělení nového pro každé volání vytvořit fond instancí. To lze implementovat pomocí rozhraní poskytovatele instancí. Příklad najdete v tématu [sdružování](../samples/pooling.md).

- Leasing instance. Uživatelé můžou implementovat způsob zapůjčení pro dobu života instance, podobně jako u .NET Framework vzdálené komunikace. To lze provést pomocí rozhraní pro životní dobu kontextu instance.

- Vlastní zpracování chyb. Uživatelé můžou řídit, jak se zpracovávají místní chyby, a jak se chyby sdělují klientům zpátky. To lze implementovat pomocí <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní.

- Vlastní autorizační chování. Uživatelé můžou implementovat vlastní řízení přístupu tím, že rozšíří pracovní části kontraktu nebo operace a přidají kontroly zabezpečení na základě tokenů přítomných ve zprávě. To lze provést buď pomocí rozhraní zachytávací zprávy, nebo parametrů. Příklady najdete v tématu [rozšiřitelnost zabezpečení](../samples/security-extensibility.md).

  > [!CAUTION]
  > Vzhledem k tomu, že změna vlastností zabezpečení má potenciál narušit zabezpečení aplikací WCF, důrazně doporučujeme, abyste před nasazením provedli úpravy související se zabezpečením a důkladně se otestovali.

- Vlastní validátory runtime služby WCF. Můžete nainstalovat vlastní validátory, které prozkoumají služby, kontrakty a vazby, aby vynutily zásady na podnikové úrovni vzhledem k aplikacím WCF. (Například viz [How to: Zamčení koncových bodů v](how-to-lock-down-endpoints-in-the-enterprise.md)podniku.)

### <a name="using-the-dispatchruntime-class"></a>Použití třídy DispatchRuntime

<xref:System.ServiceModel.Dispatcher.DispatchRuntime> Třídu můžete použít buď k úpravě výchozího chování služby nebo jednotlivého koncového bodu, nebo k vložení objektů, které implementují vlastní úpravy jednoho nebo obou následujících procesů služby (nebo procesů klienta v případě duplexního klienta):

- Transformace příchozích zpráv do objektů a uvolnění těchto objektů jako vyvolání metod u objektu služby.

- Transformace objektů přijatých z odpovědi na vyvolání operace služby do odchozích zpráv.

<xref:System.ServiceModel.Dispatcher.DispatchRuntime> Umožňuje zachytit a zvětšit kanál nebo dispečera koncového bodu pro všechny zprávy v rámci konkrétní smlouvy, a to i v případě, že zpráva není rozpoznána. Když zpráva dorazí, že se neshoduje s žádnou deklarovanou v kontraktu, je odeslána na operaci vrácenou <xref:System.ServiceModel.Dispatcher.DispatchRuntime.UnhandledDispatchOperation%2A> vlastností. Chcete-li zachytit nebo roztáhnout ve všech zprávách pro konkrétní operaci, <xref:System.ServiceModel.Dispatcher.DispatchOperation> Přečtěte si třídu.

Existují čtyři hlavní oblasti rozšiřitelnosti dispečera vystavené <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídou:

1. Komponenty kanálu používají vlastnosti <xref:System.ServiceModel.Dispatcher.DispatchRuntime> a přidružených dispečerů kanálů vrácených <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ChannelDispatcher%2A> vlastností k přizpůsobení způsobu, jakým dispečer kanálu akceptuje a uzavírá kanály. Tato kategorie zahrnuje <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ChannelInitializers%2A> vlastnosti a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InputSessionShutdownHandlers%2A> .

2. Součásti zpráv jsou přizpůsobené pro každou zpracovávanou zprávu. Tato <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A>kategorie zahrnuje <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> vlastnosti<xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ErrorHandlers%2A> ,, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A>a.

3. Komponenty instancí přizpůsobují vytváření, životnost a odstraňování instancí typu služby. Další informace o životních cyklech objektů služby naleznete v <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> tématu vlastnost. Tato kategorie zahrnuje <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> a vlastnosti.

4. Součásti související se zabezpečením mohou používat následující vlastnosti:

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>indikuje, kde se zapisují události auditu.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ImpersonateCallerForAllOperations%2A>Určuje, zda se služba pokusí o zosobnění s použitím pověření poskytnutých příchozí zprávou.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageAuthenticationAuditLevel%2A>Určuje, zda jsou události úspěšného ověření zprávy zapisovány do protokolu událostí <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>určeného parametrem.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.PrincipalPermissionMode%2A>Určuje, <xref:System.Threading.Thread.CurrentPrincipal%2A> jak je nastavena vlastnost.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ServiceAuthorizationAuditLevel%2A>Určuje způsob, jakým se provádí auditování událostí autorizace.

    - <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SuppressAuditFailure%2A>Určuje, zda se mají potlačit nekritické výjimky, ke kterým dojde během procesu protokolování.

Vlastní objekty rozšíření se obvykle přiřazují k <xref:System.ServiceModel.Dispatcher.DispatchRuntime> vlastnosti nebo vložené do kolekce chování služby (objekt, který implementuje <xref:System.ServiceModel.Description.IServiceBehavior>), chování kontraktu (objekt, který implementuje <xref:System.ServiceModel.Description.IContractBehavior>), nebo koncový bod. chování (objekt, který implementuje <xref:System.ServiceModel.Description.IEndpointBehavior>). Pak se objekt chování při instalaci přidá do příslušné kolekce chování buď programově, nebo implementací vlastního <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> objektu, aby bylo možné chování vložit pomocí konfiguračního souboru aplikace.

Duplexní klienti (klienti, kteří implementují kontrakt zpětného volání určené duplexovou službou) <xref:System.ServiceModel.Dispatcher.DispatchRuntime> mají také objekt, ke kterému lze <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> přistupovat pomocí vlastnosti.

### <a name="using-the-dispatchoperation-class"></a>Použití třídy DispatchOperation

<xref:System.ServiceModel.Dispatcher.DispatchOperation> Třída je umístění pro úpravy v době běhu a místo vložení pro vlastní rozšíření, která jsou vymezena pouze pro jednu operaci služby. (Chcete-li upravit chování služby za běhu pro všechny zprávy ve kontraktu, použijte <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídu.)

Nainstalujte <xref:System.ServiceModel.Dispatcher.DispatchOperation> změny pomocí objektu vlastního chování služby.

<xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A> Pomocí vlastnosti<xref:System.ServiceModel.Dispatcher.DispatchOperation> vyhledejte objekt, který představuje konkrétní operaci služby.

Následující vlastnosti řídí spuštění za běhu na úrovni operace:

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.Action%2A>Vlastnosti, <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReplyAction%2A>, ,<xref:System.ServiceModel.Dispatcher.DispatchOperation.FaultContractInfos%2A>, a<xref:System.ServiceModel.Dispatcher.DispatchOperation.Name%2A>získávají příslušné hodnoty pro operaci. <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsTerminating%2A> <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsOneWay%2A>

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionAutoComplete%2A> A<xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionRequired%2A> určení chování transakce.

- Vlastnosti <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceBeforeCall%2A> <xref:System.ServiceModel.InstanceContext>a <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceAfterCall%2A> určují dobu života uživatelem definovaného objektu služby relativně k.

- Vlastnosti, <xref:System.ServiceModel.Dispatcher.DispatchOperation.SerializeReply%2A>a umožňují explicitní kontrolu nad převodem zpráv na objekty a objekty na zprávy. <xref:System.ServiceModel.Dispatcher.DispatchOperation.DeserializeRequest%2A> <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A>

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.Impersonation%2A> Vlastnost určuje úroveň zosobnění operace.

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.CallContextInitializers%2A> Vlastnost vloží rozšíření vlastního kontextu volání pro danou operaci.

- Vlastnost <xref:System.ServiceModel.Dispatcher.DispatchOperation.AutoDisposeParameters%2A> určuje, kdy jsou zničeny objekty parametrů.

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.Invoker%2A> Vlastnost pro vložení vlastního objektu původce

- <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A> Vlastnost umožňuje vložit vlastní inspektor parametrů, který můžete použít ke kontrole a úpravám parametrů a vrácených hodnot.

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Dispatcher.DispatchRuntime>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation>
- [Postupy: Kontrola a úprava zpráv ve službě](how-to-inspect-and-modify-messages-on-the-service.md)
- [Postupy: Kontrola nebo úprava parametrů](how-to-inspect-or-modify-parameters.md)
- [Postupy: Zamčení koncových bodů v podniku](how-to-lock-down-endpoints-in-the-enterprise.md)
