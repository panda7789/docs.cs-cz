---
title: Poradce při potížích s používáním nástroje .NET Core
description: Seznamte se s běžnými problémy při spouštění nástrojů .NET Core a možných řešení.
author: kdollard
ms.date: 02/14/2020
ms.openlocfilehash: ed6243f802c4d3ce56a742916a1a28676e3cd876
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146447"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a>Poradce při potížích s používáním nástroje .NET Core

Při pokusu o instalaci nebo spuštění nástroje .NET Core, který může být globálním nástrojem nebo místním nástrojem, se mohou narazit na problémy. Tento článek popisuje běžné hlavní příčiny a některá možná řešení.

## <a name="installed-net-core-tool-fails-to-run"></a>Nainstalovaný nástroj .NET Core se nepodařilo spustit

Pokud se nástroj .NET Core nepodaří spustit, s největší pravděpodobností jste narazili na jeden z následujících problémů:

* Spustitelný soubor nástroje nebyl nalezen.
* Nebyla nalezena správná verze runtime jádra .NET.

### <a name="executable-file-not-found"></a>Spustitelný soubor nebyl nalezen.

Pokud se spustitelný soubor nenašel, zobrazí se zpráva podobná následující:

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

Název spustitelného souboru určuje způsob vyvolání nástroje. Následující tabulka popisuje formát:

| Formát spustitelného názvu  | Formát vyvolání   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* Globální nástroje

  Globální nástroje lze nainstalovat do výchozího adresáře nebo do určitého umístění. Výchozí adresáře jsou:

  | Operační systém          | Cesta                          |
  |-------------|-------------------------------|
  | Linux/macOS | `$HOME/.dotnet/tools`         |
  | Windows     | `%USERPROFILE%\.dotnet\tools` |

  Pokud se pokoušíte spustit globální nástroj, `PATH` zkontrolujte, zda proměnná prostředí v počítači obsahuje cestu, kam jste nainstalovali globální nástroj, a zda je spustitelný soubor v této cestě.

  Rozhraní .NET Core CLI se pokusí přidat výchozí umístění do proměnné prostředí PATH při prvním použití. Existují však některé scénáře, kde umístění nemusí být přidáno do cesty automaticky:

  * Pokud používáte Linux a nainstalovali jste sdk .NET Core SDK pomocí souborů *.tar.gz* a ne apt-get nebo rpm.
  * Pokud používáte macOS 10.15 "Catalina" nebo novější verze.
  * Pokud používáte macOS 10.14 "Mojave" nebo starší verze a nainstalovali jste sdk .NET Core SDK pomocí souborů *.tar.gz* a ne *.pkg*.
  * Pokud jste nainstalovali sadu .NET Core 3.0 SDK `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` a `false`nastavili jste proměnnou prostředí na .
  * Pokud jste nainstalovali sadu .NET Core 2.2 SDK nebo starší `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` verze `true`a nastavili jste proměnnou prostředí na .

  V těchto scénářích nebo `--tool-path` pokud `PATH` jste zadali možnost, proměnná prostředí v počítači automaticky neobsahuje cestu, kam jste nainstalovali globální nástroj. V takovém případě přidejte umístění nástroje `$HOME/.dotnet/tools`(například) k proměnné `PATH` prostředí pomocí jakékoli metody, kterou prostředí poskytuje pro aktualizaci proměnných prostředí. Další informace naleznete v tématu [.NET Core tools](global-tools.md).

* Místní nástroje

  Pokud se pokoušíte spustit místní nástroj, ověřte, zda je v aktuálním adresáři nebo v některém z nadřazených adresářů soubor manifestu nazývaný *dotnet-tools.json.* Tento soubor může také žít pod složkou s názvem *.config* kdekoli v hierarchii složek projektu, namísto kořenové složky. Pokud *dotnet-tools.json* existuje, otevřete jej a zkontrolujte nástroj, který se pokoušíte spustit. Pokud soubor neobsahuje položku `"isRoot": true`pro aplikaci , zkontrolujte také další hierarchii souborů pro další soubory manifestu nástroje.

  Pokud se pokoušíte spustit nástroj .NET Core, který byl nainstalován se zadanou cestou, je třeba tuto cestu zahrnout při používání nástroje. Příkladem použití nástroje nainstalovaného nástroje je:

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a>Doba běhu nebyla nalezena.

Nástroje .NET Core jsou [aplikace závislé na rámci](../deploying/index.md#publish-runtime-dependent), což znamená, že spoléhají na runtime .NET Core nainstalovaného v počítači. Pokud není nalezen očekávaný čas runtime, postupujte podle normálních pravidel pro přetápění vpřed .NET Core, například:

* Aplikace se převádí dopředu na nejvyšší verzi opravy zadané hlavní a dílčí verze.
* Pokud neexistuje žádný odpovídající runtime s odpovídajícím hlavním a dílčím číslem verze, použije se další vyšší dílčí verze.
* Posunout vpřed nedochází mezi verzemi náhledu runtime nebo mezi verzemi náhledu a verzemi vydání. Nástroje .NET Core vytvořené pomocí verzí ve verzi preview musí být autorem znovu sestaveny a znovu publikovány a znovu nainstalovány.

K přechodu vpřed ve výchozím nastavení nedojde ve dvou běžných scénářích:

* K dispozici jsou pouze nižší verze runtime. Posunutím vpřed vyberete pouze novější verze běhu.
* K dispozici jsou pouze vyšší hlavní verze runtime. Posun vpřed nepřekračuje hranice hlavní verze.

Pokud aplikace nemůže najít vhodný běh, se nepodaří spustit a hlásí chybu.

Pomocí jednoho z následujících příkazů můžete zjistit, které runčasy jádra .NET jsou v počítači nainstalovány:

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

Pokud se domníváte, že by nástroj měl podporovat aktuálně nainstalovanou verzi runtime, můžete se obrátit na autora nástroje a zjistit, zda mohou aktualizovat číslo verze nebo více cílů. Po překompilované a znovu publikovat jejich balíček nástrojů nuget s aktualizovaným číslem verze, můžete aktualizovat kopii. I když k tomu nedojde, nejrychlejším řešením je instalace verze runtime, která by fungovala s nástrojem, který se pokoušíte spustit. Chcete-li stáhnout konkrétní verzi runtime .NET Core, navštivte [stránku pro stažení jádra .NET](https://dotnet.microsoft.com/download/dotnet-core).

Pokud nainstalujete sadu .NET Core SDK do jiného než `DOTNET_ROOT` výchozího umístění, `dotnet` je třeba nastavit proměnnou prostředí na adresář, který obsahuje spustitelný soubor.

## <a name="net-core-tool-installation-fails"></a>Instalace nástroje .NET Core se nezdaří

Existuje několik důvodů, proč instalace globálního nebo místního nástroje .NET Core může selhat. Pokud se instalace nástroje nezdaří, zobrazí se zpráva podobná následující:

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

Chcete-li diagnostikovat tyto chyby, NuGet zprávy jsou zobrazeny přímo uživateli, spolu s předchozí zprávy. Zpráva NuGet vám může pomoci identifikovat problém.

### <a name="package-naming-enforcement"></a>Vynucení pojmenování balíčků

Společnost Microsoft změnila pokyny k ID balíčku pro nástroje, což má za následek řadu nástrojů, které nebyly nalezeny s předpokládaným názvem. Nové pokyny je, že všechny nástroje společnosti Microsoft s předponou "Microsoft". Tato předpona je vyhrazena a lze ji použít pouze pro balíčky podepsané autorizovaným certifikátem společnosti Microsoft.

Během přechodu budou mít některé nástroje společnosti Microsoft starou formu ID balíčku, zatímco jiné budou mít nový formulář:

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

Při aktualizaci ID balíčků budete muset změnit na nové ID balíčku, abyste získali nejnovější aktualizace. Balíčky se zjednodušeným názvem nástroje budou zastaralé.

### <a name="preview-releases"></a>Náhled vydání

* Pokoušíte se nainstalovat verzi preview a nepoužili `--version` jste možnost k zadání verze.

Nástroje .NET Core, které jsou ve verzi Preview, musí být zadány s částí názvu, která označuje, že jsou ve verzi Preview. Není nutné zahrnout celý náhled. Za předpokladu, že čísla verzí jsou v očekávaném formátu, můžete použít něco jako v následujícím příkladu:

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a>Balíček není nástroj .NET Core

* Balíček NuGet s tímto názvem byl nalezen, ale nebyl nástrojem .NET Core.

Pokud se pokusíte nainstalovat balíček NuGet, který je běžným balíčkem NuGet a nikoli nástrojem .NET Core, zobrazí se chyba podobná následující:

> NU1212: Neplatná kombinace `<ToolName>`balíčku projektu pro . DotnetToolReference styl projektu může obsahovat pouze odkazy typu DotnetTool.

### <a name="nuget-feed-cant-be-accessed"></a>NuGet krmivo nelze získat přístup

* Požadovaný informační kanál NuGet nelze získat přístup, například z důvodu problému s připojením k Internetu.

Instalace nástroje vyžaduje přístup k nugetový informační kanál, který obsahuje balíček nástrojů. Selže, pokud zdroj není k dispozici. Pomocí souborů můžete `nuget.config`měnit , `nuget.config` požadovat konkrétní soubor nebo určit `--add-source` další informační kanály pomocí přepínače. Ve výchozím nastavení NuGet vyvolá chybu pro všechny zdroje, které nelze připojit. Příznak `--ignore-failed-sources` můžete přeskočit tyto nedosažitelné zdroje.

### <a name="package-id-incorrect"></a>ID balíčku nesprávné

* Chybně jste zadali název nástroje.

Častým důvodem selhání je, že název nástroje není správný. K tomu může dojít z důvodu nesprávného zapsaní nebo proto, že nástroj byl přesunut nebo byl zastaral. Pro nástroje na NuGet.org, jeden způsob, jak zajistit, že máte správný název, je vyhledat nástroj na NuGet.org a zkopírovat příkaz instalace.

## <a name="see-also"></a>Viz také

* [Nástroje .NET Core](global-tools.md)
