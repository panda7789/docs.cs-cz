---
title: Volba mezi .NET Core a .NET Framework pro serverové aplikace
description: Průvodce, který vám pomůže rozhodnout, jakou implementaci rozhraní .NET použít při vytváření serverové aplikace.
author: cartermp
ms.date: 04/28/2020
ms.openlocfilehash: 30157276bce53ed44dca5b660172e5556dab14f8
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507439"
---
# <a name="net-core-vs-net-framework-for-server-apps"></a>.NET Core vs. .NET Framework pro serverové aplikace

Pro vytváření aplikací na straně serveru jsou k dispozici dvě podporované implementace .NET: .NET Framework a .NET Core. Oba sdílejí mnoho stejných komponent a můžete sdílet kód mezi dvěma. Existují však zásadní rozdíly mezi těmito dvěma a volbami, záleží na tom, co chcete provést. Tento článek poskytuje pokyny k použití jednotlivých.

Pro serverovou aplikaci použijte .NET Core v těchto případech:

- Máte různé požadavky na více platforem.
- Cílíte na mikroslužby.
- Používáte kontejnery Docker.
- Potřebujete vysoce výkonné a škálovatelné systémy.
- Pro každou aplikaci potřebujete souběžnou verzi rozhraní .NET.

Pro serverovou aplikaci použijte .NET Framework v těchto případech:

- Vaše aplikace aktuálně používá .NET Framework (doporučení je místo migrace).
- Vaše aplikace používá knihovny .NET třetích stran nebo balíčky NuGet, které nejsou k dispozici pro .NET Core.
- Vaše aplikace používá technologie .NET, které nejsou k dispozici pro .NET Core.
- Vaše aplikace používá platformu, která nepodporuje .NET Core. Rozhraní .NET Core podporují Windows, macOS a Linux.

## <a name="when-to-choose-net-core"></a>Kdy zvolit .NET Core

V následujících částech najdete podrobnější vysvětlení výše uvedených důvodů pro výběr .NET Core.

### <a name="cross-platform-needs"></a>Požadavky na různé platformy

Pokud vaše aplikace (Web/služba) potřebuje běžet na více platformách (Windows, Linux a macOS), použijte .NET Core.

.NET Core podporuje dříve zmíněné operační systémy jako pracovní stanici pro vývoj. Visual Studio poskytuje integrované vývojové prostředí (IDE) pro Windows a macOS. Můžete také použít Visual Studio Code, která běží na macOS, Linux a Windows. Visual Studio Code podporuje rozhraní .NET Core, včetně technologie IntelliSense a ladění. Většina editorů třetích stran, jako např. (Emacs), a VI, fungují s .NET Core. Tyto editory třetích stran získávají IntelliSense editoru pomocí [omnisharp](https://www.omnisharp.net/). Můžete také zabránit jakémukoli editoru kódu a přímo použít [.NET Core CLI](../core/tools/index.md), k dispozici pro všechny podporované platformy.

### <a name="microservices-architecture"></a>Architektura mikroslužeb

Architektura mikroslužeb umožňuje kombinovat technologie napříč hranicí služby. Tato kombinace technologie umožňuje postupný podíl rozhraní .NET Core pro nové mikroslužby, které pracují s dalšími mikroslužbami nebo službami. Můžete například kombinovat mikroslužby nebo služby vyvinuté pomocí .NET Framework, Java, Ruby nebo jiných technologií monolitické.

K dispozici je mnoho platforem infrastruktury. Služba [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) je navržená pro rozsáhlé a komplexní systémy mikroslužeb. [Azure App Service](https://azure.microsoft.com/services/app-service/) je dobrou volbou pro bezstavové mikroslužby. Alternativy mikroslužeb na základě Docker vyhovují jakémukoli druhu přístupu ke mikroslužbám, jak je vysvětleno v části [Containers (kontejnery](#containers) ). Všechny tyto platformy podporují .NET Core a jsou ideální pro hostování vašich mikroslužeb.

Další informace o architektuře mikroslužeb najdete v tématu [mikroslužby .NET. Architektura pro kontejnerové aplikace .NET](../architecture/microservices/index.md).

### <a name="containers"></a>Containers

Kontejnery se běžně používají ve spojení s architekturou mikroslužeb. Kontejnery lze také použít k kontejnerizaceí webových aplikací nebo služeb, které sledují model architektury. .NET Framework lze použít v kontejnerech Windows, ale modulární a odlehčená povaha .NET Core umožňuje lepší volbu kontejnerů. Při vytváření a nasazování kontejneru je velikost jeho image mnohem menší s .NET Core než s .NET Framework. Vzhledem k tomu, že se jedná o různé platformy, můžete nasadit serverové aplikace do kontejnerů Docker pro Linux, například.

Kontejnery Docker je možné hostovat ve vlastní infrastruktuře systému Linux nebo Windows nebo v cloudové službě, jako je například [Služba Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/). Služba Azure Kubernetes může spravovat, orchestrovat a škálovat aplikace založené na kontejnerech v cloudu.

### <a name="high-performance-and-scalable-systems"></a>Vysoce výkonné a škálovatelné systémy

V případě, že váš systém potřebuje nejlepší možný výkon a škálovatelnost, je nejlepší možností rozhraní .NET Core a ASP.NET Core. Vysoce výkonný modul runtime serveru pro Windows Server a Linux přináší .NET a nejvyšší výkonnou webovou architekturu na [TechEmpower srovnávacích testech](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

Výkon a škálovatelnost jsou obzvláště důležité pro architektury mikroslužeb, kde můžou běžet stovky mikroslužeb. V ASP.NET Core se systémy spouštějí s mnohem menším počtem serverů/Virtual Machines (VM). Omezené servery a virtuální počítače šetří náklady v oblasti infrastruktury a hostování.

### <a name="side-by-side-net-versions-per-application-level"></a>Souběžné verze .NET na úrovni aplikace

Pro instalaci aplikací se závislostmi na různých verzích rozhraní .NET doporučujeme .NET Core. .NET Core podporuje souběžnou instalaci různých verzí modulu runtime .NET Core na stejném počítači. Tato Souběžná instalace umožňuje více služeb na stejném serveru, každý z nich na vlastní verzi .NET Core. Také snižuje rizika a šetří peníze v upgradech aplikací a IT operacích.

Souběžná instalace není u .NET Framework možná. Jedná se o součást systému Windows a v počítači v jednom okamžiku může existovat pouze jedna verze. Každá verze .NET Framework nahrazuje předchozí verzi. Pokud instalujete novou aplikaci, která cílí na novější verzi .NET Framework, můžete rušit existující aplikace, které běží na počítači, protože předchozí verze byla nahrazena.

## <a name="when-to-choose-net-framework"></a>Kdy zvolit .NET Framework

.NET Core nabízí významné výhody pro nové aplikace a vzory aplikací. .NET Framework však nadále přirozené možnosti pro mnoho stávajících scénářů a jako takový je .NET Framework nenahrazuje rozhraním .NET Core pro všechny serverové aplikace.

### <a name="current-net-framework-applications"></a>Aktuální aplikace .NET Framework

Ve většině případů nemusíte migrovat stávající aplikace do .NET Core. Místo toho doporučujeme použít .NET Core při rozšiřování existující aplikace, jako je například zápis nové webové služby v ASP.NET Core.

### <a name="aspnet-core-on-net-framework"></a>ASP.NET Core v .NET Framework

Informace o podpoře ASP.NET Core v .NET Framework najdete v tématu [zásady podpory .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

### <a name="third-party-libraries-or-nuget-packages-not-available-for-net-core"></a>Knihovny třetích stran nebo balíčky NuGet nejsou k dispozici pro .NET Core

Knihovny jsou rychle přechodu .NET Standard. .NET Standard umožňuje sdílení kódu napříč všemi implementacemi .NET, včetně .NET Core. S .NET Standard 2,0 je to ještě snazší:

- Plocha rozhraní API se stala mnohem větší.
- Představil .NET Framework režim kompatibility.

  Tento režim kompatibility umožňuje projektům .NET Standard a .NET Core odkazovat na .NET Framework knihovny. Další informace o režimu kompatibility naleznete v tématu [oznamujeme .NET Standard 2,0](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/).

Je nutné použít .NET Framework pouze v případě, že knihovny nebo balíčky NuGet využívají technologie, které nejsou k dispozici v .NET Standard nebo .NET Core.

### <a name="net-technologies-not-available-for-net-core"></a>Technologie .NET nejsou k dispozici pro .NET Core

Některé technologie .NET Framework nejsou dostupné v .NET Core. Některé z nich mohou být k dispozici v novějších verzích .NET Core. Ostatní se nevztahují na nové vzory aplikací, na které cílí .NET Core, a nemusí být nikdy k dispozici. V následujícím seznamu jsou uvedeny nejběžnější technologie, které se v .NET Core nenašly:

- ASP.NET webové formuláře aplikace: webové formuláře ASP.NET jsou k dispozici pouze v .NET Framework. ASP.NET Core nelze použít pro webové formuláře ASP.NET. Neexistují žádné plány k převedení ASP.NET webových formulářů do .NET Core.

- ASP.NET webové stránky aplikace: webové stránky ASP.NET nejsou zahrnuté do ASP.NET Core.

- Implementace služeb WCF. I v případě, že existuje [Knihovna klienta WCF](https://github.com/dotnet/wcf) pro využívání služeb WCF z .NET Core, implementace WCF serveru je aktuálně dostupná jenom v .NET Framework. Tento scénář není součástí aktuálního plánu pro .NET Core, ale je považován za budoucí.

- Služby související s pracovním postupem: programovací model Windows Workflow Foundation (WF), služby pracovních postupů (WCF + WF v jedné službě) a WCF Data Services (dříve označované jako "ADO.NET Data Services") jsou k dispozici pouze v .NET Framework. Nejsou k dispozici žádné plány pro uvedení těchto technologií do .NET Core.

- Podpora jazyků: Visual Basic a F # se aktuálně podporují v .NET Core, ale ne pro všechny typy projektů. Seznam podporovaných šablon projektů naleznete v tématu [Možnosti šablony pro dotnet New](../core/tools/dotnet-new.md#arguments).

### <a name="platform-doesnt-support-net-core"></a>Platforma nepodporuje .NET Core.

Některé platformy společnosti Microsoft nebo třetích stran nepodporují .NET Core. Některé služby Azure poskytují sadu SDK, která ještě není dostupná pro využití v .NET Core. Jedná se o přechodnou okolnost, protože všechny služby Azure využívají .NET Core. Do té doby můžete místo klientské sady SDK použít ekvivalentní REST API.

## <a name="see-also"></a>Viz také

- [Volba mezi ASP.NET a ASP.NET Core](/aspnet/core/choose-aspnet-framework)
- [Cílení ASP.NET Core na .NET Framework](/aspnet/core/introduction-to-aspnet-core#aspnet-core-targeting-net-framework)
- [Cílové architektury](frameworks.md)
- [Průvodce .NET Core](../core/index.yml)
- [Přenos z .NET Framework do .NET Core](../core/porting/index.md)
- [Úvod k .NET a Dockeru](../core/docker/introduction.md)
- [Přehled komponent .NET](components.md)
- [Mikroslužby .NET. Architektura pro kontejnerové aplikace .NET](../architecture/microservices/index.md)
