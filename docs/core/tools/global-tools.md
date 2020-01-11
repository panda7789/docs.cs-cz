---
title: Globální nástroje .NET Core
description: Přehled toho, jaké globální nástroje .NET Core jsou a jaké jsou .NET Core CLI příkazy, které jsou pro ně k dispozici.
author: KathleenDollard
ms.date: 05/29/2018
ms.openlocfilehash: 0df3c1b615adfeaaf41542dc8252a8f14f49f6f9
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899869"
---
# <a name="net-core-global-tools-overview"></a>Přehled globálních nástrojů .NET Core

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

Globální nástroj .NET Core je speciální balíček NuGet, který obsahuje konzolovou aplikaci. Globální nástroj lze nainstalovat do počítače ve výchozím umístění, které je součástí proměnné prostředí PATH nebo ve vlastním umístění.

Pokud chcete použít globální nástroj .NET Core:

* Vyhledejte informace o nástroji (obvykle stránka webu nebo GitHub).
* Podívejte se na údaje o autorovi a statistice v domovském kanálu (obvykle NuGet.org).
* Nainstalujte nástroj.
* Zavolejte nástroj.
* Aktualizujte nástroj.
* Odinstalujte nástroj.

> [!IMPORTANT]
> Globální nástroje .NET Core se zobrazí ve vaší cestě a spustí se v úplném vztahu důvěryhodnosti. Neinstalujte globální nástroje .NET Core, pokud nedůvěřujete autorovi.

## <a name="find-a-net-core-global-tool"></a>Najít globální nástroj .NET Core

V současné době není v rozhraní příkazového řádku (CLI) .NET Core k dispozici funkce pro vyhledávání globálních nástrojů. Níže jsou uvedená doporučení pro hledání nástrojů:

* Globální nástroje .NET Core najdete na [NuGet](https://www.nuget.org). NuGet ale ještě neumožňuje vyhledávat konkrétně globální nástroje .NET Core.
* Doporučení k nástrojům můžete najít v blogovém příspěvku nebo v úložišti GitHubu [natemcmaster/dotnet-Tools](https://github.com/natemcmaster/dotnet-tools) .
* Zdrojový kód pro globální nástroje vytvořené týmem ASP.NET můžete zobrazit v úložišti GitHub [/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools) .
* Informace o diagnostických nástrojích najdete v [části .NET Core dotnet – globální nástroje diagnostiky](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).

## <a name="check-the-author-and-statistics"></a>Kontrolovat autora a statistiky

Vzhledem k tomu, že globální nástroje .NET Core běží v úplném vztahu důvěryhodnosti a jsou všeobecně nainstalované v cestě, můžou být velmi výkonné. Nestahujte nástroje od lidí, kterým nedůvěřujete.

Pokud je nástroj hostovaný na NuGet, můžete si ho vyhledat pomocí hledání tohoto nástroje.

## <a name="install-a-global-tool"></a>Instalace globálního nástroje

K instalaci globálního nástroje použijte příkaz [dotnet nástroje install](dotnet-tool-install.md) .NET Core CLI. Následující příklad ukazuje, jak nainstalovat globální nástroj ve výchozím umístění:

```dotnetcli
dotnet tool install -g dotnetsay
```

Pokud nástroj není možné nainstalovat, zobrazí se chybové zprávy. Ověřte, zda jsou kontrolovány informační kanály, které jste očekávali.

Pokud se pokoušíte nainstalovat předběžnou verzi nebo konkrétní verzi nástroje, můžete číslo verze zadat v následujícím formátu:

```dotnetcli
dotnet tool install -g <package-name> --version <version-number>
```

Pokud je instalace úspěšná, zobrazí se zpráva s příkazem použitým pro volání nástroje a nainstalované verze, podobně jako v následujícím příkladu:

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

Globální nástroje mohou být nainstalovány ve výchozím adresáři nebo v určitém umístění. Výchozí adresáře jsou:

| OS          | Cesta                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Tato umístění jsou přidána do cesty uživatele při prvním spuštění sady SDK, takže je možné nainstalovanou sadu globálních nástrojů volat přímo.

Všimněte si, že globální nástroje jsou specifické pro uživatele, ne jako globální počítač. To znamená, že nemůžete nainstalovat globální nástroj, který je k dispozici pro všechny uživatele počítače. Nástroj je k dispozici pouze pro každý profil uživatele, ve kterém byl nástroj nainstalován.

Globální nástroje je také možné nainstalovat do konkrétního adresáře. Při instalaci do konkrétního adresáře musí uživatel ověřit, zda je příkaz k dispozici, zahrnutím tohoto adresáře do cesty, voláním příkazu se zadaným adresářem nebo voláním nástroje ze zadaného adresáře.
V takovém případě .NET Core CLI nepřidá toto umístění automaticky do proměnné prostředí PATH.

## <a name="use-the-tool"></a>Použití nástroje

Po instalaci nástroje jej můžete zavolat pomocí jeho příkazu. Všimněte si, že tento příkaz nemůže být stejný jako název balíčku.

Pokud je příkaz `dotnetsay`, zavolejte ho pomocí:

```console
dotnetsay
```

Pokud autor nástroje chtěl zobrazit nástroj v kontextu `dotnet` výzvy, mohl by jej napsat způsobem, který ho zavolá jako `dotnet <command>`, například:

```dotnetcli
dotnet doc
```

To, které nástroje jsou součástí nainstalovaného globálního balíčku nástroje, můžete najít tak, že zobrazíte nainstalované balíčky pomocí příkazu pro [Výpis seznamu nástrojů dotnet](dotnet-tool-list.md) .

Pokyny k použití můžete vyhledat také na webu nástroje nebo zadáním jednoho z následujících příkazů:

```console
<command> --help
dotnet <command> --help
```

## <a name="other-cli-commands"></a>Další příkazy rozhraní příkazového řádku

.NET Core SDK obsahuje další příkazy, které podporují globální nástroje .NET Core. Použijte kterýkoli z `dotnet tool` příkazů s jednou z následujících možností:

* `--global` nebo `-g` určuje, že se příkaz vztahuje na globální nástroje pro uživatele.
* `--tool-path` určuje vlastní umístění pro globální nástroje.

Zjistit, které příkazy jsou k dispozici pro globální nástroje:

```dotnetcli
dotnet tool --help
```

Aktualizace globálního nástroje zahrnuje odinstalaci a opětovnou instalaci s nejnovější stabilní verzí. Pokud chcete aktualizovat globální nástroj, použijte příkaz [dotnet nástroje Update](dotnet-tool-update.md) :

```dotnetcli
dotnet tool update -g <packagename>
```

Odeberte globální nástroj pomocí [odinstalace nástroje dotnet](dotnet-tool-uninstall.md):

```dotnetcli
dotnet tool uninstall -g <packagename>
```

Chcete-li zobrazit všechny globální nástroje, které jsou aktuálně nainstalovány v počítači, spolu s jejich verzí a příkazy, použijte příkaz pro [seznam nástrojů dotnet](dotnet-tool-list.md) :

```dotnetcli
dotnet tool list -g
```

## <a name="see-also"></a>Viz také:

* [Řešení potíží s používáním nástrojů .NET Core](troubleshoot-usage-issues.md)
