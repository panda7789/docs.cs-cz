---
title: Komunikace front-endového klienta
description: Informace o tom, jak klienti front-endu komunikují s nativními systémy cloudu
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 97421e9b90b19c720b1ab0ff8dd1e5f029cba5e4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614055"
---
# <a name="front-end-client-communication"></a>Komunikace front-endového klienta

V rámci nativního cloudového systému musí klienti front-end (mobilní, webové a desktopové aplikace) komunikovat s nezávislými mikroslužbami.  

Jaké jsou možnosti?

Aby bylo možné tyto věci jednoduché, může klient front-end *komunikovat přímo* s back-end mikroslužbami, které jsou znázorněné na obrázku 4-2.

![Směrování komunikace mezi klientem a službou](./media/direct-client-to-service-communication.png)

**Obrázek 4-2.** Směrování komunikace mezi klientem a službou

S tímto přístupem má každá mikroslužba veřejný koncový bod, ke kterému mají přístup klienti front-end. V produkčním prostředí byste si vyrovnávání zatížení umístili před mikroslužby a poměrně směrují provoz.

I když je jednoduchá implementace, je přímá komunikace s klientem přijatelná jenom pro jednoduché aplikace mikroslužeb. Tento model těsně Couples klientské klienty na základní back-endové služby a otevírá dvířka pro řadu problémů, včetně:

- Náchylnost klienta k refaktoringu služby back-end.
- Širší plocha pro útoky, jako jsou základní back-endové služby, je přímo vystavená.
- Duplikace otázek mezi jednotlivými mikroslužbami mezi průřezy.
- Vysoce složitý klientský kód – klienti musí sledovat více koncových bodů a zpracovávat chyby odolným způsobem.

Místo toho široce přijatý model návrhu cloudu je implementace [služby API Gateway](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) mezi front-end aplikacemi a back-end službami. Vzor je zobrazen na obrázku 4-3.

![Vzor brány API](./media/api-gateway-pattern.png)

**Obrázek 4-3.** Vzor brány API

Na předchozím obrázku si všimněte, jak služba brány rozhraní API abstrakce back-endové základní mikroslužby. Implementované jako webové rozhraní API funguje jako *reverzní proxy server*, který směruje příchozí provoz do interních mikroslužeb.

Brána zaizolační klienta z interního vytváření oddílů a refaktoringu služby. Změníte-li back-endové služby, budete pro ni pro bránu v bráně, aniž by došlo k narušení klienta. Je také první linií obrany pro průřezy, jako je například identita, ukládání do mezipaměti, odolnost, měření a omezování. Mnohé z těchto otázek mezi jednotlivými průřezy je možné z back-endové základní služby na bránu vypnout a zjednodušit tak back-endové služby.

Je potřeba zajistit, aby brána API byla jednoduchá a rychlá. Obchodní logika se obvykle uchovává mimo bránu. Složitá rizika brány se stávají kritickým bodem a nakonec monolitu sám sebe. Větší systémy často zveřejňují několik bran API, které jsou segmentované podle typu klienta (mobilní, webové, desktopové) nebo funkce back-endu. Vzor [back-endu pro front-endu](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) nabízí směr pro implementaci více bran. Vzor je zobrazen na obrázku 4-4.

![Vzor brány API](./media/backend-for-frontend-pattern.png)

**Obrázek 4-4.** Back-end pro vzor front-endu

Všimněte si, jak se na předchozím obrázku odesílají příchozí přenosy na konkrétní bránu API – na základě typu klienta: webové, mobilní nebo desktopové aplikace. Tento přístup má smysl, protože možnosti jednotlivých zařízení se výrazně liší v rámci omezení počtu formulářů, výkonu a zobrazení. Mobilní aplikace obvykle zpřístupňují méně funkcí než prohlížeč nebo desktopové aplikace. Každou bránu je možné optimalizovat tak, aby odpovídala možnostem a funkcím příslušného zařízení.

Začněte tím, že vytvoříte vlastní službu API Gateway. Rychlé prohledání GitHubu vám nabídne mnoho příkladů. K dispozici je však několik platforem a komerčních produktů brány.

## <a name="ocelot-gateway"></a>Ocelot bránu

V případě jednoduchých cloudových aplikací .NET je vhodné zvážit [bránu ocelot](https://github.com/ThreeMammals/Ocelot). Ocelot je open source brána API vytvořená pro mikroslužby .NET, které vyžadují jednotný bod vstupu do systému. Je to odlehčené, rychlé a škálovatelné.

Stejně jako u libovolné brány rozhraní API je jejich primární funkce předávána příchozím požadavkům HTTP na služby pro příjem dat. Kromě toho podporuje širokou škálu funkcí, které lze konfigurovat v kanálu middlewaru .NET Core. Její sada funkcí je uvedena v následující tabulce.

|Funkce Ocelot  | |
| :-------- | :-------- |
| Směrování | Authentication |
| Agregace požadavků | Autorizace |
| Zjišťování služeb (s Consul a Eureka) | Throttling |
| Vyrovnávání zatížení | Protokolování, trasování |
| Ukládání do mezipaměti | Transformace hlaviček nebo řetězce dotazu |
| Průchod korelacemi | Vlastní middleware |
| Kvalita služby | Zásady opakování |

Každá brána Ocelot Určuje nadřazené a podřízené adresy a konfigurovatelné funkce v konfiguračním souboru JSON. Klient odešle požadavek HTTP do brány Ocelot. Po přijetí Ocelot předá objekt HttpRequest prostřednictvím kanálu, který ho manipuluje do stavu určeného jeho konfigurací. Na konci kanálu Ocelot vytvoří nový HTTPResponseObject a předá ho službě pro příjem dat. Pro odpověď Ocelot obrátí kanál a odešle odpověď zpět klientovi.

Ocelot je k dispozici jako balíček NuGet. Cílí na síť Standard 2,0, která je kompatibilní s .NET Core 2.0 + i .NET Framework 4.6.1 + runtime. Ocelot se integruje s cokoli, co mluví s HTTP a běží na platformách, které .NET Core podporuje: Linux, macOS a Windows. Ocelot je rozšiřitelná a podporuje mnoho moderních platforem, včetně kontejnerů Docker, služeb Azure Kubernetes nebo jiných veřejných cloudů.  Ocelot se integruje s open source balíčky, jako je [Consul](https://www.consul.io), [GraphQL](https://graphql.org)a Netflix [Eureka](https://github.com/Netflix/eureka).

Zvažte Ocelot pro jednoduché aplikace nativní pro Cloud, které nevyžadují bohatou sadu funkcí komerční brány API.

## <a name="azure-application-gateway"></a>Azure Application Gateway

V případě požadavků na jednoduchou bránu můžete zvážit [Application Gateway Azure](https://docs.microsoft.com/azure/application-gateway/overview). K dispozici jako [Služba Azure PaaS](https://azure.microsoft.com/overview/what-is-paas/), zahrnuje základní funkce brány, jako je směrování adres URL, ukončení protokolu SSL a firewall webových aplikací. Služba podporuje funkce [Vyrovnávání zatížení vrstvy 7](https://www.nginx.com/resources/glossary/layer-7-load-balancing/) . U vrstvy 7 můžete směrovat požadavky na základě skutečného obsahu zprávy HTTP, nikoli jenom síťových paketů TCP nízké úrovně.

V celé této příručce jsme evangelizovat hostování nativních systémů cloudu v [Kubernetes](https://www.infoworld.com/article/3268073/what-is-kubernetes-your-next-application-platform.html). Produkt Orchestrator v kontejneru Kubernetes automatizuje nasazení, škálování a provozní obavy týkající se kontejnerových úloh. Azure Application Gateway můžete nakonfigurovat jako bránu rozhraní API pro cluster [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) .

[Kontroler Application Gateway](https://azure.github.io/application-gateway-kubernetes-ingress/) příchozího přenosu dat umožňuje službě Azure Application Gateway pracovat přímo se [službou Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/). Obrázek 4,5 ukazuje architekturu.

![Kontroler příchozího přenosu dat služby Application Gateway](./media/application-gateway-ingress-controller.png)

**Obrázek 4-5.** Kontroler příchozího přenosu dat služby Application Gateway

Kubernetes zahrnuje integrovanou funkci, která podporuje vyrovnávání zatížení HTTP (Level 7), které [se nazývá příchozí](https://kubernetes.io/docs/concepts/services-networking/ingress/)přenos dat. Příchozí připojení definuje sadu pravidel, jak můžou být instance mikroslužeb uvnitř AKS vystaveny vnějšímu světě. Na předchozím obrázku kontroler příchozího přenosu dat přeloží pravidla příchozího přenosu nakonfigurovaná pro cluster a automaticky nakonfiguruje Application Gateway Azure. Na základě těchto pravidel Application Gateway směruje provoz na mikroslužby běžící v rámci AKS. Kontroler příchozího přenosu dat naslouchá změnám pravidel příchozího přenosu dat a provádí příslušné změny v Application Gateway Azure.

## <a name="azure-api-management"></a>Azure API Management

Pro středně velká až rozsáhlá cloudová řešení systému můžete zvážit [API Management Azure](https://azure.microsoft.com/services/api-management/). Jedná se o cloudovou službu, která nejen vyřeší vaše požadavky na bránu API, ale poskytuje plnohodnotné vývojářské a administrativní prostředí. API Management se zobrazuje na obrázku 4-6.

![Azure API Management](./media/azure-api-management.png)

**Obrázek 4-6.** Azure API Management

Aby bylo možné začít, API Management zveřejňuje server brány, který umožňuje řízený přístup k back-endové službě na základě konfigurovatelných pravidel a zásad. Tyto služby můžou být v cloudu Azure, v Prem datovém centru nebo v jiných veřejných cloudech. Klíče rozhraní API a tokeny JWT určují, kdo může co dělat. Veškerý provoz se protokoluje pro účely analýzy.

Pro vývojáře API Management nabízí portál pro vývojáře, který poskytuje přístup ke službám, dokumentaci a ukázkovému kódu pro jejich vyvolání. Vývojáři můžou k kontrole koncových bodů služby a k analýze jejich využití použít rozhraní Swagger nebo Open API. Služba funguje v rámci hlavních vývojových platforem: .NET, Java, golang a další.

Portál vydavatele zveřejňuje řídicí panel pro správu, ve kterém správci zveřejňují rozhraní API a spravují jejich chování. Přístup k službě se dá udělit, sledovat stav služby a shromažďovat telemetrii o službě. Správci aplikují *zásady* na každý koncový bod tak, aby ovlivnily chování. [Zásady](https://docs.microsoft.com/azure/api-management/api-management-howto-policies) jsou předem sestavené příkazy, které se spouštějí postupně pro každé volání služby.  Zásady jsou nakonfigurovány pro příchozí volání, odchozí volání nebo při chybě vyvolány. Zásady je možné použít v různých oborech služby, které umožňují deterministické řazení při kombinování zásad. Produkt se dodává s velkým množstvím předem připravených [zásad](https://docs.microsoft.com/azure/api-management/api-management-policies).

Tady jsou příklady, jak můžou zásady ovlivnit chování vašich cloudových nativních služeb:  

- Omezte přístup k službě.
- Vyvynuťte ověřování.  
- V případě potřeby omezení volání z jednoho zdroje.
- Povolit ukládání do mezipaměti.
- Zablokuje volání z konkrétních IP adres.
- Řízení toku služby.
- Převeďte požadavky z SOAP na REST nebo mezi různými datovými formáty, jako je například z XML na JSON.

Azure API Management může vystavovat back-endové služby, které jsou hostované kdekoli – v cloudu nebo v datovém centru. U starších služeb, které můžete zveřejnit v systémech nativních pro Cloud, podporuje rozhraní API REST i protokolu SOAP. I další služby Azure mohou být zpřístupněny prostřednictvím API Management. Spravované rozhraní API můžete umístit nad službu zálohování Azure, jako je [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) nebo [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/). Služba Azure API Management nezahrnuje integrovanou podporu vyrovnávání zatížení a měla by se používat ve spojení se službou Vyrovnávání zatížení.

Azure API Management je k dispozici ve [čtyřech různých úrovních](https://azure.microsoft.com/pricing/details/api-management/):

- Vývojář
- Základní
- Standard
- Premium

Úroveň pro vývojáře je určena pro úlohy, které nejsou v produkčním prostředí, a vyhodnocení. Ostatní úrovně nabízejí postupně větší možnosti napájení, funkcí a vyšších smluv o úrovni služeb (SLA). Úroveň Premium poskytuje podporu [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) a [více oblastí](https://docs.microsoft.com/azure/api-management/api-management-howto-deploy-multi-region). Všechny úrovně mají pevnou cenu za hodinu.

Cloud Azure také nabízí úroveň bez [serveru](https://azure.microsoft.com/blog/announcing-azure-api-management-for-serverless-architectures/) pro Azure API Management. Tato služba se označuje jako *cenová úroveň spotřeby*, což je varianta API Management navržená kolem výpočetního modelu bez serveru. Na rozdíl od výše uvedených cenových úrovní "předem přidělené" poskytuje úroveň spotřeby okamžité zřizování a ceny za akci.

Umožňuje funkce brány API v následujících případech použití:

- Mikroslužby implementované pomocí technologií bez serveru, jako jsou [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview) a [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/).
- Prostředky služby Azure pro zálohování, například Service Bus fronty a témata, úložiště Azure a další.
- Mikroslužby, ve kterých provoz má příležitostné velké špičky, ale zůstává ve většině času malý čas.

Úroveň spotřeby používá stejné základní součásti API Management služby, ale využívá zcela jinou architekturu založenou na dynamicky přidělených prostředcích. Přesně se zarovnává s výpočetním modelem bez serveru:

- Žádná infrastruktura ke správě.
- Žádná nečinná kapacita.
- Vysoká dostupnost.
- Automatické škálování.
- Náklady vycházejí ze skutečného využití.
  
Nová úroveň spotřeby je skvělou volbou pro systémy nativní pro Cloud, které zveřejňují prostředky bez serveru jako rozhraní API.

## <a name="real-time-communication"></a>Komunikace v reálném čase

Komunikace v reálném čase nebo nabízená oznámení je další možností pro front-endové aplikace, které komunikují s back-end cloudovým systémem přes protokol HTTP. Aplikace, jako jsou finanční služby, vzdělávání online, hry a aktualizace probíhajících úloh, vyžadují okamžité odezvy v reálném čase z back-endu. V případě normální komunikace HTTP neexistuje žádný způsob, jak by klient věděl, že jsou k dispozici nová data. Klient musí nepřetržitě *dotazovat* nebo odesílat požadavky na server. Při komunikaci v *reálném čase* může server kdykoli do klienta nabízet nová data.

Systémy v reálném čase jsou často charakteristické datovými toky s vysokou frekvencí a velkým počtem souběžných připojení klientů. Ruční implementace připojení v reálném čase se může rychle stát složitou a vyžadovat netriviální infrastrukturu, aby se zajistila škálovatelnost a spolehlivé zasílání zpráv připojeným klientům. Mohli byste najít správu instance Azure Redis Cache a sadu nástrojů pro vyrovnávání zatížení nakonfigurovaných s rychlými relacemi pro spřažení klientů.

[Služba signalizace Azure](https://azure.microsoft.com/services/signalr-service/) je plně spravovaná služba Azure, která zjednodušuje komunikaci v reálném čase pro vaše cloudové nativní aplikace. Podrobnosti o technické implementaci, jako je zřizování kapacity, škálování a trvalá připojení, se odříznout. Jsou zpracovávány za vás s 99,9% smlouvou o úrovni služeb. Zaměřte se na funkce aplikace, ne na instalace infrastruktury.

Po povolení může cloudová služba HTTP nabízet aktualizace obsahu přímo připojeným klientům, včetně prohlížeče, mobilních aplikací a aplikací klasické pracovní plochy. Klienti se aktualizují bez nutnosti cyklického dotazování serveru. Signál Azure vyabstrakce transportní technologie, které vytvářejí připojení v reálném čase, včetně WebSockets, událostí na straně serveru a dlouhého cyklického dotazování. Vývojář se zaměřuje na posílání zpráv na všechny nebo konkrétní podmnožiny připojených klientů.

Obrázek 4-7 ukazuje sadu klientů HTTP připojujících se k nativní aplikaci cloudu s povolenou službou Azure Signal.

![Azure SignalR](./media/azure-signalr-service.png)

**Obrázek 4-7.** Azure SignalR

Další výhodou služby signalizace Azure je implementace cloudových služeb bez serveru. Je možné, že váš kód je spuštěn na vyžádání s Azure Functions triggery. Tento scénář může být obtížné, protože váš kód neudržuje dlouhá připojení ke klientům. Služba Azure SignalR dokáže tuto situaci řešit díky tomu, že už za vás spravuje připojení.

Služba signalizace Azure se úzce integruje s ostatními službami Azure, jako je Azure SQL Database, Service Bus nebo Redis Cache, a otevírá mnoho možností pro cloudové nativní aplikace.

>[!div class="step-by-step"]
>[Předchozí](communication-patterns.md) 
> [Další](service-to-service-communication.md)
