---
title: Řešení potíží s používáním nástrojů .NET Core
description: Seznamte se s běžnými problémy při používání nástrojů .NET Core a možných řešení.
author: kdollard
ms.date: 02/14/2020
ms.openlocfilehash: ab5d1be8f201ea283f8537f18886feab46157127
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543271"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a>Řešení potíží s používáním nástrojů .NET Core

Při pokusu o instalaci nebo spuštění nástroje .NET Core, který může být globálním nástrojem nebo místním nástrojem, může docházet k problémům. Tento článek popisuje běžné hlavní příčiny a některá možná řešení.

## <a name="installed-net-core-tool-fails-to-run"></a>Nepodařilo se spustit nainstalovaný nástroj .NET Core.

Když se nepovede spustit nástroj .NET Core, pravděpodobně došlo k jednomu z následujících problémů:

* Spustitelný soubor pro nástroj se nenašel.
* Nenašla se správná verze modulu runtime .NET Core.

### <a name="executable-file-not-found"></a>Spustitelný soubor se nenašel.

Pokud se spustitelný soubor nenajde, zobrazí se zpráva podobná následující:

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

Název spustitelného souboru určuje způsob, jakým se nástroj vyvolá. Následující tabulka popisuje formát:

| Formát názvu spustitelného souboru  | Formát vyvolání   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* Globální nástroje

    Globální nástroje mohou být nainstalovány ve výchozím adresáři nebo v určitém umístění. Výchozí adresáře jsou:

    | Operační systém          | Cesta                          |
    |-------------|-------------------------------|
    | Linux/macOS | `$HOME/.dotnet/tools`         |
    | Windows     | `%USERPROFILE%\.dotnet\tools` |

    Pokud se pokoušíte spustit globální nástroj, ověřte, že proměnná prostředí `PATH` v počítači obsahuje cestu, kam jste nainstalovali globální nástroj a že je spustitelný soubor v této cestě.

    .NET Core CLI se pokusí přidat výchozí umístění do proměnné prostředí PATH při prvním použití. Existuje však několik scénářů, kdy umístění nemusí být přidáno do cesty automaticky, takže budete muset upravit cestu pro konfiguraci v následujících případech:

  * Pokud používáte Linux a nainstalujete .NET Core SDK pomocí souborů *. tar. gz* , a ne apt-get nebo ot/min.
  * Pokud používáte macOS 10,15 "Catalina" nebo novější verze.
  * Pokud používáte macOS 10,14 "Mojave" nebo starší verze a nainstalovali jste .NET Core SDK pomocí souborů *. tar. gz* , a ne *. pkg*.
  * Pokud jste nainstalovali sadu .NET Core 3,0 SDK a nastavili jste proměnnou prostředí `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` na `false`.
  * Pokud jste nainstalovali sadu .NET Core 2,2 SDK nebo starší verze a nastavili jste proměnnou prostředí `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` na `true`.

  Další informace najdete v tématu [nástroje .NET Core](global-tools.md).

* Místní nástroje

  Pokud se pokoušíte spustit místní nástroj, ověřte, zda je v aktuálním adresáři nebo v některém z jeho nadřazených adresářů soubor manifestu s názvem *dotnet-Tools. JSON* . Tento soubor může být také živý v rámci složky s názvem *. config* kdekoli v hierarchii složek projektu místo kořenové složky. Pokud *dotnet-Tools. JSON* existuje, otevřete ho a vyhledejte nástroj, který se pokoušíte spustit. Pokud soubor neobsahuje položku pro `"isRoot": true`, pak dále zkontrolujte hierarchii souborů pro další soubory manifestu nástroje.

  Pokud se pokoušíte spustit nástroj .NET Core, který byl nainstalován se zadanou cestou, je nutné při používání nástroje použít tuto cestu. Příklad použití nástroje, který je nainstalovaný nástrojem Path, je:

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a>Modul runtime se nenašel.

Nástroje .NET Core jsou [aplikace závislé na rozhraních](../deploying/index.md#publish-runtime-dependent), což znamená, že spoléhají na modul runtime .NET Core nainstalovaný na vašem počítači. Pokud se očekávaný modul runtime nenajde, dodržuje normální pravidla předávaných modulem runtime .NET Core, jako například:

* Aplikace se vrátí k nejvyšší verzi opravy zadané hlavní a dílčí verze.
* Pokud neexistuje žádný vyhovující modul runtime s párové číslo hlavní verze a podverze, použije se další vyšší dílčí verze.
* Mezi verzemi verze Preview modulu runtime nebo verzí Preview a verzí verze Preview nedochází k posunutí. Proto musí být nástroje .NET Core vytvořené pomocí verzí Preview znovu sestavené a znovu publikovány autorem a opětovnou instalací.

Ve výchozím nastavení se v obou běžných scénářích neobjevují žádné možnosti přeposlání:

* K dispozici jsou pouze nižší verze modulu runtime. Přeposílání jenom vybírá novější verze modulu runtime.
* K dispozici jsou pouze vyšší hlavní verze modulu runtime. Přeposílání nepřekračuje hlavní hranice verze.

Pokud aplikace nemůže najít vhodný modul runtime, spuštění se nespustí a ohlásí chybu.

Pomocí jednoho z následujících příkazů můžete zjistit, které moduly runtime .NET Core jsou nainstalovány na vašem počítači:

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

Pokud si myslíte, že by měl nástroj podporovat verzi modulu runtime, kterou máte aktuálně nainstalovanou, můžete se obrátit na autora nástroje a zjistit, jestli můžou aktualizovat číslo verze nebo více cílů. Jakmile znovu zkompilujete a znovu publikujete balíček nástrojů do NuGet s aktualizovaným číslem verze, můžete kopii aktualizovat. I když k tomu nedojde, nejrychlejší řešení pro vás je instalace verze modulu runtime, která by fungovala s nástrojem, který se pokoušíte spustit. Pokud si chcete stáhnout specifickou verzi modulu runtime .NET Core, navštivte [stránku ke stažení pro .NET Core](https://dotnet.microsoft.com/download/dotnet-core).

Pokud nainstalujete .NET Core SDK do jiného než výchozího umístění, je třeba nastavit proměnnou prostředí `DOTNET_ROOT` na adresář, který obsahuje `dotnet` spustitelný soubor.

## <a name="net-core-tool-installation-fails"></a>Instalace nástroje .NET Core Tool se nezdařila

Existuje několik důvodů, proč nemusí dojít k selhání instalace globálního nebo místního nástroje .NET Core. Pokud se instalace nástroje nezdařila, zobrazí se zpráva podobná následující:

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

Abychom vám pomohli diagnostikovat tyto chyby, zobrazují se zprávy NuGet přímo uživateli společně s předchozí zprávou. Zpráva NuGet vám může pomohly tento problém identifikovat.

### <a name="package-naming-enforcement"></a>Vynucení pojmenování balíčků

Společnost Microsoft změnila své doprovodné materiály na ID balíčku pro nástroje, což vede k tomu, že se nenalezne řada nástrojů s předpokládaným názvem. Nové doprovodné materiály jsou všechny nástroje Microsoftu s předponou "Microsoft". Tato předpona je vyhrazená a dá se použít jenom pro balíčky podepsané certifikátem autorizovaným společností Microsoft.

V průběhu přechodu budou mít některé nástroje Microsoftu starou formu ID balíčku, zatímco ostatní budou mít novou formu:

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

ID balíčků se aktualizují, takže budete muset přejít na nové ID balíčku, abyste získali nejnovější aktualizace. Balíčky s zjednodušeným názvem nástroje budou zastaralé.

### <a name="preview-releases"></a>Verze Preview

* Pokoušíte se nainstalovat verzi Preview a nepoužili jste k určení verze možnost `--version`.

Nástroje .NET Core, které jsou ve verzi Preview, se musí zadat s částí názvu, aby označovaly, že jsou ve verzi Preview. Nemusíte zahrnovat celou verzi Preview. Za předpokladu, že čísla verzí jsou v očekávaném formátu, můžete použít něco podobného jako v následujícím příkladu:

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a>Balíček není nástroj .NET Core.

* Našel se balíček NuGet s tímto názvem, ale Nejednalo se o nástroj .NET Core.

Pokud se pokusíte nainstalovat balíček NuGet, který je regulárním balíčkem NuGet, a ne nástrojem .NET Core, zobrazí se chybová zpráva podobná následující:

> NU1212: Neplatná kombinace projektu a balíčku pro `<ToolName>`. Styl projektu DotnetToolReference může obsahovat pouze odkazy na typ DotnetTool.

### <a name="nuget-feed-cant-be-accessed"></a>K informačnímu kanálu NuGet nelze přicházet.

* Požadovaný informační kanál NuGet není k dispozici, možná kvůli problému s připojením k Internetu.

Instalace nástroje vyžaduje přístup k informačnímu kanálu NuGet, který obsahuje balíček nástroje. Dojde k chybě, pokud informační kanál není k dispozici. Můžete měnit informační kanály pomocí `nuget.config`, požadovat konkrétní `nuget.config` soubor nebo zadat další kanály s přepínačem `--add-source`. Ve výchozím nastavení vyvolá NuGet chybu pro jakýkoliv informační kanál, který se nemůže připojit. Příznak `--ignore-failed-sources` může přeskočit tyto nedostupné zdroje.

### <a name="package-id-incorrect"></a>ID balíčku je nesprávné.

* Nezadali jste název nástroje.

Běžným důvodem selhání je, že název nástroje není správný. K tomu může dojít z důvodu neúspěšného zadání, nebo proto, že se nástroj přesunul nebo byl zastaralý. V případě nástrojů na NuGet.org je třeba, abyste si ověřili, že je správný název, hledání nástroje na NuGet.org a zkopírování instalačního příkazu.

## <a name="see-also"></a>Viz také:

* [Nástroje .NET Core](global-tools.md)
