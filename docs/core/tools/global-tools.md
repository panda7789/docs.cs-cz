---
title: " Nástroje .NET Core"
description: Jak nainstalovat, používat, aktualizovat a odebrat nástroje .NET Core Zahrnuje globální nástroje, nástroje nástroje pro cestu a místní nástroje.
author: KathleenDollard
ms.date: 02/12/2020
ms.openlocfilehash: 75bdedcbc3ebe9c23477795415076d160ab9a642
ms.sourcegitcommit: 7499bdb428d63ed0e19e97f54d3d576c41598659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2020
ms.locfileid: "87455726"
---
# <a name="how-to-manage-net-core-tools"></a>Správa nástrojů .NET Core

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

Nástroj .NET Core je speciální balíček NuGet, který obsahuje konzolovou aplikaci. Nástroj lze nainstalovat do počítače následujícími způsoby:

* Jako globální nástroj.

  Binární soubory nástroje jsou nainstalovány ve výchozím adresáři, který je přidán do proměnné prostředí PATH. Nástroj můžete vyvolat z libovolného adresáře v počítači bez zadání jeho umístění. Pro všechny adresáře v počítači se používá jedna verze nástroje.

* Jako globální nástroj ve vlastním umístění (označované také jako nástroj pro cestu nástroje).

  Binární soubory nástroje jsou nainstalovány v umístění, které zadáte. Nástroj můžete vyvolat z instalačního adresáře nebo zadáním adresáře s názvem příkazu nebo přidáním adresáře do proměnné prostředí PATH. Pro všechny adresáře v počítači se používá jedna verze nástroje.

* Jako místní nástroj (platí pro .NET Core SDK 3,0 a novější).

  Binární soubory nástroje jsou nainstalovány ve výchozím adresáři. Nástroj byste vyvolali z instalačního adresáře nebo kteréhokoli z jeho podadresářů. Různé adresáře mohou používat různé verze nástroje.
  
  Rozhraní .NET CLI používá soubory manifestu k udržení přehledu o tom, které nástroje jsou nainstalovány jako místní do adresáře. Když je soubor manifestu uložen v kořenovém adresáři úložiště zdrojového kódu, může Přispěvatel klonovat úložiště a vyvolat jeden .NET Core CLI příkaz, který nainstaluje všechny nástroje, které jsou uvedeny v souborech manifestu.

> [!IMPORTANT]
> Nástroje .NET Core běží v úplném vztahu důvěryhodnosti. Neinstalujte nástroj .NET Core, pokud nedůvěřujete autorovi.

## <a name="find-a-tool"></a>Najít nástroj

V současné době .NET Core nemá funkci pro hledání v nástroji. Tady je několik způsobů, jak najít nástroje:

* Prohledejte web [NuGet](https://www.nuget.org) pomocí filtru typu balíčku .NET nástroje. Další informace najdete v tématu [vyhledání a výběr balíčků](/nuget/consume-packages/finding-and-choosing-packages).
* Podívejte se na seznam nástrojů v úložišti GitHub [natemcmaster/dotnet-Tools](https://github.com/natemcmaster/dotnet-tools) .
* Pomocí [ToolGet](https://www.toolget.net/) můžete vyhledat nástroje .NET.
* Podívejte se na zdrojový kód pro nástroje vytvořené týmem ASP.NET Core v [adresáři Tools úložiště GitHubu pro dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).
* Seznamte se s diagnostickými nástroji na [diagnostických nástrojích rozhraní .NET Core dotnet](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).

## <a name="check-the-author-and-statistics"></a>Kontrolovat autora a statistiky

Vzhledem k tomu, že nástroje .NET Core běží v úplném vztahu důvěryhodnosti a globální nástroje se přidávají do proměnné prostředí PATH, můžou být velmi výkonné. Nestahujte nástroje od lidí, kterým nedůvěřujete.

Pokud je nástroj hostovaný na NuGet, můžete si ho vyhledat pomocí hledání tohoto nástroje.

## <a name="install-a-global-tool"></a>Instalace globálního nástroje

Chcete-li nainstalovat nástroj jako globální nástroj, použijte `-g` možnost nebo pro `--global` [instalaci nástroje dotnet](dotnet-tool-install.md), jak je znázorněno v následujícím příkladu:

```dotnetcli
dotnet tool install -g dotnetsay
```

Výstup ukazuje příkaz použitý k vyvolání nástroje a nainstalovanou verzi, podobně jako v následujícím příkladu:

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

Výchozí umístění binárních souborů nástroje závisí na operačním systému:

| Operační systém          | Cesta                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Toto umístění se přidá do cesty uživatele při prvním spuštění sady SDK, takže globální nástroje lze vyvolat z libovolného adresáře bez určení umístění nástroje.

Přístup k nástroji je specifický pro uživatele, ne jako globální počítač. Globální nástroj je k dispozici pouze pro uživatele, který nástroj nainstaloval.

### <a name="install-a-global-tool-in-a-custom-location"></a>Instalace globálního nástroje ve vlastním umístění

Chcete-li nainstalovat nástroj jako globální nástroj ve vlastním umístění, použijte `--tool-path` možnost [Instalace nástroje dotnet](dotnet-tool-install.md), jak je znázorněno v následujících příkladech.

Ve Windows:

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

V systému Linux nebo macOS:

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

.NET Core SDK nepřidá toto umístění automaticky do proměnné prostředí PATH. Chcete [-li vyvolat Nástroj pro cestu nástroje](#invoke-a-tool-path-tool), je nutné zajistit, aby byl příkaz k dispozici pomocí jedné z následujících metod:

* Přidejte instalační adresář do proměnné prostředí PATH.
* Zadejte úplnou cestu k nástroji, když ji vyvoláte.
* Vyvolejte nástroj v instalačním adresáři.

## <a name="install-a-local-tool"></a>Instalace místního nástroje

**Platí pro .NET Core 3,0 SDK a novější.**

Chcete-li nainstalovat nástroj pouze pro místní přístup (pro aktuální adresář a podadresáře), je nutné jej přidat do souboru manifestu nástroje. Chcete-li vytvořit soubor manifestu nástroje, spusťte `dotnet new tool-manifest` příkaz:

```dotnetcli
dotnet new tool-manifest
```

Tento příkaz vytvoří soubor manifestu s názvem *dotnet-tools.jsv* adresáři *. config* . Chcete-li přidat místní nástroj do souboru manifestu, použijte příkaz pro [instalaci nástroje dotnet](dotnet-tool-install.md) a **vynechejte** `--global` `--tool-path` Možnosti a, jak je znázorněno v následujícím příkladu:

```dotnetcli
dotnet tool install dotnetsay
```

Výstup příkazu ukazuje, ve kterém souboru manifestu je nově nainstalovaný nástroj, podobně jako v následujícím příkladu:

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

Místní nástroj se obvykle přidává do kořenového adresáře úložiště. Až vrátíte se změnami soubor manifestu do úložiště, vývojáři, kteří si zaregistrují kód z úložiště, získají nejnovější soubor manifestu. Chcete-li nainstalovat všechny nástroje, které jsou uvedeny v souboru manifestu, spusťte `dotnet tool restore` příkaz:

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

Chcete-li nainstalovat předběžnou verzi nástroje nebo konkrétní verzi nástroje, zadejte číslo verze pomocí `--version` Možnosti, jak je znázorněno v následujícím příkladu:

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a>Použití nástroje

Příkaz, který použijete k vyvolání nástroje, se může lišit od názvu balíčku, který nainstalujete. Chcete-li zobrazit všechny nástroje, které jsou aktuálně nainstalovány v počítači pro aktuálního uživatele, použijte příkaz [seznam nástrojů dotnet](dotnet-tool-list.md) :

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

Jak je znázorněno v tomto příkladu, v seznamu se zobrazí místní nástroje. Chcete-li zobrazit globální nástroje, použijte `--global` možnost a k zobrazení nástrojů cest k nástrojům použijte `--tool-path` možnost.

### <a name="invoke-a-global-tool"></a>Vyvolání globálního nástroje

U globálních nástrojů použijte samotný příkaz nástroje. Například pokud je příkaz nebo, to je to, `dotnetsay` `dotnet-doc` co používáte k vyvolání příkazu:

```console
dotnetsay
dotnet-doc
```

Pokud příkaz začíná předponou `dotnet-` , alternativní způsob, jak nástroj vyvolat, je použít `dotnet` příkaz a vynechat prefix příkazu nástroje. Například pokud je příkaz `dotnet-doc` , následující příkaz vyvolá nástroj:

```dotnetcli
dotnet doc
```

V následujícím scénáři ale nemůžete použít `dotnet` příkaz k vyvolání globálního nástroje:

* Globální nástroj a místní nástroj mají stejný příkaz jako s předponou `dotnet-` .
* Chcete vyvolat globální nástroj z adresáře, který je v oboru pro místní nástroj.

V tomto scénáři `dotnet doc` a `dotnet dotnet-doc` vyvolat místní nástroj. K vyvolání globálního nástroje použijte samotný příkaz:

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a>Vyvolání nástroje pro cestu k nástroji

Chcete-li vyvolat globální nástroj, který je nainstalován pomocí `tool-path` Možnosti, ujistěte se, že je příkaz k dispozici, jak je vysvětleno [výše v tomto článku](#install-a-global-tool-in-a-custom-location).

### <a name="invoke-a-local-tool"></a>Vyvolání místního nástroje

Chcete-li vyvolat místní nástroj, je nutné použít `dotnet` příkaz v instalačním adresáři. Můžete použít dlouhý tvar ( `dotnet tool run <COMMAND_NAME>` ) nebo krátký tvar ( `dotnet <COMMAND_NAME>` ), jak je znázorněno v následujících příkladech:

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

Pokud je příkaz `dotnet-` předponou, můžete při vyvolání nástroje použít nebo vynechat předponu. Například pokud je příkaz `dotnet-doc` , některý z následujících příkladů vyvolá místní nástroj:

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a>Aktualizace nástroje

Aktualizace nástroje zahrnuje odinstalaci a opětovnou instalaci s nejnovější stabilní verzí. Pokud chcete nástroj aktualizovat, použijte příkaz [dotnet nástroje Update](dotnet-tool-update.md) se stejnou možností, jakou jste použili k instalaci nástroje:

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

V případě místního nástroje vyhledá sada SDK první soubor manifestu, který obsahuje ID balíčku, a to tak, že hledá v aktuálním adresáři a v nadřazených adresářích. Pokud v žádném souboru manifestu není žádné takové ID balíčku, sada SDK přidá novou položku do nejbližšího souboru manifestu.

## <a name="uninstall-a-tool"></a>Odinstalace nástroje

Odeberte nástroj pomocí příkazu pro [odinstalaci nástroje dotnet](dotnet-tool-uninstall.md) se stejnou možností, jakou jste použili k instalaci nástroje:

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path <packagename>
dotnet tool uninstall <packagename>
```

V případě místního nástroje vyhledá sada SDK první soubor manifestu, který obsahuje ID balíčku, a to tak, že hledá v aktuálním adresáři a v nadřazených adresářích.

## <a name="get-help-and-troubleshoot"></a>Získat nápovědu a řešit potíže

Seznam dostupných příkazů zobrazíte `dotnet tool` zadáním následujícího příkazu:

```dotnetcli
dotnet tool --help
```

Pokud chcete získat pokyny k používání nástrojů, zadejte jeden z následujících příkazů nebo si přečtěte web tohoto nástroje:

```dotnetcli
<command> --help
dotnet <command> --help
```

Pokud se nemůžete nainstalovat nebo spustit nástroj, přečtěte si téma řešení potíží s [používáním nástrojů .NET Core](troubleshoot-usage-issues.md).

## <a name="see-also"></a>Viz také

- [Kurz: Vytvoření nástroje .NET Core pomocí .NET Core CLI](global-tools-how-to-create.md)
- [Kurz: instalace a použití globálního nástroje .NET Core pomocí .NET Core CLI](global-tools-how-to-use.md)
- [Kurz: instalace a použití místního nástroje .NET Core pomocí .NET Core CLI](local-tools-how-to-use.md)
