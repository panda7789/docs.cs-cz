---
title: Kdy pro kontejnery Dockeru zvolit .NET Core
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Kdy zvolit .NET Core pro kontejnery Docker
ms.date: 09/11/2018
ms.openlocfilehash: 54ed1b4bbb16352b8c99204383f85ffb25d62be7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296500"
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Kdy pro kontejnery Dockeru zvolit .NET Core

Modularita a zjednodušená povaha .NET Core usnadňuje kontejnery. Při nasazení a spuštění kontejneru je jeho obrázek mnohem menší s rozhraním .NET Core než s .NET Framework. Naproti tomu, pokud chcete použít .NET Framework pro kontejner, musíte image založit na základní imagi Windows serveru, což je hodně těžší než image Windows nano serveru nebo Linux, které používáte pro .NET Core.

.NET Core je navíc pro různé platformy, takže můžete nasazovat serverové aplikace s imagemi kontejnerů pro Linux nebo Windows. Pokud ale používáte tradiční .NET Framework, můžete nasadit jenom image založené na jádru Windows serveru.

Následuje podrobnější vysvětlení, proč zvolit .NET Core.

## <a name="developing-and-deploying-cross-platform"></a>Vývoj a nasazení pro různé platformy

Jasně platí, že pokud je vaším cílem aplikace (webová aplikace nebo služba), která může běžet na různých platformách, které podporuje Docker (Linux a Windows), je správná volba rozhraní .NET Core, protože .NET Framework podporuje jenom Windows.

.NET Core také podporuje macOS jako vývojovou platformu. Pokud však nasazujete kontejnery na hostitele Docker, musí být tento hostitel (aktuálně) založen na systému Linux nebo Windows. Ve vývojovém prostředí můžete například použít virtuální počítač Linux, který běží na Macu.

[Visual Studio](https://www.visualstudio.com/vs/) poskytuje integrované vývojové prostředí (IDE) pro Windows a podporuje vývoj v Docker.

[Visual Studio pro Mac](https://www.visualstudio.com/vs/visual-studio-mac/) je rozhraní IDE, vývoj Xamarin Studio, který běží na MacOS a podporuje vývoj aplikací na bázi Docker. To by mělo být Upřednostňovaná volba pro vývojáře pracující v počítačích Mac, kteří chtějí také používat výkonné integrované vývojové prostředí (IDE).

Můžete také použít [Visual Studio Code](https://code.visualstudio.com/) (vs Code) v systémech MacOS, Linux a Windows. VS Code plně podporuje rozhraní .NET Core, včetně technologie IntelliSense a ladění. Vzhledem k tomu, že VS Code je odlehčený editor, můžete ho použít k vývoji kontejnerových aplikací na Macu ve spojení s [rozhraním příkazového řádku Docker CLI a .NET Core (CLI)](../../../core/tools/index.md). .NET Core můžete také cílit pomocí většiny editorů třetích stran, jako je například (Emacs), VI a open-source projekt OmniSharp, který také poskytuje podporu technologie IntelliSense.

Kromě platforem a editorů můžete použít nástroje [.NET Core CLI](../../../core/tools/index.md) pro všechny podporované platformy.

## <a name="using-containers-for-new-green-field-projects"></a>Použití kontejnerů pro nové projekty ("zelená pole")

Kontejnery se běžně používají ve spojení s architekturou mikroslužeb, i když je lze použít také k kontejnerizaceí webových aplikací nebo služeb, které následují podle modelu architektury. Můžete použít .NET Framework v kontejnerech Windows, ale modularita a zjednodušená povaha .NET Core je ideální pro kontejnery a architektury mikroslužeb. Při vytváření a nasazování kontejneru je jeho obrázek mnohem menší s .NET Core než s .NET Framework.

## <a name="creating-and-deploying-microservices-on-containers"></a>Vytváření a nasazování mikroslužeb na kontejnery

Pomocí jednoduchých procesů můžete použít tradiční .NET Framework pro vytváření aplikací založených na mikroslužbách (bez kontejnerů). Proto protože .NET Framework je už nainstalovaná a sdílená napříč procesy, procesy jsou lehké a rychlé, aby se spouštěly. Pokud však používáte kontejnery, je obrázek pro tradiční .NET Framework také založen na systému Windows Server Core a je příliš velký pro přístup k mikroslužbám v rámci kontejnerů.

Naproti tomu je .NET Core nejlepší kandidát, pokud jste přechodu systém orientovaný na mikroslužby, který je založený na kontejnerech, protože .NET Core je odlehčené. Spolu se souvisejícími imagemi kontejnerů, jako je Linux nebo image Windows nano, jsou navíc štíhlé a malé vytváření kontejnerů a jejich rychlé spuštění.

Mikroslužba má být co nejnižší, což je co nejmenší: Pokud chcete mít v provozu malý prostor s malým přístavem, můžete mít malý ohraničený kontext (kontrolu DDD, [návrh založený na doméně](https://en.wikipedia.org/wiki/Domain-driven_design)), který představuje malou oblast obav a který je možné rychle spustit a zastavit. Pro tyto požadavky budete chtít použít malé a rychlé vytváření instancí imagí kontejneru, jako je například Image kontejneru .NET Core.

Architektura mikroslužeb také umožňuje kombinovat technologie napříč hranicí služby. To umožňuje postupný přechod na .NET Core pro nové mikroslužby, které fungují společně s dalšími mikroslužbami nebo službami vyvinutými pomocí Node. js, Pythonu, Java, GoLang nebo jiných technologií.

## <a name="deploying-high-density-in-scalable-systems"></a>Nasazení vysoké hustoty v škálovatelných systémech

Když váš systém založený na kontejneru potřebuje nejlepší možnou hustotu, členitost a výkon, .NET Core a ASP.NET Core jsou nejlepší možnosti. ASP.NET Core je až desetkrát rychlejší než ASP.NET v tradičním .NET Framework a má za následek jiné oblíbené oborové technologie pro mikroslužby, jako je Java servletů, přejít a Node. js.

To je obzvláště důležité pro architektury mikroslužeb, kde můžete mít spuštěné stovky mikroslužeb (kontejnerů). Díky ASP.NET Core imagí (na základě modulu runtime .NET Core) v systému Linux nebo Windows nano můžete spustit systém s mnohem menším počtem serverů nebo virtuálních počítačů, čímž ušetříte náklady na infrastrukturu a hostování.

>[!div class="step-by-step"]
>[Předchozí](general-guidance.md)Další
>[](net-framework-container-scenarios.md)
