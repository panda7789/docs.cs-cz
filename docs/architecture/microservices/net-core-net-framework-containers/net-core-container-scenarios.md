---
title: Kdy pro kontejnery Dockeru zvolit .NET Core
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Kdy zvolit .NET Core pro kontejnery Dockeru
ms.date: 01/30/2020
ms.openlocfilehash: f784512af3f520f96d499ab002eda58071b3c284
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147372"
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Kdy pro kontejnery Dockeru zvolit .NET Core

Díky modularitě a lehké povaze .NET Core je ideální pro kontejnery. Při nasazení a spuštění kontejneru je jeho image mnohem menší s rozhraním .NET Core než s rozhraním .NET Framework. Chcete-li naopak použít rozhraní .NET Framework pro kontejner, musíte svou bitovou kopii založit na bitové kopii Windows Server Core, která je mnohem těžší než bitové kopie Windows Nano Server nebo Linux, které používáte pro rozhraní .NET Core.

Kromě toho .NET Core je multiplatformní, takže můžete nasadit serverové aplikace s linuxovými nebo windows kontejnerovými iimage. Pokud však používáte tradiční rozhraní .NET Framework, můžete nasadit pouze bitové kopie založené na jádru systému Windows Server Core.

Následuje podrobnější vysvětlení, proč zvolit .NET Core.

## <a name="developing-and-deploying-cross-platform"></a>Vývoj a nasazení napříč platformami

Je zřejmé, že pokud je vaším cílem mít aplikaci (webovou aplikaci nebo službu), která může běžet na více platformách podporovaných Dockerem (Linux a Windows), správná volba je .NET Core, protože rozhraní .NET Framework podporuje pouze windows.

.NET Core také podporuje macOS jako vývojovou platformu. Však při nasazení kontejnerů do hostitele Dockeru, že hostitel musí (v současné době) být založen na Linuxu nebo Windows. Například ve vývojovém prostředí můžete použít virtuální počítač s Linuxem spuštěný na Macu.

[Visual Studio](https://www.visualstudio.com/vs/) poskytuje integrované vývojové prostředí (IDE) pro Windows a podporuje vývoj Dockeru.

[Visual Studio pro Mac](https://www.visualstudio.com/vs/visual-studio-mac/) je IDE, vývoj Xamarin Studio, který běží na macOS a podporuje vývoj aplikací založených na Dockeru. To by mělo být preferovanou volbou pro vývojáře pracující v počítačích Mac, kteří také chtějí používat výkonné ide.

Kód Visual [Studia](https://code.visualstudio.com/) můžete taky použít v systémech macOS, Linux a Windows. Visual Studio Code plně podporuje .NET Core, včetně IntelliSense a ladění. Vzhledem k tomu, že VS Code je zjednodušený editor, můžete ho použít k vývoji kontejnerizovaných aplikací na Macu ve spojení s rozhraním se křovisovou střižovou a [.NET Core CLI](../../../core/tools/index.md). Můžete také cílit na .NET Core s většinou editorů třetích stran, jako je Sublime, Emacs, vi a open source omnisharp projektu, který také poskytuje podporu IntelliSense.

Kromě INEŽ a editory, můžete použít [.NET Core CLI](../../../core/tools/index.md) pro všechny podporované platformy.

## <a name="using-containers-for-new-green-field-projects"></a>Použití kontejnerů pro nové projekty ("zelená pole")

Kontejnery se běžně používají ve spojení s architekturou mikroslužeb, i když je lze také použít ke kontejnerizaci webových aplikací nebo služeb, které se řídí libovolným architektonickým vzorem. Rozhraní .NET Framework můžete použít v kontejnerech Windows, ale modularita a zjednodušená povaha .NET Core je ideální pro architektury kontejnerů a mikroslužeb. Když vytvoříte a nasadíte kontejner, jeho image je mnohem menší s .NET Core než s rozhraním .NET Framework.

## <a name="create-and-deploy-microservices-on-containers"></a>Vytváření a nasazování mikroslužeb v kontejnerech

Tradiční rozhraní .NET Framework můžete použít pro vytváření aplikací založených na mikroslužbách (bez kontejnerů) pomocí prostých procesů. Tímto způsobem, protože rozhraní .NET Framework je již nainstalován a sdílenmezi procesy, procesy jsou lehké a rychlé spuštění. Pokud však používáte kontejnery, bitová kopie pro tradiční rozhraní .NET Framework je také založena na jádru systému Windows Server Core a je příliš těžká pro přístup mikroslužeb na kontejnerech. Týmy však hledají příležitosti ke zlepšení prostředí pro uživatele rozhraní .NET Framework. V poslední době byla velikost [iložek kontejneru Jádra systému Windows Server snížena na >o 40 % menší](https://devblogs.microsoft.com/dotnet/we-made-windows-server-core-container-images-40-smaller).

Na druhou stranu .NET Core je nejlepší kandidát, pokud jste zahrnující mikroslužeb orientovaný systém, který je založen na kontejnerech, protože .NET Core je lehký. Kromě toho, jeho související kontejner obrázky, pro Linux nebo Windows Nano Server, jsou štíhlé a malé, takže kontejnery lehké a rychlé spuštění.

Mikroslužba má být co nejmenší: být lehká při otáčení, mít malé rozměry, mít malý ohraničený kontext (kontrola DDD, [Návrh řízený doménou),](https://en.wikipedia.org/wiki/Domain-driven_design)která představuje malou oblast problémů a bude možné rychle spustit a zastavit. Pro tyto požadavky budete chtít použít malé a rychlé konkretizovat image kontejneru, jako je bitová kopie kontejneru .NET Core.

Architektura mikroslužeb také umožňuje kombinovat technologie přes hranice služby. To umožňuje postupnou migraci do .NET Core pro nové mikroslužby, které pracují ve spojení s jinými mikroslužbami nebo se službami vyvinutými pomocí Node.js, Pythonu, Javy, GoLangu nebo jiných technologií.

## <a name="deploying-high-density-in-scalable-systems"></a>Nasazení vysoké hustoty ve škálovatelných systémech

Když váš systém založený na kontejneru potřebuje nejlepší možnou hustotu, rozlišovací schopnost a výkon, jsou nejlepší mise .NET Core a ASP.NET Core. ASP.NET Core je až desetkrát rychlejší než ASP.NET v tradiční rozhraní .NET Framework a vede další populární oborové technologie pro mikroslužby, jako jsou servlety Java, Go a Node.js.

To je zvláště důležité pro architektury mikroslužeb, kde můžete mít stovky mikroslužeb (kontejnery) spuštěna. Díky ASP.NET image Core (založené na běhu .NET Core) na Linuxu nebo Windows Nano, můžete spustit systém s mnohem nižším počtem serverů nebo virtuálních počítačích, což nakonec ušetří náklady na infrastrukturu a hostování.

>[!div class="step-by-step"]
>[Předchozí](general-guidance.md)
>[další](net-framework-container-scenarios.md)
