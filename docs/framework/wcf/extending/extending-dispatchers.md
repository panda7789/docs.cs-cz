---
title: Rozšíření dispečerů
ms.date: 03/30/2017
helpviewer_keywords:
- dispatcher extensions [WCF]
ms.assetid: d0ad15ac-fa12-4f27-80e8-7ac2271e5985
ms.openlocfilehash: 653b22adb5ed53c9c3eb44db598ad5d1c50ff1a9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808235"
---
# <a name="extending-dispatchers"></a>Rozšíření dispečerů
Dispečerů jsou zodpovědní za stahování příchozí zprávy mimo základní kanály, převedena do volání metod v kódu aplikace a odesílání výsledky zpět k volajícímu. Rozšíření dispečerů umožňují upravit zpracování.  Můžete implementovat zprávy nebo parametr kontroly, které zkontrolovat nebo upravit obsah zprávy nebo parametry.  Můžete změnit způsob zprávy jsou směrovány do operace nebo zadejte některé další funkce.  
  
 Toto téma popisuje postup použití <xref:System.ServiceModel.Dispatcher.DispatchRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchOperation> aplikace změnit výchozí chování při spuštění systému dispečera nebo k zachycení nebo upravit zprávy, parametry nebo může vracet služby třídy v Windows Communication Foundation (WCF) hodnoty před nebo po odeslání nebo načítat vrstvy kanálu. Další informace o zpracování zprávy runtime ekvivalentní klienta najdete v tématu [rozšíření klienti](../../../../docs/framework/wcf/extending/extending-clients.md). Zjistit roli, <xref:System.ServiceModel.IExtensibleObject%601> typy přehrání při přístupu ke sdílené stavu mezi různými objekty přizpůsobení modulu runtime naleznete v tématu [rozšiřitelné objekty](../../../../docs/framework/wcf/extending/extensible-objects.md).  
  
## <a name="dispatchers"></a>Dispečerů  
 Vrstva modelu služby provede převod mezi programovací model pro vývojáře a základní exchange zprávu, označovaného jako vrstvy kanálu. V WCF kanál a koncový bod dispečerů (<xref:System.ServiceModel.Dispatcher.ChannelDispatcher> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>, v uvedeném pořadí) jsou součásti služby zodpovědní za přijetí nové kanály, přijímání zpráv, operace odesílání a volání a zpracování odpovědi. Dispečer jsou objekty příjemce, ale implementace kontraktu zpětného volání v duplexní služby také vystavit jejich dispečera objekty pro kontrolu, změna nebo rozšíření.  
  
 Dispečera channel (a doprovodné <xref:System.ServiceModel.Channels.IChannelListener>) vrátí zprávy mimo základní slovník kanál a předává zprávy do jejich dispečerů příslušného koncového bodu. Má každý koncový bod dispečera <xref:System.ServiceModel.Dispatcher.DispatchRuntime> který směruje zprávy do příslušné <xref:System.ServiceModel.Dispatcher.DispatchOperation>, který zodpovídá za volání metody, která implementuje operaci. Různé požadované a volitelné rozšíření třídy jsou vyvolány na cestě. Toto téma vysvětluje, jak tyto součásti zapadají a jak můžete upravit vlastnosti a zařaďte vlastní kód pro rozšíření základní funkce.  
  
 Dispečer vlastnosti a objekty upravené přizpůsobení jsou vloženy pomocí služby koncového bodu, kontrakt operaci nebo objekty chování. Toto téma nepopisuje používání chování. Další informace o typech používaný k vkládání dispečera úpravy najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
 Následující obrázek poskytuje podrobný pohled architektury položky ve službě.  
  
 ![Architektura modulu runtime odesílání](../../../../docs/framework/wcf/extending/media/wcfc-dispatchruntimearchc.gif "wcfc_DispatchRuntimeArchc")  
  
### <a name="channel-dispatchers"></a>Kanál dispečerů  
 A <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> objekt se vytvoří pro přidružení <xref:System.ServiceModel.Channels.IChannelListener> na konkrétní identifikátoru URI (nazývané naslouchání URI) s instancí služby. Každý <xref:System.ServiceModel.ServiceHost> objekt může mít mnoho <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> objekty, každý přidružený jenom jeden naslouchací proces a naslouchání identifikátor URI. Při doručení zprávy <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> dotazuje každý přidruženého <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objekty zda koncového bodu může přijmout zprávu a odesláním do ten, který můžete.  
  
 Jsou k dispozici pro kontroly nebo změna na všechny vlastnosti, které řídí životnost a chování relace kanál <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> objektu. Patří mezi ně vlastní kanál inicializátory, naslouchací proces kanálu nástroje, hostitele, s přiřazenou třídou <xref:System.ServiceModel.InstanceContext>a tak dále.  
  
### <a name="endpoint-dispatchers"></a>Koncový bod dispečerů  
 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Objektu je zodpovědná za zpracování zprávy ze <xref:System.ServiceModel.Dispatcher.ChannelDispatcher> při cílovou adresu zprávu odpovídá <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a odpovídá akce zpráva <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> vlastnost. Pokud dva <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objekty může přijmout zprávu, <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.FilterPriority%2A> hodnota vlastnosti určuje vyšší priorita koncového bodu.  
  
 Použít <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> získat dva hlavní služby modelu body rozšíření – <xref:System.ServiceModel.Dispatcher.DispatchRuntime> a <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy –, můžete použít k přizpůsobení zpracování dispečera. <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Třída umožňuje uživatelům zachytávat a rozšířit dispečera v oboru kontrakt (který je pro všechny zprávy ve smlouvě). <xref:System.ServiceModel.Dispatcher.DispatchOperation> Třída umožňuje uživatelům zachytávat a rozšířit dispečera ve operace oboru (který je pro všechny zprávy ve operace).  
  
## <a name="scenarios"></a>Scénáře  
 Zde několik důvodů, proč rozšířit dispečera:  
  
-   Vlastní zprávy ověření. Uživatele můžete vynutit, že je platný pro určité schéma zprávu. Tento krok můžete provést implementací rozhraní interceptoru zprávy. Příklad, naleznete v části [inspektoři zpráv](../../../../docs/framework/wcf/samples/message-inspectors.md).  
  
-   Vlastní zprávu při protokolování. Uživatelé můžou kontrolovat a protokolu některé sadu zpráv aplikace, které procházet skrz koncový bod. To můžete provést také s rozhraními interceptoru zprávy.  
  
-   Vlastní zprávu transformace. Uživatele můžete použít některé transformace na zprávu v modulu runtime (například pro správu verzí). Můžete to provést, znovu s rozhraními interceptoru zprávy.  
  
-   Vlastní datový Model. Uživatelé mohou mít datový model serializace nejsou podporovány ve výchozím nastavení ve službě WCF (konkrétně, <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>, <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>a nezpracované zprávy). To můžete provést implementace rozhraní formátování zprávy. Příklad, naleznete v části [formátovací modul a selektor operace](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
-   Vlastní parametr ověření. Uživatele můžete vynutit, aby typové parametry jsou platné (na rozdíl od XML). To lze provést pomocí rozhraní inspector parametr.  
  
-   Vlastní operaci odeslání. Uživatele můžete implementovat odeslání na něco jiného než akce – například v textu elementu nebo na vlastní zprávu vlastnost. To lze provést pomocí <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> rozhraní. Příklad, naleznete v části [formátovací modul a selektor operace](../../../../docs/framework/wcf/samples/operation-formatter-and-operation-selector.md).  
  
-   Sdružování objektů. Uživatelé může vytvořit fond instancí spíše než přidělování novou pro každé volání. To můžete implementovat pomocí rozhraní instance zprostředkovatele. Příklad, naleznete v části [Pooling](../../../../docs/framework/wcf/samples/pooling.md).  
  
-   Instance Leasing. Uživatele můžete implementovat leasingu vzor pro instanci doba platnosti podobná vzdálené komunikace rozhraní .NET Framework. To lze provést pomocí rozhraní instance kontextu životního cyklu.  
  
-   Zpracování vlastních chyb. Uživatelé můžou řídit, jak oba místní chyby jsou zpracovávány a jak se předávají chyb zpět klientům. To lze provést, pomocí <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní.  
  
-   Chování autorizace. Uživatele můžete implementovat řízení přístupu vlastní rozšíření běhu částí kontrakt nebo operace a přidáním kontrol zabezpečení na základě tokeny ve zprávě. Můžete to provést pomocí zachycování zpráv nebo parametr interceptoru rozhraní. Příklady najdete v tématu [rozšiřitelnost zabezpečení](../../../../docs/framework/wcf/samples/security-extensibility.md).  
  
    > [!CAUTION]
    >  Vzhledem k tomu, že změna vlastnosti zabezpečení se může ohrozit zabezpečení aplikací služby WCF, doporučujeme provést změny související se zabezpečením dát pozor a důkladně otestovat před jejich nasazením.  
  
-   Validátory Runtime vlastní WCF. Vlastní validátory, které zkontrolujte služby, smlouvy a vazby k vynucení zásad podnikové úrovni s ohledem na aplikace WCF je možné nainstalovat. (Například najdete v části [postup: uzamčení mimo provoz koncovými body v podnikové síti](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).)  
  
### <a name="using-the-dispatchruntime-class"></a>Používání třídy DispatchRuntime  
 Použití <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třída změnit výchozí chování služby nebo jednotlivé koncový bod, nebo vložit objekty, které implementují vlastní úpravy jedno nebo obě následující procesy služeb (nebo procesy klienta v případě duplexní klienta):  
  
-   Transformaci příchozích zpráv do objekty a uvolnění těchto objektů jako volání metod u objektu služby.  
  
-   Transformace objektů přijatých ze odpověď na volání operace služby do odchozí zprávy.  
  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> Umožňuje zachytit a rozšířit dispečera kanál nebo koncový bod pro všechny zprávy přes konkrétní kontraktu, i v případě, že zprávy nebyl rozpoznán. Při doručení zprávy, který neodpovídá žádnému deklarované v kontraktu odeslaných operaci vrácený <xref:System.ServiceModel.Dispatcher.DispatchRuntime.UnhandledDispatchOperation%2A> vlastnost. Zachytit nebo rozšířit na všechny zprávy pro určité operace, najdete v článku <xref:System.ServiceModel.Dispatcher.DispatchOperation> třídy.  
  
 Existují čtyři hlavní oblasti dispečera rozšiřitelnost vystavené <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy:  
  
1.  Komponentů kanálu použít vlastnosti <xref:System.ServiceModel.Dispatcher.DispatchRuntime> a jejích přidružených kanál dispečera vrácené <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ChannelDispatcher%2A> vlastnost přizpůsobit jak dispečera kanál přijme a zavře kanály. Tato kategorie zahrnuje <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ChannelInitializers%2A> a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InputSessionShutdownHandlers%2A> vlastnosti.  
  
2.  Zprávy součásti jsou přizpůsobené pro každou zprávu zpracovat. Tato kategorie zahrnuje <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A>, <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A>a <xref:System.ServiceModel.Dispatcher.ChannelDispatcher.ErrorHandlers%2A> vlastnosti.  
  
3.  Instance součásti přizpůsobit vytváření, životnost a uvolnění instancí typu služby. Další informace o životnosti objektu služby najdete v tématu <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> vlastnost. Tato kategorie zahrnuje <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> vlastnosti.  
  
4.  Součásti související se zabezpečením, můžete použít následující vlastnosti:  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A> Určuje, kde se zapisují událostí auditu.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ImpersonateCallerForAllOperations%2A> Určuje, zda se služba pokusí zosobnit pomocí přihlašovacích údajů zadaných příchozí zprávy.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageAuthenticationAuditLevel%2A> Určuje, zda zpráva úspěšné ověřování události se zapisují do protokolu událostí určeného <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SecurityAuditLogLocation%2A>.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.PrincipalPermissionMode%2A> ovládací prvky jak <xref:System.Threading.Thread.CurrentPrincipal%2A> je nastavena.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.ServiceAuthorizationAuditLevel%2A> Určuje, jak se provádí auditování událostí autorizace.  
  
    -   <xref:System.ServiceModel.Dispatcher.DispatchRuntime.SuppressAuditFailure%2A> Určuje, jestli se má potlačit nekritické výjimky, ke kterým došlo během procesu protokolování.  
  
 Obvykle jsou vlastní rozšíření objekty přiřazeny k <xref:System.ServiceModel.Dispatcher.DispatchRuntime> vlastnost vložit do kolekce podle chování služby ani (objekt, který implementuje <xref:System.ServiceModel.Description.IServiceBehavior>), kontrakt chování (objekt, který implementuje <xref:System.ServiceModel.Description.IContractBehavior>), nebo koncový bod chování (objekt, který implementuje <xref:System.ServiceModel.Description.IEndpointBehavior>). Potom objekt instalaci chování je přidán do příslušné kolekce chování prostřednictvím kódu programu nebo implementací vlastní <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> objekt, který chcete povolit chování má být vložen pomocí konfiguračního souboru aplikace.  
  
 Také mít duplexní klientů (klientů, které implementace kontraktu zpětného volání určeného duplexní služby) <xref:System.ServiceModel.Dispatcher.DispatchRuntime> objekt, který lze přistupovat pomocí <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> vlastnost.  
  
### <a name="using-the-dispatchoperation-class"></a>Používání třídy DispatchOperation  
 <xref:System.ServiceModel.Dispatcher.DispatchOperation> Třída je umístění pro spuštění úpravy a vložení bodu pro vlastní rozšíření, která jsou omezená na operaci pouze jedna služba. (Chcete-li upravit chování běhové služby pro všechny zprávy ve smlouvě, použijte <xref:System.ServiceModel.Dispatcher.DispatchRuntime> třídy.)  
  
 Nainstalujte <xref:System.ServiceModel.Dispatcher.DispatchOperation> úpravy pomocí objekt chování vlastní službu.  
  
 Použití <xref:System.ServiceModel.Dispatcher.DispatchRuntime.Operations%2A> vlastnost najít <xref:System.ServiceModel.Dispatcher.DispatchOperation> objekt, který reprezentuje operaci konkrétní služby.  
  
 Následující vlastnosti řízení provádění modul runtime na úrovni operace:  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Action%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReplyAction%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.FaultContractInfos%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsOneWay%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.IsTerminating%2A>, A <xref:System.ServiceModel.Dispatcher.DispatchOperation.Name%2A> vlastnosti získání příslušných hodnot pro operaci.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionAutoComplete%2A> a <xref:System.ServiceModel.Dispatcher.DispatchOperation.TransactionRequired%2A> zadejte chování transakce.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceBeforeCall%2A> a <xref:System.ServiceModel.Dispatcher.DispatchOperation.ReleaseInstanceAfterCall%2A> vlastnosti řídí životnost objektu služby uživatelem definované vzhledem k <xref:System.ServiceModel.InstanceContext>.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.DeserializeRequest%2A>, <xref:System.ServiceModel.Dispatcher.DispatchOperation.SerializeReply%2A>a <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> vlastnosti povolit explicitní kontrolu nad převod zprávy objekty a objekty na zprávy.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Impersonation%2A> Vlastnost určuje úroveň zosobnění operaci.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.CallContextInitializers%2A> Vlastnost vloží vlastní volání kontextu rozšíření pro operaci.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.AutoDisposeParameters%2A> Vlastnost řídí, pokud jsou objekty parametr zničena.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.Invoker%2A> Vlastnost vložit objekt vlastní původce volání.  
  
-   <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A> Vlastnost umožňuje vložit inspector vlastní parametr, který vám pomůže zkontrolovat nebo změnit parametry a návratové hodnoty.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Dispatcher.DispatchRuntime>  
 <xref:System.ServiceModel.Dispatcher.DispatchOperation>  
 [Postupy: Kontrola a změny zpráv ve službě](../../../../docs/framework/wcf/extending/how-to-inspect-and-modify-messages-on-the-service.md)  
 [Postupy: Kontrola nebo úprava parametrů](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)  
 [Postupy: Uzamknutí koncových bodů v podniku](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)
