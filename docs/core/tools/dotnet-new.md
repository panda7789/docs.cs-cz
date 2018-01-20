---
title: "nový příkaz DotNet - .NET Core rozhraní příkazového řádku"
description: "Nový příkaz dotnet vytvoří nové projekty .NET Core na základě zadané šablony."
keywords: "DotNet nové rozhraní příkazového řádku, rozhraní příkazového řádku příkaz .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.workload: dotnetcore
ms.openlocfilehash: cf65dc80f135badcb1580726a12a9ae9d94ae3d7
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/20/2018
---
# <a name="dotnet-new"></a>nové DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet new`-Vytvoří nový projekt, konfigurační soubor nebo řešení v závislosti na určené šablony.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a>Popis

`dotnet new` Příkaz nabízí pohodlný způsob, jak inicializovat platný projekt .NET Core. 

Příkaz volání [modulu šablon](https://github.com/dotnet/templating) vytvořit artefakty na disku na základě určené šablony a možnosti.

## <a name="arguments"></a>Arguments

`TEMPLATE`

Šablona pro vytvoření instance při vyvolání příkazu. Každá šablona může mít specifické možnosti, které lze předat. Další informace najdete v tématu [možnosti šablony](#template-options).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Příkaz obsahuje seznam výchozích šablon. Použití `dotnet new -l` získat seznam dostupných šablon. V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core 2.0 SDK. Výchozí jazyk pro šablonu se zobrazí v závorkách.

|Popis šablony                          | Název šablony | Jazyky     |
|----------------------------------------------|---------------|---------------|
| Konzolová aplikace                          | `console`     | [C#], F#, VB  |
| Knihovna tříd                                | `classlib`    | [C#], F#, VB  |
| Projektu testování částí                            | `mstest`      | [C#], F#, VB  |
| xUnit testovacího projektu                           | `xunit`       | [C#], F#, VB  |
| ASP.NET Core prázdný                           | `web`         | [C#], F #      |
| Webové aplikace ASP.NET Core (Model-View-Controller) | `mvc`         | [C#], F #      |
| Webové aplikace ASP.NET Core                         | `razor`       | [C#]          |
| ASP.NET Core s úhlová                    | `angular`     | [C#]          |
| ASP.NET Core s React.js                   | `react`       | [C#]          |
| ASP.NET Core s React.js a – obnovení         | `reactredux`  | [C#]          |
| Jádro ASP.NET Web API                         | `webapi`      | [C#], F #      |
| global.json file                             | `globaljson`  |               |
| Konfigurace Nuget                                 | `nugetconfig` |               |
| Webové konfigurace                                   | `webconfig`   |               |
| Soubor řešení                                | `sln`         |               |
| Stránky Razor                                   | `page`        |               |
| MVC/ViewImports                              | `viewimports` |               |
| MVC ViewStart                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

Příkaz obsahuje seznam výchozích šablon. Použití `dotnet new -all` získat seznam dostupných šablon. V následující tabulce jsou uvedeny šablony, které jsou předinstalované .NET Core 1.x SDK. Výchozí jazyk pro šablonu se zobrazí v závorkách.

|Popis šablony  | Název šablony | Jazyky |
|----------------------|---------------|-----------|
| Konzolová aplikace  | `console`     | [C#], F #  |
| Knihovna tříd        | `classlib`    | [C#], F #  |
| Projektu testování částí    | `mstest`      | [C#], F #  |
| xUnit testovacího projektu   | `xunit`       | [C#], F #  |
| ASP.NET Core prázdný   | `web`         | [C#]      |
| Webové aplikace ASP.NET Core | `mvc`         | [C#], F #  |
| Jádro ASP.NET Web API | `webapi`      | [C#]      |
| Konfigurace Nuget         | `nugetconfig` |           |
| Webové konfigurace           | `webconfig`   |           |
| Soubor řešení        | `sln`         |           |

---

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`--force`

Vynutí obsah má být vygenerován i v případě, že se změní stávající soubory. To je potřeba, když výstupnímu adresáři již obsahuje projektu.

`-h|--help`

Vytiskne nápovědy pro příkaz. Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Nainstaluje sadu zdroje nebo šablony z `PATH` nebo `NUGET_ID` zadat. Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).

`-l|--list`

Obsahuje seznam šablon, které obsahují zadaný název. Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář. Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.

`-lang|--language {C#|F#|VB}`

Jazyk šablonu, kterou chcete vytvořit. Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části). Pro některé šablony není platná.

`-n|--name <OUTPUT_NAME>`

Název pro vytvoření výstupu. Pokud není zadán žádný název, použije se název aktuálního adresáře.

`-o|--output <OUTPUT_DIRECTORY>`

Umístění pro generovaný výstup. Výchozí je aktuální adresář.

`--type`

Filtry šablony vycházející z dostupných typů. Předdefinované hodnoty jsou "projektu", "položka" nebo "ostatní".

`-u|--uninstall <PATH|NUGET_ID>`

Odinstaluje sadu zdroje nebo šablony v `PATH` nebo `NUGET_ID` zadat.

> [!NOTE]
> Chcete-li odinstalovat šablony pomocí `PATH`, budete muset plně kvalifikovanou cestu. Například *C: či uživatelů nebo\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahující složka se není.
> Kromě toho nezahrnují konečné ukončující lomítko adresáře na cestu k šabloně.

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

`-all|--show-all`

Při spuštění v kontextu jsou uvedeny všechny šablony pro konkrétní typ projektu `dotnet new` příkaz samostatně. Při spuštění v rámci konkrétní šablonu, jako například `dotnet new web -all`, `-all` interpretována jako vytvoření příznak force. To je potřeba, když výstupnímu adresáři již obsahuje projektu.

`-h|--help`

Vytiskne nápovědy pro příkaz. Nelze vyvolat pro `dotnet new` příkaz sám sebe nebo pro všechny šablony, jako například `dotnet new mvc --help`.

`-l|--list`

Obsahuje seznam šablon, které obsahují zadaný název. Pokud je vyvolána pro `dotnet new` příkaz, zobrazí seznam možných šablony, které jsou k dispozici pro daný adresář. Například pokud adresář již obsahuje projekt, nepodporuje zobrazí seznam všech šablon projektu.

`-lang|--language {C#|F#}`

Jazyk šablonu, kterou chcete vytvořit. Jazyk přijata, se liší podle šablony (viz výchozí hodnoty v [argumenty](#arguments) části). Pro některé šablony není platná.

`-n|--name <OUTPUT_NAME>`

Název pro vytvoření výstupu. Pokud není zadán žádný název, použije se název aktuálního adresáře.

`-o|--output <OUTPUT_DIRECTORY>`

Umístění pro generovaný výstup. Výchozí je aktuální adresář.

---

## <a name="template-options"></a>Možnosti šablony

Každá šablona projektu může mít další možnosti, které jsou k dispozici. Základní šablony mají následující možnosti:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**konzole úhlová, reagovat, reactredux**

`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.

**classlib**

`-f|--framework <FRAMEWORK>`-Určuje [framework](../../standard/frameworks.md) k cíli. Hodnoty: `netcoreapp2.0` pro vytvoření základní knihovny tříd rozhraní .NET nebo `netstandard2.0` vytvořit standardní knihovny tříd rozhraní .NET. Výchozí hodnota je `netstandard2.0`.

`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.

**mstest, xunit**

`-p|--enable-pack`– Umožňuje vytváření balíčků pro projekt pomocí [dotnet pack](dotnet-pack.md).

`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.

**globaljson**

`--sdk-version <VERSION_NUMBER>`-Určuje verzi rozhraní .NET Core SDK pro použití v *global.json* souboru.

**web**

`--use-launch-settings`-Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.

`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>`-Typ ověřování. Možné hodnoty jsou:

- `None`-Bez ověřování (výchozí).
- `IndividualB2C`-Jednotlivé ověřování s Azure AD B2C.
- `SingleOrg`-Organizační ověřování pro jednoho klienta.
- `Windows`-Ověřování systému Windows.

`--aad-b2c-instance <INSTANCE>`-Instance Azure Active Directory B2C se připojit k. Použití s `IndividualB2C` ověřování. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>`– ID přihlášení a odhlášení zásady pro tento projekt. Použití s `IndividualB2C` ověřování.

`--aad-instance <INSTANCE>`-Instance služby Azure Active Directory pro připojení k. Použití s `SingleOrg` ověřování. Výchozí hodnota je `https://login.microsoftonline.com/`.

`--client-id <ID>`– ID klienta pro tento projekt. Použití s `IndividualB2C` nebo `SingleOrg` ověřování. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>`-Doména pro directory klienta. Použití s `SingleOrg` nebo `IndividualB2C` ověřování. Výchozí hodnota je `qualified.domain.name`.

`--tenant-id <ID>`-TenantId ID adresáře pro připojení k. Použití s `SingleOrg` ověřování. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access`– Umožňuje této aplikaci přístup pro čtení k adresáři. Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.

`--use-launch-settings`-Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.

`-uld|--use-local-db`-Určuje, že místo SQLite by použít LocalDB. Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.

`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.

**MVC, razor**

`-au|--auth <AUTHENTICATION_TYPE>`-Typ ověřování. Možné hodnoty jsou:

- `None`-Bez ověřování (výchozí).
- `Individual`-Jednotlivé ověřování.
- `IndividualB2C`-Jednotlivé ověřování s Azure AD B2C.
- `SingleOrg`-Organizační ověřování pro jednoho klienta.
- `MultiOrg`-Organizační ověřování pro víc klientů.
- `Windows`-Ověřování systému Windows.

`--aad-b2c-instance <INSTANCE>`-Instance Azure Active Directory B2C se připojit k. Použití s `IndividualB2C` ověřování. Výchozí hodnota je `https://login.microsoftonline.com/tfp/` .

`-ssp|--susi-policy-id <ID>`– ID přihlášení a odhlášení zásady pro tento projekt. Použití s `IndividualB2C` ověřování.

`-rp|--reset-password-policy-id <ID>`-Resetování hesla ID zásady pro tento projekt. Použití s `IndividualB2C` ověřování.

`-ep|--edit-profile-policy-id <ID>`-Upravit profil ID zásady pro tento projekt. Použití s `IndividualB2C` ověřování.

`--aad-instance <INSTANCE>`-Instance služby Azure Active Directory pro připojení k. Použití s `SingleOrg` nebo `MultiOrg` ověřování. Výchozí hodnota je `https://login.microsoftonline.com/`.

`--client-id <ID>`– ID klienta pro tento projekt. Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>`-Doména pro directory klienta. Použití s `SingleOrg` nebo `IndividualB2C` ověřování... Výchozí hodnota je `qualified.domain.name`.

`--tenant-id <ID>`-TenantId ID adresáře pro připojení k. Použití s `SingleOrg` ověřování... Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>`– Cesta žádosti v rámci základní cesty aplikace identifikátor URI přesměrování. Použití s `SingleOrg` nebo `IndividualB2C` ověřování... Výchozí hodnota je `/signin-oidc`.

`-r|--org-read-access`– Umožňuje této aplikaci přístup pro čtení k adresáři. Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.

`--use-launch-settings`-Zahrnuje *launchSettings.json* ve výstupu vygenerované šablony.

`--use-browserlink`-Zahrnuje BrowserLink v projektu.

`-uld|--use-local-db`-Určuje, že místo SQLite by použít LocalDB. Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.

`--no-restore`-Nepodporuje provedení implicitní obnovení během vytváření projektu.

**stránka**

`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód. Výchozí hodnota je `MyApp.Namespace`.

`-np|--no-pagemodel`-Vytvoří danou stránku bez PageModel.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>`-Namespace pro generovaný kód. Výchozí hodnota je `MyApp.Namespace`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

**console, xunit, mstest, web, webapi**

`-f|--framework`-Určuje [framework](../../standard/frameworks.md) k cíli. Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`. Výchozí hodnota je `netcoreapp1.0`.

**classlib**

`-f|--framework`-Určuje [framework](../../standard/frameworks.md) k cíli. Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` k `netstandard1.6`. Výchozí hodnota je `netstandard1.4`.

**mvc**

`-f|--framework`-Určuje [framework](../../standard/frameworks.md) k cíli. Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`. Výchozí hodnota je `netcoreapp1.0`.

`-au|--auth`-Typ ověřování. Hodnoty: `None` nebo `Individual`. Výchozí hodnota je `None`.

`-uld|--use-local-db`-Určuje, zda pro použití LocalDB místo SQLite. Hodnoty: `true` nebo `false`. Výchozí hodnota je `false`.

---

## <a name="examples"></a>Příklady

Vytvoření projektu aplikace konzoly F # v aktuálním adresáři:

`dotnet new console -lang f#`

Vytvořte standardní rozhraní .NET projektu knihovny tříd v zadaný adresář (dostupné pouze s .NET Core 2.0 SDK nebo novější verze):

`dotnet new classlib -lang VB -o MyLibrary`

Vytvořte nový projekt aplikace ASP.NET Core C# MVC v aktuálním adresáři bez jakéhokoli ověřování cílení na rozhraní .NET 2.0 jádra:

`dotnet new mvc -au None -f netcoreapp2.0`

Vytvoření nové aplikace xUnit cílení na rozhraní .NET 2.0 jádra:

`dotnet new xunit --framework netcoreapp2.0`

Seznam všech šablon, které jsou k dispozici pro MVC:

`dotnet new mvc -l`

## <a name="see-also"></a>Viz také

[Vlastní šablony pro nové dotnet.](custom-templates.md)  
[Vytvoření vlastní šablony pro dotnet new](~/docs/core/tutorials/create-custom-template.md)  
[dotnet/dotnet-template-samples GitHub repo](https://github.com/dotnet/dotnet-template-samples)  
[Dostupné šablony pro nové dotnet.](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
