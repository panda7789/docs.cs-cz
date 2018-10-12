---
title: Modernizujte stávající .NET aplikací s Azure Cloud a kontejnerů Windows (verze 2.)
description: Zjistěte, jak přenést a podržte klávesu shift a modernizace stávajících aplikací do cloudu Azure a kontejnery s tuto elektronickou příručku.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: f4ca3789ec4b3d84960f2ecd4494a899339a787b
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121438"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Modernizace stávajících aplikací .NET pomocí cloudu Azure a kontejnery Windows (verze 2.)

![titulní obrázek](./media/cover.png)

PUBLIKOVAL(A)  
Microsoft Press a Microsoft DevDiv  
Divize společnosti Microsoft Corporation  
One Microsoft Way  
Redmond, Washington 98052-6399  

Copyright © 2018 Microsoft Corporation  

Všechna práva vyhrazena. Žádná část obsahu této knihy může reprodukovat v libovolné formě nebo jakýmikoli prostředky bez písemného souhlasu vydavatele.

Tato kniha je dostupná zdarma ve formě elektronickou knihu (elektronická kniha) k dispozici prostřednictvím více kanálů v Microsoftu, jako <http://dot.net/architecture>.

Pokud máte dotazy týkající se této knihy, e-mailové adrese [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)

Tato kniha je k dispozici "jako-je" a vyjadřuje zobrazení autora a názory. Zobrazení, názory a informace v této knize, včetně adres URL a jiných odkazů na internetové weby, mohou změnit bez předchozího upozornění.

Některé zde uvedené příklady jsou k dispozici pouze pro ilustraci a jsou smyšlené. Žádný skutečný vztah nebo spojení ani je určena ji vyvozovat.

Microsoft a ochranné známky uvedený na <https://www.microsoft.com> na webové stránce "Ochranné známky" jsou obchodní známky společností skupiny Microsoft. Všechny ostatní značky jsou majetkem příslušných vlastníků.

Autor:
> **De la Torre Cesarovi**, vyšší ODP., .NET produktu Team, Microsoft Corp.

Účastníci a recenzenti:
> **Scott Hunter**, Partner Director oddělení PM, týmu .NET, Microsoft  
> **Paulem Yuknewiczem**, hlavní manažer PM, týmu Visual Studio Tools, Microsoft  
> **Lisa Guthrie**, vyšší ODP., týmu Visual Studio Tools, Microsoft  
> **Ankit Asthana**, hlavní manažer PM, týmu .NET, Microsoft  
> **Unai Zorrilla**, vedoucí vývojář, Plain Concepts  
> **Javier Valero**, hlavní, provozní ředitel ve Grupo řešení  

## <a name="introduction"></a>Úvod

Pokud se rozhodnete k modernizaci webových aplikací nebo služeb a přesunout do cloudu, není nutné nutně plně úprava architektury aplikací. Změna architektury aplikace s využitím metodiky pokročilé, jako jsou mikroslužby není vždy z důvodu omezení času a nákladů. V závislosti na typu aplikace změna architektury aplikace nemusí být také nezbytné. K optimalizaci nákladovou efektivitu strategie migrace do cloudu vaší organizace, je důležité vzít v úvahu požadavky na vašich aplikací a potřebám vašeho podnikání. Je potřeba určit:

- Které aplikace potřebuje k transformaci nebo změna architektury.

- Aplikace, které je potřeba jenom částečně modernizovala.

- Aplikace, které vám můžou metodou "lift and shift" přímo do cloudu.

## <a name="about-this-guide"></a>Informace o této příručce

Tato příručka se zaměřují hlavně na počáteční modernizaci stávající webové rozhraní Microsoft .NET Framework nebo aplikace orientované na služby, což znamená akce přesunu úlohy do novějšího nebo modernějšího prostředí beze změny výrazně kódu vaší aplikace a základní architektury. 

Tento průvodce také zvýrazní výhod přesun aplikací do cloudu a částečně modernizaci aplikací s použitím konkrétní sadu nových technologií a postupů, jako jsou kontejnery Windows a související výpočetních platforem v Azure podporuje kontejnery Windows.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Cestou ke cloudu pro existující aplikace .NET

Organizace obvykle zvolit přesunout do cloudu pro flexibilitu a rychlost, kterou můžete získat pro své aplikace. Nastavením serverů (VM) v cloudu v řádu minut a ve srovnání s týdnů, které obvykle trvá nastavit na místních serverech.

Není k dispozici jednotné, univerzální strategie pro migraci aplikací do cloudu. Strategie správné migrace pro vás bude záviset na potřebám vaší organizace a priority a typ aplikace, kterou migrujete. U některých aplikací není zaručujete investice přechodu na platforma jako služba ([PaaS](https://azure.microsoft.com/overview/what-is-paas/)) modelu nebo vývoj [nativní pro cloud](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikačního modelu. V mnoha případech můžete provést postupné nebo přírůstkové přístup investovat do Přesun do cloudu, na základě obchodních potřeb vašich prostředků.

Pro moderní aplikace s nejlepším dlouhodobým flexibilitu a hodnota pro organizace, které může mít užitek z investic do *nativní pro cloud* aplikačních architektur. Pro aplikace, které jsou existující nebo starší verzi prostředky klíč je však věnovat minimální čas a peníze (změny bez kódu nebo změna architektury) při přesunu do cloudu, jak začít využívat významné výhody.

Obrázek 1-1 zobrazuje možné cesty, které můžete provést při přesunu stávajících aplikací .NET do cloudu v přírůstkové fází.

 ![Cesty modernizaci stávajících aplikací .NET a služeb](./media/image1-1.png)

> **Obrázek 1-1**. Cesty modernizaci stávajících aplikací .NET a služeb

Každý přístup k migraci má různé výhody a důvody k jeho používání. Můžete zvolit jeden přístup při migraci aplikací do cloudu, nebo vyberte určité komponenty z více přístupů. Nejsou omezené na jeden přístup nebo vyspělosti stavu jednotlivých aplikací. Běžným přístupem hybridní by například mají určité místní komponenty, a navíc další součásti v cloudu.

Definice a krátkým vysvětlením pro každou úroveň vyspělosti aplikace jsou následující:

**Úrovně 1: Infrastruktury připravené Cloud** aplikací: V rámci tohoto přístupu migrace můžete jednoduše migrovat nebo opětovným hostováním stávajících místních aplikací pro infrastrukturu jako službu ([IaaS](https://azure.microsoft.com/overview/what-is-iaas/)) platformu. Vaše aplikace mají téměř stejné složení jako před, ale teď je nasadit na virtuální počítače v cloudu.
Tento jednoduchý typ migrace se obvykle označuje v odvětví jako "Lift & Posunout."

**Úroveň 2: Cloud optimalizovaný** aplikace: na této úrovni a stále bez změna architektury nebo změnou významné kódu můžete získat další výhody spuštění vaší aplikace v cloudu s využitím moderních technologií, jako jsou kontejnery a další spravované cloudové služby. Je zvýšit flexibilitu, vaše aplikace rychleji dodávat tím, že upřesníte vašich podnikových procesů vývoje operací (DevOps). Můžete toho dosáhnout pomocí technologie, jako jsou kontejnery Windows, která je založena na modul Docker. Kontejnery odeberte řešit zádrhele spojené s, jež je způsobena závislosti aplikací při nasazení v několika fázích. V tomto modelu vyspělosti můžete nasadit kontejnery na IaaS nebo PaaS při používání další spravované cloudové služby související s databází, mezipaměti jako služba, monitorování a průběžné integrace a nasazování (CI/CD) kanálů.

Na třetí úrovni vyspělosti je konečným cílem v cloudu, ale je nepovinné pro mnoho aplikací a nikoli hlavní fokus této příručky:

**Úroveň 3: Cloudově nativních** aplikací: Tento postup migrace obvykle doprovází cíle modernizace klíčových aplikací a obchodní potřeby. Na této úrovni pomocí služeb PaaS přesunout vaše aplikace na výpočetní platformy PaaS. Můžete implementovat [nativní pro cloud](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) architektury mikroslužeb a aplikace rozvoj aplikací s flexibilitou dlouhodobé a škálovat na nová omezení. Tento typ modernizaci obvykle vyžaduje aplikační architektura založená na speciálně pro cloud. Nové často musí být kód zapsán, zejména v případě, že přejdete na aplikace nativní pro cloud a modely založených na mikroslužbách. Tento přístup vám může pomoct získat výhody, které je obtížné dosáhnout v monolitické i v místním prostředí pro vaše aplikace.

Tabulka 1-1 popisuje hlavní výhody a důvodů pro volbu každý migrace nebo modernizaci přístup.

| **Infrastruktury připravené pro cloud** <br /> *Přenést* | **Optimalizované pro cloud** <br /> *Modernizujte* | **Nativní pro cloud** <br /> *Modernizace, úprava architektury a revize* |
|---|---|---|
| **Cílové výpočetní prostředí vaší aplikace** |
| Aplikace nasazené pro virtuální počítače v Azure | Monolitické nebo N-vrstvá aplikace nasazené do služby Azure App Service, Azure Container Instance (ACI), virtuální počítače s kontejnery, Azure Service Fabric nebo AKS (služby Azure Kubernetes Service) | Kontejnerizované mikroslužby v Azure Kubernetes Service (AKS), Service Fabric a/nebo založené na Azure Functions bez serveru mikroslužeb. |
| **Cíl dat** |
| SQL nebo jakoukoli relační databázi na virtuálním počítači | Azure SQL Database Managed Instance nebo jiné spravované databáze v cloudu. | Pokutu intervalem databází na mikroslužbách, založené na Azure SQL Database, Azure Cosmos DB nebo jiné spravované databáze v cloudu |
| **Výhody**|
| <li>Žádná změna architektury, nové kódu <li> Minimálním úsilí pro rychlé migrace <li> Nejméně společným faktorem podporované v Azure <li> Zaručuje základní dostupnosti <li> Po přesunu do cloudu, je jednodušší modernizovat ještě víc | <li> Žádná změna architektury <li> Změny minimální kódu/konfigurace <li> Vylepšené nasazení a flexibilita DevOps uvolnit z důvodu kontejnery <li> Vyšší hustotu a nižší náklady na nasazení <li> Přenositelnost aplikací a závislostí <li> Flexibilita hostitele cíle: PaaS přístupy nebo IaaS | <li> Návrhář pro cloud, získáte nejlepší výhody z cloudu, ale je potřeba nový kód <li> Mikroslužby cloudově nativních postupů <li> Moderní aplikace, odolné cloudové hyperškálovatelném <li> Plně spravované služby <li> Optimalizováno pro škálování <li> Optimalizovaný pro flexibilitu autonomní podsystémem <li> Založená na nasazení a nástroji DevOps |
| **Výzvy** |
| <li> Menší hodnota cloudu, než shift v provozních výdajů nebo zavírání datových centrech <li> Trochu spravuje: žádný operační systém nebo middleware oprav; použít řešení infrastruktury, jako jsou Puppet, Terraformu nebo Spinnaker | <li> Uzavření do kontejneru se na další krok v Křivka osvojování znalostí pro vývojáře a IT oddělení <li> Kanály DevOps a CI/CD je obvykle "nezbytnost' pro tento přístup. Pokud není aktuálně k dispozici v jazykové verzi organizace, může být dalším problémem| <li> Vyžaduje rearchitecture pro architektury mikroslužeb a nativních aplikací pro cloud a obvykle vyžaduje významné kódu refaktoringu nebo přepsání při modernizaci (zvýšená času a prostředků) <li> Kanály DevOps a CI/CD je obvykle "nezbytnost' pro tento přístup. Pokud není aktuálně k dispozici v jazykové verzi organizace, může být dalším problémem|
> **Tabulka 1-1.** Výhody i výzvy cest modernizaci stávajících aplikací .NET a služeb

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Klíčové technologie a architektury podle úrovně vyspělosti

Aplikace rozhraní .NET framework s rozhraním .NET Framework verze 1.0, která byla vydaná v pozdní 2001 prvním spuštění. Potom přesunout společnosti na novější verze (například 2.0, 3.5 a .NET 4.x). Většina těchto aplikací byly spuštěny v systému Windows Server a Internet Information Server (IIS) a používá relační databázi, jako je SQL Server, Oracle, MySQL nebo jiné RDBMS.

Většina stávajících aplikací .NET může být v současné době založen na rozhraní .NET Framework 4.x, nebo dokonce i na rozhraní .NET Framework 3.5 a pomocí webové architektury, jako je ASP.NET MVC, webových formulářů ASP.NET, ASP.NET Web API, Windows Communication Foundation (WCF), funkce SignalR technologie ASP.NET a ASP.NET Web Pages . Tyto zřizuje technologií rozhraní .NET Framework jsou závislé na Windows. Tuto závislost je důležité vzít v úvahu, pokud migrujete jednoduše starší verze aplikací a chcete provést minimální změny vaší aplikační infrastruktury.

Obrázek 1 – 2 ukazuje primární technologie a architekturu stylů použitých na jednotlivé úrovně vyspělosti tři cloudu:

![Primární technologie pro každou úroveň vyspělosti pro modernizaci stávajících .NET webové aplikace](./media/image1-2.png)

> **Obrázek 1 – 2.** Primární technologie pro každou úroveň vyspělosti pro modernizaci stávajících .NET webové aplikace

Obrázek 1 – 2 zvýrazní nejběžnějších scénářů, ale mnoho hybridní a smíšené odchylky je možné, pokud jde o architektuře. Splatnosti modely například použít nejen na monolitické architektury do existující webové aplikace, ale také pro orientaci na služby, N-vrstvé a další varianty konfigurací styl architektury. Vyšší fokusu nebo procenta v architektura jednoho nebo jiný typ a souvisejících technologiích Určuje celkový úrovni vyspělosti vašich aplikací.

Každé úrovni vyspělosti v procesu modernizaci je přidružen následující klíčových technologií a postupů:

- **Cloud připravený pro infrastrukturu** (metody opětovného hostování nebo basic lift & shift): jako první krok, řada organizací má jenom rychle provést strategii migrace na cloud. V tomto případě aplikace se změněným hostováním. Změna hostování většiny je možné automatizovat pomocí [Azure Migrate](https://aka.ms/azuremigrate), služba, která poskytuje pokyny, přehledy a mechanizmy, které potřebuje pomoc při migraci do Azure založené na cloudu nástrojů, jako je [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)a [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/). Můžete vytvořit také ručně, změna hostování tak, aby informace infrastruktury podrobnosti o vašich prostředků při přesunu starší verze aplikací do cloudu. Například můžete přesunout vaše aplikace na virtuální počítače v Azure s minimem úpravy – pravděpodobně s pouze změny menší konfigurace. Sítě je v tomto případě podobné v místním prostředí, zejména v případě, že vytvoříte virtuální sítě v Azure.

- **Optimalizované pro cloud** (spravované služby a kontejnery Windows): Tento model je o tom, že několik důležitých nasazení optimalizace získat některé velké výhody cloudu, beze změny základní architektury aplikace. Tady základní krokem je přidání [kontejnery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) podporu pro existující aplikace rozhraní .NET Framework. Tento krok důležité (kontejnerizace) nevyžaduje, aby vůbec měnil kód, tak celkové úsilí výtah a posunout je světla. Můžete použít nástroje, jako je [Image2Docker](https://github.com/docker/communitytools-image2docker-win) nebo Visual Studio se svými nástroji pro [Docker](https://www.docker.com/). Visual Studio automaticky zvolí inteligentních výchozích hodnot pro aplikace ASP.NET a imagí kontejnerů Windows. Tyto nástroje nabízejí rychlý vnitřní smyčky a Rychlá cesta k získání kontejnerů do Azure. Zlepšení vaší flexibilitu při nasazování do různých prostředí. Potom přesunem do produkčního prostředí, můžete nasadit kontejnery Windows na [Azure Web App for Containers](https://azure.microsoft.com/en-us/services/app-service/containers/), [Azure Container Instances (ACI) a virtuální počítače Azure s Windows serverem 2016 a kontejnery, pokud chcete přístup IaaS. Pro o něco složitější vícekontejnerových aplikací do orchestrátorů, jako je [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) nebo [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/en-us/services/container-service/). Během této počáteční modernizaci, můžete také přidat prostředky z cloudu, např. monitorování pomocí nástrojů, jako je [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview); Kanály CI/CD pro váš životní cyklus aplikace s [Azure DevOps služby](https://visualstudio.microsoft.com/team-services/); a mnoho více datových prostředků služeb, které jsou dostupné v Azure. Například můžete upravit monolitické webovou aplikaci, která byla původně vyvinuta pomocí tradiční [webových formulářů ASP.NET](https://www.asp.net/web-forms) nebo [ASP.NET MVC](https://www.asp.net/mvc), ale teď můžete nasadit s využitím kontejnerů Windows. Při použití kontejnerů Windows by měl taky migrovat data do databáze v [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/), všechny beze změny základní architektury vaší aplikace.

- **Nativní pro cloud**: zavedeném, byste uvažovat o navrhování [nativní pro cloud](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikací, pokud cílíte na velkých a složitých aplikací s více nezávislých vývojové týmy pracující na různé mikroslužeb, která můžete vyvinuli a nasadit samostatně. Také kvůli škálovatelnosti granularized a nezávisle na mikroslužbách. Tyto přístupy k architektuře pro rozpoznávání tváře velmi důležité výzev a složitosti ale může být výrazně zjednodušuje použití cloudu PaaS a orchestrátorů, jako jsou [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/en-us/services/container-service/) (managed Kubernetes), [Azure Service Prostředky infrastruktury, a [Azure Functions](https://azure.microsoft.com/services/functions/) a bez serveru přístup. Všechny tyto přístupy (jako jsou mikroslužby a bez serveru) obvykle vyžadují, abyste navrhovat pro cloud a vytvoření nového kódu – kód, který je přizpůsobené pro konkrétní platformy PaaS nebo kód, který odpovídá různé architektury, jako jsou mikroslužby.

Obrázek 1 – 3 ukazuje interní technologie, můžete použít pro každou úroveň vyspělosti:

![Interní technologie pro každou úroveň vyspělosti modernizaci](./media/image1-3.png)

> **Obrázek 1 – 3.** Interní technologie pro každou úroveň vyspělosti modernizaci

## <a name="lift-and-shift-scenario"></a>Výtah a posunout scénář

Pro výtah a posunout migrace mít na paměti, že můžete použít mnoha různými variantami výtah a posunout ve vašich scénářích aplikací. Pokud pouze změna hostitele aplikace, bude pravděpodobně scénář podobný jako v 1 obrázek – 4, kde se budou virtuální počítače v cloudu pouze pro vaši aplikaci a na serveru databáze používat.

![Příklad scénáře IaaS čistě v cloudu](./media/image1-4.png)

> **Obrázek 1 – 4**. Příklad scénáře IaaS čistě v cloudu

## <a name="modernization-scenarios"></a>Modernizace scénáře

Pro scénáře, modernizaci může mít čistě optimalizované pro Cloud aplikace v jazyce, který používá prvky pouze z této úrovni vyspělosti. Nebo může být přechodný stav aplikace pomocí některé prvky z infrastruktury připravené pro Cloud a další prvky z optimalizovaných pro Cloud (a "zvolit" nebo smíšené model), jako obrázek 1 – 5.

![Příklad "zvolit" scénáři s databází na IaaS, DevOps a kontejnerizačních majetku](./media/image1-5.png)

> **Obrázek 1 – 5.** Příklad "zvolit" scénáři s databází na IaaS, DevOps a kontejnerizačních majetku

Další, jako by v ideálním případě mnoho existujících aplikací rozhraní .NET Framework pro migraci můžete migrovat do aplikace optimalizované pro Cloud, abyste získali významné výhody z mnoho zásahů. Tento přístup také nastaví pro nativní pro Cloud jako možný budoucí vývoj. Obrázek 1 – 6 ukazuje příklad.

![Příklad scénáře aplikací optimalizovaných pro Cloud, s kontejnery Windows a spravované služby](./media/image1-6.png)

> **Obrázek 1 – 6.** Příklad scénáře aplikací optimalizovaných pro Cloud, s kontejnery Windows a spravované služby

Když se ještě dál, můžete rozšířit existující aplikace optimalizované pro Cloud tak, že přidáte několik mikroslužeb pro konkrétní scénáře. To by posunula je částečně na úrovni modelu nativní pro Cloud, který není hlavním účelem k dispozici pokyny.


## <a name="what-this-guide-does-not-cover"></a>Co tato příručka nepopisuje

Tento průvodce popisuje určitou podmnožinu ukázkové scénáře, jak ukazuje obrázek 1 – 7. Tato příručka se zaměřuje pouze na scénáře výtah a posunout a nakonec na modelu optimalizovaných pro Cloud. V modelu optimalizovaných pro Cloud s využitím kontejnerů Windows a další komponenty, jako jsou monitorování je modernizovala aplikace rozhraní .NET Framework a kanály CI/CD. Jednotlivé komponenty je nezbytné k nasazení aplikací do cloudu a rychleji a s flexibilitou.

![Nativní pro cloud není součástí této příručky](./media/image1-7.png)

> **Obrázek 1 – 7.** Nativní pro cloud není součástí této příručky

Fokus Tato příručka se věnuje. Zobrazuje cestu, která můžete provést k dosažení lift and shift existující aplikace .NET bez změna architektury a beze změny kódu. Nakonec se ukazuje, jak vaše aplikace optimalizované pro Cloud.

Tato příručka nepodporuje ukazují, jak vytvářet aplikace nativní pro Cloud, jako je například způsobu, jak rozvíjet na architekturu mikroslužeb. Úprava architektury aplikace nebo vytvoření zcela nové aplikace, které jsou založené na mikroslužbách najdete v e kniha [Mikroslužby .NET: architektura pro kontejnerizované aplikace .NET](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Další zdroje

- **Životní cyklus aplikace Dockeru s platformou a nástroji Microsoft kontejnerizovaných** (ke stažení e kniha): [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

- **Mikroslužby .NET: Architektura pro kontejnerizované aplikace .NET** (ke stažení e kniha): [*https://aka.ms/microservicesebook*](https://aka.ms/microservicesebook)

- **Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure** (ke stažení e kniha): [*https://aka.ms/webappebook*](https://aka.ms/webappebook)

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tohoto průvodce

Tato příručka je určen pro vývojáře a architekty řešení, které chtějí modernizovat existující webové aplikace ASP.NET nebo služby WCF, které jsou založeny na rozhraní .NET Framework pro vyšší flexibility v přesouvání a uvolněním aplikace.

Také můžou být užitečné tohoto průvodce máte technický pracovník s rozhodovací pravomocí, jako je enterprise architekta nebo vývoj zájemce/ředitel který stačí chce přehled výhod, které můžete získat pomocí kontejnery Windows a nasazením do cloudu, při použití Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Jak používat tohoto průvodce

Tento průvodce řeší "Proč"-důvod, proč můžete chtít modernizovat existující aplikace a konkrétní výhod, které pomocí kontejnerů Windows, když přesouváte aplikace do cloudu. Obsah v prvních několika kapitoly v průvodci je určená pro architekty a technické rozhodovací pravomocí, kteří chtějí přehled, ale který nemusíte soustředit na implementaci a krok za krokem, technické podrobnosti.

Poslední kapitol tohoto průvodce zavádí několik návodů, které se zaměřují na konkrétní scénáře nasazení. Tento průvodce nabízí kratší verze návody, Shrňte scénáře a zvýraznit jejich výhody. Úplný Průvodce přejít na podrobnosti o instalaci a provedení a publikují jako sada [wiki příspěvků](https://github.com/dotnet-architecture/eShopModernizing/wiki) na stejné veřejných [úložiště GitHub se vzorovými](https://github.com/dotnet-architecture/eShopModernizing) tam, kde se nacházejí související ukázkové aplikace (popsané v následujících oddíl). Poslední kapitoly wiki podrobné návody na Githubu to důležitější vývojářům a architektům, kteří chtějí zaměřit se na podrobnosti implementace.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Ukázkové aplikace pro modernizaci starší verze aplikací: eShopModernizing

[EShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) úložišti na Githubu nabízí dvě ukázkové aplikace, které simulují starších monolitických webových aplikací. Je jedné webové aplikace vyvinuté pomocí ASP.NET MVC; je druhý webové aplikace vyvinuté pomocí technologie ASP.NET webové formuláře a třetí aplikace je N-vrstvá aplikace s aplikací klasické pracovní plochy klienta WinForms využívání back-endu služby WCF. Tyto aplikace jsou založeny na tradiční rozhraní .NET Framework. Tyto ukázkové aplikace nepoužívejte .NET Core nebo ASP.NET Core, protože mají být být modernizovala existující/starší verze aplikací rozhraní .NET Framework.

Tyto ukázkové aplikace druhou verzi, modernizované kódem a která jsou poměrně jednoduché. Nejdůležitější rozdíl mezi verzemi aplikace je, že druhý verze používat kontejnery Windows jako možnost nasazení. Existuje také několik dodatky na druhý verze, jako je úložiště objektů BLOB Azure ke správě imagí, Azure Active Directory pro správu zabezpečení a Azure Application Insights pro sledování a auditování v aplikacích.

## <a name="send-your-feedback"></a>Pošlete svůj názor

Tato příručka byla zapsána do vám pomůže pochopit možnosti zlepšení a modernizaci stávajících webových aplikací .NET. Průvodce a související ukázkové aplikace se vyvíjejí. Vaše zpětná vazba je Vítejte! Pokud máte poznámky o tom, jak tento průvodce může být užitečnější, odešlete jim [ dotnet-architecture-ebooks-feedback@service.microsoft.com ](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

>[!div class="step-by-step"]
[Next](lift-and-shift-existing-apps-azure-iaas.md)
