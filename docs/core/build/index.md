---
title: Sestavení .NET Core ze zdroje
description: Zjistěte, jak sestavení .NET Core a .NET Core CLI ze zdrojového kódu.
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.openlocfilehash: 2623c5d21121b71960d174301c35bdd0d7f8558a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468795"
---
# <a name="build-net-core-from-source"></a>Sestavení .NET Core ze zdroje

Možnost vyvíjet aplikace .NET Core z jeho zdrojový kód je důležité několika různými způsoby: usnadňuje na port .NET Core pro nové platformy, umožňuje příspěvky a opravy produktu a umožňuje vytvářet vlastní verze rozhraní .NET.
Tento článek obsahuje pokyny pro vývojáře, kteří chtějí vytvářet a distribuovat vlastní verzi .NET Core.

## <a name="build-the-clr-from-source"></a>Sestavení CLR ze zdroje

Zdrojový kód pro .NET CoreCLR najdete v [dotnet/coreclr](https://github.com/dotnet/coreclr/) úložišti na Githubu.

Sestavení aktuálně závisí na následujících požadavků:

* [Git](https://git-scm.com/)
* [CMake](https://cmake.org/)
* [Python](https://www.python.org/)
* Kompilátor jazyka C++.

Po instalaci těchto nezbytných podmínkách, můžete vytvořit CLR vyvoláním skript sestavení (`build.cmd` na Windows, nebo `build.sh` v Linuxu a macOS) na základě [dotnet/coreclr](https://github.com/dotnet/coreclr/) úložiště.

Instalace komponent se liší v závislosti na operačním systému (OS). Přečtěte si pokyny sestavení pro konkrétní operační systém:

* [Windows](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
* [Linux](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
* [macOS](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
* [FreeBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
* [NetBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

Nevzniká žádný napříč vytváření přes operační systém (pouze pro ARM, které je postavené na X64).  
Musíte být na konkrétní platformě k vytvoření této platformy.  

Sestavení má dvě hlavní `buildTypes`:

* Ladění (výchozí) – zkompiluje modul runtime s minimální optimalizace a kontroly za běhu další (kontrolních příkazů). Toto omezení úroveň optimalizace a další kontroly zpomalit spuštění modulu runtime, ale jsou důležité pro ladění. Toto je doporučené nastavení pro vývojová a testovací prostředí.
* Release – zkompiluje modul runtime se úplná optimalizace a bez kontroly další za běhu. To povede k mnohem rychlejšímu běhu výkon, ale může trvat delší dobu sestavení a může být obtížné ladit. Předejte `release` k buildu skript, který tuto možnost vyberte, typ sestavení.

Kromě toho ve výchozím nastavení sestavení nejen vytvoří spustitelné soubory modulu runtime, ale zároveň vytvoří všechny testy.
Existuje mnoho zkoušky významné množství času, které není nezbytné, pokud chcete experimentovat s změny.
Můžete přeskočit sestavení testů tak, že přidáte `skiptests` argument na skript sestavení, jako v následujícím příkladu (nahradit `.\build` s `./build.sh` na počítačích Unix):

```bat
    .\build skiptests
```

Předchozí příklad ukázal, jak vytvořit `Debug` charakter, který má kontrol za vývoj (kontrolní výrazy) povolené i zakázané optimalizace. K sestavení charakter (plné rychlosti) verzi, postupujte takto:

```bat
    .\build release skiptests
```

Můžete najít další možnosti sestavení se sestavením pomocí /? nebo – help kvalifikátoru.

### <a name="using-your-build"></a>Pomocí sestavení

Sestavení umístí všechny jeho generované soubory v rámci `bin` adresáři základní úložiště.
Je *bin\Log* adresáře, který obsahuje soubory protokolu vygenerované během sestavování (nejužitečnější, když sestavení selže).
Aktuální výstup je umístěn v *bin\Product\[platformy]. [ Architektura procesoru]. [typ sestavení]*  adresář, jako například *bin\Product\Windows_NT.x64.Release*.

'Nezpracovanou' výstupy sestavení je někdy užitečné, obvykle vás zajímá jenom balíčky NuGet, které jsou umístěny v `.nuget\pkg` podadresář předchozí výstupní adresář.

Existují dva základní postupy pro použití nového modulu runtime:

 1. **Můžete vytvořit aplikaci dotnet.exe a NuGet**.
    Zobrazit [pomocí sestavení](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) pokyny k vytvoření programu, který používá nový modul runtime pomocí balíčků NuGet jste právě vytvořili a "dotnet" rozhraní příkazového řádku (CLI). Tato technika je, že vývojáři – modul runtime očekávané způsob, jak můžou využívat nové prostředí runtime.

 2. **Ke spuštění aplikace pomocí nezabalené knihovny DLL použijte corerun.exe**.
    Toto úložiště také definuje jednoduché hostitelské volá corerun.exe, který nemá žádné závislosti na webu NuGet.
    Musíte určit hostitele získání požadovaných knihoven DLL, které skutečně používáte, a budete muset ručně shromáždit je společně.
    Tato technika je používána všemi testy v [dotnet/coreclr](https://github.com/dotnet/coreclr) úložiště a je užitečné pro rychlé místní "úpravy kompilace – ladění" smyčka například předběžné testování částí.
    Zobrazit [spouštění aplikací .NET Core s CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) podrobnosti o použití této techniky.

## <a name="build-the-cli-from-source"></a>Rozhraní příkazového řádku ze zdroje sestavení

Zdrojový kód pro rozhraní příkazového řádku .NET Core najdete v [dotnet/cli](https://github.com/dotnet/cli/) úložišti na Githubu.

Aby bylo možné sestavit rozhraní příkazového řádku .NET Core, potřebujete následující v počítači byly nainstalovány.

* Windows a Linuxu:
  * Git na CESTĚ
* macOS:
  * Git na CESTĚ
  * Xcode
  * OpenSSL

Aby bylo možné sestavit, spustit `build.cmd` na Windows, nebo `build.sh` v Linuxu a macOS z kořenového adresáře. Pokud nechcete, aby ke spuštění testů, spouštění `build.cmd /t:Compile` nebo `./build.sh /t:Compile`. K vytvoření rozhraní příkazového řádku v systému macOS Sierra, je nutné nastavit proměnnou prostředí DOTNET_RUNTIME_ID spuštěním `export DOTNET_RUNTIME_ID=osx.10.11-x64`.

### <a name="using-your-build"></a>Pomocí sestavení

Použití `dotnet` spustitelného souboru z *artefakty / {os} – {arch} / stage2* můžete vyzkoušet na nově vytvořený rozhraní příkazového řádku. Pokud chcete použít výstup při vyvolání sestavení `dotnet` na aktuální konzolu, můžete také přidat *artefakty / {os} – {arch} / stage2* k CESTĚ.

## <a name="see-also"></a>Viz také:

* [.NET core Common Language Runtime (CoreCLR)](https://github.com/dotnet/coreclr/blob/master/README.md)
* [Příručka pro vývojáře rozhraní příkazového řádku .NET core](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [Vytváření distribučních balíčků .NET Core](./distribution-packaging.md)
