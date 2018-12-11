---
title: Kdy pro kontejnery Dockeru zvolit .NET Core
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Kdy pro kontejnery Dockeru zvolit .NET Core
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: b283916d6ae4d19fdc6a4f7976a3adbb66d26b2c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143400"
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Kdy pro kontejnery Dockeru zvolit .NET Core

Modulární struktura a zjednodušené povahu .NET Core je ideální pro kontejnery. Při nasazení a spuštění kontejneru, je mnohem menší s .NET Core s rozhraním .NET Framework než jeho image. Naproti tomu musí používat rozhraní .NET Framework pro kontejner, základní bitové kopie v imagi Windows Server Core, což je mnohem větším než Windows Nano Server nebo Linuxových imagí, které používáte pro .NET Core.

Kromě toho .NET Core je multiplatformní, abyste mohli nasadit aplikace serveru s Linuxem nebo Windows Image kontejneru. Nicméně pokud používáte tradiční rozhraní .NET Framework, můžete nasadit jenom imagí založených na jádru Windows serveru.

Tady je podrobnější vysvětlení, proč zvolit .NET Core.

## <a name="developing-and-deploying-cross-platform"></a>Vývoj a nasazení pro různé platformy

Je zřejmé Pokud je vaším cílem je, aby aplikace (webová aplikace nebo služby), který může spouštět na více platformách podporovaných aplikací Dockeru (Linux a Windows), tou správnou volbou je .NET Core, protože rozhraní .NET Framework podporuje pouze Windows.

.NET core podporuje také macOS jako vývojářskou platformu. Ale při nasazování kontejnerů do hostitele Docker, které jsou hostiteli musí (aktuálně) zakládat na Linuxu nebo Windows. Například ve vývojovém prostředí, můžete použít virtuální počítač s Linuxem spouštění v počítačích Mac.

[Visual Studio](https://www.visualstudio.com/vs/) poskytuje integrované vývojové prostředí (IDE) pro Windows, která podporuje vývoj Dockeru.

[Visual Studio pro Mac](https://www.visualstudio.com/vs/visual-studio-mac/) je integrované vývojové prostředí, vývoj Xamarin Studio, který běží v systému macOS a podporuje vývoj aplikací založených na Dockeru. To by měl být upřednostňovanou volbu pro vývojáře pracující na počítačích Mac, které také chtějí využívat výkonné integrované vývojové prostředí.

Můžete také použít [Visual Studio Code](https://code.visualstudio.com/) (VS Code) v systémech macOS, Linux a Windows. VS Code plně podporuje .NET Core, včetně technologie IntelliSense a ladění. Vzhledem k tomu, že VS Code je jednoduchý editor, je můžete použít pro vývoj kontejnerizovaných aplikací v počítačích Mac ve spojení s rozhraní příkazového řádku Dockeru a [rozhraní příkazového řádku .NET Core (CLI)](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x). .NET Core můžete také směrovat pomocí editorů nejvíce třetích stran, jako je Sublime (emacs), vi a OmniSharp projekt open source, který také poskytuje podporu technologie IntelliSense.

Kromě Integrovaná vývojová prostředí a editory, můžete použít [rozhraní příkazového řádku .NET Core](https://docs.microsoft.com/dotnet/core/tools/?tabs=netcore2x) nástroje pro všechny podporované platformy.

## <a name="using-containers-for-new-green-field-projects"></a>Pomocí kontejnerů pro nové projekty ("zelená pole")

Kontejnery se běžně používají ve spojení s architekturu mikroslužeb, ačkoli může být také použit kontejnerizaci webových aplikací a služeb, které následují žádné z možných architektonických. Můžete použít rozhraní .NET Framework v kontejnerech Windows, ale modularitu a zjednodušené povaze .NET Core je ideální pro architektur mikroslužeb a kontejnerů. Když vytvoříte a nasadíte kontejner, je mnohem menší s .NET Core s rozhraním .NET Framework než jeho image.

## <a name="creating-and-deploying-microservices-on-containers"></a>Vytváření a nasazování mikroslužeb pro kontejnery

Můžete použít tradiční rozhraní .NET Framework pro vytváření aplikací založených na mikroslužbách (bez kontejnery) s použitím jednoduché procesy. Tímto způsobem, protože rozhraní .NET Framework je již nainstalována a sdílet mezi procesy, procesy jsou světla a rychlé spuštění. Pokud používáte kontejnery, image pro tradiční rozhraní .NET Framework je taky založený na systému Windows Server Core a díky tomu se příliš těžká pro přístup založený na mikroslužbách v kontejnerech.

Naproti tomu .NET Core je nejlepší Release candidate, je-li využívají systém orientované na mikroslužby založenou na kontejnerech, protože .NET Core je jednoduché. Související kontejner Image, image Linuxu nebo image Windows Nano, jsou navíc Štíhlá a malé, provádění světla kontejnery a rychlý start.

Mikroslužba je určena být co nejmenší: při roztáčení být světlo, mají malé náklady, aby malé ohraničená kontextu (DDD, zkontrolujte [Domain-Driven Design](https://en.wikipedia.org/wiki/Domain-driven_design)), představují malé oblast zájmu a bude možné spustit a rychle zastavit. Pro požadavky můžete použít Image malé a rychle instance kontejnerů jako image kontejneru .NET Core.

Architektura mikroslužeb umožňuje kombinovat technologie přes hranice služeb. To umožňuje postupné migraci až po .NET Core pro nové mikroslužby, které pracují ve spojení s další mikroslužby nebo službami využily výsledky mnohaletých Node.js, Python, Java, go nebo jiné technologie.

## <a name="deploying-high-density-in-scalable-systems"></a>Nasazení s vysokou hustotou v škálovatelné systémy

Pokud váš systém založených na kontejnerech potřebuje nejlepší možné hustota, členitosti a výkonu, .NET Core a ASP.NET Core jsou nejlepší možností. ASP.NET Core je až 10 x rychlejší než technologie ASP.NET v tradiční rozhraní .NET Framework a vede další oblíbené oborovými technologiemi pro mikroslužby, jako jsou Java servletů, Go a Node.js.

To je obzvláště důležité pro architekturu mikroslužeb, ve které jste mohli stovky mikroslužby (kontejnerů) spuštěná. S ASP.NET Core Image (na platformě .NET Core runtime) v systému Linux nebo Windows Nano můžete spustit váš systém s mnohem menším počtem serverů nebo virtuálních počítačů, takže v konečném důsledku ušetří náklady v infrastruktuře a hostování.

>[!div class="step-by-step"]
>[Předchozí](general-guidance.md)
>[další](net-framework-container-scenarios.md)