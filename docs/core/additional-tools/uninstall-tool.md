---
title: Nástroj odinstalace
description: Přehled nástroje .NET Core Uninstall Tool, což je nástroj s průvodcem, který umožňuje řízené vyčištění sad SDK jádra .NET a runčase.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 816aef6ab8bc0e51bb8befb14fde60513d4fadfc
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507318"
---
# <a name="net-core-uninstall-tool"></a>Nástroj pro odinstalaci .NET Core

[Nástroj .NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) umožňuje odebrat sady .NET Core SDK a runtimes ze systému. K dispozici je kolekce možností, které určují, které verze chcete odinstalovat.

Nástroj podporuje Windows a macOS. Linux není v současné době podporován.

V systému Windows může nástroj odinstalovat pouze sady SDK a runtimes, které byly nainstalovány pomocí jednoho z následujících instalačních programů:

- Instalační program .NET Core SDK a runtime.
- Instalační program sady Visual Studio ve verzích starších než Visual Studio 2019 verze 16.3.

V systému macOS může nástroj odinstalovat pouze sady SDK a runtimes umístěné ve složce */usr/local/share/dotnet.*

Z důvodu těchto omezení nemusí být nástroj schopen odinstalovat všechny sady .NET Core SDK a runtimes v počítači. Pomocí příkazu `dotnet --info` můžete najít všechny nainstalované sady .NET Core SDK a runtimes, včetně těchto sad SDK a runtimes, které tento nástroj nelze odebrat. Příkaz `dotnet-core-uninstall list` zobrazí sady SDK, které lze pomocí nástroje odinstalovat.

## <a name="install-the-tool"></a>Instalace nástroje

Zde si můžete stáhnout nástroj .NET Core Uninstall Tool [a](https://aka.ms/dotnet-core-uninstall-tool) zdrojový kód najdete v úložišti GitHub [dotnet/cli-lab.](https://github.com/dotnet/cli-lab)

> [!NOTE]
> Nástroj vyžaduje zvýšení odinstalace sad SDK jádra .NET a runčase. Proto by měl být nainstalován v adresáři chráněném pro zápis, například *C:\Program Files* v systému Windows nebo */usr/local/bin* v systému macOS. Viz také [zvýšený přístup pro příkazy dotnet](../tools/elevated-access.md). Další informace naleznete v [podrobných pokynech k instalaci](https://aka.ms/dotnet-core-uninstall-tool).

## <a name="run-the-tool"></a>Spuštění nástroje

Následující kroky ukazují doporučený postup pro spuštění nástroje pro odinstalaci:

- [Krok 1 – Zobrazení nainstalovaných sad SDK .NET Core A RunTimes](#step-1---display-installed-net-core-sdks-and-runtimes)
- [Krok 2 - Proveďte suchý běh](#step-2---do-a-dry-run)
- [Krok 3 – Odinstalace sad SDK jádra .NET a runčase](#step-3---uninstall-net-core-sdks-and-runtimes)
- [Krok 4 – Odstranění záložní složky NuGet (volitelné)](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a>Krok 1 – Zobrazení nainstalovaných sad SDK .NET Core A RunTimes

Příkaz `dotnet-core-uninstall list` obsahuje seznam nainstalovaných sad SDK jádra .NET a dob běhu, které lze pomocí tohoto nástroje odebrat. Některé sady SDK a runtimes mohou být vyžadovány sadou Visual Studio a zobrazí se s poznámkou, proč se nedoporučuje je odinstalovat.

> [!NOTE]
> Výstup příkazu `dotnet-core-uninstall list` nebude odpovídat seznamu nainstalovaných verzí ve `dotnet --info` výstupu ve většině případů. Konkrétně tento nástroj nebude zobrazovat verze nainstalované soubory ZIP nebo spravované aplikací Visual Studio (libovolná verze nainstalovaná v sadě Visual Studio 2019 16.3 nebo novější). Jedním ze způsobů, jak zkontrolovat, zda je verze `Add or Remove Programs`spravována visual studio je zobrazit v aplikaci , kde Visual Studio spravované verze jsou označeny jako takové v jejich zobrazované názvy.

**seznam odinstalace dotnet-core-uninstall**

#### <a name="synopsis"></a>Synopse

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a>Možnosti

## <a name="windows"></a>[Windows](#tab/windows)

* **`--aspnet-runtime`**

  Zobrazí seznam všech ASP.NET za běhu jádra, které lze odinstalovat pomocí tohoto nástroje.

* **`--hosting-bundle`**

  Zobrazí seznam všech runtime rozhraní .NET Core a hostingových balíčků, které lze odinstalovat pomocí tohoto nástroje.

* **`--runtime`**

  Zobrazí seznam všech runčasů jádra .NET, které lze tímto nástrojem odinstalovat.

* **`--sdk`**

  Zobrazí seznam všech sad SDK jádra .NET, které lze tímto nástrojem odinstalovat.

* **`-v, --verbosity <LEVEL>`**

  Nastaví úroveň podrobností. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a . Výchozí hodnota je `normal`.

* **`--x64`**

  Zobrazí seznam všech sad X64 .NET Core SDK a runtimes, které lze odinstalovat pomocí tohoto nástroje.

* **`--x86`**

  Zobrazí seznam všech sad X86 .NET Core SDK a runtimes, které lze odinstalovat pomocí tohoto nástroje.

## <a name="macos"></a>[Macos](#tab/macos)

* **`--runtime`**

  Zobrazí seznam všech runčasů jádra .NET, které lze tímto nástrojem odinstalovat.

* **`--sdk`**

  Zobrazí seznam všech sad SDK jádra .NET, které lze tímto nástrojem odinstalovat.

* **`-v, --verbosity <LEVEL>`**

  Nastaví úroveň podrobností. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a . Výchozí hodnota je `normal`.
  
---

#### <a name="examples"></a>Příklady

* Seznam všech sad SDK jádra .NET a runtimes, které lze odebrat pomocí tohoto nástroje:

  ```console
  dotnet-core-uninstall list
  ```

* Seznam všech sad sdsad a runčase jádra x64 .NET:

  ```console
  dotnet-core-uninstall list --x64
  ```

* Seznam všech sad sdsad x86 .NET Core:

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a>Krok 2 - Proveďte suchý běh

`dotnet-core-uninstall dry-run` Příkazy `dotnet-core-uninstall whatif` a zobrazují sady .NET Core SDK a runtimes, které budou odebrány na základě možností, které jsou k dispozici bez provedení odinstalace. Tyto příkazy jsou synonyma.

**dotnet-core-uninstall dry-run a dotnet-core-uninstall whatif**

#### <a name="synopsis"></a>Synopse

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a>Argumenty

* **`VERSION`**

  Zadaná verze k odinstalaci. Můžete uvést několik verzí jeden po druhém, oddělené mezerami. Soubory odpovědí jsou také podporovány.

  > [!TIP]
  > Soubory odpovědí jsou alternativou k umístění všech verzí na příkazovém řádku.
  > Jedná se o textové soubory, \*obvykle s příponou RSP, a každá verze je uvedena na samostatném řádku.
  > Chcete-li zadat soubor `VERSION` odpovědí pro \@ argument, použijte znak bezprostředně následovaný názvem souboru odpovědi.

#### <a name="options"></a>Možnosti

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Odebere všechny sady .NET Core SDK a runtimes.

* **`--all-below <VERSION>`**

  Odebere pouze sady .NET Core SDK a runtimes s verzí menší než zadaná verze. Zadaná verze zůstane nainstalována.

* **`--all-but <VERSIONS>`**

  Odebere všechny sady .NET Core SDK a runtimes, s výjimkou těch, které byly zadány.

* **`--all-but-latest`**

  Odebere sady .NET Core SDK a runtimes, s výjimkou jedné nejvyšší verze.

* **`--all-lower-patches`**

  Odebere sady .NET Core SDK a runtimes nahrazené vyššími opravami. Tato možnost chrání global.json.

* **`--all-previews`**

  Odebere sady .NET Core SDK a runtimes označené jako náhledy.

* **`--all-previews-but-latest`**

  Odebere sady .NET Core SDK a runtimes označené jako náhledy s výjimkou jednoho nejvyššího náhledu.

* **`--aspnet-runtime`**

  Odebere pouze ASP.NET za běhu jádra.

* **`--hosting-bundle`**

  Odebere pouze runtime .NET Core a hostování balíčků.

* **`--major-minor <MAJOR_MINOR>`**

  Odebere sady .NET Core SDK a `major.minor` runtimes, které odpovídají zadané verzi.

* **`--runtime`**

  Odebere pouze runtimes jádra .NET.

* **`--sdk`**

  Odebere pouze sady SDK jádra .NET.

* **`-v, --verbosity <LEVEL>`**

  Nastaví úroveň podrobností. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a . Výchozí hodnota je `normal`.

* **`--x64`**

  Musí být `--sdk`použit `--runtime`s `--aspnet-runtime` , a odebrat x64 SDK nebo runtimes.

* **`--x86`**

  Musí být `--sdk`použit `--runtime`s `--aspnet-runtime` , a odebrat x86 SDK nebo runtimes.

* **`--force`** Vynutí odebrání verzí, které mohou být použity visual studio.

Poznámky:

1. Přesně jeden `--sdk` `--runtime`z `--aspnet-runtime`, `--hosting-bundle` , , a je požadováno.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , a jsou výlučné.
3. Pokud `--x64` `--x86` nebo nejsou zadány, budou odebrány x64 i x86.

## <a name="macos"></a>[Macos](#tab/macos)

* **`--all`**

  Odebere všechny sady .NET Core SDK a runtimes.

* **`--all-below <VERSION>`**

  Odebere sady .NET Core SDK a runtimes pod zadanou verzí. Zadaná verze zůstane zachována.

* **`--all-but <VERSIONS>`**

  Odebere sady .NET Core SDK a runtimes, s výjimkou těch, které byly zadány.

* **`--all-but-latest`**

  Odebere sady .NET Core SDK a runtimes, s výjimkou jedné nejvyšší verze.

* **`--all-lower-patches`**

  Odebere sady .NET Core SDK a runtimes nahrazené vyššími opravami. Tato možnost chrání global.json.

* **`--all-previews`**

  Odebere sady .NET Core SDK a runtimes označené jako náhledy.

* **`--all-previews-but-latest`**

  Odebere sady .NET Core SDK a runtimes označené jako náhledy s výjimkou jednoho nejvyššího náhledu.

* **`--major-minor <MAJOR_MINOR>`**

  Odebere sady .NET Core SDK a `major.minor` runtimes, které odpovídají zadané verzi.

* **`--runtime`**

  Odebere pouze runtimes jádra .NET.

* **`--sdk`**

  Odebere pouze sady SDK jádra .NET.

* **`-v, --verbosity <LEVEL>`**

  Nastaví úroveň podrobností. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a . Výchozí hodnota je `normal`.
  
* **`--force`** Vynutí odebrání verzí, které mohou být používány sady Visual Studio nebo sady SDK.

Poznámky:

1. Přesně jeden `--sdk` `--runtime` z a je nutné.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , a jsou výlučné.

---

#### <a name="examples"></a>Příklady

> [!NOTE]
> Ve výchozím nastavení nejsou ve `dotnet-core-uninstall dry-run` výstupu zahrnuty sady .NET Core SDK a runtimes, které mohou být vyžadovány sadou Visual Studio nebo jinými sadami SDK. V následujících příkladech některé zadané sady SDK a doba běhu nemusí být zahrnuty do výstupu, v závislosti na stavu počítače. Chcete-li zahrnout všechny sady SDK a dobu běhu, `--force` uveďte je explicitně jako argumenty nebo použijte možnost.

* Běh nasucho odebrání všech runčasů .NET Core, které byly nahrazeny vyššími opravami:

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* Nasucho odstranit všechny sady .NET Core `2.2.301`SDK pod verzí :

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a>Krok 3 – Odinstalace sad SDK jádra .NET a runčase

`dotnet-core-uninstall remove`odinstaluje sady .NET Core SDK a runtimes, které jsou určeny kolekcí možností. Nástroj nelze použít k odinstalaci sad SDK a runtimes s verzí 5.0 nebo vyšší.

Vzhledem k tomu, že tento nástroj má destruktivní chování, **důrazně** doporučujeme provést spuštění nasucho před spuštěním příkazu remove. Běh na sucho vám ukáže, jaké sady .NET Core SDK `remove` a runtimes budou odebrány při použití příkazu. Odkazovat na [Mám odebrat verzi?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) chcete-li zjistit, které sady SDK a runtimes jsou bezpečné odebrat.

> [!CAUTION]
> Mějte na paměti následující upozornění:
>
>- Tento nástroj může odinstalovat verze sady .NET Core SDK, které jsou vyžadovány `global.json` soubory v počítači. Sady SDK jádra .NET můžete přeinstalovat na stránce [Download .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)
>- Tento nástroj může odinstalovat verze runtime .NET Core, které jsou vyžadovány aplikacemi závislými na rámci počítače. Runtime jádra .NET můžete přeinstalovat na stránce [Download .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)
>- Tento nástroj může odinstalovat verze sady .NET Core SDK a runtime, na které aplikace Visual Studio spoléhá. Pokud přerušíte instalaci sady Visual Studio, spusťte "Oprava" v instalačním programu sady Visual Studio a vraťte se do pracovního stavu.

Ve výchozím nastavení všechny příkazy zachovat .NET Core SDK a runtimes, které mohou být vyžadovány Visual Studio nebo jiné sady SDK. Tyto sady SDK a runtimes lze odinstalovat jejich výpisem `--force` explicitně jako argumenty nebo pomocí možnosti.

Nástroj vyžaduje zvýšení odinstalace sad SDK jádra .NET a runčase. Spusťte nástroj v příkazovém `sudo` řádku Správce v systému Windows a v systému macOS. `dry-run` Příkazy `whatif` a nevyžadují zvýšení oprávnění.

**dotnet-core-uninstall odebrat**

#### <a name="synopsis"></a>Synopse

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a>Argumenty

* **`VERSION`**

  Zadaná verze k odinstalaci. Můžete uvést několik verzí jeden po druhém, oddělené mezerami. Soubory odpovědí jsou také podporovány.

  > [!TIP]
  > Soubory odpovědí jsou alternativou k umístění všech verzí na příkazovém řádku.
  > Jedná se o textové soubory, \*obvykle s příponou RSP, a každá verze je uvedena na samostatném řádku.
  > Chcete-li zadat soubor `VERSION` odpovědí pro \@ argument, použijte znak bezprostředně následovaný názvem souboru odpovědi.

#### <a name="options"></a>Možnosti

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Odebere všechny sady .NET Core SDK a runtimes.

* **`--all-below <VERSION>`**

  Odebere pouze sady .NET Core SDK a runtimes s verzí menší než zadaná verze. Zadaná verze zůstane nainstalována.

* **`--all-but <VERSIONS>`**

  Odebere všechny sady .NET Core SDK a runtimes, s výjimkou těch, které byly zadány.

* **`--all-but-latest`**

  Odebere sady .NET Core SDK a runtimes, s výjimkou jedné nejvyšší verze.

* **`--all-lower-patches`**

  Odebere sady .NET Core SDK a runtimes nahrazené vyššími opravami. Tato možnost chrání global.json.

* **`--all-previews`**

  Odebere sady .NET Core SDK a runtimes označené jako náhledy.

* **`--all-previews-but-latest`**

  Odebere sady .NET Core SDK a runtimes označené jako náhledy s výjimkou jednoho nejvyššího náhledu.

* **`--aspnet-runtime`**

  Odebere pouze ASP.NET za běhu jádra.

* **`--hosting-bundle`**

  Odebere pouze runtime .NET Core a hostování balíčků.

* **`--major-minor <MAJOR_MINOR>`**

  Odebere sady .NET Core SDK a `major.minor` runtimes, které odpovídají zadané verzi.

* **`--runtime`**

  Odebere pouze runtimes jádra .NET.

* **`--sdk`**

  Odebere pouze sady SDK jádra .NET.

* **`-v, --verbosity <LEVEL>`**

  Nastaví úroveň podrobností. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a . Výchozí hodnota je `normal`.

* **`--x64`**

  Musí být `--sdk`použit `--runtime`s `--aspnet-runtime` , a odebrat x64 SDK nebo runtimes.

* **`--x86`**

  Musí být `--sdk`použit `--runtime`s `--aspnet-runtime` , a odebrat x86 SDK nebo runtimes.

* **`-y, --yes`** Provede příkaz bez nutnosti potvrzení ano nebo ne.

* **`--force`** Vynutí odebrání verzí, které mohou být použity visual studio.

Poznámky:

1. Přesně jeden `--sdk` `--runtime`z `--aspnet-runtime`, `--hosting-bundle` , , a je požadováno.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , a jsou výlučné.
3. Pokud `--x64` `--x86` nebo nejsou zadány, budou odebrány x64 i x86.

## <a name="macos"></a>[Macos](#tab/macos)

* **`--all`**

  Odebere všechny sady .NET Core SDK a runtimes.

* **`--all-below <VERSION>`**

  Odebere sady .NET Core SDK a runtimes pod zadanou verzí. Zadaná verze zůstane zachována.

* **`--all-but <VERSIONS>`**

  Odebere sady .NET Core SDK a runtimes, s výjimkou těch, které byly zadány.

* **`--all-but-latest`**

  Odebere sady .NET Core SDK a runtimes, s výjimkou jedné nejvyšší verze.

* **`--all-lower-patches`**

  Odebere sady .NET Core SDK a runtimes nahrazené vyššími opravami. Tato možnost chrání global.json.

* **`--all-previews`**

  Odebere sady .NET Core SDK a runtimes označené jako náhledy.

* **`--all-previews-but-latest`**

  Odebere sady .NET Core SDK a runtimes označené jako náhledy s výjimkou jednoho nejvyššího náhledu.

* **`--major-minor <MAJOR_MINOR>`**

  Odebere sady .NET Core SDK a `major.minor` runtimes, které odpovídají zadané verzi.

* **`--runtime`**

  Odebere pouze runtimes jádra .NET.

* **`--sdk`**

  Odebere pouze sady SDK jádra .NET.

* **`-v, --verbosity <LEVEL>`**

  Nastaví úroveň podrobností. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a . Výchozí hodnota je `normal`.

* **`-y, --yes`** Provede příkaz bez nutnosti potvrzení Y/N.
  
* **`--force`** Vynutí odebrání verzí, které mohou být používány sady Visual Studio nebo sady SDK.

Poznámky:

1. Přesně jeden `--sdk` `--runtime` z a je nutné.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , a jsou výlučné.

---

#### <a name="examples"></a>Příklady

> [!NOTE]
> Ve výchozím nastavení jsou uloženy sady .NET Core SDK a runtimes, které mohou být vyžadovány sadou Visual Studio nebo jinými sadami SDK. V následujících příkladech mohou některé zadané sady SDK a doba běhu zůstat v závislosti na stavu počítače. Chcete-li odebrat všechny sady SDK a dobu běhu, uveďte je explicitně jako argumenty nebo použijte `--force` možnost.

* Odeberte všechny runtimes jádra .NET kromě verze `3.0.0-preview6-27804-01` bez nutnosti potvrzení y/n:

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* Odeberte všechny sady .NET Core 1.1 SDK bez nutnosti potvrzení Y/n:

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* Odeberte sdk .NET Core 1.1.11 bez výstupu konzoly:

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* Odeberte všechny sady .NET Core SDK, které lze bezpečně odebrat tímto nástrojem:

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* Odeberte všechny sady .NET Core SDK, které lze odebrat tímto nástrojem, včetně sad SDK, které mohou být vyžadovány sadou Visual Studio (nedoporučuje se):

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* Odebrání všech sad SDK jádra ROZHRANÍ .NET, které jsou zadány v souboru odpovědí`versions.rsp`

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  Obsah *versions.rsp* je následující:
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a>Krok 4 – Odstranění záložní složky NuGet (volitelné)

V některých případech již `NuGetFallbackFolder` nepotřebujete a možná budete chtít odstranit. Další informace o odstranění této složky naleznete [v tématu Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).

## <a name="uninstall-the-tool"></a>Odinstalace nástroje

## <a name="windows"></a>[Windows](#tab/windows)

1. Sem **Přidat nebo odebrat programy**.
2. Vyhledejte `Microsoft .NET Core SDK Uninstall Tool`.
3. Vyberte **možnost Odinstalovat**.

## <a name="macos"></a>[Macos](#tab/macos)

Odstraňte stažený soubor *dotnet-core-uninstall.tar.gz* z adresáře, ve kterém byl nainstalován. Pokud jste rozbalili obsah tohoto souboru do jiného adresáře, nezapomeňte tento obsah také odstranit.

---
