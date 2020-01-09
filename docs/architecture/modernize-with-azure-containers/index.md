---
title: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows (druhá edice)
description: Naučte se přezvednout a přemodernizovat stávající aplikace do cloudu Azure a kontejnerů pomocí této elektronické knihy.
ms.date: 04/28/2018
ms.openlocfilehash: fa20e606c9a1364fbdf8c9a58c8703420d9e65a9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714575"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows (druhá edice)

![Titulní obrázek Průvodce aplikacemi rozhraní .NET pro modernizovat](./media/index/web-application-guide-cover-image.png)

PUBLIKOVAL(A)  
Microsoft Press a Microsoft DevDiv  
Divize společnosti Microsoft Corporation  
One Microsoft Way  
Redmond, Washington 98052-6399  

Copyright © 2018 by Microsoft Corporation  

Všechna práva vyhrazena. Žádná část obsahu této knihy nemůže být reprodukována v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.

Tato kniha je zdarma dostupná ve formě elektronické knihy (elektronické knihy), která je dostupná prostřednictvím několika kanálů v Microsoftu, jako je <https://dot.net/architecture>.

Pokud máte dotazy související s touto knihou, pošlete e-mail na [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora. Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.

Některé příklady, které jsou zde uvedeny, slouží pouze pro ilustraci a jsou smyšlené. Jakákoli spojitost s kterýmkoli skutečným subjektem není zamýšlená a nelze ji vyvozovat.

Microsoft a ochranné známky uvedené na adrese <https://www.microsoft.com> na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft. Všechny ostatní značky jsou majetkem příslušných vlastníků.

Autor:
> **Cesar de la Torre**, SR. PM, produktový tým .NET, Microsoft Corp.

Účastníci a kontroloři:
> **Scott Hunterem**, ředitel pro partnery, tým .NET, Microsoft  
> **Paul Yuknewicz**, hlavní správce odp, Visual Studio Tools tým, Microsoft  
> **Lisa Guthrie**, SR. odp, Visual Studio Tools tým, Microsoft  
> **Ankit Asthana**, hlavní správce odpoledne, tým .NET, Microsoft  
> **Unai Zorrilla**, vedoucí pro vývojáře, jednoduché koncepty  
> **Javier Valero**, vedoucí pracovník v Grupo solutio  

## <a name="introduction"></a>Úvod

Pokud se rozhodnete modernizovat své webové aplikace nebo služby a přesunete je do cloudu, nemusíte nutně muset své aplikace zcela rearchitektovat. Změna architektury aplikace pomocí pokročilého přístupu, jako jsou mikroslužby, není vždycky možnost z důvodu omezení nákladů a času. V závislosti na typu aplikace nemusí být také nutné měnit architekturu aplikace. Pro optimalizaci nákladů strategie migrace cloudu ve vaší organizaci je důležité vzít v úvahu potřeby vašich obchodních a požadavků vašich aplikací. Musíte určit:

- Které aplikace vyžadují transformaci nebo přestavbu.

- Které aplikace je třeba částečně promoderních.

- Které aplikace můžete přímo do cloudu nazvednutím a přesunutím.

## <a name="about-this-guide"></a>O této příručce

Tato příručka se zaměřuje především na počáteční modernizaci stávajících aplikací orientovaných na web nebo na služby Microsoft .NET Framework, což znamená, že akce přesunu úlohy do novějšího nebo více moderních prostředí, aniž by došlo k výrazné změně kódu aplikace. a základní architektura.

Tato příručka také zvýrazní výhody přesunu vašich aplikací do cloudu a částečně modernizaci aplikací pomocí konkrétní sady nových technologií a přístupů, jako jsou kontejnery Windows a související výpočetní platformy v Azure, které podporují kontejnery Windows.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Cesta ke cloudu pro existující aplikace .NET

Organizace se obvykle rozhodnou přesunout do cloudu s cílem zajistit flexibilitu a rychlost, kterou můžou získat pro své aplikace. V cloudu můžete během několika minut nastavit tisíce serverů (virtuálních počítačů), ve srovnání s týdny, které obvykle trvá nastavení místních serverů.

Pro migraci aplikací do cloudu není k dispozici jediná jedna velikost. Správná strategie migrace pro vás bude záviset na potřebách a prioritách vaší organizace a na typu aplikací, které migrujete. Ne všechny aplikace zaručují investici přechodu na model[PaaS](https://azure.microsoft.com/overview/what-is-paas/)(Platform as a Service) nebo pro vývoj modelu aplikace [Cloud Native](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) . V mnoha případech můžete postupovat podle fáze nebo přírůstkového přístupu k investicím do cloudu, a to na základě vašich obchodních potřeb.

Pro moderní aplikace s nejlepší dlouhodobou flexibilitou a hodnotou pro organizaci můžete využít výhod investování do architektury *cloudových nativních* aplikací. U aplikací, které jsou existujícími nebo staršími prostředky, se však klíč věnuje minimálnímu času a penězi (bez změny architektury ani změny kódu) při jejich přesunu do cloudu, aby se mohly realizovat významné výhody.

Obrázek 1-1 ukazuje možné cesty, které můžete provést při přesunu stávajících aplikací .NET do cloudu v přírůstkových fázích.

 ![Cesty k modernizaci pro stávající aplikace a služby .NET](./media/image1-1.png)

**Obrázek 1-1**. Cesty k modernizaci pro stávající aplikace a služby .NET

Každý přístup k migraci má jiné výhody a důvody pro jeho použití. Když migrujete aplikace do cloudu, můžete zvolit jeden z nich, nebo vybrat některé součásti z více přístupů. Jednotlivé aplikace nejsou omezeny pouze na jediný přístup nebo na stav splatnosti. Například společný hybridní přístup by měl určité místní komponenty a další komponenty v cloudu.

Definice a krátké vysvětlení pro každou úroveň splatnosti aplikace jsou následující:

**Úroveň 1: aplikace připravené pro cloudovou infrastrukturu** : v tomto postupu migrace jednoduše migrujete nebo znovu Hostujte své aktuální místní aplikace na platformu[IaaS](https://azure.microsoft.com/overview/what-is-iaas/)(infrastruktura jako služba). Vaše aplikace mají skoro stejné složení jako předtím, ale teď je nasadíte do virtuálních počítačů v cloudu.
Tento jednoduchý typ migrace je obvykle známý v oboru jako "výtah & Shift".

**Úroveň 2: cloudové optimalizované** aplikace: na této úrovni a pořád bez přemístění nebo změny významného kódu můžete získat další výhody spuštění vaší aplikace v cloudu s moderními technologiemi, jako jsou kontejnery a další cloudové služby spravované službou. Vylepšením procesů podnikového vývoje (DevOps) můžete zlepšit flexibilitu vašich aplikací pro rychlejší dodávání. Dosáhnete toho pomocí technologií, jako jsou kontejnery Windows, které jsou založené na modulech Docker. Kontejnery odstraňují tření, které je způsobeno závislostmi aplikace při nasazení v několika fázích. V tomto modelu splatnosti můžete nasazovat kontejnery na IaaS nebo PaaS při používání dalších cloudových služeb, které souvisejí s databázemi, mezipaměti jako služby, monitorování a průběžné integrace/průběžné nasazování (CI/CD).

Třetí úroveň zralosti je konečným cílem v cloudu, ale je to pro mnoho aplikací volitelné, ale ne hlavní fokus tohoto průvodce:

**Úroveň 3: aplikace nativní pro Cloud** : Tento přístup k migraci je typicky založený na obchodních potřebách a cílech modernizaci vaší klíčové aplikace. Na této úrovni používáte služby PaaS Services k přesunu aplikací na výpočetní platformy PaaS. Implementujete [cloudové nativní](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikace a architekturu mikroslužeb pro vývoj aplikací s dlouhodobou flexibilitou a pro škálování na nové limity. Tento typ modernizace obvykle vyžaduje architekty specificky pro Cloud. Nový kód se často musí zapsat, obzvláště když přejdete na cloudové nativní aplikace a modely založené na mikroslužbách. Tento přístup vám může pomáhat získat výhody, které se obtížně dosahují ve vašich monolitické a místních aplikačních prostředích.

Tabulka 1-1 popisuje hlavní výhody a důvody pro výběr každé migrace nebo přístupu k moderním účelům.

| **Cloudová infrastruktura – připraveno** <br /> *Zvednutí a posunutí* | **Optimalizované pro Cloud** <br /> *Modernizovat* | **Cloud-Native** <br /> *Modernizovat, rearchitekt a přepis* |
|---|---|---|
| **Cíl výpočtů aplikace** |
| Aplikace nasazené na virtuální počítače v Azure | Monolitické nebo N-vrstvé aplikace nasazené do Azure App Service, Azure Container instance (ACI), virtuální počítače s kontejnery nebo AKS (služba Azure Kubernetes) | Kontejnerové mikroslužby založené na službě Azure Kubernetes (AKS) nebo mikroslužby bez serveru založené na Azure Functions. |
| **Cíl dat** |
| SQL nebo jakákoli relační databáze na virtuálním počítači | Azure SQL Database spravované instance nebo jiné spravované databáze v cloudu. | Jemně odstupňované databáze na mikroslužby na základě Azure SQL Database, Azure Cosmos DB nebo jiné spravované databáze v cloudu |
| **Výhody**|
| <li>Bez nového architekta, žádný nový kód <li> Minimální úsilí pro rychlou migraci <li> Nejméně běžný jmenovatel podporovaný v Azure <li> Základní záruky dostupnosti <li> Po přesunu do cloudu je snazší modernizovat ještě víc | <li> Žádná změna architektury <li> Minimální změny kódu a konfigurace <li> Vylepšené nasazení a DevOps flexibilitu pro vypuštění z důvodu kontejnerů <li> Zvýšená hustota a nižší náklady na nasazení <li> Přenositelnost aplikací a závislostí <li> Flexibilita cílů hostitele: přístupy k PaaS nebo IaaS | <li> Architekt pro Cloud získáte nejlepší výhody cloudu, ale je potřeba nový kód. <li> Cloud mikroslužeb – nativní přístupy <li> Moderní důležité aplikace, škálovatelné s technologií Hyper-odolné <li> Plně spravované služby <li> Optimalizováno pro škálování <li> Optimalizováno pro autonomní flexibilitu podle subsystému <li> Postavené na nasazení a DevOps |
| **Problémy** |
| <li> Menší hodnota cloudu, která je jiná než SHIFT v provozních nákladech nebo uzavírání datových center <li> Nízká je spravovaná: žádné operační systémy nebo opravy middlewaru; může používat řešení infrastruktury, jako je Terraformu, Spinnaker nebo Puppet. | <li> Uzavření je dalším krokem v výukové křivce pro vývojáře a IT operace. <li> Kanály DevOps a CI/CD jsou pro tento přístup obvykle "a". Pokud v jazykové verzi organizace není v současné době přítomná, může se jednat o další výzvu.| <li> Vyžaduje rearchitekturu pro nativní cloudové aplikace a architektury mikroslužeb a obvykle vyžaduje významné refaktoring kódu nebo přepsání, když modernizaci (zvýšil čas a rozpočet).|
> **Tabulka 1-1.** Výhody a výzvy k modernizaci cest pro stávající aplikace a služby .NET

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Klíčové technologie a architektury podle úrovně vyspělosti

.NET Framework aplikace zpočátku začaly s .NET Framework verze 1,0, která byla vydána v. 2001. Společnosti byly přesunuty do novější verze (například 2,0, 3,5 a .NET 4. x). Většina těchto aplikací běžela na serverech Windows Server a Internet Information Server (IIS) a používá relační databázi, jako je SQL Server, Oracle, MySQL nebo jakýkoli jiný RDBMS.

Většina stávajících aplikací .NET může současné době být založená na .NET Framework 4. x nebo dokonce na .NET Framework 3,5 a používat webové architektury, jako je ASP.NET MVC, ASP.NET Web Forms, ASP.NET Web API, Windows Communication Foundation (WCF), ASP.NET Signal a ASP.NET webové stránky. . Tyto navázané .NET Framework technologie závisí na systému Windows. Tato závislost je důležité vzít v úvahu, pokud jednoduše migrujete starší aplikace a chcete provést minimální změny v infrastruktuře vaší aplikace.

Obrázek 1-2 ukazuje primární technologie a styly architektury používané v každé ze tří úrovní splatnosti cloudu:

![Primární technologie pro každou úroveň splatnosti pro modernizaci stávající webové aplikace .NET](./media/image1-2.png)

**Obrázek 1-2.** Primární technologie pro každou úroveň splatnosti pro modernizaci stávající webové aplikace .NET

Obrázek 1-2 zvýrazňuje nejběžnější scénáře, ale mnoho hybridních a smíšených variant je možné, pokud je to architektura. Například modely splatnosti se vztahují nejen na architektury monolitické ve stávajících webových aplikacích, ale také na orientaci služeb, N-vrstvách a jiné varianty stylu architektury. Vyšší fokus nebo procento na jednom nebo jiném typu architektury a související technologie určují celkovou úroveň zralosti vašich aplikací.

Jednotlivé úrovně splatnosti v procesu modernizace jsou spojeny s následujícími klíčovými technologiemi a přístupy:

- **Cloudová infrastruktura – připravená** (rehosted nebo basic výtah & Shift): jako první krok mnoho organizací chce jenom rychle provést strategii migrace do cloudu. V takovém případě se aplikace rehostují. Většinu opětovného hostování můžete automatizovat pomocí [Azure Migrate](https://aka.ms/azuremigrate), služby, která poskytuje pokyny, přehledy a mechanismy potřebné k tomu, aby vám pomohla při migraci do Azure na základě cloudových nástrojů, jako je [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/) a [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/). Můžete také nastavit ruční hostování ručně, abyste se seznámili s podrobnostmi o prostředcích infrastruktury při přesunu starších verzí aplikací do cloudu. Můžete například přesunout své aplikace na virtuální počítače v Azure s malým množstvím změn – pravděpodobně pouze drobné změny konfigurace. Síť v tomto případě je podobná místnímu prostředí, zejména pokud vytváříte virtuální sítě v Azure.

- **Cloudově optimalizované** (spravované služby a kontejnery Windows): Tento model spočívá v několika důležitých optimalizacích nasazení, které získají některé významné výhody z cloudu, aniž by došlo ke změně základní architektury aplikace. Základem tohoto kroku je přidání podpory [kontejnerů Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) do stávajících aplikací .NET Framework. V tomto důležitém kroku (containering) není nutné se dotýkat kódu, takže celkové úsilí na výtah a posun jsou světla. Pomocí nástrojů, jako je [Image2Docker](https://github.com/docker/communitytools-image2docker-win) nebo Visual Studio, můžete použít nástroje pro [Docker](https://www.docker.com/). Visual Studio automaticky zvolí inteligentní výchozí hodnoty pro aplikace ASP.NET a image Windows Containers. Tyto nástroje nabízejí rychlou vnitřní smyčku a rychlou cestu k získání kontejnerů do Azure. Flexibilita je vylepšena při nasazení do více prostředí.
Pak přejdete do produkčního prostředí. kontejnery Windows můžete nasadit do [Azure Web App for Containers](https://azure.microsoft.com/services/app-service/containers/), [Azure Container Instances (ACI)](https://azure.microsoft.com/services/container-instances/)a virtuální počítače azure s Windows serverem 2016 a kontejnery, pokud dáváte přednost přístupu IaaS. Pro složitější aplikace s více kontejnery zvažte použití Orchestration, jako je [Služba Azure Kubernetes (AKS/ACS)](https://azure.microsoft.com/services/container-service/).

Během této počáteční modernizace můžete také přidat prostředky z cloudu, například monitorování pomocí nástrojů, jako je [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview); Kanály CI/CD pro životní cyklus vaší aplikace s [Azure DevOps Services](https://azure.microsoft.com/services/devops/); a spousta dalších služeb datových prostředků, které jsou k dispozici v Azure. Můžete například upravit webovou aplikaci monolitické, která byla původně vyvinutá pomocí tradičních [webových formulářů ASP.NET](https://www.asp.net/web-forms) nebo [ASP.NET MVC](https://www.asp.net/mvc), ale teď ji nasadíte pomocí kontejnerů Windows. Pokud používáte kontejnery Windows, měli byste také migrovat data do databáze ve [Azure SQL Database Managed instance](https://docs.microsoft.com/azure/sql-database/), a to vše beze změny základní architektury aplikace.

- **Cloud-Native**: jak jsme zavedli, měli byste se domnívat o navrhování [cloudových aplikací v cloudu](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) , když cílíte na velké a komplexní aplikace s více nezávislými vývojovými týmy, které se dají vyvíjet a nasazovat samostatně. Také z důvodu členitosti a nezávislé škálovatelnosti na mikroslužby. Tyto architektury čelí velmi důležitým problémům a složitosti, ale můžou být výrazně zjednodušeny pomocí cloudových PaaS a orchestrací, jako je [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/services/container-service/) (spravované Kubernetes), a [Azure Functions](https://azure.microsoft.com/services/functions/) pro přístup bez serveru. Všechny tyto přístupy (například mikroslužby a bez serveru) obvykle vyžadují architekty pro Cloud a psaní nového kódu – kód, který je přizpůsobený konkrétním PaaS platformám, nebo kód, který se zarovnává s konkrétními architekturami, jako jsou mikroslužby.

Obrázek 1-3 ukazuje interní technologie, které můžete použít pro každou úroveň splatnosti:

![Interní technologie pro každou úroveň zralosti](./media/image1-3.png)

**Obrázek 1-3.** Interní technologie pro každou úroveň zralosti

## <a name="lift-and-shift-scenario"></a>Scénář zvednutí a posunutí

U migrací z převedených a Shift Pamatujte na to, že ve scénářích vaší aplikace můžete použít spoustu různých variací zdvihů a posunutí. Pokud aplikaci znovu hostovatte, můžete mít podobný scénář jako na obrázku 1-4, kde používáte virtuální počítače v cloudu jenom pro vaši aplikaci a pro váš databázový server.

![Příklad čistě IaaS scénáře v cloudu](./media/image1-4.png)

**Obrázek 1-4**. Příklad čistě IaaS scénáře v cloudu

## <a name="modernization-scenarios"></a>Scénáře modernizace

V případě scénářů pro moderní účely je možné, že máte čistě cloudově optimalizovanou aplikaci, která používá pouze prvky z této úrovně splatnosti. Nebo můžete mít aplikaci zprostředkujícího stavu s některými prvky z cloudové infrastruktury připravené a dalšími prvky z cloudu optimalizovaného pro Cloud (výběr a výběr nebo smíšený model), jako na obrázku 1-5.

![Příklad scénáře "výběr a výběr" s databází na IaaS, DevOps a prostředcích kontejnerů](./media/image1-5.png)

**Obrázek 1-5.** Příklad scénáře "výběr a výběr" s databází na IaaS, DevOps a prostředcích kontejnerů

Teď jako ideální scénář pro mnoho stávajících .NET Frameworkch aplikací, které se mají migrovat, můžete migrovat na cloudově optimalizovanou aplikaci a získat tak významné výhody před malým množstvím práce. Tento přístup také nastavíte pro Cloud Native jako možný budoucí vývoj. Obrázek 1-6 ukazuje příklad.

![Ukázkový scénář pro cloudově optimalizované aplikace s kontejnery Windows a spravovanými službami](./media/image1-6.png)

**Obrázek 1-6.** Ukázkový scénář pro cloudově optimalizované aplikace s kontejnery Windows a spravovanými službami

Ještě dál můžete rozšířit svou stávající cloudovou aplikaci tím, že přidáte několik mikroslužeb pro konkrétní scénáře. Tím byste částečně přesunuli na úroveň cloudového nativního modelu, což není hlavním soustředěním na stávající doprovodné materiály.

## <a name="what-this-guide-does-not-cover"></a>Co tato příručka nepokrývá

Tato příručka se zabývá konkrétní podmnožinou ukázkových scénářů, jak je znázorněno na obrázku 1-7. Tato příručka se zaměřuje pouze na scénáře navýšení a posunutí a nakonec na model optimalizovaný pro Cloud. V modelu optimalizovaném pro Cloud je .NET Framework aplikace moderní pomocí kontejnerů Windows a navíc dalších komponent, jako jsou monitorování a kanály CI/CD. Jednotlivé komponenty jsou zásadní pro nasazení aplikací do cloudu, rychlejší a flexibilitu.

![V této příručce se nezabývá Cloud – nativní.](./media/image1-7.png)

**Obrázek 1-7.** V této příručce se nezabývá Cloud – nativní.

Tato příručka je zaměřená na konkrétní. Zobrazuje cestu, kterou můžete provést, abyste dosáhli přezvednutí a posunutí stávajících aplikací .NET, aniž byste museli měnit architekturu a bez jakýchkoli změn kódu. Nakonec vám ukáže, jak nastavit optimalizaci cloudu aplikace.

V této příručce se dozvíte, jak vytvářet aplikace nativní pro Cloud, jako je například vývoj v architektuře mikroslužeb. Informace o tom, jak měnit architekt svých aplikací nebo vytvářet nové aplikace založené na mikroslužbách, najdete v tématu mikroslužby v elektronické knize [.NET: architektura pro kontejnery aplikací .NET](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Další materiály a zdroje informací

- **Kontejnerový životní cyklus aplikace Docker s platformou a nástroji Microsoftu** (elektronická kniha ke stažení) \
  <https://aka.ms/dockerlifecycleebook>

- **Mikroslužby .NET: architektura pro kontejnerové aplikace .NET** (elektronická kniha ke stažení) \
  <https://aka.ms/microservicesebook>

- **Navržení moderních webových aplikací pomocí ASP.NET Core a Azure** (elektronická kniha ke stažení) \
  <https://aka.ms/webappebook>

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tuto příručku

Tato příručka je určená pro vývojáře a architekty řešení, kteří chtějí modernizovat stávající webové aplikace ASP.NET nebo služby WCF založené na .NET Framework, a to pro zlepšení flexibility při expedici a uvolňování aplikací.

Tento průvodce může být užitečný i v případě, že jste Tvůrce technického rozhodnutí, jako je například podnikový architekt nebo vedoucí vývoj/ředitel, který chce jenom přehled výhod, které můžete získat pomocí kontejnerů Windows, a nasazením do cloudu při použití Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Jak používat tohoto průvodce

Tato příručka řeší "Proč", proč byste mohli chtít modernizovat své stávající aplikace a konkrétní výhody, které se při přesunu aplikací do cloudu dostanete při používání kontejnerů Windows. Obsah v prvních několika kapitolách příručky je navržený pro architekty a pracovníky technického rozhodování, kteří chtějí mít přehled, ale nepotřebují se zaměřit na implementaci a technický krok, podrobné informace.

Poslední kapitola této příručky zavádí několik návodů, které se zaměřují na konkrétní scénáře nasazení. Tato příručka nabízí kratší verze návodů pro Shrnutí scénářů a zdůraznění jejich výhod. Kompletní návody podrobněji procházejí podrobnostmi o nastavení a implementaci a publikují se jako sada příspěvků na [wikiwebu](https://github.com/dotnet-architecture/eShopModernizing/wiki) ve stejném veřejném [úložišti GitHubu](https://github.com/dotnet-architecture/eShopModernizing) , kde jsou umístěné související ukázkové aplikace (popsané v další části). Poslední kapitola a podrobné návody k wiki na GitHubu budou mít větší význam pro vývojáře a architekty, kteří se chtějí zaměřit na podrobnosti implementace.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Ukázkové aplikace pro starší verze aplikací modernizaci: eShopModernizing

Úložiště [eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) na GitHubu nabízí dvě ukázkové aplikace, které simulují starší webové aplikace v monolitické. Jedna webová aplikace se vyvíjí pomocí ASP.NET MVC; Druhá webová aplikace se vyvíjí pomocí webových formulářů ASP.NET a třetí aplikace je N-vrstvá aplikace s klientskou desktopovou aplikací WinForms, která spotřebovává back-end služby WCF. Všechny tyto aplikace jsou založené na tradičních .NET Framework. Tyto ukázkové aplikace nepoužívají .NET Core ani ASP.NET Core, protože by měly být moderní a starší .NET Framework aplikace.

Tyto ukázkové aplikace mají druhou verzi s moderním kódem, které jsou poměrně jasné. Nejdůležitější rozdíl mezi verzemi aplikací je, že druhá verze jako volba nasazení používá kontejnery Windows. K dispozici je také několik dalších verzí, jako jsou Azure Storage objekty blob pro správu imagí, Azure Active Directory pro správu zabezpečení a Azure Application Insights pro monitorování a auditování aplikací.

## <a name="send-your-feedback"></a>Poslat svůj názor

Tato příručka byla popsána, která vám pomůže pochopit vaše možnosti pro vylepšení a modernizacií stávajících webových aplikací .NET. Vyvíjejí se příručka a související ukázkové aplikace. Vítáme vaše připomínky a názory. Pokud máte komentáře o tom, jak by tato příručka mohla být užitečnější, pošlete je prosím na [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

>[!div class="step-by-step"]
>[Next](lift-and-shift-existing-apps-azure-iaas.md) <!-- Next Chapter -->
