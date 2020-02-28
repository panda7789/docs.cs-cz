---
title: Volba mezi .NET Core a .NET Framework serverových aplikací
description: Průvodce implementací rozhraní .NET, který byste měli zvážit při vytváření serverové aplikace v .NET.
author: cartermp
ms.date: 06/19/2018
ms.openlocfilehash: 0b6bf4c2eb66aa4de497923a0a16b65a955ba6fc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159972"
---
# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>Volba mezi .NET Core a .NET Framework pro serverové aplikace

Existují dvě podporované implementace pro vytváření aplikací na straně serveru pomocí .NET: .NET Framework a .NET Core. Oba sdílejí mnoho stejných komponent a můžete sdílet kód mezi dvěma. Existují však zásadní rozdíly mezi těmito dvěma a volbami, záleží na tom, co chcete provést.  Tento článek poskytuje pokyny k použití jednotlivých.

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

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Potřeba vysoce výkonné a škálovatelné systémy

V případě, že váš systém potřebuje nejlepší možný výkon a škálovatelnost, je nejlepší možností rozhraní .NET Core a ASP.NET Core. Vysoce výkonný modul runtime serveru pro Windows Server a Linux přináší .NET a nejvyšší výkonnou webovou architekturu na [TechEmpower srovnávacích testech](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

Výkon a škálovatelnost jsou obzvláště důležité pro architektury mikroslužeb, kde můžou běžet stovky mikroslužeb. V ASP.NET Core se systémy spouštějí s mnohem menším počtem serverů/Virtual Machines (VM). Omezené servery a virtuální počítače šetří náklady v oblasti infrastruktury a hostování.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Potřeba souběžně s verzemi .NET na úrovni aplikace

Pro instalaci aplikací se závislostmi na různých verzích rozhraní .NET doporučujeme .NET Core. .NET Core nabízí souběžnou instalaci různých verzí modulu runtime .NET Core na stejném počítači. Tato Souběžná instalace umožňuje více služeb na stejném serveru, každý z nich na vlastní verzi .NET Core. Také snižuje rizika a šetří peníze v upgradech aplikací a IT operacích.

## <a name="when-to-choose-net-framework"></a>Kdy zvolit .NET Framework

.NET Core nabízí významné výhody pro nové aplikace a vzory aplikací. .NET Framework však nadále je přirozenou volbou pro mnoho stávajících scénářů a protože .NET Framework není nahrazeno rozhraním .NET Core pro všechny serverové aplikace.

### <a name="current-net-framework-applications"></a>Aktuální aplikace .NET Framework

Ve většině případů nemusíte migrovat stávající aplikace do .NET Core. Místo toho doporučujeme použít .NET Core při rozšiřování existující aplikace, jako je například zápis nové webové služby v ASP.NET Core.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Pro .NET Core je potřeba použít knihovny .NET nebo balíčky NuGet třetích stran, které nejsou k dispozici.

Knihovny jsou rychle přechodu .NET Standard. .NET Standard umožňuje sdílení kódu napříč všemi implementacemi .NET, včetně .NET Core. S .NET Standard 2,0 je to ještě snazší:

- Plocha rozhraní API se stala mnohem větší.
- Byl zaveden režim kompatibility .NET Framework. Tento režim kompatibility umožňuje projektům .NET Standard/. NET Core odkazovat na .NET Framework knihovny. Další informace o režimu kompatibility naleznete v tématu [oznamujeme .NET Standard 2,0](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/).

Takže v případě, že knihovny nebo balíčky NuGet využívají technologie, které nejsou dostupné v .NET Standard/. NET Core, je nutné použít .NET Framework.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>Potřeba používat technologie .NET, které nejsou k dispozici pro .NET Core

Některé technologie .NET Framework nejsou dostupné v .NET Core. Některé z nich mohou být k dispozici v novějších verzích .NET Core. Ostatní se nevztahují na nové vzory aplikací, na které cílí .NET Core, a nemusí být nikdy k dispozici. V následujícím seznamu jsou uvedeny nejběžnější technologie, které se v .NET Core nenašly:

- ASP.NET webové formuláře aplikace: webové formuláře ASP.NET jsou k dispozici pouze v .NET Framework. ASP.NET Core nelze použít pro webové formuláře ASP.NET. Neexistují žádné plány k převedení ASP.NET webových formulářů do .NET Core.

- ASP.NET webové stránky aplikace: webové stránky ASP.NET nejsou zahrnuté do ASP.NET Core.

- Implementace služeb WCF. I když existuje [Knihovna WCF-Client](https://github.com/dotnet/wcf) ke využívání služeb WCF z .NET Core, implementace serveru WCF je aktuálně dostupná jenom v .NET Framework. Tento scénář není součástí aktuálního plánu pro .NET Core, ale je považován za budoucí.

- Služby související s pracovním postupem: programovací model Windows Workflow Foundation (WF), služby pracovních postupů (WCF + WF v jedné službě) a WCF Data Services (dříve označované jako "ADO.NET Data Services") jsou k dispozici pouze v .NET Framework.  Neexistují žádné plány, jak přenést WF/WCF + WF/WCF Data Services do .NET Core.

- Podpora jazyků: Visual Basic a F# jsou aktuálně podporované v rozhraní .NET Core, ale ne pro všechny typy projektů. Seznam podporovaných šablon projektů naleznete v tématu [Možnosti šablony pro dotnet New](../core/tools/dotnet-new.md#arguments).

Kromě oficiálního plánu jsou k dispozici i další rozhraní .NET Core. Úplný seznam najdete v tématu CoreFX problémy označené jako [port-to-Core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core). Tento seznam nepředstavuje závazek společnosti Microsoft, aby tyto komponenty byly součástí .NET Core. Jednoduše zachytíte přáním z komunity. Pokud se rozhodnete o kterékoli součásti označené jako `port-to-core`, účastníte se diskusí na GitHubu. A pokud si myslíte, že chybí něco, zapište nový problém do [úložiště .NET](https://github.com/dotnet/runtime/issues/new).

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>Je potřeba použít platformu, která nepodporuje .NET Core.

Některé platformy společnosti Microsoft nebo třetích stran nepodporují .NET Core. Některé služby Azure poskytují sadu SDK, která ještě není dostupná pro využití v .NET Core. Jedná se o přechodnou okolnost, protože všechny služby Azure využívají .NET Core. Do té doby můžete místo sady SDK klienta vždy použít ekvivalentní REST API.

## <a name="see-also"></a>Viz také

- [Volba mezi ASP.NET a ASP.NET Core](/aspnet/core/choose-aspnet-framework)
- [ASP.NET Core cílení na .NET Framework](/aspnet/core#aspnet-core-targeting-net-framework)
- [Cílové architektury](frameworks.md)
- [Průvodce platformou .NET Core](../core/index.md)
- [Přenos z .NET Framework do .NET Core](../core/porting/index.md)
- [Úvod k .NET a Dockeru](../core/docker/introduction.md)
- [Přehled komponent .NET](components.md)
- [Mikroslužby .NET. Architektura pro kontejnerové aplikace .NET](../architecture/microservices/index.md)
