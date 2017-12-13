---
title: ".NET core rozhraní příkazového řádku (CLI) nástroje"
description: "Přehled funkcí a nástrojů .NET Core rozhraní příkazového řádku (CLI)."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 0f43f569cdb8b9e4be68b61ba7b5cc4686fdb871
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2017
---
# <a name="net-core-command-line-interface-cli-tools"></a>.NET core nástrojů rozhraní příkazového řádku (CLI)

Rozhraní .NET Core příkazového řádku (CLI) je nová sada nástrojů a platformy pro vývoj aplikací .NET. Rozhraní příkazového řádku je foundation, při které vyšší úrovně nástroje, jako je, přesuňte integrované vývojové prostředí (integrovaného vývojového prostředí), editory a orchestrators sestavení.

## <a name="installation"></a>Instalace

Buď použijte nativní instalační programy nebo použít skripty prostředí instalace:

* Nativní instalační programy se primárně používají na počítačích pro vývojáře a použití každé podporované platformy nativní nainstalujte mechanismus, například bázi DEB balíčků na Ubuntu nebo MSI sady v systému Windows. Tyto instalační programy instalace a konfigurace prostředí pro okamžitou používá vývojář ale vyžadují oprávnění správce na počítači. Můžete zobrazit v pokynech k instalaci v [Průvodce instalací .NET Core](https://aka.ms/dotnetcoregs).
* Skripty prostředí se primárně používají pro nastavení servery sestavení nebo pokud chcete nainstalovat nástroje bez oprávnění správce. Nainstalujte skripty neinstalujte požadavky na počítač, který musí být nainstalován ručně. Další informace najdete v tématu [instalaci skriptu referenční téma](dotnet-install-script.md). Informace o tom, jak nastavit rozhraní příkazového řádku na vašem serveru sestavení průběžnou integraci (CI) najdete v tématu [pomocí rozhraní .NET Core SDK a nástrojů v nepřetržité integrace konfigurace](using-ci-with-cli.md).

Ve výchozím nastavení nainstaluje rozhraní příkazového řádku (SxS) způsobem vedle sebe, tak mohou existovat vedle sebe více verzí nástrojů příkazového řádku na jednom počítači. Určení, které verze se má použít na počítači, kde je nainstalováno více verzí je vysvětlené podrobněji v [ovladač](#driver) části.

## <a name="cli-commands"></a>Rozhraní příkazového řádku

Ve výchozím nastavení instalují se následující příkazy:

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

**Základní příkazy**

* [new](dotnet-new.md)
* [obnovení](dotnet-restore.md)
* [sestavení](dotnet-build.md)
* [publikování](dotnet-publish.md)
* [Spustit](dotnet-run.md)
* [Test](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [pack](dotnet-pack.md)
* [migrace](dotnet-migrate.md)
* [Vyčištění](dotnet-clean.md)
* [SLN –](dotnet-sln.md)
* [Pomoc](dotnet-help.md)
* [úložiště](dotnet-store.md)

**Příkazy Úpravy projektu**

* [Přidání balíčku](dotnet-add-package.md)
* [Přidání odkazu](dotnet-add-reference.md)
* [Odebrání balíčku](dotnet-remove-package.md)
* [Odebrat odkaz](dotnet-remove-reference.md)
* [odkaz na seznamu](dotnet-list-reference.md)

**Pokročilé příkazy**

* [odstranění nuget](dotnet-nuget-delete.md)
* [místní hodnoty – nuget](dotnet-nuget-locals.md)
* [nabízená nuget](dotnet-nuget-push.md)
* [nástroje MSBuild](dotnet-msbuild.md)
* [Instalační skript pro DotNet.](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

**Základní příkazy**

* [new](dotnet-new.md)
* [obnovení](dotnet-restore.md)
* [sestavení](dotnet-build.md)
* [publikování](dotnet-publish.md)
* [Spustit](dotnet-run.md)
* [Test](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [pack](dotnet-pack.md)
* [migrace](dotnet-migrate.md)
* [Vyčištění](dotnet-clean.md)
* [SLN –](dotnet-sln.md)

**Příkazy Úpravy projektu**

* [Přidání balíčku](dotnet-add-package.md)
* [Přidání odkazu](dotnet-add-reference.md)
* [Odebrání balíčku](dotnet-remove-package.md)
* [Odebrat odkaz](dotnet-remove-reference.md)
* [odkaz na seznamu](dotnet-list-reference.md)

**Pokročilé příkazy**

* [odstranění nuget](dotnet-nuget-delete.md)
* [místní hodnoty – nuget](dotnet-nuget-locals.md)
* [nabízená nuget](dotnet-nuget-push.md)
* [nástroje MSBuild](dotnet-msbuild.md)
* [Instalační skript pro DotNet.](dotnet-install-script.md)

---

Rozhraní příkazového řádku přijme model rozšiřitelnosti, které vám umožní určit dalších nástrojů pro projekty. Další informace najdete v tématu [model rozšiřitelnosti .NET Core rozhraní příkazového řádku](extensibility.md) tématu.

## <a name="command-structure"></a>Příkaz struktura

Struktura rozhraní příkazového řádku příkaz se skládá z [ovladače ("dotnet")](#driver), [příkazu (nebo "akce")](#command-verb)a případně příkaz [argumenty](#arguments) a [možnosti](#options). Zobrazí tento vzor většinu operací rozhraní příkazového řádku, jako je například vytváření novou konzolovou aplikaci a spuštění z příkazového řádku jako následující příkazy, zobrazit, když je proveden z adresáře, s názvem *my_app*:

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```


---

### <a name="driver"></a>Ovladače

Ovladač jmenuje [dotnet](dotnet.md) a má dva odpovědnosti, buď spuštěná [framework závislé aplikace](../deploying/index.md) nebo spuštěním příkazu. Pouze `dotnet` se používá bez příkaz se, pokud se používá ke spuštění aplikace.

Chcete spustit framework závislé aplikace, zadejte aplikaci po ovladače, například `dotnet /path/to/my_app.dll`. Při provádění příkazu ze složky, které se nachází aplikace DLL, stačí spustit `dotnet my_app.dll`.

Když zadáte příkaz, který má ovladače, `dotnet.exe` spustí se proces spuštění příkazu rozhraní příkazového řádku. Nejprve ovladač Určuje verzi sady SDK k použití. Pokud verze není zadané v příkazu Možnosti, používá ovladač na nejnovější dostupnou verzi. K určení verze než poslední instalované verzi, použijte `--fx-version <VERSION>` možnost (najdete v článku [dotnet. příkaz](dotnet.md) odkaz). Jakmile je určena verze sady SDK, ovladač provede příkaz.

### <a name="command-verb"></a>Příkaz ("akce")

Příkaz (nebo "akce") je jednoduše příkaz, který provádí akce. Například `dotnet build` sestavení vašeho kódu. `dotnet publish`publikuje vašeho kódu. Příkazy jsou implementované jako aplikace konzoly pomocí `dotnet {verb}` konvence.

### <a name="arguments"></a>Arguments

Argumenty, které můžete předat na příkazovém řádku jsou argumenty pro příkaz vyvolat. Například při spuštění `dotnet publish my_app.csproj`, `my_app.csproj` argument určuje projekt, který má publikovat a je předána `publish` příkaz.

### <a name="options"></a>Možnosti

Možnosti, které můžete předat na příkazovém řádku jsou možnosti k vyvolání příkazu. Například při spuštění `dotnet publish --output /build_output`, `--output` možnost a jeho hodnota se budou předávat `publish` příkaz. 

## <a name="migration-from-projectjson"></a>Migrace ze souboru project.json

Pokud jste použili Preview 2 nástrojů k vytvoření *project.json*– na základě projekty, najdete [dotnet migrovat](dotnet-migrate.md) tématu informace o migraci projektu nástroje MSBuild /*.csproj*pro použití s verzí nástroje. Pro .NET Core projekty vytvořené před vydáním nástrojů Preview 2 buď ručně aktualizovat následující pokyny v projektu [migrace z DNX na .NET Core rozhraní příkazového řádku (project.json)](../migration/from-dnx.md) a pak použijte `dotnet migrate` nebo přímo upgradovat. projekty.

## <a name="see-also"></a>Viz také

 [DotNet nebo rozhraní příkazového řádku úložiště GitHub](https://github.com/dotnet/cli/)  
 [Průvodce instalací .NET core](https://aka.ms/dotnetcoregs)  
