---
title: nový příkaz DotNet – rozhraní příkazového řádku .NET Core
description: Vytvoří nový příkaz dotnet nových projektů .NET Core založených na zadané šabloně.
author: mairaw
ms.author: mairaw
ms.date: 07/31/2018
ms.openlocfilehash: 396c4ddf09854fa4582226bdb1422f8c929e459b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208630"
---
# <a name="dotnet-new"></a>nový příkaz DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet new` -Vytvoří nový projekt, konfigurační soubor nebo řešení založené na zadané šabloně.

## <a name="synopsis"></a>Souhrn

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [--nuget-source] [-o|--output]
    [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

```console
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

```console
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```

---

## <a name="description"></a>Popis

`dotnet new` Příkaz poskytuje pohodlný způsob, jak inicializovat platný projekt .NET Core.

Příkaz volání [modulu šablon](https://github.com/dotnet/templating) vytvořit artefakty na disku na základě určené šablony a možnosti.

## <a name="arguments"></a>Arguments

`TEMPLATE`

Šablona pro vytvoření instance při vyvolání příkazu. Každá šablona může mít specifické možnosti, které lze předat. Další informace najdete v tématu [možnosti šablony](#template-options).

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

Příkaz obsahuje výchozí seznam šablon. Použití `dotnet new -l` získat seznam dostupných šablon. V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou .NET Core SDK 2.1.300. Výchozí jazyk šablony se zobrazí v závorkách.

|Popis šablony                          | Název šablony   | Jazyky     |
|----------------------------------------------|-----------------|---------------|
| Konzolová aplikace                          | `console`       | [C#], F #, VB  |
| Knihovna tříd                                | `classlib`      | [C#], F #, VB  |
| Projekt testu jednotek                            | `mstest`        | [C#], F #, VB  |
| Projekt testů xUnit                           | `xunit`         | [C#], F #, VB  |
| Stránka Razor                                   | `page`          | [C#]          |
| MVC ViewImports                              | `viewimports`   | [C#]          |
| MVC ViewStart                                | `viewstart`     | [C#]          |
| ASP.NET Core je prázdný                           | `web`           | [C#], F #      |
| Webové aplikace ASP.NET Core (Model-View-Controller) | `mvc`           | [C#], F #      |
| Webové aplikace ASP.NET Core                         | `razor`         | [C#]          |
| ASP.NET Core pomocí Angular                    | `angular`       | [C#]          |
| ASP.NET Core pomocí React.js                   | `react`         | [C#]          |
| ASP.NET Core pomocí React.js a Redux         | `reactredux`    | [C#]          |
| Webové rozhraní API ASP.NET Core                         | `webapi`        | [C#], F #      |
| Knihovny tříd Razor                          | `razorclasslib` | [C#]          |
| soubor Global.JSON                             | `globaljson`    |               |
| NuGet config                                 | `nugetconfig`   |               |
| Webové konfigurace                                   | `webconfig`     |               |
| Soubor řešení                                | `sln`           |               |

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

Příkaz obsahuje výchozí seznam šablon. Použití `dotnet new -l` získat seznam dostupných šablon. V následující tabulce jsou uvedeny šablony, které jsou předem nainstalované s .NET Core SDK 2.0. Výchozí jazyk šablony se zobrazí v závorkách.

|Popis šablony                          | Název šablony | Jazyky     |
|----------------------------------------------|---------------|---------------|
| Konzolová aplikace                          | `console`     | [C#], F #, VB  |
| Knihovna tříd                                | `classlib`    | [C#], F #, VB  |
| Projekt testu jednotek                            | `mstest`      | [C#], F #, VB  |
| Projekt testů xUnit                           | `xunit`       | [C#], F #, VB  |
| ASP.NET Core je prázdný                           | `web`         | [C#], F #      |
| Webové aplikace ASP.NET Core (Model-View-Controller) | `mvc`         | [C#], F #      |
| Webové aplikace ASP.NET Core                         | `razor`       | [C#]          |
| ASP.NET Core pomocí Angular                    | `angular`     | [C#]          |
| ASP.NET Core pomocí React.js                   | `react`       | [C#]          |
| ASP.NET Core pomocí React.js a Redux         | `reactredux`  | [C#]          |
| Webové rozhraní API ASP.NET Core                         | `webapi`      | [C#], F #      |
| soubor Global.JSON                             | `globaljson`  |               |
| NuGet config                                 | `nugetconfig` |               |
| Webové konfigurace                                   | `webconfig`   |               |
| Soubor řešení                                | `sln`         |               |
| Stránka Razor                                   | `page`        |               |
| MVC ViewImports                              | `viewimports` |               |
| MVC ViewStart                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

Příkaz obsahuje výchozí seznam šablon. Použití `dotnet new -all` získat seznam dostupných šablon. V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou SDK .NET Core 1.x. Výchozí jazyk šablony se zobrazí v závorkách.

|Popis šablony  | Název šablony | Jazyky |
|----------------------|---------------|-----------|
| Konzolová aplikace  | `console`     | [C#], F #  |
| Knihovna tříd        | `classlib`    | [C#], F #  |
| Projekt testu jednotek    | `mstest`      | [C#], F #  |
| Projekt testů xUnit   | `xunit`       | [C#], F #  |
| ASP.NET Core je prázdný   | `web`         | [C#]      |
| Webové aplikace ASP.NET Core | `mvc`         | [C#], F #  |
| Webové rozhraní API ASP.NET Core | `webapi`      | [C#]      |
| NuGet config         | `nugetconfig` |           |
| Webové konfigurace           | `webconfig`   |           |
| Soubor řešení        | `sln`         |           |

---

## <a name="options"></a>Možnosti

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--force`

Vynutí obsahu chcete vygenerovat i v případě, že by došlo ke změně existujících souborů. To je potřeba při výstupní adresář již obsahuje projekt.

`-h|--help`

Vytiskne nápovědy pro příkaz. Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Nainstaluje zdroj nebo šablony pack z `PATH` nebo `NUGET_ID` k dispozici. Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat verzi ve formátu `<package-name>::<package-version>`. Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíček verze. Podívejte se příklad na [příklady](#examples) oddílu.

Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).

`-l|--list`

Zobrazí seznam šablon, které obsahují zadaný název. Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář. Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.

`-lang|--language {C#|F#|VB}`

Jazyk šablony k vytvoření. Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části). Pro některé šablony není platná.

> [!NOTE]
> Některé součásti pro interpretaci `#` jako speciální znak. V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Název pro výstup vytvořený. Pokud není zadán žádný název, použije se název aktuálního adresáře.

`--nuget-source`

Určuje zdroj NuGet, který chcete použít během instalace.

`-o|--output <OUTPUT_DIRECTORY>`

Umístění pro vygenerovaný výstup. Výchozí je aktuální adresář.

`--type`

Vyfiltruje šablony podle dostupných typů. Předdefinované hodnoty jsou "projekt", "item" nebo "jiné".

`-u|--uninstall <PATH|NUGET_ID>`

Odinstaluje zdroj nebo šablony pack na `PATH` nebo `NUGET_ID` k dispozici.

> [!NOTE]
> Chcete-li odinstalovat sadu pomocí šablony `PATH`, budete potřebovat plně kvalifikovanou cestu. Například *C:/uživatele/\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahuje složky nebudou.
> Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`--force`

Vynutí obsahu chcete vygenerovat i v případě, že by došlo ke změně existujících souborů. To je potřeba při výstupní adresář již obsahuje projekt.

`-h|--help`

Vytiskne nápovědy pro příkaz. Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Nainstaluje zdroj nebo šablony pack z `PATH` nebo `NUGET_ID` k dispozici. Pokud chcete nainstalovat zkušební verzi balíčku šablony, je třeba zadat verzi ve formátu `<package-name>::<package-version>`. Ve výchozím nastavení `dotnet new` předá \* pro verzi, která představuje poslední stabilní balíček verze. Podívejte se příklad na [příklady](#examples) oddílu.

Informace o vytváření vlastních šablon najdete v tématu [vlastních šablon pro dotnet nové](custom-templates.md).

`-l|--list`

Zobrazí seznam šablon, které obsahují zadaný název. Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář. Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.

`-lang|--language {C#|F#|VB}`

Jazyk šablony k vytvoření. Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části). Pro některé šablony není platná.

> [!NOTE]
> Některé součásti pro interpretaci `#` jako speciální znak. V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Název pro výstup vytvořený. Pokud není zadán žádný název, použije se název aktuálního adresáře.

`-o|--output <OUTPUT_DIRECTORY>`

Umístění pro vygenerovaný výstup. Výchozí je aktuální adresář.

`--type`

Vyfiltruje šablony podle dostupných typů. Předdefinované hodnoty jsou "projekt", "item" nebo "jiné".

`-u|--uninstall <PATH|NUGET_ID>`

Odinstaluje zdroj nebo šablony pack na `PATH` nebo `NUGET_ID` k dispozici.

> [!NOTE]
> Odinstalace pomocí zdroj `PATH`, budete potřebovat plně kvalifikovanou cestu. Například *C:/uživatele/\<uživatele > /Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahuje složky nebudou. Kromě toho nesmí být znak konečné ukončující znak lomítka adresáře na cestu k šabloně.
> 
> Pokud se nemůžete určit `PATH` nebo `NUGET_ID` argumentů potřebných k odinstalaci šablonu s `dotnet new --uninstall` bez argumentu zobrazí seznam všech nainstalovaných šablon a argument nutné je odinstalovat.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`-all|--show-all`

Zobrazí všechny šablony pro konkrétní typ projektu při spuštění v kontextu `dotnet new` samotný příkaz. Při spuštění v kontextu konkrétní šablony, jako například `dotnet new web -all`, `-all` je interpretován jako vytvoření příznak force. To je potřeba při výstupní adresář již obsahuje projekt.

`-h|--help`

Vytiskne nápovědy pro příkaz. Může být vyvolána pro `dotnet new` samotný příkaz nebo pro všechny šablony, jako například `dotnet new mvc --help`.

`-l|--list`

Zobrazí seznam šablon, které obsahují zadaný název. Pokud je vyvolána `dotnet new` příkazu, uvádí možné šablony, které jsou k dispozici pro daný adresář. Například pokud adresář, projekt již obsahuje, neobsahuje všechny šablony projektů.

`-lang|--language {C#|F#}`

Jazyk šablony k vytvoření. Jazyk přijato, se liší podle šablony (Zobrazit výchozí hodnoty v [argumenty](#arguments) části). Pro některé šablony není platná.

> [!NOTE]
> Některé součásti pro interpretaci `#` jako speciální znak. V takových případech bude nutné uvést hodnotu parametru jazyka, jako `dotnet new console -lang "F#"`.

`-n|--name <OUTPUT_NAME>`

Název pro výstup vytvořený. Pokud není zadán žádný název, použije se název aktuálního adresáře.

`-o|--output <OUTPUT_DIRECTORY>`

Umístění pro vygenerovaný výstup. Výchozí je aktuální adresář.

---

## <a name="template-options"></a>Nastavení šablony

Každá šablona projektu může mít k dispozici další možnosti. Základní šablony mají následující další možnosti:

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

**konzola, angular, react, reactredux, razorclasslib**

  `--no-restore` -Neprovede implicitní obnovení při vytváření projektu.

**classlib**

`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle. Hodnoty: `netcoreapp2.0` k vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard. Výchozí hodnota je `netstandard2.0`.

`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.

**mstest, xunit**

`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).

`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.

**globaljson**

`--sdk-version <VERSION_NUMBER>` : Určuje verzi .NET Core SDK pro použití v *global.json* souboru.

**web**

`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.

`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.

`--no-https` -Projektu nebude vyžadovat protokol HTTPS. Tato možnost platí, pouze pokud `IndividualAuth` nebo `OrganizationalAuth` nejsou používány.

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít. Možné hodnoty jsou:

- `None` -Bez ověřování (výchozí).
- `IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.
- `SingleOrg` – Ověřování organizace pro jednoho tenanta.
- `Windows` -Ověřování Windows.

`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k. Použití s `IndividualB2C` ověřování. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt. Použití s `IndividualB2C` ověřování.

`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k. Použití s `SingleOrg` ověřování. Výchozí hodnota je `https://login.microsoftonline.com/`.

`--client-id <ID>` – ID klienta pro tento projekt. Použití s `IndividualB2C` nebo `SingleOrg` ověřování. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` -Domény tenantu Active directory. Použití s `SingleOrg` nebo `IndividualB2C` ověřování. Výchozí hodnota je `qualified.domain.name`.

`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k. Použití s `SingleOrg` ověřování. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře. Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.

`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.

`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite. Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.

`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.

`--no-https` -Projektu nebude vyžadovat protokol HTTPS. `app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`. Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.

**MVC, razor**

`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít. Možné hodnoty jsou:

- `None` -Bez ověřování (výchozí).
- `Individual` -Jednotlivé ověřování.
- `IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.
- `SingleOrg` – Ověřování organizace pro jednoho tenanta.
- `MultiOrg` – Ověřování organizace pro více tenantů.
- `Windows` -Ověřování Windows.

`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k. Použití s `IndividualB2C` ověřování. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt. Použití s `IndividualB2C` ověřování.

`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt. Použití s `IndividualB2C` ověřování.

`-ep|--edit-profile-policy-id <ID>` – Upravit profil zásady ID pro tento projekt. Použití s `IndividualB2C` ověřování.

`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k. Použití s `SingleOrg` nebo `MultiOrg` ověřování. Výchozí hodnota je `https://login.microsoftonline.com/`.

`--client-id <ID>` – ID klienta pro tento projekt. Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` -Domény tenantu Active directory. Použití s `SingleOrg` nebo `IndividualB2C` ověřování. Výchozí hodnota je `qualified.domain.name`.

`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k. Použití s `SingleOrg` ověřování. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>` -Cestu požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování. Použití s `SingleOrg` nebo `IndividualB2C` ověřování. Výchozí hodnota je `/signin-oidc`.

`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře. Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.

`--exclude-launch-settings` -Vyloučení *launchSettings.json* z vygenerované šablony.

`--use-browserlink` -Obsahuje BrowserLink v projektu.

`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite. Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.

`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.

`--no-https` -Projektu nebude vyžadovat protokol HTTPS. `app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`. Tato možnost platí, pouze pokud `Individual`, `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` nejsou používány.

**Stránka**

`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód. Výchozí hodnota je `MyApp.Namespace`.

`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód. Výchozí hodnota je `MyApp.Namespace`.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

**konzola, angular, react, reactredux**

  `--no-restore` -Neprovede implicitní obnovení při vytváření projektu.

**classlib**

`-f|--framework <FRAMEWORK>` : Určuje, že [framework](../../standard/frameworks.md) do cíle. Hodnoty: `netcoreapp2.0` k vytvoření knihovny tříd .NET Core nebo `netstandard2.0` k vytvoření knihovny tříd .NET Standard. Výchozí hodnota je `netstandard2.0`.

`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.

**mstest, xunit**

`-p|--enable-pack` – Povolí balení pro projekt pomocí [balíčku dotnet](dotnet-pack.md).

`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.

**globaljson**

`--sdk-version <VERSION_NUMBER>` : Určuje verzi .NET Core SDK pro použití v *global.json* souboru.

**web**

`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.

`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít. Možné hodnoty jsou:

- `None` -Bez ověřování (výchozí).
- `IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.
- `SingleOrg` – Ověřování organizace pro jednoho tenanta.
- `Windows` -Ověřování Windows.

`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k. Použití s `IndividualB2C` ověřování. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt. Použití s `IndividualB2C` ověřování.

`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k. Použití s `SingleOrg` ověřování. Výchozí hodnota je `https://login.microsoftonline.com/`.

`--client-id <ID>` – ID klienta pro tento projekt. Použití s `IndividualB2C` nebo `SingleOrg` ověřování. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` -Domény tenantu Active directory. Použití s `SingleOrg` nebo `IndividualB2C` ověřování. Výchozí hodnota je `qualified.domain.name`.

`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k. Použití s `SingleOrg` ověřování. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře. Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.

`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.

`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite. Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.

`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.

**MVC, razor**

`-au|--auth <AUTHENTICATION_TYPE>` -Typ ověřování, který má použít. Možné hodnoty jsou:

- `None` -Bez ověřování (výchozí).
- `Individual` -Jednotlivé ověřování.
- `IndividualB2C` -Jednotlivé ověřování pomocí Azure AD B2C.
- `SingleOrg` – Ověřování organizace pro jednoho tenanta.
- `MultiOrg` – Ověřování organizace pro více tenantů.
- `Windows` -Ověřování Windows.

`--aad-b2c-instance <INSTANCE>` -Instanci Azure Active Directory B2C pro připojení k. Použití s `IndividualB2C` ověřování. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` – ID přihlášení a registraci zásady pro tento projekt. Použití s `IndividualB2C` ověřování.

`-rp|--reset-password-policy-id <ID>` -Resetování hesla ID zásady pro tento projekt. Použití s `IndividualB2C` ověřování.

`-ep|--edit-profile-policy-id <ID>` – Upravit profil zásady ID pro tento projekt. Použití s `IndividualB2C` ověřování.

`--aad-instance <INSTANCE>` – Instance služby Azure Active Directory pro připojení k. Použití s `SingleOrg` nebo `MultiOrg` ověřování. Výchozí hodnota je `https://login.microsoftonline.com/`.

`--client-id <ID>` – ID klienta pro tento projekt. Použití s `IndividualB2C`, `SingleOrg`, nebo `MultiOrg` ověřování. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` -Domény tenantu Active directory. Použití s `SingleOrg` nebo `IndividualB2C` ověřování. Výchozí hodnota je `qualified.domain.name`.

`--tenant-id <ID>` – ID Tenanta ID adresáře pro připojení k. Použití s `SingleOrg` ověřování. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>` -Cestu požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování. Použití s `SingleOrg` nebo `IndividualB2C` ověřování. Výchozí hodnota je `/signin-oidc`.

`-r|--org-read-access` – Povolí této aplikaci přístup pro čtení do adresáře. Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.

`--use-launch-settings` -Zahrnuje *launchSettings.json* ve výstupu vygenerovanou šablonu.

`--use-browserlink` -Obsahuje BrowserLink v projektu.

`-uld|--use-local-db` : Určuje, že by měl být LocalDB použít místo SQLite. Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.

`--no-restore` -Neprovede implicitní obnovení při vytváření projektu.

**Stránka**

`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód. Výchozí hodnota je `MyApp.Namespace`.

`-np|--no-pagemodel` -Vytvoří danou stránku bez PageModel.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>`-Namespace pro vygenerovaný kód. Výchozí hodnota je `MyApp.Namespace`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

**konzola, xunit, mstest, web, webapi**

`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle. Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`. Výchozí hodnota je `netcoreapp1.0`.

**classlib**

`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle. Hodnoty: `netcoreapp1.0`, `netcoreapp1.1`, nebo `netstandard1.0` k `netstandard1.6`. Výchozí hodnota je `netstandard1.4`.

**mvc**

`-f|--framework` : Určuje, že [framework](../../standard/frameworks.md) do cíle. Hodnoty: `netcoreapp1.0` nebo `netcoreapp1.1`. Výchozí hodnota je `netcoreapp1.0`.

`-au|--auth` -Typ ověřování, který má použít. Hodnoty: `None` nebo `Individual`. Výchozí hodnota je `None`.

`-uld|--use-local-db` : Určuje, jestli se mají použít databázi LocalDB místo SQLite. Hodnoty: `true` nebo `false`. Výchozí hodnota je `false`.

---

## <a name="examples"></a>Příklady

Vytvoření projektu aplikace konzoly F # v aktuálním adresáři:

`dotnet new console -lang F#`

Vytvořte projekt knihovny tříd .NET Standard v zadaném adresáři (k dispozici pouze s .NET Core SDK 2.0 a novějšími verzemi):

`dotnet new classlib -lang VB -o MyLibrary`

Vytvoření nového projektu aplikace ASP.NET Core C# MVC v aktuálním adresáři bez ověřování:

`dotnet new mvc -au None`

Vytvořte novou aplikaci xUnit:

`dotnet new xunit`

Seznam všech šablon, které jsou k dispozici pro rozhraní MVC:

`dotnet new mvc -l`

Instalace verze 2.0 šablon jednostránkové aplikace ASP.NET Core (příkaz Možnosti dostupné pro .NET Core SDK 1.1 a novějších verzích pouze):

`dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0`

Vytvoření *global.json* v aktuálním adresáři nastavení sady SDK verze 2.0.0 (k dispozici pouze s .NET Core SDK 2.0 a novějšími verzemi):

`dotnet new globaljson --sdk-version 2.0.0`

## <a name="see-also"></a>Viz také:

* [Vlastních šablon pro dotnet nové](custom-templates.md)  
* [Vytvoření vlastní šablony pro dotnet new](~/docs/core/tutorials/create-custom-template.md)  
* [úložiště GitHub DotNet/dotnet – šablony – ukázky](https://github.com/dotnet/dotnet-template-samples)  
* [Dostupné šablony pro dotnet nové](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
