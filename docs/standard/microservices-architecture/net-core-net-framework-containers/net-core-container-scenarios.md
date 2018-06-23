---
title: Kdy zvolte .NET Core Docker kontejnerů
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Kdy zvolte .NET Core Docker kontejnerů
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 45917a9dbfbd6610c3cca9ab7dcf9f924c329c10
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314923"
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Kdy zvolte .NET Core Docker kontejnerů

Modularitu a lightweight povaha .NET Core je ideální pro kontejnery. Při nasazení a spusťte kontejner, jeho image je mnohem menší s .NET Core než v rozhraní .NET Framework. Naproti tomu musí používat rozhraní .NET Framework pro kontejner, základní bitové kopie na bitovou kopii systému Windows Server Core, což je mnohem větší než Nano Server systému Windows nebo Linux bitové kopie, které používáte pro .NET Core.

Kromě toho .NET Core je a platformy, takže můžete nasadit aplikace na serveru s obrázky kontejneru Linux nebo Windows. Ale pokud používáte tradiční rozhraní .NET Framework, můžete nasadit jenom Image založené na Windows Server Core.

Následuje podrobnější vysvětlení důvod, proč zvolit .NET Core.

## <a name="developing-and-deploying-cross-platform"></a>Vývoj a nasazení pro různé platformy

Je zřejmé Pokud vaším cílem je, aby aplikace (webové aplikace nebo služby), která můžete spustit na několika platformách podporovaných aplikací Docker (Linux a Windows), správná volba je .NET Core, protože rozhraní .NET Framework podporuje pouze systému Windows.

.NET core také podporuje systému macOS jako vývojové platformy. Ale když nasadíte kontejnery Docker hostitele, které jsou hostiteli musí (aktuálně) být založená na Linux nebo Windows. Například ve vývojovém prostředí, můžete použít virtuální počítač s Linuxem spuštěna v počítačích Mac.

[Visual Studio](https://visualstudio.microsoft.com/) poskytuje integrované vývojové prostředí (IDE) pro Windows která podporuje vývoj Docker. 

[Visual Studio pro Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/) IDE, vývoje Xamarin Studio, spuštěné v systému macOS a podporuje Docker od mid 2017.

Můžete také použít [Visual Studio Code](https://code.visualstudio.com/) (VS Code) v systému macOS, Linux a Windows. VS Code plně podporuje .NET Core, včetně technologie IntelliSense a ladění. Protože VS Code je lightweight editor, můžete ho vyvíjet kontejnerizované aplikace v systému Mac ve spojení s rozhraní příkazového řádku Dockeru a [nástrojů rozhraní příkazového řádku (CLI) .NET Core](../../../core/tools/index.md). S editory většina jiných výrobců jako Sublime Text, Emacs, vi a open-source OmniSharp projekt, který poskytuje podporu technologie IntelliSense pro jazyky rozhraní .NET, můžete také vybrat .NET Core. Kromě integrovaného vývojového prostředí a editory můžete použít rozhraní příkazového řádku .NET Core pro všechny podporované platformy.

## <a name="using-containers-for-new-green-field-projects"></a>Použití kontejnerů pro nové projekty ("zelená pole")

Kontejnery běžně se používají ve spojení s mikroslužeb architekturu, i když může být rovněž používají pro containerize webové aplikace nebo služby, které následují žádné architekturní vzor. Můžete použít rozhraní .NET Framework na Windows kontejnery, ale modularitu a lightweight povaha .NET Core je ideální pro kontejnery a mikroslužeb architektury. Když vytvoříte a nasadíte kontejner, jeho image je mnohem menší s .NET Core než v rozhraní .NET Framework.

## <a name="creating-and-deploying-microservices-on-containers"></a>Vytvoření a nasazení mikroslužeb kontejnerům

Můžete použít tradiční rozhraní .NET Framework pro vytváření aplikací na základě mikroslužeb (bez kontejnery) pomocí prostý procesů. Tímto způsobem, protože rozhraní .NET Framework je již nainstalován a sdílet mezi procesy, procesy se lehký a rychlé spuštění. Pokud používáte kontejnery, bitovou kopii pro tradiční rozhraní .NET Framework je také založena na jádru serveru Windows a který zpřístupňuje příliš velkou způsob mikroslužeb na kontejnery.

.NET Core spočívá v tom, nejlepší candidate Pokud mikroslužeb zaměřené na konkrétní systém, který je založen na kontejnery, jsou osvojují, protože je lightweight .NET Core. Kromě toho související kontejneru Image, Linux image nebo bitovou kopii systému Windows Nano, jsou Štíhlá a malé provedení light kontejnery a rychlý start.

Mikroslužbu měl by být co nejmenší: být light při otáčí nahoru, tak, aby měl malé nároky, tak, aby měl malé ohraničenou kontextu, představují malé části otázky a abyste mohli spustit a zastavit rychlé. Tyto požadavky můžete použít Image malé a fast doložit kontejneru jako obrázek kontejneru .NET Core.

Architektura mikroslužeb můžete také kombinovat technologie přes hranice služby. To umožňuje postupné migrace pro nové mikroslužeb, které pracují ve spojení s další mikroslužeb nebo službou vyvinuté pomocí Node.js, Python, Java, GoLang ani jiné technologie .NET Core.

## <a name="deploying-high-density-in-scalable-systems"></a>Nasazení s vysokou hustotou v škálovatelné systémy

Když se na základě kontejneru systému potřebuje nejlepší možný hustotu, členitosti a výkonu, .NET Core a ASP.NET Core jsou nejlepší možnosti. ASP.NET Core je až 10 x rychlejší než ASP.NET v tradiční rozhraní .NET Framework a jeho vede dalších oblíbených oborovými technologiemi pro mikroslužeb, například servlets Java, přejděte a Node.js.

To je obzvláště důležité pro mikroslužeb architektury, kde můžete mít stovky mikroslužeb (kontejnerů) spuštěna. Pomocí ASP.NET Core bitových kopií (podle na .NET Core runtime) v systému Linux nebo Windows Nano můžete spustit systém s mnohem nižší číslo serverů nebo virtuální počítače, nakonec ukládání náklady na infrastrukturu a hostování.


>[!div class="step-by-step"]
[Předchozí] (guidance.md obecné) [Další] (net-framework kontejneru scenarios.md)
