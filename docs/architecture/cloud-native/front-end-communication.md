---
title: Komunikace front-endového klienta
description: Zjistěte, jak front-endklienti komunikují se systémy nativními pro cloud
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: af26873381509df7807db6ecb37a7d73669adb37
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989074"
---
# <a name="front-end-client-communication"></a>Komunikace front-endového klienta

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

V cloudově nativním systému vyžadují klienti front-endu (mobilní, webové a desktopové aplikace) komunikační kanál pro interakci s nezávislými back-endovými mikroslužbami.  

Jaké jsou možnosti?

Chcete-li, aby věci jednoduché, front-end klient a může *přímo komunikovat* s back-endové mikroslužby, znázorněno na obrázku 4-2.

![Přímá komunikace klienta ke službám](./media/direct-client-to-service-communication.png)

**Obrázek 4-2.** Přímá komunikace klienta ke službám

S tímto přístupem má každá mikroslužba veřejný koncový bod, který je přístupný front-endovým klientům. V produkčním prostředí byste umístit nástroje pro vyrovnávání zatížení před mikroslužeb, směrování provozu úměrně.

Zatímco jednoduché implementovat, přímá komunikace klienta by bylo přijatelné pouze pro jednoduché aplikace mikroslužeb. Tento vzor pevně spojuje front-end klienty s jádrem back-end služby, otevírá dveře pro řadu problémů, včetně:

- Náchylnost klienta k refaktoringu back-endové služby.
- Širší prostor pro útok jako základní back-endové služby jsou přímo vystaveny.
- Duplikace průřezových obav v každé mikroslužbě.
- Příliš složitý kód klienta – klienti musí sledovat více koncových bodů a zpracovávat selhání odolným způsobem.

Místo toho široce přijímaný vzor návrhu cloudu je implementovat [službu brány rozhraní API](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) mezi front-endovými aplikacemi a back-endovými službami. Vzorek je znázorněn na obrázku 4-3.

![Vzor brány rozhraní API](./media/api-gateway-pattern.png)

**Obrázek 4-3.** Vzor brány rozhraní API

Na předchozím obrázku si všimněte, jak služba brány rozhraní API abstrahuje back-endové základní mikroslužby. Implementováno jako webové rozhraní API, funguje jako *reverzní proxy server*, směrování příchozí provoz na interní mikroslužeb.

Brána izoluje klienta od vnitřní služby dělení a refaktoring. Pokud změníte back-endslužby, můžete přizpůsobit pro něj v bráně bez porušení klienta. Je to také vaše první obranná linie pro průřezové obavy, jako je identita, ukládání do mezipaměti, odolnost proti chybám, měření a škrcení. Mnohé z těchto průřezových problémů lze odložit z back-endových základních služeb do brány, což zjednodušuje back-endové služby.

Je třeba dbát na to, aby brána rozhraní API byla jednoduchá a rychlá. Obchodní logika je obvykle udržována mimo bránu. Komplexní brána riskuje, že se stane úzkým místem a nakonec samotným monolitem. Větší systémy často zveřejňují více bran rozhraní API segmentovaných podle typu klienta (mobilní, webové, desktopové) nebo back-endové funkce. [Back-end pro front-endy](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) vzor poskytuje směr pro implementaci více bran. Vzorek je znázorněn na obrázku 4-4.

![Vzor brány rozhraní API](./media/backend-for-frontend-pattern.png)

**Obrázek 4-4.** Back-end pro front-endový vzor

Všimněte si na předchozím obrázku, jak se příchozí provoz odesílá do konkrétní brány rozhraní API – na základě typu klienta: web, mobilní nebo desktopová aplikace. Tento přístup má smysl, protože možnosti každého zařízení se výrazně liší v různých faktorech, výkonu a omezeních zobrazení. Mobilní aplikace obvykle zveřejňují méně funkcí než aplikace prohlížeče nebo stolních počítačů. Každá brána může být optimalizována tak, aby odpovídala možnostem a funkcím odpovídajícího zařízení.

Chcete-li začít, můžete vytvořit vlastní službu brány rozhraní API. Rychlé vyhledávání GitHubu poskytne mnoho příkladů. Existuje však několik rámců a komerčních produktů brány, které jsou k dispozici.

## <a name="ocelot-gateway"></a>Ocelot brána

Pro jednoduché aplikace nativní pro cloud .NET můžete zvážit [bránu Ocelot](https://github.com/ThreeMammals/Ocelot). Ocelot je brána rozhraní API s otevřeným zdrojovým kódem vytvořená pro mikroslužby .NET, které vyžadují jednotný vstupní bod do jejich systému. Je lehký, rychlý, škálovatelný.

Stejně jako každá brána rozhraní API, jeho primární funkce je předávat příchozí požadavky HTTP na příjem dat služby. Kromě toho podporuje širokou škálu funkcí, které jsou konfigurovatelné v kanálu middlewaru .NET Core. Jeho sada funkcí je uvedena v následující tabulce.

|Funkce Ocelot  | |
| :-------- | :-------- |
| Směrování | Authentication |
| Agregace požadavků | Autorizace |
| Service Discovery (s konzulem a Eurekou) | Throttling |
| Vyrovnávání zatížení | Protokolování, trasování |
| Ukládání do mezipaměti | Transformace řetězce záhlaví/dotazu |
| Průchod korelace | Vlastní middleware |
| Kvalita služeb | Zásady opakování |

Každá brána Ocelot určuje upstream a downstream adresy a konfigurovatelné funkce v konfiguračním souboru JSON. Klient odešle požadavek HTTP do brány Ocelot. Po přijetí Ocelot předá objekt HttpRequest prostřednictvím svého kanálu, který s ním manipuluje do stavu určeného jeho konfigurací. Na konci kanálu Ocelot vytvoří nový HTTPResponseObject a předá ji navazující služby. Pro odpověď Ocelot obrátí kanál a odešle odpověď zpět klientovi.

Ocelot je k dispozici jako balíček NuGet. Zaměřuje se na net standard 2.0, takže je kompatibilní s rozhraním .NET Core 2.0+ a .NET Framework 4.6.1+ za běhu. Ocelot integruje se vším, co mluví HTTP a běží na platformách, které podporuje .NET Core: Linux, macOS a Windows. Ocelot je rozšiřitelný a podporuje mnoho moderních platforem, včetně kontejnerů Dockeru, služeb Azure Kubernetes nebo jiných veřejných cloudů.  Ocelot se integruje s open-source balíčky, jako je [konzul](https://www.consul.io), [GraphQL](https://graphql.org)a [Eureka Netflixu](https://github.com/Netflix/eureka).

Zvažte Ocelot pro jednoduché aplikace nativní pro cloud, které nevyžadují bohatou sadu funkcí komerční brány rozhraní API.

## <a name="azure-application-gateway"></a>Azure Application Gateway

Pro jednoduché požadavky na bránu můžete zvážit [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/overview). Je k dispozici jako služba Azure [PaaS](https://azure.microsoft.com/overview/what-is-paas/)a obsahuje základní funkce brány, jako je směrování adres URL, ukončení protokolu SSL a brána firewall webové aplikace. Služba podporuje možnosti [vyrovnávání zatížení vrstvy 7.](https://www.nginx.com/resources/glossary/layer-7-load-balancing/) Pomocí vrstvy 7 můžete směrovat požadavky na základě skutečného obsahu zprávy HTTP, nikoli pouze nízkoúrovňových síťových paketů TCP.

V celé této knize evangelizujeme hosting cloud-nativní systémy v [Kubernetes](https://www.infoworld.com/article/3268073/what-is-kubernetes-your-next-application-platform.html). Orchestrátor kontejnerů Kubernetes automatizuje problémy nasazení, škálování a provozu kontejnerizovaných úloh. Azure Application Gateway se dá nakonfigurovat jako bránu rozhraní API pro cluster [služby Azure Kubernetes.](https://azure.microsoft.com/services/kubernetes-service/)

[Ingress controller aplikační brány](https://azure.github.io/application-gateway-kubernetes-ingress/) umožňuje Azure Application Gateway pracovat přímo se [službou Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/). Obrázek 4.5 ukazuje architekturu.

![Kontroler příchozího přenosu dat služby Application Gateway](./media/application-gateway-ingress-controller.png)

**Obrázek 4-5.** Kontroler příchozího přenosu dat služby Application Gateway

Kubernetes obsahuje integrovanou funkci, která podporuje vyrovnávání zatížení HTTP (úroveň 7), nazývanou [Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/). Ingress definuje sadu pravidel pro to, jak mohou být instance mikroslužeb uvnitř AKS vystaveny vnějšímu světu. V předchozí bitové kopii ingress řadič interpretuje pravidla příchozího přenosu dat nakonfigurované pro cluster a automaticky konfiguruje Aplikační brána Azure. Na základě těchto pravidel, application gateway směruje provoz na mikroslužby spuštěné uvnitř AKS. Ingress řadič naslouchá změnám pravidel příchozího přenosu dat a provede příslušné změny brány aplikace Azure.

## <a name="azure-api-management"></a>Azure API Management

Pro středně rozsáhlé až rozsáhlé cloudové nativní systémy můžete zvážit [Azure API Management](https://azure.microsoft.com/services/api-management/). Jedná se o cloudovou službu, která nejen řeší vaše potřeby brány rozhraní API, ale poskytuje plnohodnotné vývojářské a administrativní prostředí. Správa rozhraní API je znázorněna na obrázku 4-6.

![Azure API Management](./media/azure-api-management.png)

**Obrázek 4-6.** Azure API Management

Chcete-li spustit, api management zpřístupňuje server brány, který umožňuje řízený přístup ke službám back-end na základě konfigurovatelných pravidel a zásad. Tyto služby můžou být v cloudu Azure, v datovém centru on-prem nebo v jiných veřejných cloudech. Klíče ROZHRANÍ API a tokeny JWT určují, kdo může co dělat. Veškerý provoz je zaznamenán pro analytické účely.

Pro vývojáře nabízí api Management vývojářský portál, který poskytuje přístup ke službám, dokumentaci a ukázkovému kódu pro jejich vyvolání. Vývojáři můžou pomocí rozhraní Swagger/Open API kontrolovat koncové body služby a analyzovat jejich využití. Služba funguje napříč hlavními vývojovými platformami: .NET, Java, Golang a další.

Portál vydavatele zpřístupňuje řídicí panel správy, kde správci zveřejňují rozhraní API a spravují jejich chování. Přístup ke službě může být udělen, stav služby monitorován a služba telemetrie shromážděny. Správci používají *zásady* pro každý koncový bod ovlivnit chování. [Zásady](https://docs.microsoft.com/azure/api-management/api-management-howto-policies) jsou předem sestavené příkazy, které se spouštějí postupně pro každé volání služby.  Zásady jsou konfigurovány pro příchozí volání, odchozí volání nebo vyvolány při chybě. Zásady lze použít v různých oborech služby, aby bylo možné deterministické řazení při kombinování zásad. Výrobek je dodáván s velkým počtem předem vytvořených [politik](https://docs.microsoft.com/azure/api-management/api-management-policies).

Tady jsou příklady toho, jak můžou zásady ovlivnit chování vašich cloudových nativních služeb:  

- Omezte přístup ke službě.
- Vynucujte ověřování.  
- Omezení volání z jednoho zdroje, v případě potřeby.
- Povolte ukládání do mezipaměti.
- Blokovat volání z konkrétních IP adres.
- Řízení toku služby.
- Převést požadavky z SOAP do REST nebo mezi různými formáty dat, například z XML na JSON.

Azure API Management můžete vystavit back-end ové služby, které jsou hostované kdekoli – v cloudu nebo datovém centru. Pro starší služby, které můžete vystavit ve vašich cloudových nativních systémech, podporuje rozhraní API REST i SOAP. I ostatní služby Azure můžou být zpřístupněny prostřednictvím správy rozhraní API. Spravované rozhraní API můžete umístit nad záložní službu Azure, jako je [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) nebo Azure Logic [Apps](https://azure.microsoft.com/services/logic-apps/). Azure API Management nezahrnuje integrovanou podporu vyrovnávání zatížení a měla by se používat ve spojení se službou vyrovnávání zatížení.

Azure API Management je k dispozici ve [čtyřech různých vrstvách](https://azure.microsoft.com/pricing/details/api-management/):

- Developer
- Základní
- Standard
- Premium

Úroveň Developer je určena pro neprodukční úlohy a hodnocení. Ostatní úrovně nabízejí postupně větší výkon, funkce a smlouvy o vyšší úrovni služeb (SLA). Úroveň Premium poskytuje [podporu virtuální sítě Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) a více [oblastí](https://docs.microsoft.com/azure/api-management/api-management-howto-deploy-multi-region). Všechny úrovně mají pevnou cenu za hodinu.

Nedávno Microsoft oznámil [úroveň bez serveru pro](https://azure.microsoft.com/blog/announcing-azure-api-management-for-serverless-architectures/) Azure API Management. Tato služba, označovaná jako *cenová úroveň spotřeby*, je variantou správy rozhraní API navržené kolem výpočetního modelu bez serveru. Na rozdíl od dříve zobrazených cenových úrovní "předem přidělené", úroveň spotřeby poskytuje okamžité zřizování a ceny za akci.

Umožňuje funkce brány rozhraní API pro následující případy použití:

- Mikroslužby implementované pomocí technologií bez serveru, jako jsou [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview) a Azure [Logic Apps](https://azure.microsoft.com/services/logic-apps/).
- Prostředky azure zálohování služeb, jako jsou fronty service bus a témata, úložiště Azure a další.
- Mikroslužeb, kde má příležitostné velké špičky, ale zůstává nízká většinu času.

Úroveň spotřeby používá stejné základní součásti správy rozhraní API služby, ale využívá zcela jinou architekturu založenou na dynamicky přidělených prostředcích. Dokonale ladí s výpočetním modelem bez serveru:

- Žádná infrastruktura ke správě.
- Žádná nečinná kapacita.
- Vysoká dostupnost.
- Automatické škálování.
- Náklady jsou založeny na skutečném využití.
  
Nová úroveň spotřeby je skvělou volbou pro cloudové nativní systémy, které zveřejňují prostředky bez serveru jako rozhraní API.

> V době psaní úrovně spotřeby je ve verzi preview v cloudu Azure.

## <a name="real-time-communication"></a>Komunikace v reálném čase

Komunikace v reálném čase nebo nabízená komunikace je další možností pro front-endové aplikace, které komunikují s back-endnativními cloudovými systémy přes HTTP. Aplikace, jako jsou finanční tickers, online vzdělávání, hraní her a aktualizace pokroku v zaměstnání, vyžadují okamžité reakce v reálném čase ze back-endu. Při normální komunikaci HTTP neexistuje žádný způsob, jak klient vědět, kdy jsou k dispozici nová data. Klient musí průběžně *dotazování* nebo odesílat požadavky na server. Díky komunikaci v *reálném čase* může server kdykoli doklienta zasílat nová data.

Systémy v reálném čase jsou často charakterizovány vysokofrekvenčními datovými toky a velkým počtem souběžných klientských připojení. Ruční implementace připojení v reálném čase se může rychle stát složitým, což vyžaduje netriviální infrastrukturu, která zajišťuje škálovatelnost a spolehlivé zasílání zpráv připojeným klientům. Můžete se ocitnout ve správě instance mezipaměti Azure Redis a sady vykladačů zatížení nakonfigurovaných s nepřístupnými relacemi pro spřažení klientů.

[Azure SignalR Service](https://azure.microsoft.com/services/signalr-service/) je plně spravovaná služba Azure, která zjednodušuje komunikaci v reálném čase pro vaše aplikace nativní pro cloud. Podrobnosti technické implementace, jako je zřizování kapacity, škálování a trvalá připojení, jsou abstrahovány. Jsou za vás zpracovány s 99,9% smlouvou o úrovni služeb. Zaměřujete se na funkce aplikace, nikoli na infrastrukturu.

Jakmile je povolena, cloudová služba HTTP může tlačit aktualizace obsahu přímo připojeným klientům, včetně prohlížečových, mobilních a desktopových aplikací. Klienti jsou aktualizovány bez nutnosti dotazování serveru. Azure SignalR abstrahuje technologie přenosu, které vytvářejí připojení v reálném čase, včetně websocketů, událostí na straně serveru a dlouhého dotazování. Vývojáři se zaměřují na odesílání zpráv do všech nebo konkrétních podmnožin připojených klientů.

Obrázek 4-7 znázorňuje sadu klientů HTTP, kteří se připojují k aplikaci nativní pro cloud s povoleným Azure SignalR.

![Azure SignalR](./media/azure-signalr-service.png)

**Obrázek 4-7.** Azure SignalR

Další výhodou služby Azure SignalR je implementace cloudových nativních služeb bez serveru. Možná, že váš kód se spustí na vyžádání s Azure Functions aktivačních událostí. Tento scénář může být složité, protože váš kód neudržuje dlouhá připojení s klienty. Služba Azure SignalR dokáže tuto situaci řešit díky tomu, že už za vás spravuje připojení.

Služba Azure SignalR se úzce integruje s dalšími službami Azure, jako je Azure SQL Database, Service Bus nebo Redis Cache, což otevírá mnoho možností pro vaše nativní aplikace v cloudu.

>[!div class="step-by-step"]
>[Předchozí](communication-patterns.md)
>[další](service-to-service-communication.md)
