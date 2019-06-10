---
title: Doporučení pro webové aplikace ASP.NET Core hostování Azure
description: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure | Doporučení pro webové aplikace ASP.NET hostování Azure
author: ardalis
ms.author: wiwagn
ms.date: 06/06/2019
ms.openlocfilehash: 7cfb9ada4f963aa392a41cfb9f1b2df22f542d41
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758727"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Doporučení pro webové aplikace ASP.NET Core hostování Azure

> "Řádku obchodní vedení všude, kde jsou obcházení oddělení IT získat aplikace z cloudu (SaaS) a platit za ně je stejně, jako kdyby je sdíleli předplatné magazine. A když služby se už nevyžaduje, se předplatné zrušit se žádná zařízení left nepoužívané v pravém rohu."  
> _\- Daryl Plummer, analytik společnosti Gartner_

Všechno, co vaše aplikace potřebám a architekturu, Microsoft Azure může podporovat. Hostování potřeb může být stejně jednoduché jako statický web nebo sofistikované aplikace tvořené řadě služeb. Monolitické webové aplikace ASP.NET Core a podpůrných služeb existují některé známé konfigurace, které se doporučují. Doporučení v tomto článku se seskupují podle druhu prostředku hostovat, zda celé aplikace, jednotlivé procesy nebo data.

## <a name="web-applications"></a>Webové aplikace

Pomocí se dají hostovat webové aplikace:

- App Service Web Apps

- Kontejnery (několik možnosti)

- Virtuální počítače (VM)

App Service Web Apps z nich je doporučený postup pro většinu scénářů, včetně jednoduchých aplikací založených na kontejnerech. Pro architekturu mikroslužeb zvažte přístupu založených na kontejnerech. Pokud potřebujete větší kontrolu nad počítače spuštěné aplikace, zvažte Azure Virtual Machines.

### <a name="app-service-web-apps"></a>App Service Web Apps

App Service Web Apps nabízí plně spravovaná platforma optimalizovaná pro hostování webových aplikací. Je platforma jako služba (PaaS), nabídky, že vám umožní soustředit na obchodní logiku, zatímco Azure zajistí infrastrukturu potřebné k spouštění a škálování aplikace. Některé klíčové funkce služby App Service Web Apps:

- Optimalizace DevOps (průběžná integrace a doručování, více prostředí, A / B testování, podpora skriptování).

- Globální škálování a vysokou dostupnost.

- Připojení k platformám SaaS a firemními daty.

- Zabezpečení a dodržování předpisů.

- Integrace se sadou Visual Studio.

Azure App Service je nejlepší volbou pro většinu webových aplikací. Nasazení a správa jsou integrované do platformy, weby se rychle škálují pro zvládnutí vysokého přenosového zatížení a integrované zatížení vyrovnávání a traffic manager zajišťují vysokou dostupnost. Můžete přesunout existující weby do služby Azure App Service snadno se online nástroje pro migraci, použijte open source aplikaci z Galerie webových aplikací nebo vytvoření nového webu pomocí rozhraní a nástrojů podle vašeho výběru. Funkce WebJobs umožňuje snadno přidat úlohy na pozadí zpracování do webové aplikace služby App Service. Pokud už máte existující aplikace ASP.NET hostované v místním prostředí pomocí místní databázi, není jasný migrovat aplikace do webové aplikace služby App Service pomocí Azure SQL Database (nebo zabezpečený přístup k vaší místní databázový server, pokud tomu dávají přednost).

![Strategii doporučené migrace místních aplikací .NET do služby Azure App Service](./media/image1-6.png)

Ve většině případů přesouvá z místně hostované aplikace ASP.NET do webové aplikace služby App Service je jednoduchý proces. By měl být žádné nebo téměř žádné úpravy požadované aplikace a můžete rychle začít využívat řadu funkcí, které nabízí Azure App Service Web Apps.

Kromě toho aplikace, které nejsou optimalizovány pro cloud Azure App Service Web Apps jsou vynikající řešení pro spoustu jednoduché monolitické (nedistribuovaná) aplikací, jako je například velký počet aplikací ASP.NET Core. V takovém případě je architektura základní a snadno zjistit a spravovat:

![Základní architektura služby Azure](./media/image1-5.png)

Ke správě takové aplikace obvykle stačí malý počet prostředků v jedné skupiny prostředků. Aplikace, které jsou obvykle implementovány jako jednu jednotku, a ne na aplikace, které se skládá z mnoha samostatné procesy, jsou vhodnými kandidáty pro tuto [architektonický přístup umožňuje základní](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app). I když jsou architektonicky jednoduché, tento přístup umožňuje stále hostované aplikace škálovat i (Další prostředků na uzel) a out (více uzly prostředí) pro splnění zvýšení poptávky. S automatickým Škálováním můžete aplikaci nakonfigurovat má automaticky upravovat počet uzlů, který je hostitelem aplikace podle potřeby a průměrné zatížení mezi uzly.

### <a name="app-service-web-apps-for-containers"></a>App Service Web Apps for Containers

Kromě podpory pro hostování webových aplikací přímo [App Service Web Apps for Containers](https://azure.microsoft.com/services/app-service/containers/) je možné ke spouštění kontejnerizovaných aplikací ve Windows a Linuxu. Používání této služby, můžete snadno nasadit a spouštění kontejnerizovaných aplikací, které je možné škálovat podle vaší společnosti. Aplikace mají všechny funkce App Service Web Apps uvedené výše. Kromě toho Web Apps for Containers podporu přímočarý CI/CD s Docker Hub, Azure Container Registry a Githubu. Azure DevOps můžete použít k definování kanály sestavení a nasazení, které publikujte změny do registru. Tyto změny a otestovat v testovacím prostředí a automaticky nasadí do produkčního prostředí používání slotů nasazení, umožňující upgrady nulovými výpadky. Stejně snadno můžete provést vrácení zpět na předchozí verze.

Existuje několik scénářů, ve kterém Web Apps for Containers nejvíc vyplatí. Pokud máte existující aplikace, které můžete umístit, ať už v kontejnerech Windows nebo Linux, které můžete hostovat snadno pomocí této sady nástrojů. Jednoduše publikovat svůj kontejner a pak nakonfigurujte Web Apps for Containers ke stahování nejnovější verzi této image z registru podle výběru. Toto je "lift and shift" Postup migrace z klasické aplikaci pro hostování modely do optimalizovaných cloudů modelu.

![Migrace kontejnerizovaných místní aplikace .NET do Azure Web Apps for Containers](./media/image1-8.png)

Tento přístup také funguje dobře, pokud je váš vývojový tým moci přesunout do procesu vývoje založených na kontejnerech. "Vnitřní smyčka" vývoj aplikací s kontejnery zahrnuje vytvoření aplikace s kontejnery. Změny provedené v kódu a jde o konfiguraci kontejneru jsou vloženy do správy zdrojového kódu a automatické sestavení je zodpovědný za publikování nových imagí kontejneru do registru, jako je Docker Hub nebo Azure Container Registry. Tyto Image se použije jako základ pro další rozvoj, stejně jako pro nasazení do produkčního prostředí, jak je znázorněno v následujícím diagramu:

![Docker koncového pracovního postupu životní cyklus DevOps](./media/image1-7.png)

Vývoj s využitím kontejnerů nabízí celou řadu výhod, zejména v případě, že kontejnery se používají v produkčním prostředí. Stejnou konfiguraci kontejneru se používá k hostování aplikace v každé prostředí, ve kterém je spuštěna, od místního vývojového počítače pro sestavení a testování systémů do produkčního prostředí. To významně snižuje pravděpodobnost, že vady vyplývající z rozdíly v konfiguraci počítače nebo verze softwaru. Vývojáři mohou také použít libovolné nástroje jsou nejproduktivnější, včetně operačního systému, protože kontejnery můžete spustit na jakémkoli operačním systému. V některých případech může být distribuovaných aplikací zahrnující mnoho kontejnerů velmi náročné ke spuštění na jednoho vývojového počítače. V tomto scénáři může být vhodné, upgrade na Kubernetes a prostory vývoj Azure, najdete v další části.

Jak částí větších aplikací jsou rozdělené do své vlastní menší nezávislé *mikroslužeb*, další návrhové vzory slouží ke zlepšení chování aplikace. Místo abyste pracovali přímo pomocí individuálních služeb, *Brána rozhraní API* můžete zjednodušit přístup a oddělit klienta z back-endu. Samostatná služba back-endů pro různých front-endů také umožňuje služby vyvíjí společně s jejich příjemce. Běžné služby přístupné přes samostatné *sajdkára* kontejneru, která by mohla obsahovat společné knihovny pro připojení klienta pomocí *ambasador* vzor.

![Architektura Mikroslužeb ukázkový s několika běžných vzorů návrhů jste si poznamenali.](./media/image1-10.png)

[Další informace o vzorech návrhu, které je třeba zvážit při sestavování systémů založených na mikroslužbách.](https://docs.microsoft.com/azure/architecture/microservices/design/patterns)

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Azure Kubernetes Service (AKS) spravuje hostované prostředí Kubernetes, tak rychle a snadno nasazovat a spravovat kontejnerizované aplikace bez znalosti Orchestrace kontejnerů. Také odstraní starosti související s probíhajícími operacemi a údržbou díky zřizování, upgradování a škálování prostředků na vyžádání, bez nutnosti přepínat aplikace do offline režimu.

AKS snižuje složitost a provozní režií při správě clusteru Kubernetes tím spojenou díky přenášení většiny zodpovědnosti na Azure. Jako hostovaná služba Kubernetes, Azure stará o důležité úlohy jako sledování stavu a údržby za vás. Navíc Platíte pouze za agentské uzly v rámci vašich clusterů, ne za hlavní uzly. Jako spravovaná služba Kubernetes poskytuje AKS:

- Automatické upgrady verzí Kubernetes a opravy chyb.
- Snadné škálování clusterů.
- Hostovanou rovinu řízení (hlavní uzly).
- Úspory nákladů – Platíte pouze za spuštěné uzly fondu agentů.

S Azure stará o správu uzlů ve vašem clusteru AKS už nepotřebujete provádět mnoho úloh ručně, například upgrady clusteru. Protože Azure stará o tyto důležité úlohy údržby za vás, neposkytuje AKS přímý přístup (například pomocí protokolu SSH) do clusteru.

Týmy, které využívají AKS můžete také využít Azure Dev mezery. Azure Dev prostorech týmům soustředit se víc o rozvoji a rychlé iterace jejich aplikace mikroslužeb tím, že týmy pracovat přímo s jejich architektuře mikroslužeb celý nebo aplikace spuštěná ve službě AKS. Azure Dev prostory také poskytuje způsob, jak nezávisle aktualizovat část vaší architektury mikroslužeb v izolaci bez vlivu na zbytek jinými vývojáři nebo clusteru AKS.

![Příklad pracovního postupu Azure Dev mezery](./media/image1-9.gif)

Azure Dev mezery:

- Minimalizujte požadavky času a prostředků nastavení místního počítače
- Umožňuje týmům Iterujte rychleji
- Snížit počet prostředí integrace vyžaduje tým
- Odebrat muset napodobení určité služby v distribuovaném systému při vývoji a testování

[Další informace o prostorech vývoj Azure](https://docs.microsoft.com/azure/dev-spaces/about)

### <a name="azure-virtual-machines"></a>Azure Virtual Machines

Pokud máte existující aplikace, které by vyžadovaly výrazné změny ke spuštění ve službě App Service, můžete zvolením služby Virtual Machines pro zjednodušení migrace do cloudu. Ale správně konfiguraci, zabezpečení a správu virtuálních počítačů vyžaduje mnohem více času a znalosti v oboru IT ve srovnání s Azure App Service. Pokud zvažujete Azure Virtual Machines, nezapomeňte že vzít v úvahu náročnost průběžné údržby vyžaduje opravu, aktualizovat a spravovat prostředí virtuálních počítačů. Azure Virtual Machines je infrastruktura jako služba (IaaS), zatímco App Service nabízí PaaS. Měli byste také zvážit, zda nasazení vaší aplikace jako kontejner Windows do služby Web App for Containers může být vhodným řešením pro váš scénář.

## <a name="logical-processes"></a>Logické procesy

Jednotlivé logické procesy, které mohou být oddělené od zbytku aplikace může nezávisle nasadit do služby Azure Functions v podobě "bez serveru". Azure Functions umožňuje stačí napsat kód, který budete potřebovat pro daný problém, ale nemusíme se starat o aplikaci nebo infrastrukturu k jeho spuštění. Můžete si vybrat z nejrůznějších programovacích jazyků, včetně C\#, F\#, Node.js, Python a PHP, umožní vám vybrat nejproduktivnější jazyk pro úlohy po ruce. Jako většina řešení založené na cloudu platíte jenom po zadanou dobu používání a Azure Functions vertikálně navýšit kapacitu podle potřeby můžete důvěřovat.

## <a name="data"></a>Data

Azure nabízí širokou škálu možnosti ukládání dat, tak, aby aplikace můžete používat poskytovatele příslušná data pro dotyčný data.

Pro transakční, relační data Azure SQL Database se nejlepší možností. Pro vysoký výkon pro čtení – většinou data mezipaměti Redis se opírá o službě Azure SQL Database je dobrým řešením.

Nestrukturovaná data JSON mohou být uloženy v různými způsoby, z databáze SQL sloupců pro objekty BLOB nebo tabulek ve službě Azure Storage k DocumentDB. Z těchto DocumentDB nabízí nejlepší funkcích pro dotazování a možnost se doporučuje pro velké počty dokumentů založenými na JSON, které musí podporovat dotazování.

Přechodné příkazu - nebo založený na událostech data použít k orchestrování chování aplikace pomocí Azure Service Bus nebo front Azure Storage. Azure Service Bus úložiště nabízí větší flexibilitu a je doporučenou službu pro netriviální zasílání zpráv v rámci a mezi aplikacemi.

## <a name="architecture-recommendations"></a>Doporučení pro architekturu

Podle požadavků vaší aplikace by měly určovat jeho architektura. Nejsou k dispozici mnoho různých služeb Azure. Důležité rozhodnutí je výběr ten správný. Společnost Microsoft nabízí Galerie referenční architektury, které pomáhají identifikovat typických architekturách, které jsou optimalizované pro běžné scénáře. Může se stát referenční architekturu, map, pečlivě sledují a podle požadavků vaší aplikace nebo na nejméně nabízí, počáteční bod.

Obrázek 11-2 je znázorněný příklad referenční architekturu. Tento diagram znázorňuje postup doporučené architektury pro web systém správy obsahu Sitecore optimalizované pro uvedení na trh.

![](./media/image11-2.png)

**Obrázek 11-1.** Sitecore marketingový web referenční architekturu.

**Odkazy – hostování doporučení pro Azure**

- Architectures\ řešení Azure
  <https://azure.microsoft.com/solutions/architecture/>

- Architecture\ Azure základní webové aplikace
  <https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app>

- Způsoby návrhu pro Microservices\
  <https://docs.microsoft.com/azure/architecture/microservices/design/patterns>

- Azure Developer Guide\
  <https://azure.microsoft.com/campaigns/developer-guide/>

- Overview\ webové aplikace
  <https://docs.microsoft.com/azure/app-service/app-service-web-overview>

- Web App for Containers\
  <https://azure.microsoft.com/services/app-service/containers/>

- Úvod do služby Azure Kubernetes Service (AKS) \
  <https://docs.microsoft.com/azure/aks/intro-kubernetes>

>[!div class="step-by-step"]
>[Předchozí](development-process-for-azure.md)
