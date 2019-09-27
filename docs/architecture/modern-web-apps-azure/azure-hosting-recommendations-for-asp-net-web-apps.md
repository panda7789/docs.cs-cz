---
title: Doporučení hostování Azure pro ASP.NET Core Web Apps
description: Architekt moderních webových aplikací pomocí ASP.NET Core a Azure | Doporučení hostování Azure pro webové aplikace v ASP.NET
author: ardalis
ms.author: wiwagn
ms.date: 06/06/2019
ms.openlocfilehash: ed8771a4d79b45d8fad0e5309c886c2e00402ec7
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71331990"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Doporučení hostování Azure pro ASP.NET Core Web Apps

> "Obchodní vedoucí pracovníci obcházejí oddělení IT, aby získali aplikace z cloudu (označované také jako SaaS) a platíte za ně, jako by to bylo předplatné časopisu. A když už službu nepotřebujete, může předplatné zrušit bez nevyužitého zařízení, které se v rohu nepoužívá. "  
> _\- Daryl Plummer, analytik Gartner_

Bez ohledu na potřeby a architekturu vaší aplikace ji Microsoft Azure můžou podporovat. Vaše potřeby hostování můžou být jednoduché jako statický web nebo propracované aplikace tvořené spoustou služeb. Pro ASP.NET Core webové aplikace a podpůrné služby je k dispozici několik známých konfigurací, které se doporučují. Doporučení k tomuto článku jsou seskupená na základě druhu prostředku, který se má hostovat, bez ohledu na to, jestli jsou úplné aplikace, jednotlivé procesy nebo data.

## <a name="web-applications"></a>Webové aplikace

Webové aplikace mohou být hostovány pomocí:

- App Service Web Apps

- Kontejnery (několik možností)

- Virtual Machines (virtuální počítače)

Z těchto důvodů je App Service Web Apps doporučený postup pro většinu scénářů, včetně jednoduchých aplikací založených na kontejnerech. Pro architektury mikroslužeb zvažte přístup založený na kontejneru. Pokud potřebujete větší kontrolu nad počítači, na kterých běží vaše aplikace, vezměte v úvahu Azure Virtual Machines.

### <a name="app-service-web-apps"></a>App Service Web Apps

App Service Web Apps nabízí plně spravovanou platformu optimalizovanou pro hostování webových aplikací. Je to nabídka typu platforma jako služba (PaaS), která vám umožní soustředit se na obchodní logiku, zatímco Azure se postará o infrastrukturu potřebnou ke spuštění a škálování aplikace. Některé klíčové funkce App Service Web Apps:

- Optimalizace DevOps (průběžná integrace a doručování, více prostředí, testování a/B, podpora skriptování).

- Globální škálování a vysoká dostupnost.

- Připojení k platformám SaaS a k místním datům.

- Zabezpečení a dodržování předpisů.

- Integrace sady Visual Studio.

Azure App Service je nejlepší volbou pro většinu webových aplikací. Nasazení a správa jsou integrované do platformy, weby se můžou rychle škálovat a zvládnout tak vysoké zatížení a integrované vyrovnávání zatížení a Traffic Manager poskytují vysokou dostupnost. Stávající weby můžete přesunout do Azure App Service snadno pomocí nástroje pro migraci online, pomocí Open Source aplikace z galerie webových aplikací nebo pomocí architektury a nástrojů podle vašeho výběru vytvořit novou lokalitu. Funkce WebJobs usnadňuje přidání zpracování úloh na pozadí do webové aplikace App Service. Pokud máte existující aplikaci ASP.NET hostovanou místně pomocí místní databáze, je k migraci aplikace do App Service webové aplikace možné použít Azure SQL Database (nebo zabezpečený přístup k místnímu databázovému serveru, pokud je upřednostňovaný).

![Doporučená strategie migrace pro místní aplikace .NET pro Azure App Service](./media/image1-6.png)

Ve většině případů se přesun z místně hostované aplikace ASP.NET do webové aplikace App Service přímočarý. V samotné aplikaci by měla být vyžadována jen malá nebo žádná úprava a může rychle začít využívat celou řadu funkcí, které Azure App Service Web Apps nabídce.

Kromě aplikací, které nejsou optimalizované pro Cloud, jsou Azure App Service Web Apps vynikajícím řešením pro spoustu jednoduchých aplikací monolitické (nedistribuovaných), jako je třeba mnoho aplikací ASP.NET Core. V tomto přístupu je architektura základní a jednoduchá a srozumitelná a spravovatelná:

![Základní architektura Azure](./media/image1-5.png)

Pro správu takové aplikace obvykle stačí malý počet prostředků v jedné skupině prostředků. Aplikace, které jsou obvykle nasazené jako jedna jednotka, nikoli aplikace tvořené mnoha samostatnými procesy, jsou vhodnými kandidáty pro tento [základní přístup k architektuře](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app). I když je architektura spolehlivě jednoduchá, tato metoda stále umožňuje, aby hostovaná aplikace nastavila větší kapacitu (více prostředků na uzel) a výstupní (více hostovaných uzlů) tak, aby splňovaly jakékoli zvýšení poptávky. Díky automatickému škálování je možné aplikaci nakonfigurovat tak, aby automaticky upravila počet uzlů hostujících aplikaci na základě poptávky a průměrného zatížení napříč uzly.

### <a name="app-service-web-apps-for-containers"></a>App Service Web Apps pro kontejnery

Kromě podpory hostování webových aplikací přímo [App Service Web Apps kontejnerů](https://azure.microsoft.com/services/app-service/containers/) lze použít ke spouštění kontejnerových aplikací v systému Windows a Linux. Pomocí této služby můžete snadno nasazovat a spouštět aplikace s využitím kontejnerů, které se můžou škálovat podle vaší firmy. Aplikace mají všechny funkce App Service Web Apps uvedené výše. Kromě toho Web Apps for Containers podporuje zjednodušenou CI/CD s využitím Docker Hub, Azure Container Registry a GitHubu. Pomocí Azure DevOps můžete definovat kanály sestavení a nasazení, které publikují změny v registru. Tyto změny se pak dají testovat v přípravném prostředí a automaticky se nasazují do produkčního prostředí s využitím slotů nasazení a umožňují tak nevýpadky. Vrácení zpět na předchozí verze se může provádět stejně snadno.

K dispozici je několik scénářů, kdy Web Apps pro kontejnery nejvíc vydávat smysl. Pokud máte existující aplikace, které můžete kontejnerizace, ať už v kontejnerech Windows nebo Linux, můžete je snadno hostovat pomocí této sady nástrojů. Stačí publikovat kontejner a potom nakonfigurovat Web Apps pro kontejnery, aby si stáhli nejnovější verzi tohoto obrázku z vašeho registru dle vlastního výběru. Toto je přístup "výtah a Shift" pro migraci z klasických hostujících modelů aplikace do modelu optimalizovaného pro Cloud.

![Migrace kontejneru místní aplikace .NET do Azure Web Apps for Containers](./media/image1-8.png)

Tento přístup také funguje v případě, že váš vývojový tým může přejít na proces vývoje založený na kontejneru. Vnitřní smyčka pro vývoj aplikací pomocí kontejnerů zahrnuje vytvoření aplikace pomocí kontejnerů. Změny provedené v kódu i konfigurace kontejneru jsou vloženy do správy zdrojových kódů a automatizované sestavení zodpovídá za publikování nových imagí kontejneru do registru, jako je Docker Hub nebo Azure Container Registry. Tyto image se pak používají jako základ pro další vývoj a také pro nasazení do produkčního prostředí, jak je znázorněno v následujícím diagramu:

![Konečný pracovní postup životního cyklu Docker DevOps](./media/image1-7.png)

Vývoj s kontejnery nabízí spoustu výhod, zejména v případě, že se kontejnery používají v produkčním prostředí. Stejná konfigurace kontejneru se používá k hostování aplikace v každém prostředí, ve kterém je spuštěná, od místního vývojového počítače po vytváření a testování systémů do produkčního prostředí. Tím se významně snižuje pravděpodobnost vad vyplývající z rozdílů v konfiguraci počítače nebo verzích softwaru. Vývojáři můžou k tomu využít i jakékoli nástroje, které s nimi mají nejvyšší produktivitu, včetně operačního systému, protože kontejnery můžou běžet na jakémkoli operačním systému. V některých případech mohou být distribuované aplikace zahrnující mnoho kontejnerů velmi náročné na spouštění na jednom vývojovém počítači. V tomto scénáři může být vhodné upgradovat na používání Kubernetes a Azure Dev Spaces, které jsou popsané v další části.

V případě, že se některé větší aplikace rozdělují na vlastní menší nezávislé *mikroslužby*, můžete k vylepšení chování aplikace použít další vzory návrhu. Namísto práce přímo s jednotlivými službami může *Brána API* zjednodušit přístup a oddělit klienta od jeho back-endu. Samostatné služby back-endu pro jiné front-endy také umožňují službám vyvíjet se svými zákazníky společně. K běžným službám je možné přistupovat prostřednictvím samostatného kontejneru na *vozíku* , který může zahrnovat běžné knihovny pro připojení klientů pomocí modelu *velvyslance* .

![Ukázková architektura mikroslužeb s několika zjištěnými běžnými vzory návrhu.](./media/image1-10.png)

[Další informace o vzorech návrhu, které je potřeba vzít v úvahu při sestavování systémů založených na mikroslužbách](https://docs.microsoft.com/azure/architecture/microservices/design/patterns)

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Azure Kubernetes Service (AKS) spravuje hostované prostředí Kubernetes, díky čemuž je rychlé a snadné nasazení a Správa kontejnerových aplikací bez znalosti orchestrace kontejnerů. Také eliminuje zatížení průběžných operací a údržby díky zřizování, upgradování a škálování prostředků na vyžádání bez nutnosti přepínat aplikace do offline režimu.

AKS snižuje složitost a provozní režii při správě clusteru Kubernetes tím, že z něj přenese velkou část této zodpovědnosti do Azure. Jako hostovaná služba Kubernetes zpracovává Azure kritické úkoly, jako je monitorování stavu a údržba. Platíte taky jenom za uzly agenta v rámci svých clusterů, a ne pro hlavní servery. AKS jako spravovaná služba Kubernetes poskytuje:

- Automatizované upgrady a opravy verzí Kubernetes.
- Snadné škálování clusteru.
- Samoobslužná plocha hostovaného ovládacího prvku (hlavní servery).
- Úspora nákladů – Plaťte jenom za spuštěné uzly fondu agentů.

Díky Azure, který zpracovává správu uzlů v clusteru AKS, už nemusíte provádět mnoho úloh ručně, jako je upgrade clusteru. Vzhledem k tomu, že Azure zpracovává tyto kritické úlohy údržby za vás, neposkytuje AKS přímý přístup (například s SSH) do clusteru.

Týmy, které využívají AKS, mohou také využít výhod Azure Dev Spaces. Azure Dev Spaces pomáhá týmům soustředit se na vývoj a rychlou iteraci své aplikace mikroslužeb tím, že týmům umožní pracovat přímo s celou architekturou mikroslužeb nebo aplikací spuštěnou v AKS. Azure Dev Spaces taky poskytuje způsob, jak nezávisle aktualizovat části architektury mikroslužeb v izolaci, aniž by to ovlivnilo zbytek clusteru AKS nebo jiných vývojářů.

![Příklad pracovního postupu Azure Dev Spaces](./media/image1-9.gif)

Azure Dev Spaces:

- Minimalizace času nastavení místního počítače a požadavků na prostředky
- Umožňuje týmům rychleji iterovat.
- Snižte počet integračních prostředí vyžadovaných týmem.
- Při vývoji a testování se musí v distribuovaném systému napodobovat určité služby.

[Další informace o Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/about)

### <a name="azure-virtual-machines"></a>Azure Virtual Machines

Pokud máte existující aplikaci, která by vyžadovala významné změny pro spuštění v App Service, můžete zvolit Virtual Machines, aby bylo možné zjednodušit migraci do cloudu. Správná konfigurace, zabezpečení a údržba virtuálních počítačů ale vyžaduje mnohem více času a odbornost IT v porovnání s Azure App Service. Pokud zvažujete Virtual Machines Azure, ujistěte se, že jste přihlédli k probíhajícímu úsilí údržby potřebnému k opravě, aktualizaci a správě prostředí virtuálních počítačů. Azure Virtual Machines je infrastruktura jako služba (IaaS), zatímco App Service je PaaS. Měli byste taky zvážit, jestli nasazování aplikace jako kontejneru Windows do Web App for Containers může být možnost životaschopná pro váš scénář.

## <a name="logical-processes"></a>Logické procesy

Jednotlivé logické procesy, které je možné oddělit od zbytku aplikace, je možné nasadit nezávisle na Azure Functions způsobem bez serveru. Azure Functions vám umožňuje napsat kód, který potřebujete pro daný problém, aniž byste se museli starat o aplikaci nebo infrastrukturu, kterou by mohli spustit. Můžete si vybrat z nejrůznějších programovacích jazyků, včetně C @ no__t-0, F @ no__t-1, Node. js, Pythonu a PHP, což vám umožní vybrat pro daný úkol nejúčinnější jazyk. Podobně jako u většiny cloudových řešení platíte jenom za využité množství času a můžete Azure Functions důvěřovat, abyste mohli škálovat podle potřeby.

## <a name="data"></a>Data

Azure nabízí širokou škálu možností úložiště dat, takže vaše aplikace může pro příslušné údaje používat vhodného poskytovatele dat.

V případě transakčních, relačních dat je nejlepší volbou Azure SQL Database. Pro vysoce výkonná data pro čtení, která jsou převážně pro čtení, je Redis mezipaměť zajištěná Azure SQL Database dobrým řešením.

Nestrukturovaná data JSON můžete ukládat různými způsoby, od SQL Database sloupců po objekty blob nebo tabulek v Azure Storage až po DocumentDB. Z toho DocumentDB nabízí nejlepší funkce pro dotazování a je doporučenou možností pro velký počet dokumentů založených na JSON, které musí podporovat dotazování.

Přechodná data založená na příkazech nebo událostech sloužících k orchestraci chování aplikace mohou používat fronty Azure Service Bus nebo Azure Storage. Azure Storage sběrnice nabízí větší flexibilitu a je doporučenou službou pro netriviální zasílání zpráv v rámci aplikací a mezi nimi.

## <a name="architecture-recommendations"></a>Doporučení architektury

Požadavky vaší aplikace by měly určovat její architekturu. K dispozici je celá řada různých služeb Azure. Výběr pravého rozhodnutí je důležité rozhodnutí. Microsoft nabízí galerii referenčních architektur, které vám pomůžou identifikovat typické architektury optimalizované pro běžné scénáře. Můžete najít referenční architekturu, která se bude úzce mapovat na požadavky vaší aplikace, nebo aspoň na výchozím bodu.

Obrázek 11-1 ukazuje příklad referenční architektury. Tento diagram popisuje doporučený postup architektury pro web systému správy obsahu Sitecore optimalizovaný pro marketing.

![Obrázek 11-1](./media/image11-2.png)

**Obrázek 11-1.** Referenční architektura Sitecore marketingu webu.

**Odkazy – doporučení hostování Azure**

- Architektury řešení Azure \
  <https://azure.microsoft.com/solutions/architecture/>

- Architektura základní webové aplikace Azure
  <https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app>

- Vzory návrhu pro mikroslužby \
  <https://docs.microsoft.com/azure/architecture/microservices/design/patterns>

- Příručka pro vývojáře Azure
  <https://azure.microsoft.com/campaigns/developer-guide/>

- Přehled Web Appse \
  <https://docs.microsoft.com/azure/app-service/app-service-web-overview>

- Web App for Containers \
  <https://azure.microsoft.com/services/app-service/containers/>

- Seznámení se službou Azure Kubernetes Service (AKS) \
  <https://docs.microsoft.com/azure/aks/intro-kubernetes>

>[!div class="step-by-step"]
>[Předchozí](development-process-for-azure.md)
