---
title: Sestavení .NET Core ze zdroje
description: Naučte se, jak vytvořit .NET Core a .NET Core CLI ze zdrojového kódu.
author: bleroy
ms.date: 06/28/2017
ms.openlocfilehash: fe5431667d861d830c2ec56252e6e3e2ca08a866
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740913"
---
# <a name="build-net-core-from-source"></a>Sestavení .NET Core ze zdroje

Možnost sestavování .NET Core z jeho zdrojového kódu je důležitá v různých způsobech: usnadňuje portování .NET Core na nové platformy, umožňuje příspěvky a opravy produktu a umožňuje vytváření vlastních verzí rozhraní .NET.
Tento článek obsahuje pokyny pro vývojáře, kteří chtějí sestavovat a distribuovat vlastní verze .NET Core.

## <a name="build-the-clr-from-source"></a>Sestavení CLR ze zdroje

Zdrojový kód pro rozhraní .NET CoreCLR lze nalézt v úložišti [dotnet/runtime](https://github.com/dotnet/runtime/) na GitHubu.

Sestavení v současné době závisí na následujících předpokladech:

- [Git](https://git-scm.com/)
- [CMake](https://cmake.org/)
- [Python](https://www.python.org/)
- C++ kompilátor.

Po instalaci těchto požadavků můžete sestavit modul CLR vyvoláním skriptu sestavení (`build.cmd` ve Windows nebo `build.sh` v systémech Linux a macOS) na bázi úložiště [dotnet/runtime](https://github.com/dotnet/runtime/) .

Instalace komponent se liší v závislosti na operačním systému (OS). Podívejte se na pokyny pro sestavení pro konkrétní operační systém:

- [Windows](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
- [Linux](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
- [macOS](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
- [FreeBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
- [NetBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

V operačním systému neexistují žádné křížové sestavování (jenom pro ARM, které je postavené na platformě x64).  
Musíte být na konkrétní platformě pro sestavení této platformy.  

Sestavení má dvě hlavní `buildTypes`:

- Ladit (výchozí) – zkompiluje modul runtime s minimálními optimalizacemi a dalšími kontrolami za běhu (kontrolní výrazy). Toto snížení úrovně optimalizace a další kontroly pomaleji spouštění za běhu, ale jsou cenné pro ladění. Toto je doporučené nastavení pro vývojová a testovací prostředí.
- Release – zkompiluje modul runtime s úplnými optimalizacemi a bez dalších kontrol za běhu. To bude mít za následek mnohem rychlejší výkon, ale může trvat delší dobu, než se sestaví a může být obtížné ho ladit. Chcete-li vybrat tento typ sestavení, předejte `release` skriptu sestavení.

Kromě toho ve výchozím nastavení sestavení nejen vytvoří běhové spustitelné soubory, ale také vytvoří všechny testy.
Existuje poměrně několik testů, které zabírají značnou dobu, která není nutná, pokud chcete experimentovat pouze se změnami.
Sestavení testů můžete přeskočit přidáním argumentu `skiptests` do skriptu sestavení, jako v následujícím příkladu (nahraďte `.\build` `./build.sh` na počítačích se systémem UNIX):

```bat
    .\build skiptests
```

Předchozí příklad ukázal, jak sestavit `Debug` charakter, který má povolené kontroly doby vývoje (kontrolní výrazy) a optimalizace, které jsou zakázané. Chcete-li sestavit charakter vydaných verzí (s plnou rychlostí), postupujte takto:

```bat
    .\build release skiptests
```

Další možnosti sestavení můžete najít pomocí sestavení pomocí-? nebo – kvalifikátor pomocníka.

### <a name="using-your-build"></a>Použití sestavení

Sestavení umístí všechny své vygenerované soubory pod `bin` adresářem na bázi úložiště.
K dispozici je adresář *bin\Log* , který obsahuje soubory protokolu generované během sestavení (nejužitečnější při neúspěšném sestavení).
Skutečný výstup je umístěný v *bin\Product\[platformě]. [Architektura procesoru]. [typ sestavení]* Adresář, například *bin\product\ Windows_NT. x64. Release*.

Zatímco výstup "raw" sestavení je někdy užitečné, obvykle se zajímá pouze o balíčky NuGet, které jsou umístěny v podadresáři `.nuget\pkg` předchozího výstupního adresáře.

Existují dvě základní techniky použití nového modulu runtime:

 1. **K vytvoření aplikace použijte dotnet. exe a NuGet**.
    Pokyny k vytvoření programu, který používá váš nový modul runtime, pomocí balíčků NuGet, které jste právě vytvořili, a rozhraní příkazového řádku dotnet (CLI) najdete v tématu [použití sestavení](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-your-build.md) . Tato technika je předpokládaný způsob, jakým vývojáři mimo modul runtime využívají nový modul runtime.

 2. Pomocí souboru korutiny **. exe spusťte aplikaci pomocí nebalených knihoven DLL**.
    Toto úložiště také definuje jednoduchého hostitele s názvem spoluspustit. exe, který neprovádí žádnou závislost na NuGet.
    Je nutné sdělit hostiteli, kde mají získat požadované knihovny DLL, které skutečně používáte, a je nutné je ručně shromáždit společně.
    Tato technika je používána všemi testy v úložišti [dotnet/runtime](https://github.com/dotnet/runtime) a je užitečná pro rychlou místní smyčku "Edit-Compile-debug", jako je například předběžné testování částí.
    Podrobnosti o použití této techniky najdete v tématu [spouštění aplikací .NET Core pomocí souboru. exe.](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-corerun.md)

## <a name="build-the-cli-from-source"></a>Sestavení CLI ze zdroje

Zdrojový kód pro .NET Core CLI lze nalézt v úložišti [dotnet/CLI](https://github.com/dotnet/cli/) na GitHubu.

Aby bylo možné sestavit .NET Core CLI, potřebujete na svém počítači nainstalované následující.

- Windows & Linux:
  - Git v cestě
- MacOS
  - Git v cestě
  - Xcode
  - OpenSSL

Aby bylo možné sestavovat, spouštět `build.cmd` ve Windows nebo `build.sh` v systémech Linux a macOS z kořenového adresáře. Pokud nechcete spouštět testy, spusťte `build.cmd -t:Compile` nebo `./build.sh -t:Compile`. Chcete-li sestavit rozhraní příkazového řádku v macOS Sierra, je nutné nastavit proměnnou prostředí DOTNET_RUNTIME_ID spuštěním `export DOTNET_RUNTIME_ID=osx.10.11-x64`.

### <a name="using-your-build"></a>Použití sestavení

K vyzkoušení nově vytvořeného rozhraní příkazového řádku použijte `dotnet` spustitelný soubor z *artefaktů/{OS} – {arch}/STAGE2* . Pokud chcete použít výstup sestavení při vyvolání `dotnet` z aktuální konzoly, můžete také přidat *artefakty/{OS}-{arch}/STAGE2* do cesty.

## <a name="see-also"></a>Viz také:

- [Modul runtime .NET](https://github.com/dotnet/runtime/blob/master/README.md)
- [.NET Core CLI příručka pro vývojáře](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
- [Vytváření distribučních balíčků .NET Core](./distribution-packaging.md)
