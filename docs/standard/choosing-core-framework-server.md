---
title: Volba mezi .NET Core a rozhraní .NET Framework pro server aplikace
description: Průvodce, na které implementace rozhraní .NET, byste měli zvážit při vytváření aplikace server v rozhraní .NET.
author: cartermp
ms.author: mairaw
ms.date: 03/15/2018
ms.openlocfilehash: 5626c6c1687fe0b8d558df8772fc69c32981787c
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>Volba mezi .NET Core a rozhraní .NET Framework pro server aplikace

Existují dvě podporované implementace pro vytváření aplikací na straně serveru pomocí rozhraní .NET: rozhraní .NET Framework a .NET Core. Mnoho stejných komponent sdílejí a kódu můžete sdílet mezi dva. Ale existují základní rozdíly mezi nimi a výběr závisí na co chcete dosáhnout.  Tento článek obsahuje pokyny k použití každé.

Použít pro vaše serverová aplikace .NET Core při:

* Máte potřebám napříč platformami.
* Cílení mikroslužeb.
* Používáte Docker kontejnery.
* Potřebujete škálovatelné a vysoce výkonný systémy.
* Je třeba verze rozhraní .NET vedle sebe na aplikaci.

Použití rozhraní .NET Framework pro aplikace serveru při:

* Vaše aplikace právě používá rozhraní .NET Framework (doporučuje se rozšířit místo migrace).
* Vaše aplikace používá knihovny .NET třetích stran nebo není k dispozici balíčky NuGet pro .NET Core.
* Vaše aplikace používá technologie .NET, které nejsou k dispozici pro .NET Core.
* Vaše aplikace používá platformu, která nepodporuje .NET Core.

## <a name="when-to-choose-net-core"></a>Kdy zvolte .NET Core

Podrobnější vysvětlení výše uvedená důvody pro výběr .NET Core naleznete v následujících oddílech.

### <a name="cross-platform-needs"></a>Napříč platformami potřeb

Pokud potřebám vaší aplikace (web/service) běžela na více platforem (Windows, Linux a systému macOS), použijte .NET Core.

.NET core podporuje výše uvedených operačních systémů jako stanici vývoje. Visual Studio poskytuje integrované vývojové prostředí (IDE) pro systém Windows a systému macOS. Můžete také použít Visual Studio Code, který běží na systému macOS, Linux a Windows. Visual Studio Code podporuje .NET Core, včetně technologie IntelliSense a ladění. Většina editory třetích stran, jako je například Sublime, Emacs a VI, pracovat s .NET Core. Tyto editory třetích stran získat editor IntelliSense pomocí [Omnisharp](https://www.omnisharp.net/). Můžete také vyhnout libovolného editoru kódu a přímo použít [nástrojů příkazového řádku .NET Core](../core/tools/index.md), k dispozici pro všechny podporované platformy.

### <a name="microservices-architecture"></a>Architektura Mikroslužeb

Architektura mikroslužeb umožňuje směs technologie přes hranice služby. Kombinace tato technologie umožňuje postupná mohlo .NET jádra pro nové mikroslužeb, které pracují s jinými mikroslužeb nebo služby. Například je možné kombinovat služby vyvinuté pomocí rozhraní .NET Framework, Java, Ruby nebo jiných monolitický technologií nebo mikroslužeb.

Nejsou k dispozici mnoho platformy infrastruktury. [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) je určena pro velké a komplexní mikroslužbu systémy. [Aplikační služba Azure](https://azure.microsoft.com/services/app-service/) je vhodná pro bezstavové mikroslužeb. Alternativy Mikroslužeb podle Docker přizpůsobit jakýkoli druh mikroslužeb způsob, jak je popsáno v [kontejnery](#containers) části. Všechny tyto platformy podporují .NET Core a proveďte je ideální pro hostování vaší mikroslužeb.

Další informace o architektuře mikroslužeb najdete v tématu [Mikroslužeb .NET. Architektura pro aplikace .NET Kontejnerizované](microservices-architecture/index.md).

### <a name="containers"></a>Kontejnery

Kontejnery běžně se používají ve spojení s architekturou mikroslužeb. Kontejnery lze také containerize webové aplikace nebo služby, které následují žádné architekturní vzor. Rozhraní .NET framework lze použít v systému Windows kontejnery, ale modularitu a lightweight povaha .NET Core umožňuje lepší volbou pro kontejnery. Při vytváření a nasazování kontejner, velikost jeho bitové kopie je mnohem menší s .NET Core než v rozhraní .NET Framework. Protože je a platformy, můžete nasadit aplikace server Linux Docker kontejnery, například.

Kontejnery docker může být hostovaný v infrastruktuře vlastní Linux nebo Windows, nebo v cloudové službě, jako [Azure Container Service](https://azure.microsoft.com/services/container-service/). Azure Container Service můžete spravovat, orchestraci a škálování aplikace založené na kontejneru v cloudu.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Třeba pro vysoce výkonné a škálovatelné systémy

Když váš systém potřebuje nejlepší možný výkon a škálovatelnost, .NET Core a ASP.NET Core jsou nejlepší možnosti. Modul runtime vysoce výkonné serveru pro Server systému Windows a Linux .NET díky nejvyšší provádění webového framework na [srovnávacích testů TechEmpower](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

Výkon a škálovatelnost jsou obzvláště důležité pro mikroslužeb architektury, kde může používat stovky mikroslužeb. Základní technologie ASP.NET spusťte systémy s používá mnohem menší počet serverů/virtuální počítače (VM). Snížené serverech nebo virtuálních počítačů uložit náklady na infrastrukturu a hostování.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Potřeba vedle sebe z verzí rozhraní .NET na úrovni aplikace

Chcete-li nainstalovat aplikace se závislostmi na různé verze rozhraní .NET, doporučujeme .NET Core. .NET core nabízí vedle sebe instalace různých verzí aplikace na .NET Core runtime na stejném počítači. Tato instalace vedle sebe umožňuje více službám na stejném serveru, každý z nich na svou vlastní verzi .NET Core. Také snižuje rizika a úsporu nákladů ve upgradů aplikací a IT oddělení.

## <a name="when-to-choose-net-framework"></a>Kdy použít rozhraní .NET Framework

.NET core nabízí významné výhody pro nové aplikace a aplikace vzory. Nadále se přirozeně volba pro mnoho scénářů s existující a jako takový však rozhraní .NET Framework. Rozhraní .NET Framework není nahrazena .NET Core pro všechny serverové aplikace.

### <a name="current-net-framework-applications"></a>Aktuální aplikace rozhraní .NET Framework

Ve většině případů nemusíte migrovat stávající aplikace pro .NET Core. Doporučený postup je místo toho použijte .NET Core, jak rozšířit existující aplikace, jako je například zápis novou webovou službu v ASP.NET Core.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Potřeba používat knihovny .NET třetích stran nebo není k dispozici balíčky NuGet pro .NET Core

Knihovny jsou osvojují rychle .NET Standard. .NET standard umožňuje sdílení kódu mezi všechny implementace rozhraní .NET, včetně .NET Core. Pomocí rozhraní .NET 2.0 standardní jde to bylo ještě jednodušší:

- Plochy rozhraní API se stala mnohem větší. 
- Zavedli režim kompatibility rozhraní .NET Framework. Tento režim kompatibility umožňuje .NET Standard nebo .NET Core projekty tak, aby odkazovaly knihovny rozhraní .NET Framework. Další informace o režimu kompatibility najdete v tématu [uvedení standardní rozhraní .NET 2.0](https://blogs.msdn.microsoft.com/dotnet/2017/08/14/announcing-net-standard-2-0/).

Proto pouze v případech, kde knihoven nebo balíčků NuGet používat technologie, které nejsou k dispozici v rozhraní .NET Standard nebo .NET Core budete muset použít rozhraní .NET Framework.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>Potřeba používat technologie .NET, není k dispozici pro .NET Core

Některé technologie .NET Framework nejsou k dispozici v .NET Core. Některé z nich může být k dispozici v pozdějších verzích .NET Core. Ostatní se nevztahují na nové aplikace vzory cílem .NET Core a nikdy nemusí být k dispozici. Následující seznam uvádí nejběžnější technologie nebyla nalezena v .NET Core:

* Aplikace webových formulářů ASP.NET: webových formulářů ASP.NET jsou dostupné jenom v rozhraní .NET Framework. ASP.NET Core nelze použít pro webových formulářů ASP.NET. Neexistují žádné plány a dovést webových formulářů ASP.NET do .NET Core.

* Aplikace ASP.NET Web Pages: rozhraní ASP.NET Web Pages nejsou součástí ASP.NET Core. ASP.NET Core [stránky Razor](/aspnet/core/mvc/razor-pages/) mít mnoho společného s webovými stránkami.

* Implementace klienta nebo serveru funkce SignalR technologie ASP.NET. V současné době [funkce SignalR technologie ASP.NET](https://github.com/aspnet/SignalR) je k dispozici v režimu preview s ASP.NET Core 2.1.

* Implementace služby WCF. I když dojde [knihovny klienta WCF](https://github.com/dotnet/wcf) využívat služby WCF z .NET Core, implementaci serveru WCF je aktuálně k dispozici pouze v rozhraní .NET Framework. Tento scénář není součástí stávající plán pro .NET Core, ale je nepovažoval do budoucna.

* Služby související s pracovního postupu: Windows Workflow Foundation (WF), služby pracovních postupů (WCF + WF v jedné službě) a služby WCF Data Services (dříve označované jako "ADO.NET Data Services") jsou dostupné jenom v rozhraní .NET Framework.  Neexistují žádné plány aby WF/WCF + WF nebo součásti WCF Data Services pro .NET Core.

* Podpora jazyků: Visual Basic a F # jsou aktuálně podporovány v .NET Core, ale ne pro všechny typy projektů. Seznam podporovaných projektu šablony najdete v tématu [možnosti šablony pro dotnet nové](../core/tools/dotnet-new.md#arguments).

Kromě oficiální plán jsou ostatní platformy přenést na .NET Core. Úplný seznam najdete v tématu problémy CoreFX označen jako [port základní](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core). Tento seznam nepředstavuje závazek od společnosti Microsoft k poskytování těchto součástí na .NET Core. Budou se jednoduše zaznamenání desire od komunity Uděláte to tak. Pokud se zajímáte o libovolné součásti označeny jako `port-to-core`, zúčastnit se diskuzí na Githubu. A pokud se domníváte, že něco chybí, nový problém v souboru [CoreFX úložiště](https://github.com/dotnet/corefx/issues/new).

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>Potřeba používat platformu, která nepodporuje .NET Core

Některé společnosti Microsoft nebo třetích stran platformy nepodporují .NET Core. Například některé Azure služby, jako je Service Fabric stavové služby Reliable Services a Reliable Actors prostředků infrastruktury služby vyžadují rozhraní .NET Framework. Některé jiné služby zadejte ještě není k dispozici pro používání sady SDK na .NET Core. Jedná se přechodném okolnosti, protože všechny služby Azure pomocí .NET Core. Do té doby mohou vždy použít ekvivalentní REST API místo klienta SDK.

## <a name="see-also"></a>Viz také
 [Zvolte mezi ASP.NET a ASP.NET Core](/aspnet/core/choose-aspnet-framework)  
 [Průvodce platformou .NET Core](../core/index.md)  
 [Portování z rozhraní .NET Framework na .NET Core](../core/porting/index.md)  
 [Průvodce rozhraním .NET Framework v Dockeru](../framework/docker/index.md)  
 [Přehled součásti rozhraní .NET](components.md)  
 [Rozhraní .NET Mikroslužeb. Architektura pro aplikace .NET Kontejnerizované](microservices-architecture/index.md)
