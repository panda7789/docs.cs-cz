---
title: Nástroje .NET core rozhraní příkazového řádku (CLI)
description: Přehled funkcí a nástrojů pro .NET Core rozhraní příkazového řádku (CLI).
ms.date: 08/14/2017
ms.custom: seodec18
ms.openlocfilehash: e174867ce06e573fc85579183df0196d8276fb37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647421"
---
# <a name="net-core-command-line-interface-cli-tools"></a>Nástroje .NET core rozhraní příkazového řádku (CLI)

Rozhraní příkazového řádku .NET Core (CLI) je nová sada nástrojů napříč platformami pro vývoj aplikací .NET. Rozhraní příkazového řádku je jako základ, na které chcete získat podrobnější popis nástroje, jako je integrované vývojové prostředí (IDE), editory a orchestrátorů sestavení, můžete rozhraní rest.

## <a name="installation"></a>Instalace

Použijte nativních instalačních programů nebo použít skripty prostředí instalace:

* Nativních instalačních programů se používají především na počítačích pro vývojáře a použití každé podporované platformy nativní nainstalujte mechanismus, například DEB balíčků na Ubuntu nebo MSI svazků na Windows. Tyto instalační programy instalace a konfigurace prostředí k okamžitému použití vývojář, ale vyžadují oprávnění správce na počítači. Můžete zobrazit na pokyny k instalaci v [Průvodce instalací rozhraní .NET Core](https://aka.ms/dotnetcoregs).
* Skripty prostředí se používají především pro nastavení serverů sestavení nebo když chcete nainstalovat nástroje bez oprávnění správce. Nainstalujte skripty neinstalujte požadavky na počítač, který musí ručně doinstalovat. Další informace najdete v tématu [instalaci skriptu referenční téma](dotnet-install-script.md). Informace o tom, jak nastavení rozhraní příkazového řádku na serveru sestavení kontinuální integrace (CI), najdete v části [pomocí .NET Core SDK a nástroje v kontinuální integrace (CI)](using-ci-with-cli.md).

Ve výchozím nastavení nainstaluje rozhraní příkazového řádku (SxS) způsobem vedle sebe, tak více verzemi nástroje rozhraní příkazového řádku můžou existovat společně na jednom počítači. Určení, kterou verzi se používá na počítači, ve kterém je nainstalováno více verzí je vysvětleno podrobněji [ovladač](#driver) oddílu.

## <a name="cli-commands"></a>Příkazy rozhraní příkazového řádku

Ve výchozím nastavení jsou nainstalované následující příkazy:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**Základní příkazy**

* [new](dotnet-new.md)
* [restore](dotnet-restore.md)
* [Sestavení](dotnet-build.md)
* [Publikování](dotnet-publish.md)
* [Spuštění](dotnet-run.md)
* [test](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [pack](dotnet-pack.md)
* [Migrace](dotnet-migrate.md)
* [Vyčistit](dotnet-clean.md)
* [sln](dotnet-sln.md)
* [Pomoc](dotnet-help.md)
* [store](dotnet-store.md)

**Příkazy pro modifikaci projektů**

* [Přidání balíčku](dotnet-add-package.md)
* [Přidat odkaz](dotnet-add-reference.md)
* [Odebrat balíček](dotnet-remove-package.md)
* [Odebrat odkaz](dotnet-remove-reference.md)
* [odkaz na seznam](dotnet-list-reference.md)

**Rozšířené příkazy**

* [odstranění nuget](dotnet-nuget-delete.md)
* [nuget locals](dotnet-nuget-locals.md)
* [nuget push](dotnet-nuget-push.md)
* [msbuild](dotnet-msbuild.md)
* [DotNet instalační skript](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Základní příkazy**

* [new](dotnet-new.md)
* [restore](dotnet-restore.md)
* [Sestavení](dotnet-build.md)
* [Publikování](dotnet-publish.md)
* [Spuštění](dotnet-run.md)
* [test](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [pack](dotnet-pack.md)
* [Migrace](dotnet-migrate.md)
* [Vyčistit](dotnet-clean.md)
* [sln](dotnet-sln.md)

**Příkazy pro modifikaci projektů**

* [Přidání balíčku](dotnet-add-package.md)
* [Přidat odkaz](dotnet-add-reference.md)
* [Odebrat balíček](dotnet-remove-package.md)
* [Odebrat odkaz](dotnet-remove-reference.md)
* [odkaz na seznam](dotnet-list-reference.md)

**Rozšířené příkazy**

* [odstranění nuget](dotnet-nuget-delete.md)
* [nuget locals](dotnet-nuget-locals.md)
* [nuget push](dotnet-nuget-push.md)
* [msbuild](dotnet-msbuild.md)
* [DotNet instalační skript](dotnet-install-script.md)

---

Rozhraní příkazového řádku přijme model rozšiřitelnosti, pomocí kterých můžete zadat další nástroje pro vaše projekty. Další informace najdete v tématu [model rozšíření rozhraní příkazového řádku .NET Core](extensibility.md) tématu.

## <a name="command-structure"></a>Příkaz struktura

Struktura příkazu rozhraní příkazového řádku se skládá z [ovladače ("dotnet")](#driver), [příkazu (nebo "akce")](#command-verb)a případně příkaz [argumenty](#arguments) a [možnosti](#options). Zobrazí tento model většinu operací rozhraní příkazového řádku, jako je vytváření nových konzolovou aplikaci a spuštění z příkazového řádku jako následující příkazy, zobrazit při spuštění z adresáře s názvem *my_app*:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a>Ovladač

Ovladač jmenuje [dotnet](dotnet.md) a má dvě odpovědnosti, buď spuštěný [aplikace závisí na architektuře](../deploying/index.md) nebo spuštění příkazu. 

Spuštění aplikace závisí na architektuře, zadejte aplikace, po ovladače, například `dotnet /path/to/my_app.dll`. Při provádění příkazu ze složky, ve které se nachází aplikaci knihovny DLL, stačí provést `dotnet my_app.dll`. Pokud chcete použít konkrétní verzi modulu .NET Core Runtime, použijte `--fx-version <VERSION>` možnost (najdete v článku [příkaz dotnet](dotnet.md) odkaz).

Když zadáte příkaz k ovladači, `dotnet.exe` zahájí proces spuštění příkazu rozhraní příkazového řádku. Příklad:

```bash
> dotnet build
```

Nejprve ovladač Určuje verzi sady SDK používat. Pokud není žádný ["global.json"](global-json.md), se používá nejnovější verzi sady SDK k dispozici. To může být buď ve verzi preview nebo stabilní verze, v závislosti na tom, co je to nejnovější na počítači.  Jakmile se určí verzi sady SDK, vykoná příkaz.

### <a name="command-verb"></a>Příkaz ("operace")

Příkaz (nebo "akce") je jednoduše příkaz, který provede akci. Například `dotnet build` sestaví váš kód. `dotnet publish` publikuje váš kód. Příkazy jsou implementovány jako konzolovou aplikaci pomocí `dotnet {verb}` konvence.

### <a name="arguments"></a>Arguments

Argumenty, které můžete předat do příkazového řádku jsou argumenty k vyvolání příkazu. Například při spuštění `dotnet publish my_app.csproj`, `my_app.csproj` argument určuje projekt k publikování a je předán `publish` příkazu.

### <a name="options"></a>Možnosti

Možnosti, které můžete předat do příkazového řádku jsou možnosti k vyvolání příkazu. Například při spuštění `dotnet publish --output /build_output`, `--output` možnost a jeho hodnota jsou předány `publish` příkazu.

## <a name="migration-from-projectjson"></a>Migrace z project.json

Pokud jste použili ve verzi Preview 2 nástroje k vytvoření *project.json*-podle projektů, naleznete [dotnet migrate](dotnet-migrate.md) informace o migraci vašeho projektu nástroje MSBuild /*.csproj*pomocí verze nástroje. Pro .NET Core projekty vytvořené před verzí nástroje ve verzi Preview 2, buď ručně aktualizovat projekt následující pokyny v [migrace z DNX na .NET Core CLI (project.json)](../migration/from-dnx.md) a pak použijte `dotnet migrate` nebo přímo upgradovat. vaše projekty.

## <a name="see-also"></a>Viz také:

- [DotNet/CLI úložiště GitHub](https://github.com/dotnet/cli/)
- [Průvodce instalací rozhraní .NET core](https://aka.ms/dotnetcoregs)
