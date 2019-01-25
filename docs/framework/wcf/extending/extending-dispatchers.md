---
title: Rozšíření dispečerů
ms.date: 03/30/2017
helpviewer_keywords:
- dispatcher extensions [WCF]
ms.assetid: d0ad15ac-fa12-4f27-80e8-7ac2271e5985
ms.openlocfilehash: c34a923d70c9079a3736732d6815df0329dfd557
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715893"
---
# <a name="extending-dispatchers"></a>Rozšíření dispečerů
Dispečerů zodpovídají za přesun příchozí zprávy z podkladové kanály, překládá na volání metod v kódu aplikace a odesílá výsledky zpět volajícímu. Rozšíření dispečerů umožňují upravit toto zpracování.  Můžete implementovat zpráv nebo parametr kontroly, které zkontrolovat nebo změnit obsah zprávy nebo parametry.  Můžete změnit tak, jak zprávy jsou směrovány na operace nebo poskytuje některé další funkce.  
  
 Toto téma popisuje způsob použití <xref:System.ServiceModel.Dispatcher.DispatchRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchOperation> aplikace změnit výchozí chování spuštění dispečera nebo chcete zachytit změny zpráv, parametry nebo vrátit služby třídy v Windows Communication Foundation (WCF) hodnoty před nebo po odeslání nebo načítání z vrstvy kanálu. Další informace o zpracování zpráv modulu runtime ekvivalentní klienta najdete v tématu [rozšíření klienti](../../../../docs/framework/wcf/extending/extending-clients.md). K Seznamte se s rolí, která <xref:System.ServiceModel.IExtensibleObject%601> typy přehrávat k používání sdíleného stavu mezi různými objekty modulu runtime přizpůsobení, najdete v článku [rozšiřitelné objekty](../../../../docs/framework/wcf/extending/extensible-objects.md).  
  
## <a name="dispatchers"></a>Dispečerů  
 Vrstva modelu služby provede převod mezi programovací model pro vývojáře a základní výměně zpráv, běžně nazývá vrstvě kanálu. V kanálu WCF a dispečerů koncový bod (<xref:System.ServiceModel.Dispatcher.ChannelDispatcher> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>v uvedeném pořadí) odpovídají součásti služby pro příjem nových kanálů a přijímat zprávy, operace odesílání a vyvolání a zpracování odpovědi. Dispečer objekty jsou objekty příjemce, ale implementace kontraktu zpětného volání v duplexní služby také zveřejnit své objekty odesílatele pro kontrolu, úpravy nebo rozšíření.  
  
 Dispečer kanálu (a doprovodné <xref:System.ServiceModel.Channels.IChannelListener>) přetáhne zprávy z kanálu identifikátor a předává zprávy do jejich dispečerů příslušný koncový bod. Má každý Dispečer koncového bodu <xref:System.ServiceModel.Dispatcher.DispatchRuntime> , který provádí směrování zpráv do příslušné <xref:System.ServiceModel.Dispatcher.DispatchOperation>, která zodpovídá za volání metody, která implementuje operaci. Různé povinných a volitelných rozšíření třídy jsou vyvolány na cestě. Toto téma vysvětluje, jak přizpůsobit tyto kusy dohromady, a jak upravit vlastnosti a zapojte vlastní kód rozšířit základní funkce.  
  
 Dispečer vlastností a změny přizpůsobení objektů jsou vloženy pomocí objektů chování služby, koncový bod, smlouvy nebo operace. Toto téma nepopisuje použití chování. Další informace o typech vkládá dispečer změny, najdete v části [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Následující obrázek poskytuje souhrnný přehled architektury položky ve službě.  
  
 ![Architektura modulu runtime odeslání](../../../../docs/framework/wcf/extending/media/wcfc-dispatchruntimearchc.gif "wcfc_DispatchRuntimeArchc")  
  
### <a name="channel-dispatchers"></a>Kanál dispečerů  
 A <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> objekt je vytvořen pro přidružení <xref:System.ServiceModel.Channels.IChannelListener> konkrétní identifikátorem URI (označované jako identifikátor URI příposlechu) s instancí služby. Každý <xref:System.ServiceModel.ServiceHost> objekt může mít mnoho <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> objekty, každý přidružený pouze jeden naslouchací proces a poslechem identifikátoru URI. Při doručení zprávy <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> dotazuje všech přidružených <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objekty, jestli koncový bod může přijmout zprávu a předá zprávu do objektu, která se dá.  
  
 Jsou k dispozici pro kontrolu nebo úprav na všechny vlastnosti, které řídí životnost a chování kanálu relace <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> objektu. Patří mezi ně vlastní kanál inicializátory, modul pro naslouchání kanálu, hostitele, přidružené <xref:System.ServiceModel.InstanceContext>, a tak dále.  
  
### <a name="endpoint-dispatchers"></a>Koncový bod dispečerů  
 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Objektu je zodpovědná za zpracování zpráv ze <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> když cílová adresa zpráva odpovídá <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a akce odpovídá zprávě <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> vlastnost. Pokud dvě <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objekty může přijmout zprávu, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.FilterPriority%2A> Určuje hodnotu vlastnosti vyšší prioritního koncového bodu.  
  
 Použít <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> získat dvě hlavní součásti služby modelu Rozšiřovací body – <xref:System.ServiceModel.Dispatcher.DispatchRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy –, můžete použít k přizpůsobení zpracování dispečer. <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Třída umožňuje uživatelům zachytit a rozšířit dispečer v oboru kontraktu (to znamená, že pro všechny zprávy ve smlouvě). <xref:System.ServiceModel.Dispatcher.DispatchOperation> Třída umožňuje uživatelům zachytit a rozšířit dispečer ve operace oboru (to znamená, že pro všechny zprávy v operaci).  
  
## <a name="scenarios"></a>Scénáře  
 Tam několik důvodů, proč rozšíření dispečer:  
  
-   Ověření vlastní zprávu. Uživatelé můžou vynutit platnost zprávy pro určité schéma. To můžete udělat pomocí implementace rozhraní zachycování zpráv. Příklad najdete v tématu [Messageinspectors](../../../../docs/framework/wcf/samples/message-inspectors.md).  
  
-   Protokolování vlastních zpráv. Uživatele můžete zkontrolovat a některé sadu zpráv aplikace, které probíhá přes koncový bod protokolu. To můžete provést také pomocí rozhraní zachycování zpráv.  
  
-   Vlastní zpráva transformace. Uživatele můžete použít některé transformace zprávy v modulu runtime (například Správa verzí). Toho můžete docílit, znovu s rozhraním zachycování zpráv.  
  
-   Vlastní datový Model. Uživatelé mohou mít modelem serializace dat než ty, které nepodporuje ve výchozím nastavení ve službě WCF (konkrétně <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>a nezpracované zprávy). To můžete udělat pomocí implementace rozhraní formátovací modul zpráv. Příklad najdete v tématu [formátovací modul a selektor operace](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
-   Ověření vlastního parametru. Uživatelé můžou vynutit, že zadané parametry jsou platné (na rozdíl od XML). To lze provést pomocí rozhraní inspektoru parametru.  
  
-   Vlastní operace odeslání. Uživatelé můžou implementovat odesílání na něco jiného než akce – třeba na body element nebo u vlastnosti vlastní zprávy. To lze provést pomocí <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> rozhraní. Příklad najdete v tématu [formátovací modul a selektor operace](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
-   Sdružování objektů. Uživatele může vytvořit fond instancí namísto vynakládání nový účtujeme každé volání. To je možné implementovat pomocí rozhraní instance zprostředkovatele. Příklad najdete v tématu [Sdužování](../../../../docs/framework/wcf/samples/pooling.md).  
  
-   Instance zapůjčení. Uživatelé můžou implementovat koordinovala vzor pro instanci životnost, podobně jako u vzdálené komunikace .NET Framework. To lze provést pomocí rozhraní životnost instance kontextu.  
  
-   Zpracování vlastních chyb. Uživatelé můžou řídit, jak obě místní chyby se zpracovávají a jak se předávají chyby zpět klientům. Je možné takovou implementaci pomocí <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní.  
  
-   Vlastní autorizace chování. Uživatelé můžou implementovat řízení přístupu na vlastní rozšíření za běhu kusy smlouvy nebo operace a přidáním kontroly zabezpečení na základě tokenů ve zprávě. To lze provést pomocí zachycování zpráv nebo parametr zachycování rozhraní. Příklady najdete v tématu [rozšiřitelnost zabezpečení](../../../../docs/framework/wcf/samples/security-extensibility.md).  
  
    > [!CAUTION]
    >  Protože změny vlastností zabezpečení má potenciál k ohrožení zabezpečení aplikací služby WCF, je důrazně doporučujeme, které provádějí související se zabezpečením úprav opatrně a důkladně otestovat před nasazením.  
  
-   Vlastní WCF validátory modulu Runtime. Můžete nainstalovat vlastní validátory, které zkontrolujte služby, kontrakty a vazby k vynucení zásad na úrovni rozlehlé sítě s ohledem na aplikací služby WCF. (Viz například [jak: Uzamknutí koncových bodů v podniku](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).)  
  
### <a name="using-the-dispatchruntime-class"></a>Pomocí třídy DispatchRuntime  
 Použití <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy změnit výchozí chování služby nebo jednotlivé koncového bodu nebo vložit objekty, které implementují vlastní úpravy na jeden nebo oba tyto procesy služeb (nebo procesy klienta v případě duplexní klienta):  
  
-   Transformaci příchozích zpráv do objektů a uvolněním těchto objektů jako volání metod na objekt služby.  
  
-   Transformace objektů přijatých z odpovědi k volání operace služby do odchozích zpráv.  
  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Vám umožní zachytit a rozšířit dispečer kanálu nebo koncový bod pro všechny zprávy přes konkrétní kontraktu i v případě, že zprávy nebyl rozpoznán. Při přijetí e-mailu, který neodpovídá žádnému deklarované v kontraktu se odesílají do operace vrácené <xref:System.ServiceModel.Dispatcher.DispatchRuntime.UnhandledDispatchOperation%2A> vlastnost. Zachytit nebo přesahují všechny zprávy pro určité operace, najdete v článku <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy.  
  
 Existují čtyři hlavní oblasti dispečer rozšiřitelnosti vystavené <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy:  
  
1.  Komponentů kanálu používat vlastnosti objektů <xref:System.ServiceModel.Dispatcher.DispatchRuntime> i u dispečer přidružené kanálu vrácené <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ChannelDispatcher%2A> vlastnost přizpůsobit jak dispečer kanálu přijímá a zavře kanály. Tato kategorie zahrnuje <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ChannelInitializers%2A> a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InputSessionShutdownHandlers%2A> vlastnosti.  
  
2.  Zprávy součásti jsou přizpůsobená pro každou zprávu zpracovat. Tato kategorie zahrnuje <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A>a <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ErrorHandlers%2A> vlastnosti.  
  
3.  Instance součásti přizpůsobit vytváření, doba platnosti a vyřazení instance daného typu služby. Další informace o životnosti objektu služby, najdete v článku <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost. Tato kategorie zahrnuje <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnosti.  
  
4.  Součásti související se zabezpečením, můžete použít následující vlastnosti:  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A> Určuje, kde události auditu se zapisují.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ImpersonateCallerForAllOperations%2A> Určuje, zda se služba pokusí o zosobnění s použitím pověření poskytnutých příchozí zprávy.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageAuthenticationAuditLevel%2A> Určuje, zda úspěšně provedeného ověřování události se zapisují do protokolu událostí, které jsou určené <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.PrincipalPermissionMode%2A> ovládací prvky jak <xref:System.Threading.Thread.CurrentPrincipal%2A> je nastavena.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ServiceAuthorizationAuditLevel%2A> Určuje, jak se provádí auditování událostí autorizace.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SuppressAuditFailure%2A> Určuje, jestli se má potlačit nekritické výjimek, ke kterým dochází během procesu přihlášení.  
  
 Obvykle vlastní rozšíření objekty jsou přiřazeny k <xref:System.ServiceModel.Dispatcher.DispatchRuntime> vlastnost nebo vložení do kolekce podle chování služby (objekt, který implementuje <xref:System.ServiceModel.Description.IServiceBehavior>), smlouva chování (objekt, který implementuje <xref:System.ServiceModel.Description.IContractBehavior>), nebo koncový bod chování (objekt, který implementuje <xref:System.ServiceModel.Description.IEndpointBehavior>). Potom instalace chování objektu je přidán do příslušné kolekce chování programově nebo prostřednictvím implementace vlastního <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> objekt, má-li povolit chování, které má být vložen pomocí konfiguračního souboru aplikace.  
  
 Duplexní (klienti, které implementují určené služby duplexní kontrakt zpětného volání) také mít <xref:System.ServiceModel.Dispatcher.DispatchRuntime> objekt, který lze přistupovat pomocí <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> vlastnost.  
  
### <a name="using-the-dispatchoperation-class"></a>Třída DispatchOperation pomocí  
 <xref:System.ServiceModel.Dispatcher.DispatchOperation> Třídy je umístění pro změny za běhu a vložení bod pro vlastní rozšíření, která jsou omezená jen jedna operace. (Chcete-li upravit chování za běhu služby pro všechny zprávy ve smlouvě, použijte <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy.)  
  
 Nainstalujte <xref:System.ServiceModel.Dispatcher.DispatchOperation> změny pomocí objektu chování vlastní služby.  
  
 Použití <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A> vlastnost najít <xref:System.ServiceModel.Dispatcher.DispatchOperation> objekt, který reprezentuje operaci konkrétní službu.  
  
 Tyto vlastnosti řídit spuštění modulu runtime na úrovni operace:  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Action%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReplyAction%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.FaultContractInfos%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsOneWay%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsTerminating%2A>, A <xref:System.ServiceModel.Dispatcher.DispatchOperation.Name%2A> příslušné hodnoty pro operaci získat vlastnosti.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionAutoComplete%2A> a <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionRequired%2A> zadejte chování při transakci.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceBeforeCall%2A> a <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceAfterCall%2A> vlastnosti řídit dobu života objektu služby uživatelem definované vzhledem k <xref:System.ServiceModel.InstanceContext>.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.DeserializeRequest%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.SerializeReply%2A>a <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> vlastnosti povolit explicitní kontrolu nad převod ze zprávy k objektům a objektů na zprávy.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Impersonation%2A> Vlastnost určuje úroveň zosobnění operace.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.CallContextInitializers%2A> Vlastnost vloží vlastní volání kontextu rozšíření pro operaci.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.AutoDisposeParameters%2A> Vlastnost určuje, kdy parametr objekty jsou zničeny.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Invoker%2A> Vlastnost vložit vlastní původce volání objektu.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A> Vlastnost umožňuje vložit vlastní parametr inspector, můžete použít ke kontrole nebo úprava parametrů a návratové hodnoty.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation>
- [Postupy: Kontrola a změny zpráv ve službě](../../../../docs/framework/wcf/extending/how-to-inspect-and-modify-messages-on-the-service.md)
- [Postupy: Kontrola nebo úprava parametrů](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)
- [Postupy: Uzamknutí koncových bodů v podniku](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)
