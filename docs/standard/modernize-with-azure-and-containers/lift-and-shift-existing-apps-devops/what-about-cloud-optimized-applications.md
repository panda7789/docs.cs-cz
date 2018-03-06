---
title: "Co optimalizovaný pro cloudové aplikace?"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Co optimalizovaný pro cloudové aplikace?"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: adcb9d2352022cc94238296562b3eb7677bdf20b
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2018
---
# <a name="what-about-cloud-optimized-applications"></a>Co optimalizovaný pro cloudové aplikace?

I když optimalizovaných Cloudů a [cloudu nativní](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) aplikace nejsou hlavní výběr tohoto průvodce, je vhodné získat představu o vyspělosti tento modernizace a odlišující jej z cloudu DevOps připravené.

Obrázek 4-3 umisťuje optimalizovaných Cloudů aplikace v úrovni vyspělosti modernizace aplikace:

![Umístění optimalizovaný pro cloudové aplikace](./media/image3.png)

> **Obrázek 4-3.** Umístění optimalizovaný pro cloudové aplikace

Vyspělosti modernizace optimalizovaných Cloudů obvykle vyžaduje investice do nové vývoj. Přesun na úroveň optimalizovaných Cloudů obvykle vycházejí z obchodních potřeb modernizovat aplikace co nejvíce nižší náklady a zvýšit flexibility a pokouší využít. Jsou těchto cílů dosáhnout maximalizuje použití cloudu PaaS. To znamená, nejen pomocí služby PaaS jako DBaaS, CaaS a úložiště jako služba (STaaS), ale také migrací vlastní aplikace a služby PaaS výpočetní platformy jako služby Azure App Service, nebo pomocí orchestrators.

Tento typ modernizace obvykle vyžaduje refaktoring nebo zápis nový kód, který je optimalizovaná pro cloudové platformy PaaS (jako pro službu Azure App Service). Ho i vyžadovat architektury speciálně pro cloudové prostředí, zejména pokud přesouváte do cloudu nativní aplikace modely, které jsou založeny na mikroslužeb. Jedná se o klíč rozlišení Multi-Factor ve srovnání s Cloud DevOps-Ready, který vyžaduje žádné předělávání architektury a žádný nový kód.

V některých případech pokročilejší můžete vytvořit [cloudu nativní](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikace založené na mikroslužeb architektury, které můžete momentální s flexibility a škálovat limity, které by bylo obtížné dosáhnout v monolitický architektura nasadit do místního prostředí.

Obrázek 4 – 4 ukazuje typ aplikace, které můžete nasadit při použití modelu optimalizovaných Cloudů. Máte dvě základní možnosti moderních webových aplikací a nativní cloudové aplikace.

> ![Typy aplikací na úrovni optimalizovaných Cloudů](./media/image4.png)
>
> **Obrázek 4 – 4.** Typy aplikací na úrovni optimalizovaných Cloudů

Základní moderní webové aplikace a cloudu nativních aplikací můžete rozšířit přidáním dalších služeb, jako jsou umělé intelligence (AI), machine learning (ML) a IoT. K rozšíření některé z možných přístupů optimalizovaných Cloudů může použít kterýkoli z těchto služeb.

V architektuře aplikace je zásadní rozdíl v aplikacích na úrovni optimalizovaných Cloudů. [Nativní cloudu](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) aplikace jsou podle definice aplikace, které jsou založeny na mikroslužeb. Nativní cloudové aplikace vyžadují speciální architektury, technologie a platformy, ve srovnání s monolitický webové aplikace nebo tradiční N-vrstvá aplikace.

Vytvoření nové aplikace, které nepoužívají mikroslužeb také má smysl. Existuje mnoho nových a stále moderní scénářů, ve kterých může překročit přístup mikroslužeb podle vašich potřeb. V některých případech může jenom chcete vytvořit jednodušší monolitický webové aplikace nebo přidejte hrubý služby do vícevrstvé aplikace. V těchto případech můžete přesto provést plně využívat cloudové PaaS funkcí, jako ty, které nabízí Azure App Service. Stále snížit práci údržby limitu.

Navíc vzhledem k tomu, že budete vyvíjet nový kód v optimalizovaných Cloudů scénáře (pro celou aplikaci nebo pro částečné subsystémy), když vytvoříte nový kód, byste měli použít novější verze rozhraní .NET ([.NET Core](../../../core/index.md) a [ASP.NET Core](/aspnet/core/), zejména). To platí hlavně pokud vytvoříte mikroslužeb a kontejnerů, protože je Štíhlá a rychlé rozhraní .NET Core. Získáte rychlý start v kontejnerech a nároky paměti a vaše aplikace bude vysokým výkonem. Tento přístup perfektně vyhovuje požadavkům mikroslužeb a kontejnery a získejte výhody napříč platformami framework-vrácení může běžet stejná aplikace na systému Linux, Windows Server a Macu (Mac pro vývojové prostředí).

## <a name="cloud-native-applications-with-cloud-optimized-applications"></a>Cloud nativní aplikace s optimalizovaný pro cloudové aplikace

[Nativní cloudu](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) více pokročilé nebo vyspělá stav pro velké a důležitých aplikací. Cloud nativní aplikace obvykle vyžadují architektury a návrhu, který vytvářejí od začátku místo modernizace stávající aplikace. Klíče rozdíl mezi nativní cloudové aplikace a jednodušší optimalizovaných Cloudů webové aplikace nasazené do PaaS je doporučení k použití architektury mikroslužeb v cloudu nativní přístup. Optimalizovaný pro cloudové aplikace může být také monolitický webové aplikace nebo vícevrstvé aplikace nasazené do cloudu PaaS službu, jako je Azure App Service.

[Dvanácti-Factor aplikace](https://12factor.net/) (kolekce schémat, které úzce souvisejí s mikroslužeb přístupy) také považuje požadavek na [cloudu nativní](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) architektury aplikace.

[Foundation nativní Computing na cloudu (CNCF)](https://www.cncf.io/) je primární vykonavatel cloudu nativní norem. Společnost Microsoft [členem CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Ukázka definice a další informace o vlastnostech cloudu nativních aplikací, najdete v článku Gartner [pro navrhování a návrhu cloudu nativní aplikace](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications). Konkrétní pokyny od společnosti Microsoft o tom, jak implementovat nativní cloudové aplikace, najdete v části [mikroslužeb .NET: architektura pro kontejnerové aplikace .NET](https://aka.ms/microservicesebook).

Nejdůležitějším faktorem vzít v úvahu, pokud migrujete celou aplikaci do [cloudu nativní](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms) modelu je, že jste musí přepracování architektury se na základě mikroslužeb. To vyžaduje jasně významné investice do vývoj z důvodu velkého refaktoringu proces zahrnutý. Tato možnost je obvykle vybrána pro kritické aplikace, které potřebují nové úrovně, škálovatelnost a dlouhodobé flexibility. Ale můžete spustit přesun směrem k cloudu nativní přidáním mikroslužeb pro několika nové scénáře a nakonec Refaktorovat aplikace plně jako mikroslužeb. Toto je přírůstkové přístup, který je nejlepší možnost pro některé scénáře.

## <a name="what-about-microservices"></a>Co mikroslužeb? 

Principy mikroslužeb a jak pracují je důležité, pokud uvažujete o cloudu nativní aplikace pro vaši organizaci.

Architektura mikroslužeb je pokročilé přístup, můžete použít pro aplikace, které jsou vytvořeny od nuly nebo momentální stávající aplikace (místní nebo cloudové aplikace připravené pro DevOps) směrem k cloudu nativní aplikace. Můžete spustit přidáním několik mikroslužeb do stávajících aplikací Další informace o nových vzorů mikroslužeb. Ale je zřejmé, budete muset architekti a kód, zejména pro tento typ architektury přístup.

Mikroslužeb však nejsou povinné pro všechny nové nebo moderní aplikace. Mikroslužeb nejsou "magic bullet", a nejsou jeden, nejlepší způsob, jak vytvořit každou aplikaci. Jak a kdy použijete mikroslužeb závisí na typu aplikace, které potřebujete k vytvoření.

Architektura mikroslužeb se stává stále žádoucí pro distribuované a velké nebo složité kritické aplikace, které jsou založeny na více nezávislých subsystémy ve formě autonomního služby. V architektuře na základě mikroslužeb vychází aplikace jako kolekce služeb, které můžou být nezávisle vyvinuté, otestovaný, verzí, nasazení a škálovat. To může zahrnovat všechny související, autonomního databáze za mikroslužby.

Podrobný pohled na architekturu mikroslužeb, která můžete implementovat pomocí .NET Core, najdete v části Stažení PDF e kniha [mikroslužeb .NET: architektura pro kontejnerové aplikace .NET](https://aka.ms/microservicesebook). V průvodci je dostupná také [online](../../microservices-architecture/index.md).

Ale i ve scénářích, ve kterých mikroslužeb nabízí výkonné nasazení nezávislé na schopnosti, silné subsystému hranice a různorodost technologie-vyvolají mnoho nových problémů. Na výzvy se vztahují k vývoji distribuované aplikace, jako je například fragmentovaných a nezávislé datové modely; dosažení odolné komunikace mezi mikroslužeb; potřebu konzistence typu případné; a provozní složitost. Mikroslužeb zavést vyšší úroveň složitosti porovnání s tradiční monolitický aplikace.

Z důvodu složitosti mikroslužeb architektura jsou vhodné pro aplikace založené na mikroslužbu jenom konkrétních scénářů a některé typy aplikací. Patří mezi ně velké a komplexní aplikace, které mají více vyvíjející se subsystémy. V těchto případech je vhodné Investujete do složitější architektura softwaru, pro dlouhodobou vyšší flexibility a efektivnější Údržba aplikace. Ale pro méně složitých scénářů, může být lepší pokračujte s přístupem monolitický aplikace nebo blíží jednodušší N-vrstvá.

Jako poslední Poznámka, i jeho nebezpečí vrácení opakovaných o tento koncept nesmí si prohlédnete pomocí mikroslužeb ve svých aplikacích jako "celkovou nebo nic na všechny*.*" Můžete rozšířit a momentální stávající monolitický aplikace tak, že přidáte nový, malé scénáře podle mikroslužeb. Nemusíte začít úplně od začátku, pokud chcete začít pracovat s přístupem architektura mikroslužeb. Ve skutečnosti doporučujeme vám momentální pomocí stávající monolitický nebo vícevrstvé aplikace přidáním nové scénáře. Nakonec se analyzují aplikaci do autonomního součásti nebo mikroslužeb. Můžete začít vyvíjející se aplikace monolitický mikroslužeb směrem, krok za krokem.

## <a name="when-to-use-azure-app-service-for-modernizing-existing-net-apps"></a>Kdy použít Azure App Service pro modernizace existující aplikace .NET

Pokud jste modernizovat existující webové aplikace ASP.NET na úrovni vyspělosti optimalizovaných Cloudů, protože byly webové aplikace vyvinuté pomocí rozhraní .NET Framework, vaše hlavní závislosti jsou v systémech Windows a s největší pravděpodobností Internet Information Server (IIS). Nasazení aplikací systému Windows a službou IIS a můžete použít buď přímo nasazení do [Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is) nebo podle první containerizing vaší aplikace pomocí Windows kontejnery. Pokud containerizing, nasazení aplikací buď do kontejneru systému Windows je hostitelem (virtuálních počítačů na základě) nebo Azure Service Fabric clusteru této podporuje kontejnery systému Windows.

Pokud používáte Windows kontejnery, získáte všechny výhody rozdělení do kontejnerů. Zvýšení flexibility v přesouvání a nasazení aplikace a snížit třecí prostředí problémů (pracovní, vývoj/testování, produkční). V následujících částech několik jsme přejít do další podrobnosti o výhodách, které můžete získat z použití kontejnerů.

Azure App Service před sepsáním tohoto průvodce, nepodporuje kontejnery systému Windows. Podporuje kontejnery pro Linux. Proto může být další otázka "Jak vybrat mezi Azure App Service a kontejnery Windows?"

V zásadě platí Pokud funguje Azure App Service pro vaši aplikaci a nejsou k dispozici libovolný server nebo vlastní závislosti blokování cestu k použití služby App Service, měli byste migrovat stávající webovou aplikaci .NET do služby App Service. Který je nejjednodušší, co nejúčinnější způsob, jak udržovat vaše aplikace. V Azure vaše aplikace také bude mít jednodušší údržby cestu z důvodu výhody z PaaS infrastruktury, jako je DBaaS, CaaS a STaaS.

Pokud aplikace nemá server nebo vlastní závislosti, které nejsou podporované ve službě Azure App Service, může ale muset zvážit možnosti, které jsou založené na Windows kontejnery. Server nebo vlastní závislosti příklady software třetích stran nebo soubor .msi, které musí být nainstalovaný na serveru, ale ten se nepodporuje v Azure App Service. Dalším příkladem je ostatní konfigurace serveru, která není podporována v Azure App Service, jako je použití sestavení v globální mezipaměti sestavení (GAC) nebo COM / komponenty modelu COM +. Díky kontejneru bitových kopií systému Windows můžete zahrnout svoje vlastní závislosti ve stejné "jednotce nasazení."

Alternativně může Refaktorovat oblasti vaší aplikace, které nejsou podporovány službou Azure App Service. V závislosti na objemu práce refaktoring vyžaduje, budete muset pečlivě vyhodnotit, zda, je vhodné to.

### <a name="benefits-of-moving-to-azure-app-service"></a>Výhody přechodu na Azure App Service

Aplikační služba Azure je plně spravovaná PaaS nabídka, která umožňuje snadno vytvářet webové aplikace, které jsou zajišťované obchodní procesy. Při použití služby App Service se vyhnout náklady na správu infrastruktury přidružené k upgradu a Správa webové aplikace na místě. Konkrétně vyjmout hardwaru a náklady na licencování spuštění webové aplikace na místě.

Pokud webová aplikace je vhodné pro migraci na Azure App Service, hlavní výhodou je krátkou dobu potřebnou k přesunutí aplikace. Služby App Service nabízí prostředí, ve kterém chcete začít s velmi snadné.

Aplikační služba Azure je nejlepší volbou pro většinu webové aplikace, protože je nejjednodušší PaaS v Azure, který můžete použít ke spuštění webové aplikace. Nasazení a správy se integrují do platformy, lokality škálování rychle pro zpracování vysoké přenosové zatížení a poskytovat vysokou dostupnost, Správce vyrovnávání a provoz integrované zatížení.

I monitorování vaší webové aplikace je jednoduchý, prostřednictvím služby Azure Application Insights. Application Insights obsahuje volné službou App Service a nevyžaduje psaní speciální kódu v aplikaci. Právě spouštění vaší webové aplikace ve službě App Service a získáte poutavé monitorování systému, se žádné další kroky.

Službou App Service spousta open-source aplikací můžete použít také přímo z Galerie Azure webových aplikací (např. WordPress nebo Umbraco), nebo můžete vytvořit nové lokality pomocí framework a nástrojů dle vašeho výběru, jako je technologie ASP.NET. Součást aplikace webové služby umožňuje snadno přidat úloha na pozadí zpracování do webové aplikace služby App Service.

Následující klíčové výhody migraci vašich webových aplikací pomocí funkce Web Apps služby Azure App Service:

-   Automatické škálování pro potřeby během časy a snížit náklady na quiet v době.

-   Automatické lokality zálohování chránit změny a data.

-   Vysoké dostupnosti a odolnosti na platformě Azure PaaS.

-   Nasazovací sloty pro vývoj a přípravných prostředí a testování více návrhů lokalit.

-   Vyrovnávání zatížení a ochrany Distributed Denial of Service (DDoS).

-   Řízení provozu, které uživatele nasměrují na nejbližší geografické nasazení.

I když služby App Service může být nejlepší volbou pro nové webové aplikace, ale pro existující aplikace služby App Service může být nejlepší volbou pouze v případě, že vaše závislosti aplikací jsou podporované ve službě App Service.

### <a name="additional-resources"></a>Další zdroje

-   **Analýzy kompatibility pro Azure App Service**  
[https://www.migratetoazure.net/Resources](https://www.migratetoazure.net/Resources)


### <a name="benefits-of-moving-to-windows-containers"></a>Výhody přechodu na Windows kontejnery

Hlavní výhodou použití kontejnerů Windows je získání spolehlivější a vylepšené možnosti nasazení, ve srovnání s-kontejnerizované aplikace. Má vaše aplikace modernized s kontejnery efektivně vypnuty, vaše aplikace připravená na mnoha platformách a cloudy, které podporují Windows kontejnery. Výhody přechodu na Windows kontejnery jsou podrobněji popsány v následujících částech.

Primární výpočetních prostředích v Azure (v obecné dostupnosti od mid 2017), které podporují Windows kontejnery jsou Azure Service Fabric a základních hostitelů Windows kontejnery (virtuálních počítačů Windows serveru 2016). Tyto prostředí jsou scénáře hlavní infrastruktury v této příručce.

Také můžete nasadit kontejnery Windows na další orchestrators, jako je Kubernetes, Docker Swarm nebo DC/OS. Aktuálně (časná cokoli 2017), těchto platforem jsou ve verzi preview v Azure Container Service pro použití Windows kontejnerů.

>[!div class="step-by-step"]
[Předchozí](microsoft-technologies-in-cloud-devops-ready-applications.md)
[další](how-to-deploy-existing-net-apps-to-azure-app-service.md)
