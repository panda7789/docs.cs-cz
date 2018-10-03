---
title: Objektový model zjišťování WCF
ms.date: 03/30/2017
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
ms.openlocfilehash: b337eda40fc70a6d0e7b3aeccfc125e6e6bacf8f
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48046666"
---
# <a name="wcf-discovery-object-model"></a>Objektový model zjišťování WCF
Zjišťování WCF se skládá ze sady typů, které poskytují jednotný programovací model, který umožňuje psát služby, které jsou zjistitelný v modulu runtime a klienty, kteří vyhledání a použití těchto služeb.  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>Zjistitelné služby a služby hledání  
 Zjistitelnost služby WCF, přidejte <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> k <xref:System.ServiceModel.Description.ServiceDescription> služby hostování a přidání koncového bodu zjišťování. Pokud služba je nakonfigurovaná pro odesílání zpráv oznámení (tak, že přidáte <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>) oznámení se odešle, když se otevřel a uzavřel hostitele služby.  
  
 Klient, který chce přijímat zprávy oznámení služby je hostitelem služby oznámení a přidá jednu nebo víc koncových bodů oznámení. Služba oznámení přijímá zprávy oznámení a vyvolává události oznámení.  
  
 Klient použije <xref:System.ServiceModel.Discovery.DiscoveryClient> třídy, které chcete vyhledat dostupné služby. Vytvoří instanci klientské aplikace <xref:System.ServiceModel.Discovery.DiscoveryClient> třídy, prochází koncový bod zjišťování, která určuje, kam má odesílat zprávy zjišťování. Volání klienta <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodu, která odesílá `Probe` požadavku. Služby naslouchání pro příjem zprávy zjišťování to `Probe` požadavku. Pokud službu odpovídá kritérii zadanými v `Probe`, odešle `ProbeMatch` zpráv zpět klientovi.  
  
## <a name="object-model"></a>Objektový Model  
 Rozhraní API zjišťování WCF definuje následující třídy:  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementClient>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementService>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryClient>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>  
  
-   <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryProxy>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryService>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryVersion>  
  
-   <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>  
  
-   <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria>  
  
-   <xref:System.ServiceModel.Discovery.FindRequestContext>  
  
-   <xref:System.ServiceModel.Discovery.FindResponse>  
  
-   <xref:System.ServiceModel.Discovery.ResolveCriteria>  
  
-   <xref:System.ServiceModel.Discovery.ResolveResponse>  
  
-   <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>  
 
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="announcementclient"></a>AnnouncementClient  
 <xref:System.ServiceModel.Discovery.AnnouncementClient> Třída poskytuje synchronní a asynchronní metody k odeslání zpráv oznámení. Existují dva typy zpráv oznámení, Hello a Bye. Zpráva Hello je odeslána k označení, že služba má k dispozici a je Bye odeslána zpráva označující, že se stala existující služby není k dispozici. Vytvoří pro vývojáře <xref:System.ServiceModel.Discovery.AnnouncementClient> instance, a to předáním instance <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> jako parametr konstruktoru.  
  
## <a name="announcementendpoint"></a>AnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> představuje standardní koncový bod s pevným kontraktem oznámení. Používá se služba nebo klient k odesílání a příjem zpráv oznámení. Ve výchozím nastavení <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> třídy je nastavený na použití verze protokolu WS_Discovery 11.  
  
## <a name="announcementservice"></a>AnnouncementService  
 <xref:System.ServiceModel.Discovery.AnnouncementService> je implementace poskytnuté systémem, který přijímá a zpracovává zprávy oznámení služby oznámení. Po přijetí zprávu Hello nebo Bye <xref:System.ServiceModel.Discovery.AnnouncementService> instance zavolá odpovídající virtuální metodu <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> nebo <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A>, který vyvolá oznámení události.  
  
## <a name="discoveryclient"></a>Objekt DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Třída se používá v klientské aplikaci vyhledat a odstranit dostupných služeb. Umožňuje synchronní a asynchronní metody pro nalezení a vyřešení službám v závislosti na zadané <xref:System.ServiceModel.Discovery.FindCriteria> a <xref:System.ServiceModel.Discovery.ResolveCriteria> v uvedeném pořadí. Vytvoří pro vývojáře <xref:System.ServiceModel.Discovery.DiscoveryClient> instance a poskytuje instance <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> jako parametr konstruktoru.  
  
 K vyhledání služby, vývojář vyvolá synchronní nebo asynchronní `Find` metody, které poskytuje <xref:System.ServiceModel.Discovery.FindCriteria> instance, která obsahuje vyhledávací kritéria. <xref:System.ServiceModel.Discovery.DiscoveryClient> Vytvoří `Probe` zprávu s odpovídající záhlaví a odešle požadavek hledání. Vzhledem k tomu může dojít k více než jednomu nezpracovaných `Find` žádosti v okamžiku, klient koreluje přijaté odpovědi a ověří odezvy. Pak poskytuje výsledky do volajícího `Find` pomocí operace <xref:System.ServiceModel.Discovery.FindResponse>.  
  
 K vyřešení známých služby, vývojář vyvolá synchronní nebo asynchronní `Resolve` metodu, která obsahuje instance <xref:System.ServiceModel.Discovery.ResolveCriteria> obsahující <xref:System.ServiceModel.EndpointAddress> známé služby. <xref:System.ServiceModel.Discovery.DiscoveryClient> Vytvoří `Resolve` zprávu s příslušné záhlaví a odešle žádost o vyřešení. Přijata odpověď je porovnána s požadavky vynikající řešení a výsledek se doručí do volajícího `Resolve` pomocí operace <xref:System.ServiceModel.Discovery.ResolveResponse>.  
  
 Pokud je k dispozici v síti proxy zjišťování a <xref:System.ServiceModel.Discovery.DiscoveryClient> odešle vícesměrového vysílání může požádat o zjišťování, zjišťování proxy může odpovědět vícesměrovou zprávu Hello. <xref:System.ServiceModel.Discovery.DiscoveryClient> Vyvolá `ProxyAvailable` událost, když obdrží Hello zprávy v reakci na zbývající `Find` nebo `Resolve` požadavky. `ProxyAvailable` Událost obsahuje <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> o zjišťování proxy. Záleží vývojářům tyto informace slouží k přepnutí do spravovaného režimu z Ad hoc.  
  
## <a name="discoveryendpoint"></a>DiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> představuje standardní koncový bod s pevným kontraktem zjišťování. Služba nebo klienta se používá k odeslání nebo přijetí zprávy zjišťování. Ve výchozím nastavení <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> nastaveno pro použití <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Managed?displayProperty=nameWithType> režimu a verze WSDiscovery11 WS-Discovery.  
  
## <a name="discoverymessagesequencegenerator"></a>DiscoveryMessageSequenceGenerator  
 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator> slouží ke generování <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> když služba odesílá zprávy zjišťování nebo oznámení.  
  
## <a name="discoveryservice"></a>DiscoveryService  
 <xref:System.ServiceModel.Discovery.DiscoveryService> Abstraktní třída poskytuje rozhraní pro příjem a zpracování `Probe` a `Resolve` zprávy. Když `Probe` doručení zprávy <xref:System.ServiceModel.Discovery.DiscoveryService> vytvoří instanci <xref:System.ServiceModel.Discovery.FindRequestContext> na základě příchozí zprávy a vyvolá <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> virtuální metody. Když `Resolve` doručení zprávy <xref:System.ServiceModel.Discovery.DiscoveryService> vyvolá <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A> virtuální metody. Může dědit z této třídy a zadejte vlastní implementaci služby zjišťování.  
  
## <a name="discoveryproxy"></a>Objektu DiscoveryProxy  
 <xref:System.ServiceModel.Discovery.DiscoveryProxy> Abstraktní třída poskytuje rozhraní pro příjem a zpracování zpráv s oznámením a zjišťování. Abyste dědili z této třídy když implementujete vlastní zjišťování proxy. Když `Probe` přijata zpráva přes vícesměrové vysílání, <xref:System.ServiceModel.Discovery.DiscoveryProxy> třídy volání `BeginShouldRedirectFind` virtuální metodou ke zjištění, zda by měl vícesměrovou zprávu k odeslání. Pokud vývojář rozhodne Neodesílat vícesměrovou zprávu nebo pokud `Probe` byla přijata zpráva přes jednosměrového vysílání, vytvoří instanci <xref:System.ServiceModel.Discovery.FindRequestContext> třídy na základě příchozí zprávy a vyvolá `OnBeginFind` virtuální metody. Když `Resolve` přijata zpráva přes vícesměrové vysílání, <xref:System.ServiceModel.Discovery.DiscoveryProxy> třídy volání `ShouldRedirectResolve` virtuální metodou ke zjištění, zda by měl vícesměrovou zprávu k odeslání. Pokud vývojář rozhodne Neodesílat vícesměrovou zprávu nebo pokud `Resolve` byla přijata zpráva přes jednosměrového vysílání, vytvoří instanci <xref:System.ServiceModel.Discovery.ResolveCriteria> třídy na základě příchozí zprávy a vyvolá `OnBeginResolve` virtuální metody. Po přijetí zprávu Hello nebo Bye <xref:System.ServiceModel.Discovery.DiscoveryProxy> zavolá odpovídající virtuální metodu (`OnBeginOnlineAnnouncement` nebo `OnBeingOfflineAnnouncement`), který vyvolá oznámení události.  
  
## <a name="discoveryversion"></a>DiscoveryVersion  
 <xref:System.ServiceModel.Discovery.DiscoveryVersion> Třída reprezentuje verze protokolu zjišťování se má použít.  
  
## <a name="endpointdiscoverybehavior"></a>EndpointDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Třída se používá k řízení zjistitelnost koncového bodu, zadejte rozšíření, názvy typů dalších kontraktu. a obory přidružené k tohoto koncového bodu. Toto chování se přidá do koncového bodu aplikace ke konfiguraci jeho <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Když <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> se přidá k hostiteli služby, všechny aplikace koncových bodů hostitele služby hostované ve výchozím nastavení budou zjistitelné. Vývojář můžete vypnout zjišťování pro určitý koncový bod tak, že nastavíte <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> vlastnost `false`.  
  
## <a name="endpointdiscoverymetadata"></a>EndpointDiscoveryMetadata  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> Třída poskytuje reprezentaci verze nezávislé na koncový bod publikování ve službě. Obsahuje adresy koncových bodů, naslouchání identifikátory URI, názvy typů kontraktu, obory, verze metadat a rozšiřujících modulů uvedených vývojářem služeb. <xref:System.ServiceModel.Discovery.FindCriteria> Odeslané klientem během `Probe` je hledána operace <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Pokud kritériím odpovídá, pak bude <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> je vrácen do klienta. Adresa koncového bodu v <xref:System.ServiceModel.Discovery.ResolveCriteria> je hledána adresu koncového bodu <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Pokud kritériím odpovídá, pak bude <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> je vrácen do klienta.  
  
## <a name="findcriteria"></a>Kritéria hledání  
 <xref:System.ServiceModel.Discovery.FindCriteria> Třída je nezávislé na verzi Třída použitá pro určení kritérií použité při hledání služby. Plně podporuje WS Discovery definovaných kritérií pro odpovídající služby. Je také rozšíření, které mohou vývojáři použít k určení vlastní hodnoty, které lze použít během proces vyhledávání shody. Vývojář může zadat kritéria ukončení pro `Find` operaci zadáním <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>, který určuje celkový počet služeb hledá vývojář nebo, který určuje <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>, což je hodnota, která Určuje, jak dlouho klienta čeká na odpovědi.  
  
## <a name="findrequestcontext"></a>FindRequestContext  
 <xref:System.ServiceModel.Discovery.FindRequestContext> Službou zjišťování na základě je vytvořena instance třídy `Probe` zprávu obdrží, když klient zahájí `Find` operace. Obsahuje instanci <xref:System.ServiceModel.Discovery.FindCriteria> , který byl zadán klientem.  
  
## <a name="findresponse"></a>FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse> Třídy se vrátí volajícímu metody <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> s odezvy `Find` operace. Je také součástí <xref:System.ServiceModel.Discovery.FindCompletedEventArgs>. Obsahuje kolekci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, což je kolekce nalezených koncových bodů a slovník <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> a <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="resolvecriteria"></a>ResolveCriteria  
 <xref:System.ServiceModel.Discovery.ResolveCriteria> Třída je nezávislé na verzi Třída použitá pro určení kritérií používat při překladu služby již známé. Obsahuje adresu koncového bodu služby známé. Vývojář může zadat kritéria ukončení pro operace řešení tak, že zadáte <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A>, která určuje, jak dlouho klienta čeká na odpovědi.  
  
## <a name="resolveresponse"></a>ResolveResponse  
 <xref:System.ServiceModel.Discovery.ResolveResponse> Se vrátí volajícímu metody <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metodu s odpověď `Resolve` operace. Je také součástí <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs>. Obsahuje instanci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, což je zjištěných koncových bodů a instance <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="servicediscoverybehavior"></a>ServiceDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Třída umožňuje vývojářům přidat funkci zjišťování služby. Přidat toto chování <xref:System.ServiceModel.ServiceHost>. <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Třídy Iteruje přes aplikačními koncovými body přidat do tohoto hostitele služby a vytvoří kolekci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> z zjistitelné koncových bodů. Dostupnost ve výchozím nastavení jsou všechny koncové body. Zjistitelnost určitého koncového bodu je řídit tak, že přidáte <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> do tohoto konkrétního koncového bodu. Pokud přidáte koncových bodů oznámení <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> pak oznámení všechny koncové body zjistitelné je odeslán přes všech koncových bodů oznámení, když hostitel služby je otevřena nebo zavřena.  
  
## <a name="udpannouncementendpoint"></a>UdpAnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Třída je koncový bod standard oznámení, která je předem nakonfigurované pro oznámení přes UDP vazby vícesměrného vysílání. Ve výchozím nastavení <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> nastaveno pro použití WSApril2005 WS_Discovery verze.  
  
## <a name="udpdiscoveryendpoint"></a>UdpDiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Třída je koncový bod standard zjišťování, který je předkonfigurován pro zjišťování přes UDP vazby vícesměrného vysílání. Ve výchozím nastavení <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> je nastavený na použití verze WSDiscovery11 WS-Discovery a <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode.Adhoc?displayProperty=nameWithType> režimu.
