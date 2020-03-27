---
title: Možnost volby mezi rozhraním .NET Core a rozhraním .NET Framework pro serverové aplikace
description: Průvodce, na které implementaci rozhraní .NET byste měli zvážit při vytváření serverové aplikace v rozhraní .NET.
author: cartermp
ms.date: 06/19/2018
ms.openlocfilehash: 393d6d89fb299e87edf55cf50991537e8afe9753
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344150"
---
# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>Volba mezi .NET Core a .NET Framework pro serverové aplikace

Existují dvě podporované implementace pro vytváření aplikací na straně serveru s rozhraním .NET: Rozhraní .NET Framework a .NET Core. Oba sdílejí mnoho stejných součástí a můžete sdílet kód mezi dvěma. Existují však zásadní rozdíly mezi těmito dvěma a vaše volba závisí na tom, co chcete dosáhnout.  Tento článek obsahuje pokyny k použití.

Jádro .NET pro serverovou aplikaci použijte v:

- Máte potřeby napříč platformami.
- Zaměřujete se na mikroslužby.
- Používáte kontejnery Dockeru.
- Potřebujete vysoce výkonné a škálovatelné systémy.
- Potřebujete souběžné verze rozhraní .NET pro aplikaci.

Rozhraní .NET Framework použijte pro serverovou aplikaci, pokud:

- Vaše aplikace aktuálně používá rozhraní .NET Framework (doporučení je rozšířit místo migrace).
- Vaše aplikace používá knihovny .NET třetích stran nebo balíčky NuGet, které nejsou k dispozici pro jádro .NET Core.
- Vaše aplikace používá technologie .NET, které nejsou k dispozici pro .NET Core.
- Vaše aplikace používá platformu, která nepodporuje .NET Core. Windows, macOS a Linux podporují .NET Core.

## <a name="when-to-choose-net-core"></a>Kdy zvolit .NET Core

V následujících částech je uvedeno podrobnější vysvětlení dříve uvedených důvodů pro vychystávání .NET Core.

### <a name="cross-platform-needs"></a>Potřeby napříč platformami

Pokud vaše aplikace (web/služba) potřebuje spustit na více platformách (Windows, Linux a macOS), použijte .NET Core.

.NET Core podporuje dříve uvedené operační systémy jako vývojovou pracovní stanici. Visual Studio poskytuje integrované vývojové prostředí (IDE) pro Windows a macOS. Můžete také použít Visual Studio Code, který běží na macOS, Linux a Windows. Visual Studio Code podporuje .NET Core, včetně IntelliSense a ladění. Většina editorů třetích stran, například Sublime, Emacs a VI, pracuje s rozhraním .NET Core. Tyto editory třetích stran získat editor IntelliSense pomocí [Omnisharp](https://www.omnisharp.net/). Můžete se také vyhnout libovolnému editoru kódu a přímo použít [rozhraní PŘÍKAZOVÉHO PŘÍKAZU .NET Core](../core/tools/index.md), které je k dispozici pro všechny podporované platformy.

### <a name="microservices-architecture"></a>Architektura mikroslužeb

Architektura mikroslužeb umožňuje kombinaci technologií přes hranice služby. Tato kombinace technologií umožňuje postupné přijetí .NET Core pro nové mikroslužby, které pracují s jinými mikroslužbami nebo službami. Můžete například kombinovat mikroslužby nebo služby vyvinuté pomocí rozhraní .NET Framework, Java, Ruby nebo jiných monolitických technologií.

K dispozici je mnoho infrastrukturních platforem. [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) je určen pro velké a složité mikroslužbové systémy. [Azure App Service](https://azure.microsoft.com/services/app-service/) je dobrou volbou pro mikroslužby bez stavů. Alternativy mikroslužeb založené na Dockeru odpovídají jakémukoli přístupu mikroslužeb, jak je vysvětleno v části [Kontejnery.](#containers) Všechny tyto platformy podporují .NET Core a učinit je ideální pro hostování mikroslužeb.

Další informace o architektuře mikroslužeb naleznete v tématu [.NET Microservices. Architektura pro kontejnerizované aplikace .NET](../architecture/microservices/index.md).

### <a name="containers"></a>Kontejnery

Kontejnery se běžně používají ve spojení s architekturou mikroslužeb. Kontejnery lze také kontejnerizovat webové aplikace nebo služby, které postupují podle jakéhokoli vzoru architektury. Rozhraní .NET Framework lze použít v kontejnerech systému Windows, ale modularita a zjednodušená povaha .NET Core je lepší volbou pro kontejnery. Při vytváření a nasazování kontejneru je velikost jeho image mnohem menší s rozhraním .NET Core než u rozhraní .NET Framework. Vzhledem k tomu, že je napříč platformami, můžete například nasadit serverové aplikace do kontejnerů Linux Dockeru.

Kontejnery Dockeru můžou být hostované ve vaší vlastní infrastruktuře Linuxu nebo Windows nebo v cloudové službě, jako je [služba Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/). Služba Azure Kubernetes service může spravovat, organizovat a škálovat aplikace založené na kontejnerech v cloudu.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Potřeba vysoce výkonných a škálovatelných systémů

Když váš systém potřebuje nejlepší možný výkon a škálovatelnost, jsou nejlepšími možnostmi .NET Core a ASP.NET Core. Vysoce výkonný server runtime pro Windows Server a Linux dělá z rozhraní .NET nejvýkonnější webový rámec pro [srovnávací testy TechEmpower](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

Výkon a škálovatelnost jsou důležité zejména pro architektury mikroslužeb, kde mohou být spuštěny stovky mikroslužeb. S ASP.NET Core, systémy běží s mnohem nižší počet serverů /virtuálních počítačů (VM). Snížené servery/virtuální virtuální zařízení šetří náklady na infrastrukturu a hostování.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Potřeba souběžných verzí rozhraní .NET na úroveň aplikace

Chcete-li nainstalovat aplikace se závislostmi na různých verzích rozhraní .NET, doporučujeme .NET Core. .NET Core nabízí souběžnou instalaci různých verzí runtime .NET Core na stejném počítači. Tato souběžná instalace umožňuje více služeb na stejném serveru, každá z nich na vlastní verzi rozhraní .NET Core. Také snižuje rizika a šetří peníze při upgradu aplikací a operacích IT.

## <a name="when-to-choose-net-framework"></a>Kdy zvolit rozhraní .NET Framework

.NET Core nabízí významné výhody pro nové aplikace a vzory aplikací. Rozhraní .NET Framework je však i nadále přirozenou volbou pro mnoho existujících scénářů a jako takové rozhraní .NET Framework není nahrazeno .NET Core pro všechny serverové aplikace.

### <a name="current-net-framework-applications"></a>Aktuální aplikace rozhraní .NET Framework

Ve většině případů není nutné migrovat existující aplikace do .NET Core. Místo toho je doporučeným přístupem použití .NET Core při rozšíření existující aplikace, jako je například zápis nové webové služby v ASP.NET Core.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Potřeba používat knihovny .NET jiných výrobců nebo balíčky NuGet, které nejsou k dispozici pro jádro .NET Core

Knihovny rychle přijímají standard .NET. Standard .NET standard umožňuje sdílení kódu ve všech implementacích rozhraní .NET včetně jádra .NET. S rozhraním .NET Standard 2.0 je to ještě jednodušší:

- Povrch rozhraní API se stal mnohem větší.
- Byl zaveden režim kompatibility rozhraní .NET Framework. Tento režim kompatibility umožňuje projektům .NET Standard/.NET Core odkazovat na knihovny rozhraní .NET Framework. Další informace o režimu kompatibility naleznete v [tématu Oznámení standardu .NET Standard 2.0](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/).

Takže pouze v případech, kdy knihovny nebo balíčky NuGet používají technologie, které nejsou k dispozici v rozhraní .NET Standard/.NET Core, je třeba použít rozhraní .NET Framework.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>Potřeba používat technologie .NET není k dispozici pro .NET Core

Některé technologie rozhraní .NET Framework nejsou v jádru .NET k dispozici. Některé z nich mohou být k dispozici v pozdějších verzích .NET Core. Jiné se nevztahují na nové vzory aplikací, na které cílí .NET Core, a nemusí být nikdy k dispozici. V následujícím seznamu jsou uvedeny nejběžnější technologie, které nebyly nalezeny v rozhraní .NET Core:

- ASP.NET webových formulářů: ASP.NET webové formuláře jsou k dispozici pouze v rozhraní .NET Framework. ASP.NET Core nelze použít pro ASP.NET webových formulářů. Neexistují žádné plány přenést ASP.NET webových formulářů do .NET Core.

- ASP.NET aplikace webových stránek: ASP.NET webové stránky nejsou součástí ASP.NET jádra.

- Implementace služeb WCF. I v případě, že je [knihovna WCF-Client](https://github.com/dotnet/wcf) využívat wcf služby z .NET Core, WCF server implementace je aktuálně k dispozici pouze v rozhraní .NET Framework. Tento scénář není součástí aktuálního plánu pro .NET Core, ale je zvažován pro budoucnost.

- Služby související s pracovními postupy: Windows Workflow Foundation (WF), Workflow Services (WCF + WF v jedné službě) a WCF Data Services (dříve označované jako "ADO.NET datové služby") jsou k dispozici pouze v rozhraní .NET Framework.  Neexistují žádné plány pro přenos datových služeb WF/WCF+WF/WCF do jádra .NET.

- Podpora jazyka: Visual Basic a F# jsou aktuálně podporovány v .NET Core, ale ne pro všechny typy projektů. Seznam podporovaných šablon projektů naleznete v [tématu Možnosti šablony pro dotnet new](../core/tools/dotnet-new.md#arguments).

Kromě oficiálního plánu existují další rámce, které mají být přeneseny na .NET Core. Úplný seznam naleznete v tématu CoreFX problémy označené jako [port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core). Tento seznam nepředstavuje závazek společnosti Microsoft přenést tyto součásti do .NET Core. Jsou to prostě zachytit touhu od komunity, aby tak učinily. Pokud vám záleží na některé z `port-to-core`komponent označených jako , zúčastněte se diskusí na GitHubu. A pokud si myslíte, že něco chybí, zasoubor nový problém v [úložišti .NET](https://github.com/dotnet/runtime/issues/new).

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>Potřeba používat platformu, která nepodporuje .NET Core

Některé platformy Microsoftu nebo třetích stran nepodporují .NET Core. Některé služby Azure poskytují sdk ještě není k dispozici pro spotřebu na .NET Core. Toto je přechodná okolnost, protože všechny služby Azure používají .NET Core. Do té doby můžete vždy použít ekvivalentní rozhraní REST API namísto klienta SDK.

## <a name="see-also"></a>Viz také

- [Vyberte si mezi ASP.NET a ASP.NET Core](/aspnet/core/choose-aspnet-framework)
- [Cílení ASP.NET Core na .NET Framework](/aspnet/core#aspnet-core-targeting-net-framework)
- [Cílové architektury](frameworks.md)
- [Základní příručka rozhraní .NET](../core/index.yml)
- [Přenesení z rozhraní .NET Framework do jádra rozhraní .NET](../core/porting/index.md)
- [Úvod k .NET a Dockeru](../core/docker/introduction.md)
- [Přehled součástí rozhraní .NET](components.md)
- [Mikroslužby .NET. Architektura pro kontejnerizované aplikace .NET](../architecture/microservices/index.md)
