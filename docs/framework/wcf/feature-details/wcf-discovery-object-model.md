---
title: Objektový model zjišťování WCF
ms.date: 03/30/2017
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
ms.openlocfilehash: debcb08802894a34e16d9aa65bbbb1b0282794f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184228"
---
# <a name="wcf-discovery-object-model"></a>Objektový model zjišťování WCF
WCF Discovery se skládá ze sady typů, které poskytují jednotný programovací model, který umožňuje psát služby, které jsou zjistitelné za běhu a klienty, kteří vyhledávají a používají tyto služby.  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>Vytvoření služby zjistitelné a vyhledávaných služeb  
 Chcete-li službu WCF zjistitelné, přidejte <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> a hostitele <xref:System.ServiceModel.Description.ServiceDescription> služby a přidejte koncový bod zjišťování. Pokud je služba nakonfigurována k odesílání <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>zpráv oznámení (přidáním) oznámení je odesláno při otevření a zavření hostitele služby.  
  
 Klient, který chce naslouchat zprávy oznámení služby hostitelem služby oznámení a přidá jeden nebo více koncových bodů oznámení. Služba oznámení přijímá oznámení a vyvolává události oznámení.  
  
 Klient používá <xref:System.ServiceModel.Discovery.DiscoveryClient> třídu k hledání dostupných služeb. Klientská aplikace instanci <xref:System.ServiceModel.Discovery.DiscoveryClient> třídy, předávání v koncovém bodu zjišťování, který určuje, kam chcete odesílat zprávy zjišťování. Klient volá <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodu, která `Probe` odešle požadavek. Služby naslouchání pro `Probe` zprávy zjišťování obdrží tento požadavek. Pokud služba odpovídá kritériím `Probe`zadaným `ProbeMatch` v , odešle zprávu zpět klientovi.  
  
## <a name="object-model"></a>Objektový model  
 Rozhraní WCF Discovery API definuje následující třídy:  
  
- <xref:System.ServiceModel.Discovery.AnnouncementClient>  
  
- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
- <xref:System.ServiceModel.Discovery.AnnouncementService>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryClient>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>  
  
- <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryProxy>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryService>  
  
- <xref:System.ServiceModel.Discovery.DiscoveryVersion>  
  
- <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
  
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>  
  
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>  
  
- <xref:System.ServiceModel.Discovery.FindCriteria>  
  
- <xref:System.ServiceModel.Discovery.FindRequestContext>  
  
- <xref:System.ServiceModel.Discovery.FindResponse>  
  
- <xref:System.ServiceModel.Discovery.ResolveCriteria>  
  
- <xref:System.ServiceModel.Discovery.ResolveResponse>  
  
- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>  

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
- <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="announcementclient"></a>Klient oznámení  
 Třída <xref:System.ServiceModel.Discovery.AnnouncementClient> poskytuje synchronní a asynchronní metody pro odesílání zpráv oznámení. Existují dva typy oznámení zpráv, Hello a Bye. Hello zpráva je odeslána označující, že služba je k dispozici a bye zpráva je odeslána označující, že existující služba se stala nedostupnou. Vývojář vytvoří <xref:System.ServiceModel.Discovery.AnnouncementClient> instanci, předávání <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> instance jako parametr konstruktoru.  
  
## <a name="announcementendpoint"></a>Koncový bod oznámení  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>představuje standardní koncový bod s pevnou smlouvou o oznámení. Používá se službou nebo klientem k odesílání a přijímání zpráv s oznámením. Ve výchozím <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> nastavení je třída nastavena na použití verze protokolu WS_Discovery 11.  
  
## <a name="announcementservice"></a>Služba oznámení  
 <xref:System.ServiceModel.Discovery.AnnouncementService>je systémová implementace služby oznámení, která přijímá a zpracovává zprávy s oznámením. Při přijetí zprávy Hello nebo Bye <xref:System.ServiceModel.Discovery.AnnouncementService> instance volá <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> příslušnou <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A>virtuální metodu nebo , která vyvolává události oznámení.  
  
## <a name="discoveryclient"></a>Klient zjišťování  
 Třída <xref:System.ServiceModel.Discovery.DiscoveryClient> se používá klientská aplikace najít a vyřešit dostupné služby. Poskytuje synchronní a asynchronní metody pro hledání a řešení <xref:System.ServiceModel.Discovery.FindCriteria> služeb <xref:System.ServiceModel.Discovery.ResolveCriteria> na základě zadané a resp. Vývojář vytvoří <xref:System.ServiceModel.Discovery.DiscoveryClient> instanci a <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> poskytuje instanci jako parametr konstruktoru.  
  
 Chcete-li najít službu, vývojář vyvolá synchronní nebo `Find` asynchronní <xref:System.ServiceModel.Discovery.FindCriteria> metodu, která poskytuje instanci, která obsahuje kritéria vyhledávání, která mají být použita. Vytvoří <xref:System.ServiceModel.Discovery.DiscoveryClient> `Probe` zprávu s příslušnými záhlavía odešle požadavek na hledání. Vzhledem k tomu, `Find` že může být více než jeden nevyřízený požadavek kdykoli, klient koreluje přijaté odpovědi a ověří odpověď. Poté doručí výsledky volajícímu `Find` operace <xref:System.ServiceModel.Discovery.FindResponse>pomocí aplikace .  
  
 Chcete-li vyřešit známou službu, vývojář vyvolá synchronní nebo asynchronní `Resolve` metodu, která poskytuje <xref:System.ServiceModel.Discovery.ResolveCriteria> instanci, která obsahuje <xref:System.ServiceModel.EndpointAddress> známou službu. Vytvoří <xref:System.ServiceModel.Discovery.DiscoveryClient> `Resolve` zprávu s příslušnými záhlaví a odešle požadavek na vyřešení. Přijatá odpověď je korelována s nevyřízenými požadavky na vyřešení `Resolve` a <xref:System.ServiceModel.Discovery.ResolveResponse>výsledek je doručen volajícímu operace pomocí .  
  
 Pokud je v síti přítomen proxy <xref:System.ServiceModel.Discovery.DiscoveryClient> server zjišťování a odešle požadavek na zjišťování vícesměrovým způsobem, může proxy server zjišťování odpovědět zprávou Hello potlačení vícesměrového vysílání. Vyvolá <xref:System.ServiceModel.Discovery.DiscoveryClient> `ProxyAvailable` událost, když obdrží hello zprávy v `Find` `Resolve` reakci na nevyřízené nebo požadavky. Událost `ProxyAvailable` obsahuje <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> o proxy zjišťování. Je na vývojáři, aby tyto informace použil k přepnutí z režimu Ad hoc do spravovaného režimu.  
  
## <a name="discoveryendpoint"></a>Koncový bod zjišťování  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>představuje standardní koncový bod s pevnou smlouvou zjišťování. Používá se službou nebo klientem k odesílání nebo přijímání zpráv zjišťování. Ve výchozím <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> nastavení je <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Managed?displayProperty=nameWithType> nastaven režim použití a verze WSDiscovery-Discovery WS11.  
  
## <a name="discoverymessagesequencegenerator"></a>DiscoveryMessageSequenceGenerator  
 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>se používá ke <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> generování, když služba odesílá zprávy zjišťování nebo oznámení.  
  
## <a name="discoveryservice"></a>Služba DiscoveryService  
 Abstraktní <xref:System.ServiceModel.Discovery.DiscoveryService> třída poskytuje rámec pro `Probe` příjem `Resolve` a zpracování a zprávy. Při `Probe` přijetí zprávy <xref:System.ServiceModel.Discovery.DiscoveryService> vytvoří instanci na <xref:System.ServiceModel.Discovery.FindRequestContext> základě příchozí zprávy <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> a vyvolá virtuální metodu. Při `Resolve` přijetí zprávy <xref:System.ServiceModel.Discovery.DiscoveryService> vyvolá virtuální <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A> metodu. Z této třídy můžete dědit a poskytovat vlastní implementaci služby Discovery Service.  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 Abstraktní <xref:System.ServiceModel.Discovery.DiscoveryProxy> třída poskytuje rámec pro příjem a zpracování zpráv zjišťování a oznámení. Dědíte z této třídy při implementaci vlastní proxy zjišťování. Když `Probe` je zpráva přijata přes <xref:System.ServiceModel.Discovery.DiscoveryProxy> vícesměrové vysílání, třída volá virtuální metodu `BeginShouldRedirectFind` k určení, zda má být odeslána zpráva potlačení vícesměrového vysílání. Pokud se vývojář rozhodne neodesílat zprávu o `Probe` potlačení vícesměrového vysílání nebo pokud <xref:System.ServiceModel.Discovery.FindRequestContext> byla zpráva přijata přes jednosměrové vysílání, vytvoří instanci třídy na základě příchozí zprávy a vyvolá virtuální metodu. `OnBeginFind` Když `Resolve` je zpráva přijata přes <xref:System.ServiceModel.Discovery.DiscoveryProxy> vícesměrové vysílání, Třída volá virtuální metodu `ShouldRedirectResolve` k určení, zda má být odeslána zpráva potlačení vícesměrového vysílání. Pokud se vývojář rozhodne neodesílat zprávu o `Resolve` potlačení vícesměrového vysílání nebo pokud <xref:System.ServiceModel.Discovery.ResolveCriteria> byla zpráva přijata přes jednosměrové vysílání, vytvoří instanci třídy na základě příchozí zprávy a vyvolá virtuální metodu. `OnBeginResolve` Při přijetí zprávy Hello nebo <xref:System.ServiceModel.Discovery.DiscoveryProxy> Bye volá příslušnou`OnBeginOnlineAnnouncement` `OnBeingOfflineAnnouncement`virtuální metodu ( nebo ), která vyvolává události oznámení.  
  
## <a name="discoveryversion"></a>Discoveryversion  
 Třída <xref:System.ServiceModel.Discovery.DiscoveryVersion> představuje verzi protokolu zjišťování, která má být používána.  
  
## <a name="endpointdiscoverybehavior"></a>Chování zjišťování zjišťování koncového bodu  
 Třída <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> se používá k řízení zjistitelnosti koncového bodu, zadejte rozšíření, další názvy typů smlouvy. a obory spojené s tímto koncovým bodem. Toto chování je přidán do koncového bodu aplikace ke konfiguraci jeho <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Po <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> přidání do hostitele služby se všechny koncové body aplikace hostované hostitelem služby ve výchozím nastavení stanou zjistitelnými. Vývojář může vypnout zjišťování pro konkrétní koncový <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> bod `false`nastavením vlastnosti na .  
  
## <a name="endpointdiscoverymetadata"></a>Koncový bodDiscoveryMetadata  
 Třída <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> poskytuje reprezentaci nezávislé na verzi koncového bodu publikovaného službou. Obsahuje adresy koncových bodů, naslouchání identifikátory URI, názvy typů smluv, obory, verzi metadat a rozšíření určená vývojářem služby. Odeslané <xref:System.ServiceModel.Discovery.FindCriteria> klientem během `Probe` operace je porovnán proti <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Pokud se kritéria shodují, je <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> vrácena klientovi. Adresa koncového <xref:System.ServiceModel.Discovery.ResolveCriteria> bodu v písmenu je <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>porovnána s adresou koncového bodu . Pokud se kritéria shodují, je <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> vrácena klientovi.  
  
## <a name="findcriteria"></a>Najít kritéria  
 Třída <xref:System.ServiceModel.Discovery.FindCriteria> je třída nezávislá na verzi, která slouží k určení kritérií použitých při hledání služby. Plně podporuje kritéria definovaná ws-discovery pro odpovídající služby. Má také rozšíření, která mohou vývojáři použít k určení vlastních hodnot, které lze použít během procesu párování. Vývojář může poskytnout kritéria ukončení `Find` operace zadáním <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>, který určuje celkový počet služeb, které vývojář hledá, nebo který určuje <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>, což je hodnota, která určuje, jak dlouho klient čeká na odpovědi.  
  
## <a name="findrequestcontext"></a>FindRequestContext  
 Třída <xref:System.ServiceModel.Discovery.FindRequestContext> je vytvořena instance služby zjišťování na `Probe` základě zprávy, kterou obdrží `Find` při spuštění operace klienta. Obsahuje <xref:System.ServiceModel.Discovery.FindCriteria> instanci, která byla určena klientem.  
  
## <a name="findresponse"></a>FindResponse  
 Třída <xref:System.ServiceModel.Discovery.FindResponse> je vrácena volajícímu <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> s odpověďmi `Find` operace. Je také přítomen <xref:System.ServiceModel.Discovery.FindCompletedEventArgs>v . Obsahuje kolekci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, což je kolekce zjištěných koncových <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> bodů <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>a slovník a .  
  
## <a name="resolvecriteria"></a>Kritéria řešení  
 Třída <xref:System.ServiceModel.Discovery.ResolveCriteria> je třída nezávislá na verzi, která slouží k určení kritérií používaných při řešení již známé služby. Obsahuje adresu koncového bodu známé služby. Vývojář může poskytnout kritéria ukončení operace vyřešit <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A>zadáním , který určuje, jak dlouho klient čeká na odpovědi.  
  
## <a name="resolveresponse"></a>Vyřešit odpověď  
 Je <xref:System.ServiceModel.Discovery.ResolveResponse> vrácena volajícímu <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metody s odpovědí `Resolve` operace. Je také přítomen <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs>v . Obsahuje instanci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, což je zjištěné koncové <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>body a instance .  
  
## <a name="servicediscoverybehavior"></a>Chování servicediscoverybehavior  
 Třída <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> umožňuje vývojáři přidat funkci zjišťování do služby. Toto chování přidáte <xref:System.ServiceModel.ServiceHost>do . Třída <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> iterát přes koncové body aplikace přidané do hostitele <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> služby a vytvoří kolekci z zjistitelné koncové body. Všechny koncové body jsou zjistitelné ve výchozím nastavení. Zjistitelnost konkrétní koncový bod lze řídit přidáním tohoto konkrétního koncového <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> bodu. Pokud jsou přidány koncové <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> body oznámení pak oznámení všech zjistitelných koncových bodů je odeslána přes každý koncový bod oznámení při otevření nebo zavření hostitele služby.  
  
## <a name="udpannouncementendpoint"></a>Koncový bod oznámení Udp  
 Třída <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> je standardní koncový bod oznámení, který je předem nakonfigurován pro oznámení přes vazbu vícesměrového vysílání UDP. Ve výchozím <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> nastavení je nastavena na použití verze wsduben 2005 WS_Discovery.  
  
## <a name="udpdiscoveryendpoint"></a>Udpdiscoveryendpoint  
 Třída <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> je standardní koncový bod zjišťování, který je předem nakonfigurován pro zjišťování přes vazbu vícesměrového vysílání UDP. Ve výchozím <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> nastavení je nastavena na použití wsdiscovery11 WS-Discovery verze a <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Adhoc?displayProperty=nameWithType> režimu.
