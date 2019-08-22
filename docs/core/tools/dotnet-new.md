---
title: dotnet – nový příkaz
description: Příkaz dotnet New vytvoří nové projekty .NET Core založené na zadané šabloně.
ms.date: 05/06/2019
ms.openlocfilehash: c9e960bab0e28e88b0cc8d431dad3b9f3f00c9c0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660544"
---
# <a name="dotnet-new"></a>dotnet new

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet new`– Vytvoří nový projekt, konfigurační soubor nebo řešení na základě zadané šablony.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

```console
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a>Popis

`dotnet new` Příkaz nabízí pohodlný způsob, jak inicializovat platný projekt .NET Core.

Příkaz volá [modul šablony](https://github.com/dotnet/templating) a vytvoří artefakty na disku na základě zadané šablony a možností.

## <a name="arguments"></a>Arguments

`TEMPLATE`

Šablona, která se má vytvořit při vyvolání příkazu Každá šablona může mít konkrétní možnosti, které můžete předat. Další informace najdete v tématu [Možnosti šablony](#template-options).

Pokud hodnota není přesná shoda na textu v šablonách nebo ve sloupci **short name** , je v těchto dvou sloupcích provedena shoda podřetězce. `TEMPLATE`

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

Příkaz obsahuje výchozí seznam šablon. Použijte `dotnet new -l` k získání seznamu dostupných šablon. Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 2.2.100. Výchozí jazyk pro šablonu se zobrazí v závorkách.

| Šablony                                    | Krátký název        | Jazyk     | Značky                                  |
|----------------------------------------------|-------------------|--------------|---------------------------------------|
| Konzolová aplikace                          | `console`         | [C#], F#, VB | Společná/konzola                        |
| Knihovna tříd                                | `classlib`        | [C#], F#, VB | Společné/knihovny                        |
| Projekt testu jednotek                            | `mstest`          | [C#], F#, VB | Test/MSTest                           |
| Projekt testů NUnit 3                         | `nunit`           | [C#], F#, VB | Test/NUnit                            |
| NUnit 3 položka testu                            | `nunit-test`      | [C#], F#, VB | Test/NUnit                            |
| Projekt testů xUnit                           | `xunit`           | [C#], F#, VB | Test/xUnit                            |
| Stránka Razor                                   | `page`            | [C#]         | Web/ASP.NET                           |
| ViewImports MVC                              | `viewimports`     | [C#]         | Web/ASP.NET                           |
| ViewStart MVC                                | `viewstart`       | [C#]         | Web/ASP.NET                           |
| ASP.NET Core prázdné                           | `web`             | [C#], F#     | Web/prázdné                             |
| ASP.NET Core webová aplikace (model-zobrazení-kontroler) | `mvc`             | [C#], F#     | Web/MVC                               |
| ASP.NET Core webové aplikace                         | `webapp`, `razor` | [C#]         | Web/MVC/Razor Pages                   |
| ASP.NET Core s úhlovým                    | `angular`         | [C#]         | Web/MVC/SPA                           |
| ASP.NET Core s reagují. js                   | `react`           | [C#]         | Web/MVC/SPA                           |
| ASP.NET Core s využitím reagují. js a Redux         | `reactredux`      | [C#]         | Web/MVC/SPA                           |
| Knihovna tříd Razor                          | `razorclasslib`   | [C#]         | Knihovna tříd web/Razor/Library/Razor |
| ASP.NET Core webového rozhraní API                         | `webapi`          | [C#], F#     | Web/WebAPI                            |
| global.json file                             | `globaljson`      |              | Konfigurace                                |
| Konfigurace NuGet                                 | `nugetconfig`     |              | Konfigurace                                |
| Webová konfigurace                                   | `webconfig`       |              | Konfigurace                                |
| Soubor řešení                                | `sln`             |              | Řešení                              |

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

Příkaz obsahuje výchozí seznam šablon. Použijte `dotnet new -l` k získání seznamu dostupných šablon. Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 2.1.300. Výchozí jazyk pro šablonu se zobrazí v závorkách.

| Šablony                                    | Krátký název      | Jazyk     | Značky                                  |
|----------------------------------------------|-----------------|--------------|---------------------------------------|
| Konzolová aplikace                          | `console`       | [C#], F#, VB | Společná/konzola                        |
| Knihovna tříd                                | `classlib`      | [C#], F#, VB | Společné/knihovny                        |
| Projekt testu jednotek                            | `mstest`        | [C#], F#, VB | Test/MSTest                           |
| Projekt testů xUnit                           | `xunit`         | [C#], F#, VB | Test/xUnit                            |
| Stránka Razor                                   | `page`          | [C#]         | Web/ASP.NET                           |
| ViewImports MVC                              | `viewimports`   | [C#]         | Web/ASP.NET                           |
| ViewStart MVC                                | `viewstart`     | [C#]         | Web/ASP.NET                           |
| ASP.NET Core prázdné                           | `web`           | [C#], F#     | Web/prázdné                             |
| ASP.NET Core webová aplikace (model-zobrazení-kontroler) | `mvc`           | [C#], F#     | Web/MVC                               |
| ASP.NET Core webové aplikace                         | `razor`         | [C#]         | Web/MVC/Razor Pages                   |
| ASP.NET Core s úhlovým                    | `angular`       | [C#]         | Web/MVC/SPA                           |
| ASP.NET Core s reagují. js                   | `react`         | [C#]         | Web/MVC/SPA                           |
| ASP.NET Core s využitím reagují. js a Redux         | `reactredux`    | [C#]         | Web/MVC/SPA                           | 
| Knihovna tříd Razor                          | `razorclasslib` | [C#]         | Knihovna tříd web/Razor/Library/Razor |
| ASP.NET Core webového rozhraní API                         | `webapi`        | [C#], F#     | Web/WebAPI                            |
| global.json file                             | `globaljson`    |              | Konfigurace                                |
| Konfigurace NuGet                                 | `nugetconfig`   |              | Konfigurace                                |
| Webová konfigurace                                   | `webconfig`     |              | Konfigurace                                |
| Soubor řešení                                | `sln`           |              | Řešení                              |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

Příkaz obsahuje výchozí seznam šablon. Použijte `dotnet new -l` k získání seznamu dostupných šablon. Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 2.0.0. Výchozí jazyk pro šablonu se zobrazí v závorkách.

| Šablony                                    | Krátký název    | Jazyk     | Značky                |
|----------------------------------------------|---------------|--------------|---------------------|
| Konzolová aplikace                          | `console`     | [C#], F#, VB | Společná/konzola      |
| Knihovna tříd                                | `classlib`    | [C#], F#, VB | Společné/knihovny      |
| Projekt testu jednotek                            | `mstest`      | [C#], F#, VB | Test/MSTest         |
| Projekt testů xUnit                           | `xunit`       | [C#], F#, VB | Test/xUnit          |
| ASP.NET Core prázdné                           | `web`         | [C#], F#     | Web/prázdné           |
| ASP.NET Core webová aplikace (model-zobrazení-kontroler) | `mvc`         | [C#], F#     | Web/MVC             |
| ASP.NET Core webové aplikace                         | `razor`       | [C#]         | Web/MVC/Razor Pages |
| ASP.NET Core s úhlovým                    | `angular`     | [C#]         | Web/MVC/SPA         |
| ASP.NET Core s reagují. js                   | `react`       | [C#]         | Web/MVC/SPA         |
| ASP.NET Core s využitím reagují. js a Redux         | `reactredux`  | [C#]         | Web/MVC/SPA         |
| ASP.NET Core webového rozhraní API                         | `webapi`      | [C#], F#     | Web/WebAPI          |
| global.json file                             | `globaljson`  |              | Konfigurace              |
| Konfigurace NuGet                                 | `nugetconfig` |              | Konfigurace              |
| Webová konfigurace                                   | `webconfig`   |              | Konfigurace              |
| Soubor řešení                                | `sln`         |              | Řešení            |
| Stránka Razor                                   | `page`        |              | Web/ASP.NET         |
| ViewImports MVC                              | `viewimports` |              | Web/ASP.NET         |
| ViewStart MVC                                | `viewstart`   |              | Web/ASP.NET         |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Příkaz obsahuje výchozí seznam šablon. Použijte `dotnet new -all` k získání seznamu dostupných šablon. Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK 1.0.1. Výchozí jazyk pro šablonu se zobrazí v závorkách.

| Šablony            | Krátký název    | Jazyk | Značky           |
|----------------------|---------------|----------|----------------|
| Konzolová aplikace  | `console`     | [C#], F# | Společná/konzola |
| Knihovna tříd        | `classlib`    | [C#], F# | Společné/knihovny |
| Projekt testu jednotek    | `mstest`      | [C#], F# | Test/MSTest    |
| Projekt testů xUnit   | `xunit`       | [C#], F# | Test/xUnit     |
| ASP.NET Core prázdné   | `web`         | [C#]     | Web/prázdné      |
| ASP.NET Core webové aplikace | `mvc`         | [C#], F# | Web/MVC        |
| ASP.NET Core webového rozhraní API | `webapi`      | [C#]     | Web/WebAPI     |
| Konfigurace NuGet         | `nugetconfig` |          | Konfigurace         |
| Webová konfigurace           | `webconfig`   |          | Konfigurace         |
| Soubor řešení        | `sln`         |          | Řešení       |

---

## <a name="options"></a>Možnosti

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

`--dry-run`

Zobrazí souhrnné informace o tom, co se stane, pokud by došlo ke spuštění daného příkazu, pokud by to vedlo k vytvoření šablony.

`--force`

Vynutí vygenerování obsahu i v případě, že změní existující soubory. To je nutné v případě, že výstupní adresář již obsahuje projekt.

`-h|--help`

Vytiskne nápovědu k příkazu. Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.

`-i|--install <PATH|NUGET_ID>`

Nainstaluje zdroj nebo balíček šablony z `PATH` nebo `NUGET_ID` poskytnutého. Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`. Ve výchozím nastavení `dotnet new` se \* předá verze, která představuje poslední stabilní verzi balíčku. Podívejte se na příklad v části [Příklady](#examples) .

Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).

`-l|--list`

Vypíše seznam šablon, které obsahují zadaný název. Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář. Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.

`-lang|--language {C#|F#|VB}`

Jazyk šablony, která se má vytvořit Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ). Pro některé šablony není platná.

> [!NOTE]
> Některá prostředí jsou interpretována `#` jako speciální znak. V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Název vytvořeného výstupu. Pokud název nezadáte, použije se název aktuálního adresáře.

`--nuget-source`

Určuje zdroj NuGet, který se použije při instalaci.

`-o|--output <OUTPUT_DIRECTORY>`

Umístění, do kterého se má vygenerovaný výstup umístit. Výchozí je aktuální adresář.

`--type`

Filtruje šablony založené na dostupných typech. Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".

`-u|--uninstall <PATH|NUGET_ID>`

Odinstaluje zdrojový nebo Template Pack na `PATH` nebo `NUGET_ID` poskytnutý. Při vyloučení `<PATH|NUGET_ID>` hodnoty se zobrazí všechny aktuálně nainstalované sady šablon a jejich přidružené šablony.

> [!NOTE]
> Chcete-li odinstalovat šablonu pomocí `PATH`nástroje, je nutné plně kvalifikovat cestu. Například *C:/Users/\<User >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.
> Kromě toho Nezahrnovat koncové koncové lomítko adresáře na cestu k šabloně.

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`--force`

Vynutí vygenerování obsahu i v případě, že změní existující soubory. To je nutné v případě, že výstupní adresář již obsahuje projekt.

`-h|--help`

Vytiskne nápovědu k příkazu. Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.

`-i|--install <PATH|NUGET_ID>`

Nainstaluje zdroj nebo balíček šablony z `PATH` nebo `NUGET_ID` poskytnutého. Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`. Ve výchozím nastavení `dotnet new` se \* předá verze, která představuje poslední stabilní verzi balíčku. Podívejte se na příklad v části [Příklady](#examples) .

Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).

`-l|--list`

Vypíše seznam šablon, které obsahují zadaný název. Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář. Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.

`-lang|--language {C#|F#|VB}`

Jazyk šablony, která se má vytvořit Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ). Pro některé šablony není platná.

> [!NOTE]
> Některá prostředí jsou interpretována `#` jako speciální znak. V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Název vytvořeného výstupu. Pokud název nezadáte, použije se název aktuálního adresáře.

`--nuget-source`

Určuje zdroj NuGet, který se použije při instalaci.

`-o|--output <OUTPUT_DIRECTORY>`

Umístění, do kterého se má vygenerovaný výstup umístit. Výchozí je aktuální adresář.

`--type`

Filtruje šablony založené na dostupných typech. Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".

`-u|--uninstall <PATH|NUGET_ID>`

Odinstaluje zdrojový nebo Template Pack na `PATH` nebo `NUGET_ID` poskytnutý.

> [!NOTE]
> Chcete-li odinstalovat šablonu pomocí `PATH`nástroje, je nutné plně kvalifikovat cestu. Například *C:/Users/\<User >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.
> Kromě toho Nezahrnovat koncové koncové lomítko adresáře na cestu k šabloně.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`--force`

Vynutí vygenerování obsahu i v případě, že změní existující soubory. To je nutné v případě, že výstupní adresář již obsahuje projekt.

`-h|--help`

Vytiskne nápovědu k příkazu. Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.

`-i|--install <PATH|NUGET_ID>`

Nainstaluje zdroj nebo balíček šablony z `PATH` nebo `NUGET_ID` poskytnutého. Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`. Ve výchozím nastavení `dotnet new` se \* předá verze, která představuje poslední stabilní verzi balíčku. Podívejte se na příklad v části [Příklady](#examples) .

Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).

`-l|--list`

Vypíše seznam šablon, které obsahují zadaný název. Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář. Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.

`-lang|--language {C#|F#|VB}`

Jazyk šablony, která se má vytvořit Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ). Pro některé šablony není platná.

> [!NOTE]
> Některá prostředí jsou interpretována `#` jako speciální znak. V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Název vytvořeného výstupu. Pokud název nezadáte, použije se název aktuálního adresáře.

`-o|--output <OUTPUT_DIRECTORY>`

Umístění, do kterého se má vygenerovaný výstup umístit. Výchozí je aktuální adresář.

`--type`

Filtruje šablony založené na dostupných typech. Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".

`-u|--uninstall <PATH|NUGET_ID>`

Odinstaluje zdrojový nebo Template Pack na `PATH` nebo `NUGET_ID` poskytnutý.

> [!NOTE]
> Chcete-li odinstalovat šablonu pomocí zdroje `PATH`, je nutné cestu plně kvalifikovat. Například *C:/Users/\<User >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude. Kromě toho Nezahrnovat koncové koncové lomítko adresáře na cestu k šabloně.
> 
> Pokud nemůžete určit `PATH` argument nebo `NUGET_ID` , který je potřeba k odinstalaci šablony, `dotnet new --uninstall` při spuštění bez argumentu se zobrazí seznam všech nainstalovaných šablon a argument, který je potřeba k jejich odinstalování.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-all|--show-all`

Zobrazí všechny šablony pro konkrétní typ projektu při spuštění v kontextu `dotnet new` samotného příkazu. Při spuštění v souvislosti s konkrétní šablonou, `dotnet new web -all`jako je například, `-all` je interpretován jako příznak vytvoření vynucení. To je nutné v případě, že výstupní adresář již obsahuje projekt.

`-h|--help`

Vytiskne nápovědu k příkazu. Dá se vyvolat pro `dotnet new` samotný příkaz nebo pro libovolnou šablonu, `dotnet new mvc --help`jako je například.

`-l|--list`

Vypíše seznam šablon, které obsahují zadaný název. Pokud je vyvoláno pro `dotnet new` příkaz, zobrazí seznam možných šablon dostupných pro daný adresář. Například Pokud adresář již obsahuje projekt, nezobrazuje seznam všech šablon projektu.

`-lang|--language {C#|F#}`

Jazyk šablony, která se má vytvořit Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ). Pro některé šablony není platná.

> [!NOTE]
> Některá prostředí jsou interpretována `#` jako speciální znak. V těchto případech je nutné uvést hodnotu parametru jazyka, například `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Název vytvořeného výstupu. Pokud název nezadáte, použije se název aktuálního adresáře.

`-o|--output <OUTPUT_DIRECTORY>`

Umístění, do kterého se má vygenerovaný výstup umístit. Výchozí je aktuální adresář.

---

## <a name="template-options"></a>Možnosti šablony

Každá šablona projektu může mít k dispozici další možnosti. Základní šablony mají následující další možnosti:

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2.2](#tab/netcore22)

**stromu**

`--langVersion <VERSION_NUMBER>`-Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu. Použijte `--langVersion 7.3` například k použití C# 7,3. Nepodporuje se pro F#.

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**Úhlová, reakce, reactredux**

`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

`--no-https`-Projekt nevyžaduje protokol HTTPS. Tato možnost se vztahuje jenom `IndividualAuth` na `OrganizationalAuth` to, jestli se nepoužívají.

**razorclasslib**

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**classlib**

`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Hodnoty: `netcoreapp2.2` pro vytvoření knihovny tříd .NET Core nebo `netstandard2.0` pro vytvoření knihovny tříd .NET Standard. Výchozí hodnota je `netstandard2.0`.

`--langVersion <VERSION_NUMBER>`-Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu. Použijte `--langVersion 7.3` například k použití C# 7,3. Nepodporuje se pro F#.

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**MSTest, xUnit**

`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**nunit**

`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Výchozí hodnota je `netcoreapp2.1`.

`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**Page**

`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód. Výchozí hodnota je `MyApp.Namespace`.

`-np|--no-pagemodel`-Vytvoří stránku bez PageModel.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód. Výchozí hodnota je `MyApp.Namespace`.

**web**

`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

`--no-https`-Projekt nevyžaduje protokol HTTPS. Tato možnost se vztahuje jenom `IndividualAuth` na `OrganizationalAuth` to, jestli se nepoužívají.

**mvc, webapp**

`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít. Možné hodnoty jsou:

- `None`-Bez ověřování (výchozí).
- `Individual`-Individuální ověřování.
- `IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.
- `SingleOrg`– Ověřování organizace pro jednoho tenanta.
- `MultiOrg`– Ověřování organizace pro více tenantů.
- `Windows`– Ověřování systému Windows.

`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení. Použijte s `IndividualB2C` ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt. Použijte s `IndividualB2C` ověřováním.

`-rp|--reset-password-policy-id <ID>`– Resetování ID zásad hesla pro tento projekt. Použijte s `IndividualB2C` ověřováním.

`-ep|--edit-profile-policy-id <ID>`– Upravte ID zásad profilu pro tento projekt. Použijte s `IndividualB2C` ověřováním.

`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení. Použijte s `SingleOrg` ověřováním nebo `MultiOrg` . Výchozí hodnota je `https://login.microsoftonline.com/`.

`--client-id <ID>`– ID klienta pro tento projekt. Použijte s `IndividualB2C`ověřováním, `MultiOrg` `SingleOrg`nebo. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>`– Doména pro tenanta adresáře. Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` . Výchozí hodnota je `qualified.domain.name`.

`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit. Použijte s `SingleOrg` ověřováním. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>`– Cesta požadavku v základní cestě identifikátoru URI přesměrování. Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` . Výchozí hodnota je `/signin-oidc`.

`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři. Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.

`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .

`--no-https`-Projekt nevyžaduje protokol HTTPS. `app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`. `Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`

`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite. Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít. Možné hodnoty jsou:

- `None`-Bez ověřování (výchozí).
- `IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.
- `SingleOrg`– Ověřování organizace pro jednoho tenanta.
- `Windows`– Ověřování systému Windows.

`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení. Použijte s `IndividualB2C` ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt. Použijte s `IndividualB2C` ověřováním.

`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení. Použijte s `SingleOrg` ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/`.

`--client-id <ID>`– ID klienta pro tento projekt. Použijte s `IndividualB2C` ověřováním nebo `SingleOrg` . Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>`– Doména pro tenanta adresáře. Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` . Výchozí hodnota je `qualified.domain.name`.

`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit. Použijte s `SingleOrg` ověřováním. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři. Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.

`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .

`--no-https`-Projekt nevyžaduje protokol HTTPS. `app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`. `Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`

`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite. Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**globaljson**

`--sdk-version <VERSION_NUMBER>`-Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

**Konzola, úhlová, reakce, reactredux, razorclasslib**

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**classlib**

`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Hodnoty: `netcoreapp2.1` pro vytvoření knihovny tříd .NET Core nebo `netstandard2.0` pro vytvoření knihovny tříd .NET Standard. Výchozí hodnota je `netstandard2.0`.

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**MSTest, xUnit**

`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**globaljson**

`--sdk-version <VERSION_NUMBER>`-Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .

**web**

`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

`--no-https`-Projekt nevyžaduje protokol HTTPS. Tato možnost se vztahuje jenom `IndividualAuth` na `OrganizationalAuth` to, jestli se nepoužívají.

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít. Možné hodnoty jsou:

- `None`-Bez ověřování (výchozí).
- `IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.
- `SingleOrg`– Ověřování organizace pro jednoho tenanta.
- `Windows`– Ověřování systému Windows.

`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení. Použijte s `IndividualB2C` ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt. Použijte s `IndividualB2C` ověřováním.

`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení. Použijte s `SingleOrg` ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/`.

`--client-id <ID>`– ID klienta pro tento projekt. Použijte s `IndividualB2C` ověřováním nebo `SingleOrg` . Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>`– Doména pro tenanta adresáře. Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` . Výchozí hodnota je `qualified.domain.name`.

`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit. Použijte s `SingleOrg` ověřováním. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři. Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.

`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .

`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite. Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

`--no-https`-Projekt nevyžaduje protokol HTTPS. `app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`. `Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`

**MVC, Razor**

`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít. Možné hodnoty jsou:

- `None`-Bez ověřování (výchozí).
- `Individual`-Individuální ověřování.
- `IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.
- `SingleOrg`– Ověřování organizace pro jednoho tenanta.
- `MultiOrg`– Ověřování organizace pro více tenantů.
- `Windows`– Ověřování systému Windows.

`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení. Použijte s `IndividualB2C` ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt. Použijte s `IndividualB2C` ověřováním.

`-rp|--reset-password-policy-id <ID>`– Resetování ID zásad hesla pro tento projekt. Použijte s `IndividualB2C` ověřováním.

`-ep|--edit-profile-policy-id <ID>`– Upravte ID zásad profilu pro tento projekt. Použijte s `IndividualB2C` ověřováním.

`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení. Použijte s `SingleOrg` ověřováním nebo `MultiOrg` . Výchozí hodnota je `https://login.microsoftonline.com/`.

`--client-id <ID>`– ID klienta pro tento projekt. Použijte s `IndividualB2C`ověřováním, `MultiOrg` `SingleOrg`nebo. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>`– Doména pro tenanta adresáře. Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` . Výchozí hodnota je `qualified.domain.name`.

`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit. Použijte s `SingleOrg` ověřováním. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>`– Cesta požadavku v základní cestě identifikátoru URI přesměrování. Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` . Výchozí hodnota je `/signin-oidc`.

`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři. Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.

`--exclude-launch-settings`– Vylučte z vygenerované šablony *launchSettings. JSON* .

`--use-browserlink`-Zahrnuje BrowserLink do projektu.

`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite. Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

`--no-https`-Projekt nevyžaduje protokol HTTPS. `app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`. `Individual`Tato možnost platí pouze `IndividualB2C` `MultiOrg` v případě, že se nepoužívají, nebo.`SingleOrg`

**Page**

`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód. Výchozí hodnota je `MyApp.Namespace`.

`-np|--no-pagemodel`-Vytvoří stránku bez PageModel.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód. Výchozí hodnota je `MyApp.Namespace`.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

**Konzola, úhlová, reakce, reactredux**

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**classlib**

`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Hodnoty: `netcoreapp2.0` pro vytvoření knihovny tříd .NET Core nebo `netstandard2.0` pro vytvoření knihovny tříd .NET Standard. Výchozí hodnota je `netstandard2.0`.

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**MSTest, xUnit**

`-p|--enable-pack`– Povolí balení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**globaljson**

`--sdk-version <VERSION_NUMBER>`-Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .

**web**

`--use-launch-settings`-Zahrnuje *launchSettings. JSON* ve výstupu vygenerované šablony.

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít. Možné hodnoty jsou:

- `None`-Bez ověřování (výchozí).
- `IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.
- `SingleOrg`– Ověřování organizace pro jednoho tenanta.
- `Windows`– Ověřování systému Windows.

`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení. Použijte s `IndividualB2C` ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt. Použijte s `IndividualB2C` ověřováním.

`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení. Použijte s `SingleOrg` ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/`.

`--client-id <ID>`– ID klienta pro tento projekt. Použijte s `IndividualB2C` ověřováním nebo `SingleOrg` . Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>`– Doména pro tenanta adresáře. Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` . Výchozí hodnota je `qualified.domain.name`.

`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit. Použijte s `SingleOrg` ověřováním. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři. Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.

`--use-launch-settings`-Zahrnuje *launchSettings. JSON* ve výstupu vygenerované šablony.

`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite. Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**MVC, Razor**

`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít. Možné hodnoty jsou:

- `None`-Bez ověřování (výchozí).
- `Individual`-Individuální ověřování.
- `IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.
- `SingleOrg`– Ověřování organizace pro jednoho tenanta.
- `MultiOrg`– Ověřování organizace pro více tenantů.
- `Windows`– Ověřování systému Windows.

`--aad-b2c-instance <INSTANCE>`– Instance Azure Active Directory B2C pro připojení. Použijte s `IndividualB2C` ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>`– ID zásad přihlášení a registrace pro tento projekt. Použijte s `IndividualB2C` ověřováním.

`-rp|--reset-password-policy-id <ID>`– Resetování ID zásad hesla pro tento projekt. Použijte s `IndividualB2C` ověřováním.

`-ep|--edit-profile-policy-id <ID>`– Upravte ID zásad profilu pro tento projekt. Použijte s `IndividualB2C` ověřováním.

`--aad-instance <INSTANCE>`– Instance Azure Active Directory pro připojení. Použijte s `SingleOrg` ověřováním nebo `MultiOrg` . Výchozí hodnota je `https://login.microsoftonline.com/`.

`--client-id <ID>`– ID klienta pro tento projekt. Použijte s `IndividualB2C`ověřováním, `MultiOrg` `SingleOrg`nebo. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>`– Doména pro tenanta adresáře. Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` . Výchozí hodnota je `qualified.domain.name`.

`--tenant-id <ID>`– ID TenantId adresáře, ke kterému se má připojit. Použijte s `SingleOrg` ověřováním. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>`– Cesta požadavku v základní cestě identifikátoru URI přesměrování. Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` . Výchozí hodnota je `/signin-oidc`.

`-r|--org-read-access`– Povolí této aplikaci přístup pro čtení k adresáři. Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.

`--use-launch-settings`-Zahrnuje *launchSettings. JSON* ve výstupu vygenerované šablony.

`--use-browserlink`-Zahrnuje BrowserLink do projektu.

`-uld|--use-local-db`-Určuje LocalDB by měl být použit místo SQLite. Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.

`--no-restore`– Během vytváření projektu neprovede implicitní obnovení.

**Page**

`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód. Výchozí hodnota je `MyApp.Namespace`.

`-np|--no-pagemodel`-Vytvoří stránku bez PageModel.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>`– Obor názvů pro vygenerovaný kód. Výchozí hodnota je `MyApp.Namespace`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Konzola, xUnit, MSTest, web, WebApi**

`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`. Výchozí hodnota je `netcoreapp1.0`.

**classlib**

`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` na `netstandard1.6`. Výchozí hodnota je `netstandard1.4`.

**mvc**

`-f|--framework <FRAMEWORK>`-Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`. Výchozí hodnota je `netcoreapp1.0`.

`-au|--auth <AUTHENTICATION_TYPE>`– Typ ověřování, které se má použít. Hodnoty: `None` nebo `Individual`. Výchozí hodnota je `None`.

`-uld|--use-local-db`– Určuje, jestli se místo SQLite použije LocalDB. Hodnoty: `true` nebo `false`. Výchozí hodnota je `false`.

---

## <a name="examples"></a>Příklady

Vytvořte projekt C# konzolové aplikace zadáním názvu šablony:

`dotnet new "Console Application"`

Vytvořte projekt F# konzolové aplikace v aktuálním adresáři:

`dotnet new console -lang F#`

Vytvořit projekt knihovny tříd .NET Standard v zadaném adresáři (k dispozici pouze s .NET Core SDK 2,0 nebo novějšími verzemi):

`dotnet new classlib -lang VB -o MyLibrary`

Vytvoří nový projekt ASP.NET Core C# MVC v aktuálním adresáři bez ověřování:

`dotnet new mvc -au None`

Vytvořit nový projekt xUnit:

`dotnet new xunit`

Vypíše všechny šablony, které jsou k dispozici pro MVC:

`dotnet new mvc -l`

Vypíše všechny šablony, které odpovídají podřetězci *My* . Nebyla nalezena žádná přesná shoda, takže porovnávání dílčích řetězců se shoduje se sloupci krátkého názvu a názvu.

`dotnet new we -l`

Došlo k pokusu o vyvolání šablony, která odpovídá *NG*. Pokud nelze určit jednu shodu, Seznamte se se šablonami, které jsou částečné shody.

`dotnet new ng`

2,0 nainstalujte šablony aplikace s jednou stránkou pro ASP.NET Core (možnost příkazového řádku, která je dostupná jenom pro .NET Core SDK 1,1 a novější verze):

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

Vytvoří *Global. JSON* v aktuálním adresáři nastavení verze sady SDK na 2.0.0 (k dispozici pouze s .NET Core SDK 2,0 nebo novějšími verzemi):

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a>Viz také:

- [Vlastní šablony pro dotnet New](custom-templates.md)
- [Vytvoření vlastní šablony pro dotnet new](../tutorials/create-custom-template.md)
- [dotnet/dotnet-Template-Samples – úložiště GitHub](https://github.com/dotnet/dotnet-template-samples)
- [Dostupné šablony pro dotnet New](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
