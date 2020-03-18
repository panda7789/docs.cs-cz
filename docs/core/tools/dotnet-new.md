---
title: dotnet nový příkaz
description: Nový příkaz dotnet vytvoří nové projekty .NET Core založené na zadané šabloně.
ms.date: 02/13/2020
ms.openlocfilehash: d3c609419596b123f5bfb3ca85cf292a61154a70
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399124"
---
# <a name="dotnet-new"></a>dotnet new

**Tento článek se týká:** ✔️ .NET Core 2.0 SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet new`- Vytvoří nový projekt, konfigurační soubor nebo řešení založené na zadané šabloně.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name]
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet new` vytvoří projekt .NET Core nebo jiné artefakty založené na šabloně.

Příkaz volá [modul šablony](https://github.com/dotnet/templating) k vytvoření artefaktů na disku na základě zadané šablony a možností.

## <a name="arguments"></a>Argumenty

- **`TEMPLATE`**

  Šablona k vytvoření instance při vyvolání příkazu. Každá šablona může mít konkrétní možnosti, které můžete předat. Další informace naleznete v [tématu Možnosti šablony](#template-options).

  Seznam všech `dotnet new --list` nainstalovaných šablon můžete spustit. Pokud `TEMPLATE` hodnota není přesná shoda na text ve **sloupci Šablony** nebo **krátký název** z vrácené tabulky, podřetězec shoda se provádí na tyto dva sloupce.

  Počínaje sadou .NET Core 3.0 SDK hledá rozhraní příkazového příkazu šablony v NuGet.org při vyvolání příkazu `dotnet new` za následujících podmínek:

  - Pokud clI nemůže najít šablonu zápas při `dotnet new`vyvolání , ani částečné.
  - Pokud je k dispozici novější verze šablony. V tomto případě je vytvořen projekt nebo artefakt, ale CLI vás upozorní na aktualizovanou verzi šablony.

  Příkaz obsahuje výchozí seznam šablon. Slouží `dotnet new -l` k získání seznamu dostupných šablon. V následující tabulce jsou uvedeny šablony, které jsou předinstalovány se sadou .NET Core SDK. Výchozí jazyk šablony je zobrazen uvnitř závorek. Kliknutím na odkaz krátký název zobrazíte konkrétní možnosti šablony.

| Šablony                                    | Krátký název                      | Jazyk     | Značky                                  | Zavedena |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| Konzolová aplikace                          | [Konzoly](#console)             | [C#], F#, VB | Běžné/konzolové                        | 1.0        |
| Knihovna tříd                                | [classlib](#classlib)           | [C#], F#, VB | Společné/Knihovna                        | 1.0        |
| Aplikace WPF                              | [Wpf](#wpf)                     | [C#]         | Časté/WPF                            | 3.0        |
| Knihovna tříd WPF                            | [wpflib](#wpf)                  | [C#]         | Časté/WPF                            | 3.0        |
| Knihovna vlastních ovládacích prvků WPF                   | [wpfcustomcontrollib](#wpf)     | [C#]         | Časté/WPF                            | 3.0        |
| Knihovna uživatelských ovládacích prveků WPF                     | [wpfusercontrollib](#wpf)       | [C#]         | Časté/WPF                            | 3.0        |
| Aplikace Windows Forms (WinForms)         | [Winforms](#winforms)           | [C#]         | Běžné/WinForms                       | 3.0        |
| Knihovna tříd Windows Forms (WinForms)       | [winformslib](#winforms)        | [C#]         | Běžné/WinForms                       | 3.0        |
| Pracovní služba                               | [Pracovník](#web-others)           | [C#]         | Běžné/Pracovník/Web                     | 3.0        |
| Projekt testování částí                            | [mstest](#test)                 | [C#], F#, VB | Test/MSTest                           | 1.0        |
| Testovací projekt NUnit 3                         | [nunit](#nunit)                  | [C#], F#, VB | Testovací/NUnit                            | 2.1.400    |
| Testovací položka NUnit 3                            | `nunit-test`                    | [C#], F#, VB | Testovací/NUnit                            | 2,2        |
| XUnit testovací projekt                           | [jednotka x](#test)                  | [C#], F#, VB | Testovací/xJednotka                            | 1.0        |
| Komponenta razor                              | `razorcomponent`                | [C#]         | Web/Technologie ASP.NET                           | 3.0        |
| Holicí strojek stránka                                   | [Stránka](#page)                   | [C#]         | Web/Technologie ASP.NET                           | 2.0        |
| MVC ViewImports                              | [viewimports](#namespace)       | [C#]         | Web/Technologie ASP.NET                           | 2.0        |
| Spuštění zobrazení MVC                                | `viewstart`                     | [C#]         | Web/Technologie ASP.NET                           | 2.0        |
| Aplikace Blazor Server                            | [blazorserver](#blazorserver)   | [C#]         | Web/Blazor                            | 3.0        |
| ASP.NET jádro prázdné                           | [Webové](#web)                     | [C#], F #     | Web/Prázdný                             | 1.0        |
| ASP.NET základní webová aplikace (model-view-controller) | [Mvc](#web-options)             | [C#], F #     | Web/MVC                               | 1.0        |
| ASP.NET základní webová aplikace                         | [webapp, holicí strojek](#web-options)   | [C#]         | Webové/MVC/Razor stránky                   | 2.2, 2.0   |
| ASP.NET jádro s úhlovým                    | [Úhlové](#spa)                 | [C#]         | Web/MVC/SPA                           | 2.0        |
| ASP.NET jádro s React.js                   | [Reagovat](#spa)                   | [C#]         | Web/MVC/SPA                           | 2.0        |
| ASP.NET jádro s React.js a Redux         | [reactredux](#reactredux)       | [C#]         | Web/MVC/SPA                           | 2.0        |
| Knihovna třídy Holicí strojek                          | [razorclasslib](#razorclasslib) | [C#]         | Web/Břitva/knihovna/knihovna | 2.1        |
| Webové rozhraní API ASP.NET Core                         | [webapi](#webapi)               | [C#], F #     | Webové rozhraní API                            | 1.0        |
| ASP.NET Core gRPC Service                    | [grpc](#web-others)             | [C#]         | Web/gRPC                              | 3.0        |
| Soubor vyrovnávací paměti protokolu                         | [proto](#namespace)             |              | Web/gRPC                              | 3.0        |
| dotnet gitignore soubor                        | `gitignore`                     |              | Config                                | 3.0        |
| soubor global.json                             | [globaljson](#globaljson)       |              | Config                                | 2.0        |
| Konfigurace nugetu                                 | `nugetconfig`                   |              | Config                                | 1.0        |
| Dotnet místní nástroj manifest soubor              | `tool-manifest`                 |              | Config                                | 3.0        |
| Konfigurace webu                                   | `webconfig`                     |              | Config                                | 1.0        |
| Soubor řešení                                | `sln`                           |              | Řešení                              | 1.0        |

## <a name="options"></a>Možnosti

- **`--dry-run`**

  Zobrazí souhrn toho, co by se stalo, kdyby byl daný příkaz spuštěn. K dispozici od .NET Core 2.2 SDK.

- **`--force`**

  Vynutí vygenerování obsahu, i když by změnil existující soubory. To je nutné, pokud vybraná šablona přepíše existující soubory ve výstupním adresáři.

- **`-h|--help`**

  Vytiskne nápovědu pro příkaz. Může být vyvolána `dotnet new` pro samotný příkaz nebo pro libovolnou šablonu. Například, `dotnet new mvc --help`.

- **`-i|--install <PATH|NUGET_ID>`**

  Nainstaluje sadu šablon `PATH` z `NUGET_ID` nebo poskytované. Chcete-li nainstalovat předběžnou verzi balíčku šablony, je třeba zadat verzi `<package-name>::<package-version>`ve formátu . Ve výchozím `dotnet new` \* nastavení přechází pro verzi, která představuje nejnovější stabilní verzi balíčku. Viz příklad v části [Příklady.](#examples)
  
  Pokud byla verze šablony již nainstalována při spuštění tohoto příkazu, bude šablona aktualizována na zadanou verzi nebo na nejnovější stabilní verzi, pokud nebyla zadána žádná verze.

  Informace o vytváření vlastních šablon naleznete v [tématu Vlastní šablony pro dotnet new](custom-templates.md).

- **`-l|--list`**

  Zobrazí seznam šablon obsahujících zadaný název. Pokud není zadán žádný název, zobrazí seznam všech šablon.

- **`-lang|--language {C#|F#|VB}`**

  Jazyk šablony, kterou chcete vytvořit. Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v části [argumenty).](#arguments) Neplatí pro některé šablony.

  > [!NOTE]
  > Některé skořepiny interpretují `#` jako speciální znak. V těchto případech uzavřete hodnotu parametru jazyka do uvozovek. Například, `dotnet new console -lang "F#"`.

- **`-n|--name <OUTPUT_NAME>`**

  Název vytvořeného výstupu. Pokud není zadán žádný název, bude použit název aktuálního adresáře.

- **`--nuget-source`**

  Určuje zdroj NuGet, který se má použít během instalace. K dispozici od .NET Core 2.1 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Umístění pro umístění generovaného výstupu. Výchozí je aktuální adresář.

- **`--type`**

  Filtruje šablony založené na dostupných typech. Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".

- **`-u|--uninstall [PATH|NUGET_ID]`**

  Odinstaluje sadu `PATH` šablon `NUGET_ID` v aplikaci nebo v aplikaci. Pokud `<PATH|NUGET_ID>` není zadána hodnota, zobrazí se všechny aktuálně nainstalované balíčky šablon a jejich přidružené šablony. Při zadávání `NUGET_ID`aplikace neuvádějte číslo verze.

  Pokud nezadáte parametr této možnosti, příkaz zobrazí seznam nainstalovaných šablon a podrobnosti o nich.

  > [!NOTE]
  > Chcete-li odinstalovat `PATH`šablonu pomocí aplikace , je třeba cestu plně kvalifikovat. Například *C:/Users/\<USER>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z obsahující složky nebude.
  > Nezahrnujte konečné ukončující lomítko adresáře na cestě šablony.

- **`--update-apply`**

  Zkontroluje, zda jsou k dispozici aktualizace pro aktuálně nainstalované balíčky šablon, a nainstaluje je. K dispozici od .NET Core 3.0 SDK.

- **`--update-check`**

  Zkontroluje, zda jsou k dispozici aktualizace pro aktuálně nainstalované balíčky šablon. K dispozici od .NET Core 3.0 SDK.

## <a name="template-options"></a>Možnosti šablon

Každá šablona projektu může mít k dispozici další možnosti. Základní šablony mají následující další možnosti:

### <a name="console"></a>konzola

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rámec,](../../standard/frameworks.md) na který má být cílit. K dispozici od .NET Core 3.0 SDK.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu. Například použijte `--langVersion 7.3` použít C# 7.3. Není podporováno pro F#. K dispozici od .NET Core 2.2 SDK.

  Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Pokud je zadán, neprovede implicitní obnovení během vytváření projektu. K dispozici od .NET Core 2.2 SDK.

***

### <a name="classlib"></a>classlib

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rámec,](../../standard/frameworks.md) na který má být cílit. Hodnoty: `netcoreapp<version>` chcete-li vytvořit knihovnu `netstandard<version>` tříd .NET Core nebo vytvořit knihovnu standardních tříd .NET. Výchozí hodnota je `netstandard2.0`.

- **`--langVersion <VERSION_NUMBER>`**

  Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu. Například použijte `--langVersion 7.3` použít C# 7.3. Není podporováno pro F#. K dispozici od .NET Core 2.2 SDK.

  Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Neprovede implicitní obnovení během vytváření projektu.

***

### <a name="wpf"></a>wpf, wpflib, wpfcustomcontrollib, wpfusercontrollib

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rámec,](../../standard/frameworks.md) na který má být cílit. Výchozí hodnota je `netcoreapp3.1`. K dispozici od .NET Core 3.1 SDK.

- **`--langVersion <VERSION_NUMBER>`**

  Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu. Například použijte `--langVersion 7.3` použít C# 7.3.

  Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Neprovede implicitní obnovení během vytváření projektu.

***

### <a name="winforms"></a>winforms, winformslib

- **`--langVersion <VERSION_NUMBER>`**

  Nastaví `LangVersion` vlastnost v vytvořeném souboru projektu. Například použijte `--langVersion 7.3` použít C# 7.3.

  Seznam výchozích verzí jazyka C# naleznete [v tématu Výchozí verze](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Neprovede implicitní obnovení během vytváření projektu.

***

### <a name="web-others"></a>pracovník, grpc

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rámec,](../../standard/frameworks.md) na který má být cílit. Výchozí hodnota je `netcoreapp3.1`. K dispozici od .NET Core 3.1 SDK.

- **`--exclude-launch-settings`**

  Nezahrnuje *launchSettings.json* z generované šablony.

- **`--no-restore`**

  Neprovede implicitní obnovení během vytváření projektu.

***

### <a name="test"></a>mstest, xunit

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rámec,](../../standard/frameworks.md) na který má být cílit. Možnost je k dispozici od .NET Core 3.0 SDK.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  Umožňuje balení pro projekt pomocí [dotnet pack](dotnet-pack.md).

- **`--no-restore`**

  Neprovede implicitní obnovení během vytváření projektu.

***

### <a name="nunit"></a>nunit

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rámec,](../../standard/frameworks.md) na který má být cílit.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2,2         | `netcoreapp2.2` |
  | 2.1         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  Umožňuje balení pro projekt pomocí [dotnet pack](dotnet-pack.md).

- **`--no-restore`**

  Neprovede implicitní obnovení během vytváření projektu.

***

### <a name="page"></a>Stránka

- **`-na|--namespace <NAMESPACE_NAME>`**

  Obor názvů pro generovaný kód. Výchozí hodnota je `MyApp.Namespace`.

- **`-np|--no-pagemodel`**

  Vytvoří stránku bez PageModel.

***

### <a name="namespace"></a>viewimports, proto

- **`-na|--namespace <NAMESPACE_NAME>`**

  Obor názvů pro generovaný kód. Výchozí hodnota je `MyApp.Namespace`.

***

### <a name="blazorserver"></a>blazorserver

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ ověřování, které chcete použít. Možné hodnoty jsou:

  - `None`- Žádné ověřování (výchozí).
  - `Individual`- Individuální autentizace.
  - `IndividualB2C`- Individuální ověřování pomocí Azure AD B2C.
  - `SingleOrg`- Organizační ověřování pro jednoho klienta.
  - `MultiOrg`- Organizační ověřování pro více klientů.
  - `Windows`- Ověřování systému Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Instance Azure Active Directory B2C, ke které se chcete připojit. Použití `IndividualB2C` s ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  ID zásad přihlášení a registrace pro tento projekt. Použití `IndividualB2C` s ověřováním.

- **`-rp|--reset-password-policy-id <ID>`**

  ID zásady obnovení hesla pro tento projekt. Použití `IndividualB2C` s ověřováním.

- **`-ep|--edit-profile-policy-id <ID>`**

  ID zásady úpravy profilu pro tento projekt. Použití `IndividualB2C` s ověřováním.

- **`--aad-instance <INSTANCE>`**

  Instance služby Azure Active Directory, ke které se chcete připojit. Použití `SingleOrg` s `MultiOrg` ověřováním nebo ověřování. Výchozí hodnota je `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  ID klienta pro tento projekt. Použití `IndividualB2C`s `SingleOrg`protokolem , nebo `MultiOrg` ověřováním. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Doména klienta adresáře. Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování. Výchozí hodnota je `qualified.domain.name`.

- **`--tenant-id <ID>`**

  ID ID ID tenantid adresáře, ke kterému se chcete připojit. Použití `SingleOrg` s ověřováním. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Cesta požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování. Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování. Výchozí hodnota je `/signin-oidc`.

- **`-r|--org-read-access`**

  Umožňuje této aplikaci přístup pro čtení do adresáře. Platí pouze `SingleOrg` pro `MultiOrg` nebo ověřování.

- **`--exclude-launch-settings`**

  Nezahrnuje *launchSettings.json* z generované šablony.

- **`--no-https`**

  Vypne protokol HTTPS. Tato možnost platí `Individual`pouze `IndividualB2C` `SingleOrg`v `MultiOrg` případě, že se `--auth`pro .

- **`-uld|--use-local-db`**

  Určuje LocalDB by měl být použit místo SQLite. Platí pouze `Individual` pro `IndividualB2C` nebo ověřování.

- **`--no-restore`**

  Neprovede implicitní obnovení během vytváření projektu.

***

### <a name="web"></a>web

- **`--exclude-launch-settings`**

  Nezahrnuje *launchSettings.json* z generované šablony.

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rámec,](../../standard/frameworks.md) na který má být cílit. Možnost není k dispozici v sada .NET Core 2.2 SDK.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Neprovede implicitní obnovení během vytváření projektu.

- **`--no-https`**

  Vypne protokol HTTPS.

***

### <a name="web-options"></a>mvc, webapp

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ ověřování, které chcete použít. Možné hodnoty jsou:

  - `None`- Žádné ověřování (výchozí).
  - `Individual`- Individuální autentizace.
  - `IndividualB2C`- Individuální ověřování pomocí Azure AD B2C.
  - `SingleOrg`- Organizační ověřování pro jednoho klienta.
  - `MultiOrg`- Organizační ověřování pro více klientů.
  - `Windows`- Ověřování systému Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Instance Azure Active Directory B2C, ke které se chcete připojit. Použití `IndividualB2C` s ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  ID zásad přihlášení a registrace pro tento projekt. Použití `IndividualB2C` s ověřováním.

- **`-rp|--reset-password-policy-id <ID>`**

  ID zásady obnovení hesla pro tento projekt. Použití `IndividualB2C` s ověřováním.

- **`-ep|--edit-profile-policy-id <ID>`**

  ID zásady úpravy profilu pro tento projekt. Použití `IndividualB2C` s ověřováním.

- **`--aad-instance <INSTANCE>`**

  Instance služby Azure Active Directory, ke které se chcete připojit. Použití `SingleOrg` s `MultiOrg` ověřováním nebo ověřování. Výchozí hodnota je `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  ID klienta pro tento projekt. Použití `IndividualB2C`s `SingleOrg`protokolem , nebo `MultiOrg` ověřováním. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Doména klienta adresáře. Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování. Výchozí hodnota je `qualified.domain.name`.

- **`--tenant-id <ID>`**

  ID ID ID tenantid adresáře, ke kterému se chcete připojit. Použití `SingleOrg` s ověřováním. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Cesta požadavku v rámci základní cesty aplikace identifikátoru URI přesměrování. Použití `SingleOrg` s `IndividualB2C` ověřováním nebo ověřování. Výchozí hodnota je `/signin-oidc`.

- **`-r|--org-read-access`**

  Umožňuje této aplikaci přístup pro čtení do adresáře. Platí pouze `SingleOrg` pro `MultiOrg` nebo ověřování.

- **`--exclude-launch-settings`**

  Nezahrnuje *launchSettings.json* z generované šablony.

- **`--no-https`**

  Vypne protokol HTTPS. Tato možnost platí `Individual`pouze `IndividualB2C` `SingleOrg`v `MultiOrg` případě, , , , nebo nejsou používány.

- **`-uld|--use-local-db`**

  Určuje LocalDB by měl být použit místo SQLite. Platí pouze `Individual` pro `IndividualB2C` nebo ověřování.

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rámec,](../../standard/frameworks.md) na který má být cílit. Možnost je k dispozici od .NET Core 3.0 SDK.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--no-restore`**

  Neprovede implicitní obnovení během vytváření projektu.

- **`--use-browserlink`**

  Zahrnuje BrowserLink v projektu. Možnost není k dispozici v .NET Core 2.2 a 3.1 SDK.

***

### <a name="spa"></a>úhlové, reagovat

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ ověřování, které chcete použít. K dispozici od .NET Core 3.0 SDK.
  
  Možné hodnoty jsou:

  - `None`- Žádné ověřování (výchozí).
  - `Individual`- Individuální autentizace.

- **`--exclude-launch-settings`**

  Nezahrnuje *launchSettings.json* z generované šablony.

- **`--no-restore`**

  Neprovede implicitní obnovení během vytváření projektu.

- **`--no-https`**

  Vypne protokol HTTPS. Tato možnost platí pouze `None`v případě, že ověřování je .

- **`-uld|--use-local-db`**

  Určuje LocalDB by měl být použit místo SQLite. Platí pouze `Individual` pro `IndividualB2C` nebo ověřování. K dispozici od .NET Core 3.0 SDK.

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rámec,](../../standard/frameworks.md) na který má být cílit. Možnost není k dispozici v sada .NET Core 2.2 SDK.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

***

### <a name="reactredux"></a>reactredux

- **`--exclude-launch-settings`**

  Nezahrnuje *launchSettings.json* z generované šablony.

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rámec,](../../standard/frameworks.md) na který má být cílit. Možnost není k dispozici v sada .NET Core 2.2 SDK.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

- **`--no-restore`**

  Neprovede implicitní obnovení během vytváření projektu.

- **`--no-https`**

  Vypne protokol HTTPS.

***

### <a name="razorclasslib"></a>razorclasslib

- **`--no-restore`**

  Neprovede implicitní obnovení během vytváření projektu.

- **`-s|--support-pages-and-views`**

  Podporuje přidávání tradičních stránek Razor a zobrazení kromě komponent do této knihovny. K dispozici od .NET Core 3.0 SDK.

***
  
### <a name="webapi"></a>webapi

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ ověřování, které chcete použít. Možné hodnoty jsou:

  - `None`- Žádné ověřování (výchozí).
  - `IndividualB2C`- Individuální ověřování pomocí Azure AD B2C.
  - `SingleOrg`- Organizační ověřování pro jednoho klienta.
  - `Windows`- Ověřování systému Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Instance Azure Active Directory B2C, ke které se chcete připojit. Použití `IndividualB2C` s ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  ID zásad přihlášení a registrace pro tento projekt. Použití `IndividualB2C` s ověřováním.

- **`--aad-instance <INSTANCE>`**

  Instance služby Azure Active Directory, ke které se chcete připojit. Použití `SingleOrg` s ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  ID klienta pro tento projekt. Použití `IndividualB2C` s `SingleOrg` ověřováním nebo ověřování. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Doména klienta adresáře. Použití `IndividualB2C` s `SingleOrg` ověřováním nebo ověřování. Výchozí hodnota je `qualified.domain.name`.

- **`--tenant-id <ID>`**

  ID ID ID tenantid adresáře, ke kterému se chcete připojit. Použití `SingleOrg` s ověřováním. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

- **`-r|--org-read-access`**

  Umožňuje této aplikaci přístup pro čtení do adresáře. Platí pouze `SingleOrg` pro ověřování.

- **`--exclude-launch-settings`**

  Nezahrnuje *launchSettings.json* z generované šablony.

- **`--no-https`**

  Vypne protokol HTTPS. `app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány `Startup.Configure`do . Tato možnost platí `IndividualB2C` pouze `SingleOrg` v případě, že se k ověřování používá nebo nepoužívá.

- **`-uld|--use-local-db`**

  Určuje LocalDB by měl být použit místo SQLite. Platí pouze `IndividualB2C` pro ověřování.

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rámec,](../../standard/frameworks.md) na který má být cílit. Možnost není k dispozici v sada .NET Core 2.2 SDK.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, které používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Neprovede implicitní obnovení během vytváření projektu.

***

### <a name="globaljson"></a>globaljson

- **`--sdk-version <VERSION_NUMBER>`**

  Určuje verzi sady .NET Core SDK, která má být používána v souboru *global.json.*

***

## <a name="examples"></a>Příklady

- Vytvořte projekt aplikace konzoly Jazyka C# zadáním názvu šablony:

  ```dotnetcli
  dotnet new "Console Application"
  ```

- Vytvořte projekt aplikace konzoly F# v aktuálním adresáři:

  ```dotnetcli
  dotnet new console -lang F#
  ```

- Vytvořte projekt knihovny tříd .NET Standard v zadaném adresáři:

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- Vytvořte nový ASP.NET projektu Core C# MVC v aktuálním adresáři bez ověřování:

  ```dotnetcli
  dotnet new mvc -au None
  ```

- Vytvořte nový projekt xUnit:

  ```dotnetcli
  dotnet new xunit
  ```

- Seznam všech šablon dostupných pro jednostránkové aplikace (SPA) šablony:

  ```dotnetcli
  dotnet new spa -l
  ```

- Seznam všech šablon odpovídajících podřetězci *we.* Nebyla nalezena žádná přesná shoda, takže porovnávání podřetězců se spustí proti sloupcům krátkého názvu i názvu.

  ```dotnetcli
  dotnet new we -l
  ```

- Pokus o vyvolání šablony odpovídající *ng*. Pokud nelze určit jednu shodu, uveďte šablony, které se částečně shodují.

  ```dotnetcli
  dotnet new ng
  ```

- Nainstalujte verzi 2.0 šablon SPA pro ASP.NET Core:

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- Seznam nainstalovaných šablon a podrobnosti o nich, včetně toho, jak je odinstalovat:

  ```dotnetcli
  dotnet new -u
  ```

- Vytvořte *soubor global.json* v aktuálním adresáři, který nastavuje verzi sady SDK na 3.1.101:

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a>Viz také

- [Vlastní šablony pro dotnet nové](custom-templates.md)
- [Vytvoření vlastní šablony pro dotnet new](../tutorials/cli-templates-create-item-template.md)
- [úložiště GitHub u dotnet/dotnet-template-samples GitHub](https://github.com/dotnet/dotnet-template-samples)
- [Dostupné šablony pro dotnet nové](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
