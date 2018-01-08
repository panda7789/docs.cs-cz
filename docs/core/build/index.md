---
title: "Sestavení .NET Core ze zdroje."
description: "Naučte se vytvářet .NET Core a rozhraní příkazového řádku .NET Core ze zdrojového kódu."
keywords: "Zdroj rozhraní .NET, .NET core, sestavení"
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8b49079c-6ede-429a-92d7-ecd2fda1ab0e
ms.workload: dotnetcore
ms.openlocfilehash: 6aa5abd071355b1c1a367b35e9521e6b1af9c945
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="build-net-core-from-source"></a>Sestavení .NET Core ze zdroje.

Možnost pro sestavení .NET Core z jeho zdrojový kód je důležité několika způsoby: umožňuje jednodušší port .NET Core pro nové platformy, to umožňuje příspěvky a opravy produktu a umožňuje vytvoření vlastní verze rozhraní .NET.
Tento článek poskytuje pokyny pro vývojáře, kteří chtějí vytvořit a distribuovat jejich vlastní verze .NET Core.

## <a name="build-the-clr-from-source"></a>Sestavení CLR ze zdroje.

Zdrojový kód pro rozhraní .NET CoreCLR naleznete v [ `dotnet/coreclr` úložišti na Githubu](https://github.com/dotnet/coreclr/).

Sestavení aktuálně závisí na následující požadavky:
* [Git](https://git-scm.com/)
* [CMake](https://cmake.org/)
* [Python](https://www.python.org/)
* Kompilátor C++.

Po instalaci tyto součásti jsou nainstalovány, můžete vytvořit modulu CLR vyvoláním skriptu buildu (`build.cmd` v systému Windows, nebo `build.sh` na Linuxu a systému macOS) na bázi [úložiště CoreCLR](https://github.com/dotnet/coreclr/).

Instalaci součástí lišit v závislosti na operační systém (OS). Přečtěte si pokyny sestavení pro konkrétní operačním systému:

 * [Windows](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
 * [Linux](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
 * [systému macOS](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
 * [FreeBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md) 
 * [NetBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

Neexistuje žádné sestavení mezi napříč operačního systému (pouze pro ARM, který je založený na X64).  
Musíte být na konkrétní platformu, která sestavení této platformě.  

Sestavení má dva hlavní `buildTypes`:

 * Ladění (výchozí) – kompilovaný modul runtime s minimálním optimalizace a kontroly další runtime (vyhodnotí). Toto snížení úroveň optimalizace a další kontroly zpomalit spuštění modulu runtime, ale jsou důležité pro ladění. Toto je doporučené nastavení pro vývoj a testování prostředí.
 * Release – kompilovaný modul runtime úplná optimalizací a bez kontroly další runtime. To předá mnohem rychlejší běhu výkon, ale může trvat delší dobu sestavení a může být obtížné ladění. Předat `release` k sestavení vytvořit skript pro tuto možnost vyberte, typu.

Kromě toho ve výchozím nastavení sestavení nejen vytvoří spustitelné soubory modulu runtime, ale také sestavuje všechny testy.
Existuje několik testů, trvá významné množství času, které není nezbytné, pokud chcete experimentovat s změny.
Přidáním, můžete přeskočit sestavení testy `skiptests` argument skript sestavení, jako v následujícím příkladu (Nahraďte `.\build` s `./build.sh` na počítačích systému Unix):

```bat
    .\build skiptests 
```

Předchozí příklad ukázal, jak stavět `Debug` příchuť, který má kontroly runtime vývoj (vyhodnotí) povolených a zakázaných optimalizace. K vytvoření příchuť (vysokorychlostní) verze, postupujte takto:

```bat 
    .\build release skiptests
```

Můžete najít další možnosti sestavení s sestavení pomocí? nebo – help kvalifikátor.   

### <a name="using-your-build"></a>Pomocí vašeho sestavení

Sestavení umístí všechny jeho soubory generované v rámci `bin` adresář na bázi úložiště.
Je *bin\Log* adresář, který obsahuje soubory protokolu vygenerovaných během sestavení (velmi užitečné při sestavení selže).
Skutečný výstup je umístěn v *bin\Product\[platformu].[ Architektura procesoru]. [vytvořit typ]*  adresář, jako třeba *bin\Product\Windows_NT.x64.Release*.

Zatímco 'nezpracovaná' výstup sestavení je někdy vhodná, obvykle vás zajímá jenom balíčky NuGet, které jsou umístěny v `.nuget\pkg` podadresáři předchozí výstupnímu adresáři.

Existují dva základní postupy pro používání váš nový modul runtime:

 1. **Použitím dotnet.exe a NuGet k vytvoření aplikace**.
    V tématu [pomocí vaše sestavení](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) pokyny pro vytvoření programu, který používá váš nový modul runtime s použitím balíčky NuGet, kterou jste právě vytvořili a rozhraní příkazového řádku (CLI), dotnet'. Tento postup je, že jsou pravděpodobností používat váš nový modul runtime vývojáři – modul runtime očekávaným způsobem.    

 2. **Můžete spustit aplikaci pomocí nezabalené knihovny DLL pomocí corerun.exe**.
    Toto úložiště taky definuje jednoduché hostitele názvem corerun.exe které nevyžaduje žádné závislosti na NuGet.
    Budete muset zadat hostitele, kde se dá stáhnout požadované knihovny DLL, které skutečně používáte, a budete muset ručně shromáždit je společně.
    Tento postup je používána všemi testy v [úložišti CoreCLR](https://github.com/dotnet/coreclr)a jsou užitečné pro rychlé místní "upravit kompilaci ladění" smyčky například předběžné testování částí.
    V tématu [provádění aplikací využívajících .NET Core s CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) podrobnosti o použití této techniky.

## <a name="build-the-cli-from-source"></a>Sestavení rozhraní příkazového řádku ze zdroje.

Zdrojový kód pro rozhraní příkazového řádku .NET Core naleznete v [ `dotnet/cli` úložišti na Githubu](https://github.com/dotnet/cli/).

Chcete-li vytvořit základní rozhraní .NET, rozhraní příkazového řádku, potřebujete následující nainstalovaný na počítači.

* Windows a Linux:
    - Git v CESTĚ
* systému macOS:
    - Git v CESTĚ
    - Xcode
    - OpenSSL

K vytvoření, spuštění `build.cmd` v systému Windows, nebo `build.sh` na Linuxu a systému macOS z kořenového adresáře. Pokud nechcete provést testy, spusťte `build.cmd /t:Compile` nebo `./build.sh /t:Compile`. K vytvoření rozhraní příkazového řádku v systému macOS Sierra, budete muset nastavit proměnnou prostředí DOTNET_RUNTIME_ID spuštěním `export DOTNET_RUNTIME_ID=osx.10.11-x64`.

### <a name="using-your-build"></a>Pomocí vašeho sestavení

Použití `dotnet` spustitelného souboru z *artefakty / {os}-{architektura} / stage2* můžete vyzkoušet na nově vytvořený rozhraní příkazového řádku. Pokud chcete použít sestavení výstup v případě vyvolání `dotnet` z aktuální konzoly, můžete také přidat *artefakty / {os}-{architektura} / stage2* k CESTĚ.

## <a name="see-also"></a>Viz také

* [.NET core modul Common Language Runtime (CoreCLR)](https://github.com/dotnet/coreclr/blob/master/README.md)
* [Příručka vývojáře rozhraní příkazového řádku .NET core](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [Vytváření distribučních balíčků .NET Core](./distribution-packaging.md)
