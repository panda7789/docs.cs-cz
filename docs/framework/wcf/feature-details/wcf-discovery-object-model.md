---
title: "Objektový model zjišťování WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8365a152-eacd-4779-9130-bbc48fa5c5d9
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6d9ee9c1331c5c8754b336024f4b11a040c8a201
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-discovery-object-model"></a>Objektový model zjišťování WCF
Zjišťování WCF se skládá ze sady typy, které poskytují jednotný programovací model, který umožňuje zapisovat služby, které jsou zjistitelný v modulu runtime a klientů, které nalezne a použije tyto služby.  
  
## <a name="making-a-service-discoverable-and-finding-services"></a>Aby služba zjistitelný a vyhledání služby  
 Zjistitelnost služby WCF, přidejte <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> k <xref:System.ServiceModel.Description.ServiceDescription> služby hostování a přidat koncový bod zjišťování. Pokud služba je nakonfigurován pro odesílání zpráv oznámení (přidáním <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>) oznámení se odesílají, pokud hostitel služby je otevřít a uzavřen.  
  
 Klient, který chce přijímat zprávy oznámení služby je hostitelem služby oznámení a přidá jeden nebo více koncových bodů oznámení. Služba oznámení přijímá zprávy oznámení a vyvolá oznámení události.  
  
 Klient používá <xref:System.ServiceModel.Discovery.DiscoveryClient> třída k vyhledání dostupných služeb. Klientská aplikace vytvoří <xref:System.ServiceModel.Discovery.DiscoveryClient> třídy a předejte v koncový bod zjišťování, která určuje, kde k odesílání zprávy zjišťování. Volání klienta <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodu, která odešle `Probe` požadavku. Služby naslouchání pro zjišťování zprávy zobrazovat to `Probe` požadavku. Pokud službu odpovídá kritérii zadanými v `Probe`, odešle `ProbeMatch` zprávy zpět do klienta.  
  
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
  
-   <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension`  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
## <a name="announcementclient"></a>AnnouncementClient  
 <xref:System.ServiceModel.Discovery.AnnouncementClient> Třída poskytuje synchronní a asynchronní metody k odeslání zprávy oznámení. Existují dva typy oznámení zpráv, Hello a Bye. Uvítací zprávu posílá znamenat, že služba je k dispozici a je odeslána zpráva Bye indikující, že existující službu již není dostupná. Vytvoří vývojáře <xref:System.ServiceModel.Discovery.AnnouncementClient> instance, předávání instanci <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> jako parametr konstruktoru.  
  
## <a name="announcementendpoint"></a>AnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>představuje standardní koncový bod s pevnou oznámení kontrakt. Služba nebo klienta se používá k odesílání a příjmu zprávy oznámení. Ve výchozím nastavení <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> třída je nastavený na použití verzi protokolu WS_Discovery 11.  
  
## <a name="announcementservice"></a>AnnouncementService  
 <xref:System.ServiceModel.Discovery.AnnouncementService>je poskytované systémem implementace služby oznámení, která přijímá a zpracovává zprávy oznámení. Po přijetí zprávy Hello nebo Bye <xref:System.ServiceModel.Discovery.AnnouncementService> instance volá metodu příslušné virtuální <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOnlineAnnouncement%2A> nebo <xref:System.ServiceModel.Discovery.AnnouncementService.OnBeginOfflineAnnouncement%2A>, která vyvolává oznámení události.  
  
## <a name="discoveryclient"></a>Objekty DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> Třída se používá aplikace klienta k vyhledávání a odstraňování služby k dispozici. Poskytuje synchronní a asynchronní metody pro hledání a řešení služby založené na zadaný <xref:System.ServiceModel.Discovery.FindCriteria> a <xref:System.ServiceModel.Discovery.ResolveCriteria> v uvedeném pořadí. Vývojář vytvoří <xref:System.ServiceModel.Discovery.DiscoveryClient> instance a poskytuje instanci <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> jako parametr konstruktoru.  
  
 K vyhledání služby, vyvolá vývojář synchronní nebo asynchronní `Find` metoda, která poskytuje <!--zz <xref:System.ServiceModel.Discription.FindCriteria> --> `FindCriteria` instanci, která obsahuje kritéria hledání, abyste používat. <xref:System.ServiceModel.Discovery.DiscoveryClient> Vytvoří `Probe` zprávu s příslušnou hlavičky a odešle žádost najít. Vzhledem k tomu může být více než jedna nezpracovaných `Find` požadavků kdykoli, klient korelaci přijaté odezvy a ověří odpovědi. Potom zajišťuje výsledky do volajícího `Find` pomocí operace <xref:System.ServiceModel.Discovery.FindResponse>.  
  
 Překlad známé služby, vyvolá vývojář synchronní nebo asynchronní `Resolve` metoda, která poskytuje instanci <!--zz <xref:System.ServiceModel.ResolveCriteria>--> `ResolveCriteria` obsahující <xref:System.ServiceModel.EndpointAddress> známé služby. <xref:System.ServiceModel.Discovery.DiscoveryClient> Vytvoří `Resolve` zprávu s příslušnou hlavičky a odešle žádost vyřešit. Před požadavky nezpracovaných vyřešte je korelační přijaté odpovědi a výsledek je předána volající `Resolve` pomocí operace <xref:System.ServiceModel.Discovery.ResolveResponse>.  
  
 Pokud je k dispozici v síti proxy zjišťování a <!--zz <xref:System.ServiceModel.Discover.DiscoveryClient> --> `DiscoveryClient` zasílá vícesměrového vysílání způsobem, žádosti o zjišťování, zjišťování proxy může odpovědět s uvítací zprávu potlačení vícesměrového vysílání. <!--zz <xref:System.ServiceModel.Discover.DiscoveryClient> --> `DiscoveryClient` Vyvolá `ProxyAvailable` událost, když obdrží Hello zprávy v reakci na zbývajících `Find` nebo `Resolve` požadavky. `ProxyAvailable` Události obsahuje <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> o zjišťování proxy. Je vývojáři tyto informace slouží k přejít z Ad hoc na spravovaný režim.  
  
## <a name="discoveryendpoint"></a>DiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>představuje standardní koncový bod s pevnou zjišťování kontrakt. Služba nebo klienta se používá k odesílání nebo přijímání zprávy zjišťování. Ve výchozím nastavení <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> je nastavený na použití <!--zz <xref:System.ServiceModel.Discovery.DiscoveryMode.Managed>--> `Managed` režimu a verze WSDiscovery11 WS-Discovery.  
  
## <a name="discoverymessagesequencegenerator"></a>DiscoveryMessageSequenceGenerator  
 <xref:System.ServiceModel.Discovery.DiscoveryMessageSequenceGenerator>slouží ke generování <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence> když služba odesílá zprávy zjišťování nebo oznámení.  
  
## <a name="discoveryservice"></a>DiscoveryService  
 <xref:System.ServiceModel.Discovery.DiscoveryService> Abstraktní třída poskytuje rozhraní pro příjem a zpracování `Probe` a `Resolve` zprávy. Když `Probe` je přijatá zpráva, <xref:System.ServiceModel.Discovery.DiscoveryService> vytvoří instanci <xref:System.ServiceModel.Discovery.FindRequestContext> na základě příchozí zprávy a vyvolá <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> virtuální metoda. Když `Resolve` je přijatá zpráva, <xref:System.ServiceModel.Discovery.DiscoveryService> vyvolá <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginResolve%2A> virtuální metoda. Může dědit vlastnosti z této třídy, které poskytují vlastní implementace zjišťování služby.  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 <xref:System.ServiceModel.Discovery.DiscoveryProxy> Abstraktní třída poskytuje rozhraní pro přijímání a zpracování zpráv s zjišťování a oznámení. Tato třída se dědí při implementaci vlastní zjišťování proxy. Když `Probe` přes vícesměrové vysílání, je přijatá zpráva <xref:System.ServiceModel.Discovery.DiscoveryProxy> třídy volání `BeginShouldRedirectFind` virtuální metoda k určení, zda zprávy vícesměrového vysílání potlačení by k odeslání. Pokud vývojář rozhodne, že odeslání zprávy vícesměrového vysílání potlačení nebo pokud `Probe` byla přijata zpráva přes jednosměrového vysílání, vytvoří instanci <xref:System.ServiceModel.Discovery.FindRequestContext> třídy na základě příchozí zprávy a vyvolá `OnBeginFind` virtuální metoda. Když `Resolve` přes vícesměrové vysílání, je přijatá zpráva <xref:System.ServiceModel.Discovery.DiscoveryProxy> třídy volání `ShouldRedirectResolve` virtuální metoda k určení, zda zprávy vícesměrového vysílání potlačení by k odeslání. Pokud vývojář rozhodne, že odeslání zprávy vícesměrového vysílání potlačení nebo pokud `Resolve` byla přijata zpráva přes jednosměrového vysílání, vytvoří instanci <xref:System.ServiceModel.Discovery.ResolveCriteria> třídy na základě příchozí zprávy a vyvolá `OnBeginResolve` virtuální metoda. Po přijetí zprávy Hello nebo Bye <xref:System.ServiceModel.Discovery.DiscoveryProxy> volá metodu příslušné virtuální (`OnBeginOnlineAnnouncement` nebo `OnBeingOfflineAnnouncement`), který vyvolává oznámení události.  
  
## <a name="discoveryversion"></a>discoveryVersion  
 <xref:System.ServiceModel.Discovery.DiscoveryVersion> Třída reprezentuje zjišťování protocol verze se má použít.  
  
## <a name="endpointdiscoverybehavior"></a>EndpointDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Třída se používá k řízení zjistitelnost koncový bod, zadejte rozšíření, názvy typů další kontrakt. a obory přidružené ke tohoto koncového bodu. Toto chování se přidá do koncového bodu aplikace konfigurovat jeho <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Když <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> se přidá k hostiteli služby všechny aplikace koncových bodů hostitele služby hostované ve výchozím nastavení stane zjistitelný. Vývojář můžete vypnout zjišťování pro konkrétní koncový bod nastavením <!--zz <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enable%2A>--> `Enable` vlastnost `false`.  
  
## <a name="endpointdiscoverymetadata"></a>EndpointDiscoveryMetadata  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> Třída poskytuje nezávislé na verzi reprezentace koncový bod publikovaná pomocí služby. Obsahuje adresy koncových bodů, naslouchání identifikátory URI, názvy typů kontrakt, obory, verze metadat a rozšíření určeného vývojáře služby. <xref:System.ServiceModel.Discovery.FindCriteria> Odeslané klientem během `Probe` je operace porovnání <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Pokud kritériím odpovídá, pak se <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> je vrácen do klienta. Adresa koncového bodu v <xref:System.ServiceModel.Discovery.ResolveCriteria> je shoda na základě adresa koncového bodu <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Pokud kritériím odpovídá, pak se <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> je vrácen do klienta.  
  
## <a name="findcriteria"></a>Kritéria hledání  
 <xref:System.ServiceModel.Discovery.FindCriteria> Třída je nezávislé na verzi třída slouží k zadání kritéria, která se použijí při hledání služby. Plně podporuje WS definované zjišťování kritéria pro odpovídající služby. Je také rozšíření, které mohou vývojáři zadat vlastní hodnoty, které lze použít při proces vyhledávání shody. Vývojář může poskytnout ukončení kritéria pro `Find` operaci zadáním <!--zz <xref:System.ServiceModel.Discovery.FindCriteria.MaxResult%2A>--> `MaxResult`, který určuje celkový počet služby hledá vývojář nebo určující <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A>, který je hodnota, která určuje, jak dlouho se klient počká na odpovědi.  
  
## <a name="findrequestcontext"></a>FindRequestContext  
 <xref:System.ServiceModel.Discovery.FindRequestContext> Zjišťování služby založené na vytvoření instance třídy `Probe` zprávu obdrží při klienta iniciuje `Find` operaci. Obsahuje instanci <xref:System.ServiceModel.Discovery.FindCriteria> zadaný klientem.  
  
## <a name="findresponse"></a>FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse> Třída je vrácen do volající <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> s odpovědí z `Find` operaci. Je také k dispozici v <xref:System.ServiceModel.Discovery.FindCompletedEventArgs>. Obsahuje kolekci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, což je kolekce zjištěných koncových bodů a slovník <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> a <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="resolvecriteria"></a>ResolveCriteria  
 <xref:System.ServiceModel.Discovery.ResolveCriteria> Třída je nezávislé na verzi třída slouží k zadání kritéria použitá při rozpoznávání služby již známé. Obsahuje adresa koncového bodu služby známé. Vývojář může poskytovat ukončení kritéria pro operace řešení tak, že zadáte <xref:System.ServiceModel.Discovery.ResolveCriteria.Duration%2A>, která určuje, jak dlouho se klient počká na odpovědi.  
  
## <a name="resolveresponse"></a>ResolveResponse  
 <xref:System.ServiceModel.Discovery.ResolveResponse> Je vrácen do volající <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> metoda s odpověď `Resolve` operaci. Je také k dispozici v <xref:System.ServiceModel.Discovery.ResolveCompletedEventArgs>. Obsahuje instanci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>, což je zjištěné koncových bodů a instance <xref:System.ServiceModel.Discovery.DiscoveryMessageSequence>.  
  
## <a name="servicediscoverybehavior"></a>ServiceDiscoveryBehavior  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Třída umožňuje vývojáři přidat funkci zjišťování k službě. Přidání tohoto chování <xref:System.ServiceModel.ServiceHost>. <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Třídy iteruje nad koncových bodů aplikace přidat do hostitele služby a vytvoří kolekci <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> z zjistitelný koncových bodů. Zjistitelný ve výchozím nastavení jsou všechny koncové body. Zjistitelnost o konkrétní koncový bod se dá nastavit podle přidání <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> do daného koncového bodu. Pokud koncových bodů oznámení jsou přidány do <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> pak oznámení všechny koncové body zjistitelný odesílané přes jednotlivých koncových bodů oznámení, pokud hostitel služby je otevřít nebo uzavřený.  
  
## <a name="servicediscoveryextension"></a>ServiceDiscoveryExtension  
 <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension` Třída je vytvořený <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> třídy. Koncové body, které jsou vytvářeny zjistitelný můžete získat z <!--zz <xref:System.ServiceModel.Discovery.ServiceDiscoveryExtension> --> `ServiceDiscoveryExtension`. Tato třída slouží také k určení implementaci vlastní zjišťování služby.  
  
## <a name="udpannouncementendpoint"></a>UdpAnnouncementEndpoint  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Třída je standardní oznámení koncový bod, který je předem nakonfigurovaný pro oznámení přes UDP vícesměrového vysílání vazby. Ve výchozím nastavení <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> je nastavený na použití WSApril2005 WS_Discovery verze.  
  
## <a name="udpdiscoveryendpoint"></a>UdpDiscoveryEndpoint  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Třída je standardní zjišťování koncový bod, který je předem nakonfigurovaný pro zjišťování přes UDP vícesměrového vysílání vazby. Ve výchozím nastavení <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> je nastavený na použití verze WSDiscovery11 WS-Discovery a <!--zz <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.Adhoc>--> `Adhoc` režimu.
