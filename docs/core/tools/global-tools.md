---
title: .NET Core Global Tools
description: Přehled o co jsou globální nástroje .NET Core a .NET Core CLI příkazy pro ně k dispozici.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 3bbf1e7953482dc07f05570443cf640a9fab6258
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647747"
---
# <a name="net-core-global-tools-overview"></a>Přehled globální nástroje .NET core

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

Globální nástroje .NET Core je speciální balíčku NuGet, který obsahuje konzolovou aplikaci. Globální nástroj může být nainstalován na svém počítači na výchozím umístění, které je zahrnutý v proměnné prostředí PATH nebo vlastního umístění.

Pokud chcete použít globální nástroje .NET Core:

* Najdete informace o nástroji (obvykle webu nebo stránku na Githubu).
* Zkontrolujte Autor a statistické údaje ve Domovská stránka pro kanál (obvykle NuGet.org).
* Nainstalujte nástroj.
* Volání nástroje.
* Aktualizujte nástroj.
* Odinstalujte nástroj.

> [!IMPORTANT]
> Globální nástroje .NET core se zobrazí na vaší cestě a spustit v režimu plné důvěryhodnosti. Neinstalujte globální nástroje .NET Core, pokud důvěřujete autorovi.

## <a name="find-a-net-core-global-tool"></a>Najít globální nástroje .NET Core

V současné době není k dispozici funkce Hledat globální nástroje v rozhraní příkazového řádku .NET Core (CLI).

Globální nástroje .NET Core můžete najít na [NuGet](https://www.nuget.org). Nicméně NuGet ještě neumožňuje vyhledávání speciálně pro globální nástroje .NET Core.

Můžete také zjistit v příspěvcích na blogu nebo v doporučení v nástroji [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) úložiště GitHub.

Můžete také zobrazit zdrojový kód pro globální nástroje vytvořil tým ASP.NET na [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) úložiště GitHub.

## <a name="check-the-author-and-statistics"></a>Zkontrolujte Autor a statistiky

Protože globální nástroje .NET Core spustit v režimu plné důvěryhodnosti a se obvykle instaluje na vaší cestě, můžou být velmi výkonné. Nestahovat nástroje od lidí, kterým nedůvěřujete.

Pokud je hostitelem nástroje NuGet, můžete zkontrolovat tak, že nástroj Autor a statistiky.

## <a name="install-a-global-tool"></a>Nainstalujte nástroj Global

Instalovat nástroj globální, použijte [instalace nástrojů dotnet](dotnet-tool-install.md) rozhraní příkazového řádku .NET Core. Následující příklad ukazuje, jak nainstalovat globální nástroj ve výchozím umístění:

```console
dotnet tool install -g dotnetsay
```

Pokud nástroj nejde nainstalovat, zobrazí se chybové zprávy. Zkontrolujte, že se kontroluje informační kanály, které jste očekávali.

Pokud se snažíte nainstalovat předběžné verzi nebo konkrétní verzi nástroje, můžete zadat číslo verze v následujícím formátu:

```console
dotnet tool install -g <package-name> --version <version-number>
```

Pokud je instalace úspěšná, zobrazí se zpráva zobrazující příkazu používaný k volání nástroje a verze nainstalovaná, podobně jako v následujícím příkladu:

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

Globální nástroje mohou být nainstalovány ve výchozím adresáři nebo v konkrétním umístění. Výchozí adresáře jsou:

| Operační systém          | Cesta                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Tato místa jsou přidány do cesty uživatele při prvním spuštění sady SDK, tak že nainstalované nástroje pro globální mohou být volány.

Mějte na paměti, že globální nástroje jsou specifické pro uživatele, počítače nejsou globální. Jsou specifické pro uživatele znamená, že nemůžete nainstalovat globální nástroj, který je k dispozici pro všechny uživatele počítače. Nástroj je k dispozici pouze pro každý uživatelský profil ve kterém byl nainstalován nástroj.

Globální nástroje můžete také nainstalovat v konkrétní adresář. Při instalaci v konkrétní adresář, uživatel musí zajistit příkaz je k dispozici, včetně tohoto adresáře v cestě, voláním příkazu se do adresáře určeného, nebo zavolání nástroj v rámci zadaného adresáře.
Rozhraní příkazového řádku .NET Core nepodporuje toto umístění v tomto případě automaticky přidat do proměnné prostředí PATH.

## <a name="use-the-tool"></a>Pomocí nástroje

Po instalaci nástroje zavoláte ho pomocí jeho příkazu. Všimněte si, že příkaz nemusí být stejný jako název balíčku.

Pokud je příkaz `dotnetsay`, při volání s:

```console
dotnetsay
```

Pokud autor nástroj chtěli nástroj, který se zobrazí v kontextu `dotnet` řádku, může mít napsat ji tak, pojmenujte ji `dotnet <command>`, jako například:

```console
dotnet doc
```

Zjistíte, jaké nástroje jsou součástí nainstalovaným balíčkem globální nástroj uvedením nainstalované balíčky pomocí [seznam nástrojů dotnet](dotnet-tool-list.md) příkazu.

Můžete také vyhledat pokyny k použití na webu nástroje nebo zadáním jednoho z následujících příkazů:

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a>Co může dojít k chybě

Globální nástroje jsou [aplikace závisí na architektuře](../deploying/index.md#framework-dependent-deployments-fdd), což znamená, že spoléhají na .NET Core runtime na vašem počítači nainstalovaný. Pokud se nenajde očekávanou dobu běhu, sledují běžných pravidel vpřed modulu runtime .NET Core, jako:

* Aplikace provede dopředné obnovení nejvyšší oprava vydanou verzi zadaný hlavní verze a podverze.
* Pokud není žádný odpovídající modul runtime s odpovídající hlavní a vedlejší číslo verze, použije se další vyšší dílčí verze.
* Posunutí vpřed nedojde mezi ve verzi preview verze modulu runtime nebo verze preview a verze. Díky tomu se globální nástroje vytvořené pomocí verze preview musí být znovu sestavit a znovu publikovat autorem a přeinstalovat.
* Další problémy mohou nastat u globální nástroje vytvořené v .NET Core 2.1 Preview 1. Další informace najdete v tématu [.NET Core 2.1 Preview 2 známé problémy v sadě](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).

Pokud aplikaci nejde najít odpovídající modul runtime, selže-li a nahlásí chybu.

Jiný problém, který může dojít, je, že globální nástroj, který byl vytvořen starší verzi Preview se možná nespustí pomocí aktuálně nainstalované moduly runtime .NET Core. Můžete zobrazit, které moduly runtime jsou nainstalovány v počítači pomocí následujícího příkazu:

```console
dotnet --list-runtimes
```

Obraťte se na autora nástroj globální a podívejte se, pokud můžete znovu zkompilovat a znovu publikovat své nástroje balíček NuGet s aktualizovaným číslem verze. Až aktualizováni balíček na webu NuGet můžete aktualizovat kopii.

Rozhraní příkazového řádku .NET Core se pokusí přidat výchozí umístění pro proměnné prostředí PATH na jeho prvního použití. Existuje ale několik scénářů, kde umístění pravděpodobně být přidány do cesty automaticky, jako například:

* Pokud jste nastavili `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` proměnné prostředí.
* V systému macOS, pokud jste nainstalovali aplikaci pomocí sady .NET Core SDK *. tar.gz* souborů a nikoli *.pkg*.
* V systému Linux budete muset upravit soubor prostředí shell abyste nakonfigurovali CESTU.

## <a name="other-cli-commands"></a>Další příkazy rozhraní příkazového řádku

.NET Core SDK obsahuje další příkazy, které podporují globální nástroje .NET Core. Použít některý z `dotnet tool` příkazů s jedním z následujících možností:

* `--global` nebo `-g` Určuje, že příkaz je globální nástroje lze použít na úrovni uživatele.
* `--tool-path` Určuje vlastní umístění pro globální nástroje.

Chcete-li zjistit, které příkazy jsou k dispozici pro globální nástroje:

```console
dotnet tool --help
```

Aktualizuje se nástroj globální zahrnuje odinstalace a opětovné instalace s nejnovější stabilní verzi. Chcete-li aktualizovat globální nástroj, použijte [aktualizace nástrojů dotnet](dotnet-tool-update.md) příkaz:

```console
dotnet tool update -g <packagename>
```

Odebrat globální nástroj pomocí [dotnet odinstalační](dotnet-tool-uninstall.md):

```console
dotnet tool uninstall -g <packagename>
```

Chcete-li zobrazit všechny nástroje, globální aktuálně nainstalované na počítači, spolu s jejich verzi a příkazů, použijte [seznam nástrojů dotnet](dotnet-tool-list.md) příkaz:

```console
dotnet tool list -g
```