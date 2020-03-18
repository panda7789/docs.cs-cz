---
title: Nástroje .NET Core
description: Jak nainstalovat, používat, aktualizovat a odebírat nástroje .NET Core. Zahrnuje globální nástroje, nástroje pro cestu nástrojů a místní nástroje.
author: KathleenDollard
ms.date: 02/12/2020
ms.openlocfilehash: 2f0101c6385c41eda49bcb2458428c1f14552617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847781"
---
# <a name="how-to-manage-net-core-tools"></a>Správa nástrojů .NET Core

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

Nástroj .NET Core je speciální balíček NuGet, který obsahuje konzolovou aplikaci. Nástroj lze do počítače nainstalovat následujícími způsoby:

* Jako globální nástroj.

  Binární soubory nástrojů jsou nainstalovány ve výchozím adresáři, který je přidán do proměnné prostředí PATH. Nástroj můžete vyvolat z libovolného adresáře v počítači bez určení jeho umístění. Jedna verze nástroje se používá pro všechny adresáře na stroji.

* Jako globální nástroj ve vlastním umístění (označovaný také jako nástroj cesty nástroje).

  Binární soubory nástrojů jsou nainstalovány v zadaném umístění. Nástroj můžete vyvolat z instalačního adresáře nebo poskytnutím názvu příkazu nebo přidáním adresáře do proměnné prostředí PATH. Jedna verze nástroje se používá pro všechny adresáře na stroji.

* Jako místní nástroj (platí pro .NET Core SDK 3.0 a novější).

  Binární soubory nástrojů jsou nainstalovány ve výchozím adresáři. Nástroj vyvoláte z instalačního adresáře nebo některého z jeho podadresářů. Různé adresáře mohou používat různé verze stejného nástroje.
  
  Rozhraní .NET CLI používá soubory manifestu ke sledování, které nástroje jsou nainstalovány jako místní do adresáře. Když je soubor manifestu uložen v kořenovém adresáři úložiště zdrojového kódu, může přispěvatel naklonovat úložiště a vyvolat jeden příkaz ROZHRANÍ PŘÍKAZU .NET Core, který nainstaluje všechny nástroje uvedené v souborech manifestu.

> [!IMPORTANT]
> Nástroje .NET Core jsou spuštěny v plném vztahu důvěryhodnosti. Neinstalujte nástroj .NET Core, pokud autorovi nedůvěřujete.

## <a name="find-a-tool"></a>Nalezení nástroje

V současné době rozhraní .NET Core nemá funkci vyhledávání nástrojů. Zde je několik způsobů, jak najít nástroje:

* Podívejte se na seznam nástrojů v úložišti GitHub [natemcmaster/dotnet-tools.](https://github.com/natemcmaster/dotnet-tools)
* Pomocí [nástroje ToolGet](https://www.toolget.net/) vyhledejte nástroje rozhraní .NET.
* Podívejte se na zdrojový kód nástrojů vytvořených týmem ASP.NET Core v [adresáři Tools úložiště GitHub dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).
* Informace o diagnostických nástrojích naleznete v [diagnostických nástrojích .NET Core dotnet](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).
* Prohledejte web [NuGet.](https://www.nuget.org) Web NuGet však ještě nemá funkci, která umožňuje vyhledávat pouze balíčky nástrojů.

## <a name="check-the-author-and-statistics"></a>Podívejte se na autora a statistiky

Vzhledem k tomu, že nástroje .NET Core běží v plné důvěryhodnosti a globální nástroje jsou přidány do proměnné prostředí PATH, mohou být velmi výkonné. Nestahujte nástroje od lidí, kterým nedůvěřujete.

Pokud je nástroj hostován na NuGet, můžete zkontrolovat autora a statistiky hledáním nástroje.

## <a name="install-a-global-tool"></a>Instalace globálního nástroje

Chcete-li nainstalovat nástroj jako globální `-g` `--global` nástroj, použijte možnost nebo [instalaci nástroje dotnet](dotnet-tool-install.md), jak je znázorněno v následujícím příkladu:

```dotnetcli
dotnet tool install -g dotnetsay
```

Výstup zobrazuje příkaz použitý k vyvolání nainstalovaného nástroje a nainstalované verze, podobně jako v následujícím příkladu:

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

Výchozí umístění binárních souborů nástroje závisí na operačním systému:

| Operační systém          | Cesta                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Toto umístění je přidáno do cesty uživatele při prvním spuštění sady SDK, takže globální nástroje lze vyvolat z libovolného adresáře bez určení umístění nástroje.

Přístup k nástrojům je specifický pro uživatele, nikoli globální počítač. Globální nástroj je k dispozici pouze uživateli, který nástroj nainstaloval.

### <a name="install-a-global-tool-in-a-custom-location"></a>Instalace globálního nástroje do vlastního umístění

Chcete-li nainstalovat nástroj jako globální nástroj do `--tool-path` vlastního umístění, použijte možnost [instalace nástroje dotnet](dotnet-tool-install.md), jak je znázorněno v následujících příkladech.

Ve Windows:

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

Na Linuxu nebo macOS:

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

Sada .NET Core SDK nepřidá toto umístění automaticky do proměnné prostředí PATH. [Chcete-li vyvolat nástroj cesty nástroje](#invoke-a-tool-path-tool), musíte se ujistit, že příkaz je k dispozici pomocí jedné z následujících metod:

* Přidejte instalační adresář do proměnné prostředí PATH.
* Určete úplnou cestu k nástroji, když ho vyvoláte.
* Vyvolat nástroj z instalačního adresáře.

## <a name="install-a-local-tool"></a>Instalace místního nástroje

**Platí pro .NET Core 3.0 SDK a novější.**

Chcete-li nainstalovat nástroj pouze pro místní přístup (pro aktuální adresář a podadresáře), musí být přidán do souboru manifestu nástroje. Chcete-li vytvořit soubor manifestu nástroje, spusťte `dotnet new tool-manifest` příkaz:

```dotnetcli
dotnet new tool-manifest
```

Tento příkaz vytvoří soubor manifestu s názvem *dotnet-tools.json* pod adresářem *.config.* Chcete-li do souboru manifestu přidat místní nástroj, použijte příkaz `--global` instalace `--tool-path` [nástroje dotnet](dotnet-tool-install.md) a **vynechejte** volby a, jak je znázorněno v následujícím příkladu:

```dotnetcli
dotnet tool install dotnetsay
```

Výstup příkazu ukazuje, ve kterém souboru manifestu se nově nainstalovaný nástroj nachází, podobně jako v následujícím příkladu:

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

Následující příklad ukazuje soubor manifestu se dvěma nainstalovanými místními nástroji:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    },
    "dotnetsay": {
      "version": "2.1.3",
      "commands": [
        "dotnetsay"
      ]
    }
  }
}
```

Obvykle přidáte místní nástroj do kořenového adresáře úložiště. Po vrácení souboru manifestu do úložiště se vývojáři, kteří z úložiště získají kód, získají nejnovější soubor manifestu. Chcete-li nainstalovat všechny nástroje uvedené v souboru manifestu, `dotnet tool restore` spustí příkaz:

```dotnetcli
dotnet tool restore
```

Výstup označuje, které nástroje byly obnoveny:

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a>Instalace konkrétní verze nástroje

Chcete-li nainstalovat předběžnou verzi nebo určitou verzi nástroje, zadejte číslo verze pomocí `--version` této možnosti, jak je znázorněno v následujícím příkladu:

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a>Použití nástroje

Příkaz, který použijete k vyvolání nástroje, se může lišit od názvu balíčku, který nainstalujete. Chcete-li zobrazit všechny nástroje aktuálně nainstalované v počítači pro aktuálního uživatele, použijte příkaz [seznam nástrojů dotnet:](dotnet-tool-list.md)

```dotnetcli
dotnet tool list
```

Výstup zobrazuje verzi a příkaz každého nástroje, podobně jako v následujícím příkladu:

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

Jak je znázorněno v tomto příkladu, seznam zobrazuje místní nástroje. Chcete-li zobrazit globální `--global` nástroje, použijte tuto možnost a `--tool-path` nástroje cesty nástroje, použijte ji.

### <a name="invoke-a-global-tool"></a>Vyvolání globálního nástroje

Pro globální nástroje použijte příkaz nástroje sám o sobě. Například pokud je `dotnetsay` příkaz `dotnet-doc`nebo , to je to, co používáte k vyvolání příkazu:

```console
dotnetsay
dotnet-doc
```

Pokud příkaz začíná předponou `dotnet-`, alternativním způsobem vyvolání nástroje `dotnet` je použití příkazu a vynechání předpony příkazu nástroje. Pokud je `dotnet-doc`například příkaz , následující příkaz vyvolá nástroj:

```dotnetcli
dotnet doc
```

V následujícím scénáři však nelze `dotnet` použít příkaz k vyvolání globálního nástroje:

* Globální nástroj a místní nástroj mají stejný `dotnet-`příkaz předponou .
* Chcete vyvolat globální nástroj z adresáře, který je v oboru pro místní nástroj.

V tomto `dotnet doc` scénáři a `dotnet dotnet-doc` vyvolat místní nástroj. Chcete-li vyvolat globální nástroj, použijte příkaz sám o sobě:

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a>Vyvolání nástroje cesty nástroje

Chcete-li vyvolat globální nástroj, `tool-path` který je nainstalován pomocí této možnosti, ujistěte se, že příkaz je k dispozici, jak je vysvětleno [dříve v tomto článku](#install-a-global-tool-in-a-custom-location).

### <a name="invoke-a-local-tool"></a>Vyvolání místního nástroje

Chcete-li vyvolat místní nástroj, `dotnet` musíte použít příkaz z instalačního adresáře. Můžete použít dlouhý formulář`dotnet tool run <COMMAND_NAME>`( ) nebo`dotnet <COMMAND_NAME>`krátký formulář ( ), jak je znázorněno v následujících příkladech:

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

Pokud je příkaz předponou , `dotnet-`můžete při vyvolání nástroje zahrnout nebo vynechat předponu. Pokud je `dotnet-doc`například příkaz , některý z následujících příkladů vyvolá místní nástroj:

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a>Aktualizace nástroje

Aktualizace nástroje zahrnuje odinstalaci a přeinstalaci pomocí nejnovější stabilní verze. Chcete-li nástroj aktualizovat, použijte příkaz [aktualizace nástroje dotnet](dotnet-tool-update.md) se stejnou možností, kterou jste použili k instalaci nástroje:

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

Pro místní nástroj sada SDK vyhledá první soubor manifestu, který obsahuje ID balíčku, vyhledáním v aktuálním adresáři a nadřazených adresářích. Pokud není žádné takové ID balíčku v libovolném souboru manifestu, sada SDK přidá novou položku do nejbližšího souboru manifestu.

## <a name="uninstall-a-tool"></a>Odinstalace nástroje

Odstraňte nástroj pomocí příkazu [odinstalovat nástroj dotnet](dotnet-tool-uninstall.md) se stejnou možností, kterou jste použili k instalaci nástroje:

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path<packagename>
dotnet tool uninstall <packagename>
```

Pro místní nástroj sada SDK vyhledá první soubor manifestu, který obsahuje ID balíčku, vyhledáním v aktuálním adresáři a nadřazených adresářích.

## <a name="get-help-and-troubleshoot"></a>Získání nápovědy a řešení potíží

Chcete-li získat `dotnet tool` seznam dostupných příkazů, zadejte následující příkaz:

```dotnetcli
dotnet tool --help
```

Chcete-li získat pokyny k použití nástroje, zadejte jeden z následujících příkazů nebo se podívejte na web nástroje:

```dotnetcli
<command> --help
dotnet <command> --help
```

Pokud se nepodaří nainstalovat nebo spustit nástroj, [přečtěte si článek Poradce při potížích s používáním nástroje .NET Core](troubleshoot-usage-issues.md).

## <a name="see-also"></a>Viz také

- [Kurz: Vytvoření nástroje .NET Core pomocí rozhraní CLI jádra .NET](global-tools-how-to-create.md)
- [Kurz: Instalace a použití globálního nástroje .NET Core pomocí rozhraní CLI jádra .NET](global-tools-how-to-use.md)
- [Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET](local-tools-how-to-use.md)
