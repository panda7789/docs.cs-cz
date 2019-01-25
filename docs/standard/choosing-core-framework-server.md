---
title: Volba mezi .NET Core a .NET Framework pro serverové aplikace
description: Průvodce, na kterou implementaci rozhraní .NET, měli byste zvážit při vytváření serveru aplikace v .NET.
author: cartermp
ms.author: mairaw
ms.date: 06/19/2018
ms.openlocfilehash: fe6aa28b456d3a83b15dfcb3a65147e77b9d5f85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699503"
---
# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>Volba mezi .NET Core a .NET Framework pro serverové aplikace

Existují dvě podporované implementace pro vytváření aplikací na straně serveru s .NET: rozhraní .NET Framework a .NET Core. Ke sdílené složce i řadu stejné komponenty a kód můžete sdílet mezi nimi. Ale existují podstatné rozdíly mezi nimi a podle vašeho výběru, závisí na co chcete dosáhnout.  Tento článek obsahuje pokyny, kdy se má použít.

Použití .NET Core pro serverové aplikace při:

* Máte požadavky napříč platformami.
* Cílíte mikroslužeb.
* Používání kontejnerů Dockeru.
* Potřebujete vysoce výkonné a škálovatelné systémy.
* Je třeba verze rozhraní .NET vedle sebe na aplikaci.

Použití rozhraní .NET Framework pro serverové aplikace při:

* Vaše aplikace právě používá rozhraní .NET Framework (doporučení je rozšíření místo migrace).
* Vaše aplikace používá knihovny .NET třetích stran nebo není k dispozici balíčky NuGet pro .NET Core.
* Vaše aplikace používá technologie .NET, které nejsou k dispozici pro .NET Core.
* Vaše aplikace používá platformu, která nepodporuje .NET Core.

## <a name="when-to-choose-net-core"></a>Kdy zvolit .NET Core

Následující části poskytují podrobnější vysvětlení výše uvedená důvody pro výběr .NET Core.

### <a name="cross-platform-needs"></a>Potřebuje víc platforem

Pokud se potřeby vaší aplikace (web/service) pro spuštění na více platforem (Windows, Linux a macOS), pomocí .NET Core.

.NET core podporuje výše uvedených operačních systémů jako pracovní stanici vývoje. Visual Studio poskytuje integrované vývojové prostředí (IDE) pro Windows a macOS. Můžete také použít Visual Studio Code, který běží v systémech macOS, Linux a Windows. Visual Studio Code podporuje .NET Core, včetně technologie IntelliSense a ladění. Většina editory třetích stran, jako je například Sublime (emacs) a VI, pracovat s .NET Core. Editory těchto třetích stran získání funkce IntelliSense editoru pomocí [Omnisharp](https://www.omnisharp.net/). Můžete také zabránit libovolném editoru kódu a používat přímo [nástroje rozhraní příkazového řádku .NET Core](../core/tools/index.md), která je dostupná pro všechny podporované platformy.

### <a name="microservices-architecture"></a>Architektura Mikroslužeb

Architektura mikroslužeb umožňuje kombinace technologií přes hranice služeb. Kombinace tato technologie umožňuje postupné mohlo .NET Core pro nové mikroslužby, které pracují s jinými mikroslužby nebo službami. Například je možné kombinovat mikroslužby nebo služby vyvinuté pomocí rozhraní .NET Framework, Java, Ruby nebo jiné monolitické technologie.

Nejsou k dispozici řada platforem infrastruktury. [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) je navržená pro systémy velkých a složitých mikroslužeb. [Azure App Service](https://azure.microsoft.com/services/app-service/) je dobrou volbou pro bezstavové mikroslužby. Mikroslužby alternativy založené na Dockeru přizpůsobit jakýkoli druh mikroslužeb přístup, jak je vysvětleno v [kontejnery](#containers) oddílu. Všechny tyto platformy podporovat .NET Core a ujistěte se, je ideální pro hostování mikroslužby.

Další informace o architektuře mikroslužeb najdete v tématu [Mikroslužby .NET. Architektura pro Kontejnerizované aplikace .NET](microservices-architecture/index.md).

### <a name="containers"></a>Kontejnery

Kontejnery jsou obvykle používá ve spojení s architekturou mikroslužeb. Kontejnery lze také kontejnerizace webových aplikací a služeb, které následují všech možných architektonických řešení. Rozhraní .NET framework lze použít v kontejnerech Windows, ale modularitu a zjednodušené povaze .NET Core umožňuje lepší volbou pro kontejnery. Při vytváření a nasazení kontejneru, je mnohem menší s .NET Core s rozhraním .NET Framework než velikosti jeho image. Protože je multiplatformní, můžete nasadit server aplikace pro kontejnery linuxového Dockeru, třeba.

Kontejnery dockeru je možné hostovat ve vaší vlastní infrastruktuře Linux nebo Windows nebo v cloudové službě, jako [Azure Container Service](https://azure.microsoft.com/services/container-service/). Služba Azure Container Service můžete spravovat, organizovat a škálování kontejnerových aplikací v cloudu.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Třeba pro vysoce výkonné a škálovatelné systémy

Pokud váš systém potřebuje nejlepší možný výkon a škálovatelnost, .NET Core a ASP.NET Core jsou nejlepší možností. Modul runtime výkonné serveru pro Windows Server a Linux vytvoří .NET nejvyšší provádění webová architektura na [srovnávací testy TechEmpower](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

Výkon a škálovatelnost jsou obzvláště důležité pro architekturu mikroslužeb, ve kterém mohou běžet stovky mikroslužeb. Pomocí ASP.NET Core spusťte systémy s mnohem menším počtem serverů a virtuálních počítačů (VM). Snížení servery nebo virtuální počítače uložte náklady na infrastrukturu a hostování.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Třeba pro souběžné verze .NET na úrovni aplikace

Instalace aplikace se závislostmi na různé verze rozhraní .NET, doporučujeme .NET Core. .NET core nabízí--souběžná instalace různých verzí modulu runtime .NET Core ve stejném počítači. Tato instalace vedle sebe několik služeb, které umožňuje na stejném serveru, každý z nich na svou vlastní verzi .NET Core. Také snižuje rizika a šetří peníze v upgradech aplikací a IT operace.

## <a name="when-to-choose-net-framework"></a>Kdy zvolit rozhraní .NET Framework

.NET core nabízí významné výhody pro nové aplikace a modelům aplikací. Ale rozhraní .NET Framework je stále přirozenou volbou pro mnoho scénářů s existující a proto není rozhraní .NET Framework nahrazuje .NET Core pro všechny serverové aplikace.

### <a name="current-net-framework-applications"></a>Aktuální aplikace rozhraní .NET Framework

Ve většině případů není nutné migrovat existující aplikace až po .NET Core. Doporučený postup je místo toho, jak rozšířit existující aplikace, jako je například zápis nové webové služby v ASP.NET Core pomocí .NET Core.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Nutnost používat .NET knihovny třetích stran nebo není k dispozici balíčky NuGet pro .NET Core

Knihovny rychle využívají .NET Standard. .NET standard umožňuje sdílení kódu mezi všechny implementace .NET, včetně .NET Core. S rozhraním .NET Standard 2.0 to je ještě jednodušší:

- Mnohem větší začal být plochy rozhraní API. 
- Zavedená režim kompatibility rozhraní .NET Framework. Tento režim kompatibility umožňuje projekty .NET Standard a .NET Core k odkazování knihoven .NET Framework. Další informace o režimu kompatibility najdete v tématu [Ohlašujeme .NET Standard 2.0](https://blogs.msdn.microsoft.com/dotnet/2017/08/14/announcing-net-standard-2-0/).

Proto pouze v případech, kdy knihoven nebo balíčků NuGet používat technologie, které nejsou k dispozici v rozhraní .NET Standard a .NET Core budete muset použít rozhraní .NET Framework.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>Nutnost používat technologie .NET, není k dispozici pro .NET Core

Některé technologie rozhraní .NET Framework nejsou k dispozici v .NET Core. Některé z nich může být k dispozici v pozdějších verzích .NET Core. Ostatní se nevztahují na nové modely aplikace cílí na .NET Core a může být nikdy k dispozici. Následující seznam uvádí nejběžnější technologie nebyl nalezen v .NET Core:

* Aplikace webových formulářů ASP.NET: Webové formuláře ASP.NET jsou dostupné pouze v rozhraní .NET Framework. ASP.NET Core nelze použít pro webové formuláře ASP.NET. Nejsou žádné plány zpřístupnit webových formulářů ASP.NET pro .NET Core.

* Aplikace webové stránky ASP.NET: ASP.NET Web Pages nejsou zahrnuty v ASP.NET Core. 

* Implementace služby WCF. I když dojde [knihovna klienta WCF](https://github.com/dotnet/wcf) k využívání služeb WCF v .NET Core, implementaci serveru WCF je momentálně dostupný jenom v rozhraní .NET Framework. Tento scénář není součástí aktuální plán pro .NET Core, ale je nepovažoval v budoucnosti.

* Související pracovní postup služby: Windows Workflow Foundation (WF), služby pracovních postupů (WCF a WF v jedné službě) a služby WCF Data Services (dříve označované jako "Služby ADO.NET Data Services") jsou k dispozici pouze v rozhraní .NET Framework.  Nejsou žádné plány zpřístupnit WF/WCF + WF/WCF Data Services pro .NET Core.

* Podpora jazyků: Visual Basic a F# se aktuálně podporují v .NET Core, ale ne pro všechny typy projektů. Seznam podporovaných projektu šablony najdete v tématu [možnosti šablony pro dotnet nové](../core/tools/dotnet-new.md#arguments).

Kromě oficiální plán jsou k dispozici další architektury přenést až po .NET Core. Úplný seznam, podívejte se na problémy CoreFX označen jako [port core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core). Tento seznam nepředstavuje závazek zpřístupnit tyto komponenty pro .NET Core od společnosti Microsoft. Jednoduše zachycujete přání od komunity Uděláte to tak. Pokud vás zajímají libovolné součásti označeny jako `port-to-core`, zúčastnit se diskuzí na Githubu. A pokud se domníváte něco chybí, vytvoří nový problém v souboru [CoreFX úložiště](https://github.com/dotnet/corefx/issues/new).

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>Nutnost používat platformu, která nepodporuje .NET Core

Některé společnosti Microsoft nebo třetích stran platformy .NET Core nepodporuje. Například některé Azure services, jako je Service Fabric stavové služby Reliable Services a Service Fabric Reliable Actors vyžadují rozhraní .NET Framework. Některé služby poskytují zatím není k dispozici pro použití sady SDK .NET Core. To je závislá na přechodné, protože všechny služby Azure pomocí .NET Core. Do té doby můžete vždy použít ekvivalentní rozhraní REST API namísto klientskou sadou SDK.

## <a name="see-also"></a>Viz také:

- [Zvolte mezi ASP.NET a ASP.NET Core](/aspnet/core/choose-aspnet-framework)
- [ASP.NET Core, které cílí na rozhraní .NET Framework](/aspnet/core#aspnet-core-targeting-net-framework)
- [Cílové verze rozhraní .NET Framework](frameworks.md)
- [Průvodce platformou .NET Core](../core/index.md)
- [Portování z rozhraní .NET Framework do .NET Core](../core/porting/index.md)
- [Průvodce rozhraním .NET Framework v Dockeru](../framework/docker/index.md)
- [.NET – přehled komponenty](components.md)
- [Mikroslužby .NET. Architektura pro kontejnerizované aplikace .NET](microservices-architecture/index.md)
