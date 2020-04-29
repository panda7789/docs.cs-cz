---
title: dotnet – nový příkaz
description: Příkaz dotnet New vytvoří nové projekty .NET Core založené na zadané šabloně.
ms.date: 04/10/2020
ms.openlocfilehash: 9a68baafa7ac3e6ad2fdc8f1c6e8621d6e15f1ff
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506854"
---
# <a name="dotnet-new"></a>dotnet new

**Tento článek se týká:** ✔️ .net Core 2,0 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet new`– Vytvoří nový projekt, konfigurační soubor nebo řešení na základě zadané šablony.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install {PATH|NUGET_ID}]
    [-lang|--language {C#|F#|VB}] [-n|--name <OUTPUT_NAME>]
    [--nuget-source <SOURCE>] [-o|--output <OUTPUT_DIRECTORY>]
    [-u|--uninstall] [--update-apply] [--update-check] [Template options]

dotnet new <TEMPLATE> [-l|--list] [--type <TYPE>]

dotnet new -h|--help
```

## <a name="description"></a>Popis

`dotnet new` Příkaz vytvoří projekt .NET Core nebo jiné artefakty založené na šabloně.

Příkaz volá [modul šablony](https://github.com/dotnet/templating) a vytvoří artefakty na disku na základě zadané šablony a možností.

### <a name="implicit-restore"></a>Implicitní obnovení

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Argumenty

- **`TEMPLATE`**

  Šablona, která se má vytvořit při vyvolání příkazu Každá šablona může mít konkrétní možnosti, které můžete předat. Další informace najdete v tématu [Možnosti šablony](#template-options).

  Můžete spustit `dotnet new --list` nebo `dotnet new -l` a zobrazit seznam všech nainstalovaných šablon. Pokud `TEMPLATE` hodnota není přesná shoda na textu v **šablonách** nebo ve sloupci **krátký název** z vrácené tabulky, provede se shoda podřetězce na těchto dvou sloupcích.

  Počínaje verzí .NET Core 3,0 SDK vyhledává CLI šablony v NuGet.org při vyvolání `dotnet new` příkazu v následujících podmínkách:

  - Pokud rozhraní příkazového řádku nenalezne při vyvolání `dotnet new`odpovídající šablonu, která není ani částečná.
  - Pokud je k dispozici novější verze šablony. V tomto případě se vytvoří projekt nebo artefakt, ale rozhraní příkazového řádku vás upozorní na aktualizovanou verzi šablony.

  Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK. Výchozí jazyk pro šablonu se zobrazí v závorkách. Kliknutím na odkaz krátké jméno zobrazíte konkrétní možnosti šablony.

| Šablony                                    | Krátký název                      | Jazyk     | Značky                                  | Vedou |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| Konzolová aplikace                          | [stromu](#console)             | [C#], F #, VB | Společná/konzola                        | 1.0        |
| Knihovna tříd                                | [že knihovna tříd](#classlib)           | [C#], F #, VB | Společné/knihovny                        | 1.0        |
| Aplikace WPF                              | [subsystém](#wpf)                     | Jazyk         | Common/WPF                            | 3.0        |
| WPF – knihovna tříd                            | [wpflib](#wpf)                  | Jazyk         | Common/WPF                            | 3.0        |
| Knihovna vlastních ovládacích prvků WPF                   | [wpfcustomcontrollib](#wpf)     | Jazyk         | Common/WPF                            | 3.0        |
| Knihovna uživatelských ovládacích prvků WPF                     | [wpfusercontrollib](#wpf)       | Jazyk         | Common/WPF                            | 3.0        |
| Aplikace model Windows Forms (WinForms)         | [WinForms](#winforms)           | Jazyk         | Common/WinForms                       | 3.0        |
| Knihovna tříd model Windows Forms (WinForms)       | [winformslib](#winforms)        | Jazyk         | Common/WinForms                       | 3.0        |
| Služba pracovního procesu                               | [zaměstnanec](#web-others)           | Jazyk         | Common/Work/Web                     | 3.0        |
| Projekt testu jednotek                            | [MSTest](#test)                 | [C#], F #, VB | Test/MSTest                           | 1.0        |
| Projekt testů NUnit 3                         | [nunit](#nunit)                  | [C#], F #, VB | Test/NUnit                            | 2.1.400    |
| NUnit 3 položka testu                            | `nunit-test`                    | [C#], F #, VB | Test/NUnit                            | 2,2        |
| Projekt testů xUnit                           | [xUnit](#test)                  | [C#], F #, VB | Test/xUnit                            | 1.0        |
| Komponenta Razor                              | `razorcomponent`                | Jazyk         | Web/ASP. NET                           | 3.0        |
| Stránka Razor                                   | [Page](#page)                   | Jazyk         | Web/ASP. NET                           | 2.0        |
| ViewImports MVC                              | [viewimports](#namespace)       | Jazyk         | Web/ASP. NET                           | 2.0        |
| ViewStart MVC                                | `viewstart`                     | Jazyk         | Web/ASP. NET                           | 2.0        |
| Aplikace serveru Blazor                            | [blazorserver](#blazorserver)   | Jazyk         | Web/Blazor                            | 3.0        |
| ASP.NET Core prázdné                           | [webovém](#web)                     | [C#], F #     | Web/prázdné                             | 1.0        |
| ASP.NET Core webová aplikace (model-zobrazení-kontroler) | [Návrhový](#web-options)             | [C#], F #     | Web/MVC                               | 1.0        |
| ASP.NET Core webové aplikace                         | [WebApp, Razor](#web-options)   | Jazyk         | Web/MVC/Razor Pages                   | 2,2, 2,0   |
| ASP.NET Core s úhlovým                    | [Angular](#spa)                 | Jazyk         | Web/MVC/SPA                           | 2.0        |
| ASP.NET Core s reagují. js                   | [reaguje](#spa)                   | Jazyk         | Web/MVC/SPA                           | 2.0        |
| ASP.NET Core s využitím reagují. js a Redux         | [reactredux](#reactredux)       | Jazyk         | Web/MVC/SPA                           | 2.0        |
| Knihovna tříd Razor                          | [razorclasslib](#razorclasslib) | Jazyk         | Knihovna tříd web/Razor/Library/Razor | 2.1        |
| Webové rozhraní API ASP.NET Core                         | [WebApi](#webapi)               | [C#], F #     | Web/WebAPI                            | 1.0        |
| Služba ASP.NET Core gRPC                    | [grpc](#web-others)             | Jazyk         | Web/gRPC                              | 3.0        |
| soubor dotnet gitignore                        | `gitignore`                     |              | Config                                | 3.0        |
| soubor Global. JSON                             | [globaljson](#globaljson)       |              | Config                                | 2.0        |
| Konfigurace NuGet                                 | `nugetconfig`                   |              | Config                                | 1.0        |
| Dotnet – místní nástroj soubor manifestu              | `tool-manifest`                 |              | Config                                | 3.0        |
| Webová konfigurace                                   | `webconfig`                     |              | Config                                | 1.0        |
| Soubor řešení                                | `sln`                           |              | Řešení                              | 1.0        |
| Soubor vyrovnávací paměti protokolu                         | [Proto](#namespace)             |              | Web/gRPC                              | 3.0        |

## <a name="options"></a>Možnosti

- **`--dry-run`**

  Zobrazí souhrnné informace o tom, co se stane, pokud by došlo ke spuštění daného příkazu, pokud by to vedlo k vytvoření šablony. K dispozici od verze .NET Core 2,2 SDK.

- **`--force`**

  Vynutí vygenerování obsahu i v případě, že změní existující soubory. Tato možnost je vyžadována, pokud by vybraná šablona přepsala existující soubory ve výstupním adresáři.

- **`-h|--help`**

  Vytiskne nápovědu k příkazu. Dá se vyvolat pro samotný `dotnet new` příkaz nebo pro libovolnou šablonu. Například, `dotnet new mvc --help`.

- **`-i|--install <PATH|NUGET_ID>`**

  Nainstaluje sadu šablon z `PATH` nebo `NUGET_ID` poskytnuté. Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`. Ve výchozím nastavení `dotnet new` se \* předá verze, která představuje nejnovější stabilní verzi balíčku. Podívejte se na příklad v části [Příklady](#examples) .
  
  Pokud byla verze šablony již nainstalována při spuštění tohoto příkazu, šablona bude aktualizována na určenou verzi nebo na nejnovější stabilní verzi, pokud nebyla zadána žádná verze.

  Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).

- **`-l|--list`**

  Vypíše seznam šablon, které obsahují zadaný název. Pokud není zadán žádný název, vypíše všechny šablony.

- **`-lang|--language {C#|F#|VB}`**

  Jazyk šablony, která se má vytvořit Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ). Pro některé šablony není platná.

  > [!NOTE]
  > Některá prostředí jsou interpretována `#` jako speciální znak. V těchto případech uveďte hodnotu parametru Language v uvozovkách. Například, `dotnet new console -lang "F#"`.

- **`-n|--name <OUTPUT_NAME>`**

  Název vytvořeného výstupu. Pokud název nezadáte, použije se název aktuálního adresáře.

- **`--nuget-source <SOURCE>`**

  Určuje zdroj NuGet, který se použije při instalaci. K dispozici od verze .NET Core 2,1 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Umístění, do kterého se má vygenerovaný výstup umístit. Výchozí je aktuální adresář.

- **`--type <TYPE>`**

  Filtruje šablony založené na dostupných typech. Předdefinované hodnoty jsou `project`, `item`a `other`.

- **`-u|--uninstall [PATH|NUGET_ID]`**

  Odinstaluje sadu šablon na `PATH` nebo `NUGET_ID` poskytnutou. Pokud `<PATH|NUGET_ID>` hodnota není zadaná, zobrazí se všechny aktuálně nainstalované sady šablon a jejich přidružené šablony. Při zadávání `NUGET_ID`nezahrnujte číslo verze.

  Pokud neurčíte parametr této možnosti, příkaz zobrazí seznam nainstalovaných šablon a podrobností.

  > [!NOTE]
  > Chcete-li odinstalovat šablonu pomocí `PATH`nástroje, je nutné plně kvalifikovat cestu. Například *C:/Users/\<User>/Documents/Templates/garciasoftware.consoletemplate.CSharp* bude fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.
  > Do cesty k šabloně nezahrnujte konečné koncové lomítko adresáře.

- **`--update-apply`**

  Kontroluje, zda jsou k dispozici aktualizace pro sady šablon, které jsou aktuálně nainstalovány a instalovány. K dispozici od verze .NET Core 3,0 SDK.

- **`--update-check`**

  Kontroluje, zda jsou k dispozici aktualizace pro sady šablon, které jsou aktuálně nainstalovány. K dispozici od verze .NET Core 3,0 SDK.

## <a name="template-options"></a>Možnosti šablon

Každá šablona projektu může mít k dispozici další možnosti. Základní šablony mají následující další možnosti:

### <a name="console"></a>konzola

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. K dispozici od verze .NET Core 3,0 SDK.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--langVersion <VERSION_NUMBER>`**

  Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu. Například použijte `--langVersion 7.3` k použití jazyka C# 7,3. Nepodporováno v jazyce F #. K dispozici od verze .NET Core 2,2 SDK.

  Seznam výchozích verzí jazyka C# naleznete v tématu [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Je-li tento parametr zadán, nespustí při vytváření projektu implicitní obnovení. K dispozici od verze .NET Core 2,2 SDK.

***

### <a name="classlib"></a>že knihovna tříd

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Hodnoty: `netcoreapp<version>` pro vytvoření knihovny tříd .NET Core nebo `netstandard<version>` pro vytvoření knihovny tříd .NET Standard. Výchozí hodnota je `netstandard2.0`.

- **`--langVersion <VERSION_NUMBER>`**

  Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu. Například použijte `--langVersion 7.3` k použití jazyka C# 7,3. Nepodporováno v jazyce F #. K dispozici od verze .NET Core 2,2 SDK.

  Seznam výchozích verzí jazyka C# naleznete v tématu [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

***

### <a name="wpf-wpflib-wpfcustomcontrollib-wpfusercontrollib"></a><a name="wpf"></a>WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Výchozí hodnota je `netcoreapp3.1`. K dispozici od verze .NET Core 3,1 SDK.

- **`--langVersion <VERSION_NUMBER>`**

  Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu. Například použijte `--langVersion 7.3` k použití jazyka C# 7,3.

  Seznam výchozích verzí jazyka C# naleznete v tématu [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

***

### <a name="winforms-winformslib"></a><a name="winforms"></a>WinForms, winformslib

- **`--langVersion <VERSION_NUMBER>`**

  Nastaví `LangVersion` vlastnost v souboru vytvořeného projektu. Například použijte `--langVersion 7.3` k použití jazyka C# 7,3.

  Seznam výchozích verzí jazyka C# naleznete v tématu [Defaults](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

***

### <a name="worker-grpc"></a><a name="web-others"></a>pracovní proces, grpc

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Výchozí hodnota je `netcoreapp3.1`. K dispozici od verze .NET Core 3,1 SDK.

- **`--exclude-launch-settings`**

  Vyloučí z vygenerované šablony *launchSettings. JSON* .

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

***

### <a name="mstest-xunit"></a><a name="test"></a>MSTest, xUnit

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Možnost je k dispozici od verze .NET Core 3,0 SDK.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`-p|--enable-pack`**

  Umožňuje sbalení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

***

### <a name="nunit"></a>nunit

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2,2         | `netcoreapp2.2` |
  | 2.1         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  Umožňuje sbalení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

***

### <a name="page"></a>Page

- **`-na|--namespace <NAMESPACE_NAME>`**

  Obor názvů pro vygenerovaný kód. Výchozí hodnota je `MyApp.Namespace`.

- **`-np|--no-pagemodel`**

  Vytvoří stránku bez PageModel.

***

### <a name="viewimports-proto"></a><a name="namespace"></a>viewimports, a proto

- **`-na|--namespace <NAMESPACE_NAME>`**

  Obor názvů pro vygenerovaný kód. Výchozí hodnota je `MyApp.Namespace`.

***

### <a name="blazorserver"></a>blazorserver

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ ověřování, které se má použít. Možné hodnoty jsou:

  - `None`-Bez ověřování (výchozí).
  - `Individual`-Individuální ověřování.
  - `IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.
  - `SingleOrg`– Ověřování organizace pro jednoho tenanta.
  - `MultiOrg`– Ověřování organizace pro více tenantů.
  - `Windows`– Ověřování systému Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Instance Azure Active Directory B2C pro připojení. Použijte s `IndividualB2C` ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  ID zásad přihlášení a registrace pro tento projekt. Použijte s `IndividualB2C` ověřováním.

- **`-rp|--reset-password-policy-id <ID>`**

  ID zásad pro resetování hesla pro tento projekt. Použijte s `IndividualB2C` ověřováním.

- **`-ep|--edit-profile-policy-id <ID>`**

  Upravit ID zásad profilu pro tento projekt. Použijte s `IndividualB2C` ověřováním.

- **`--aad-instance <INSTANCE>`**

  Instance Azure Active Directory pro připojení. Použijte s `SingleOrg` ověřováním nebo `MultiOrg` . Výchozí hodnota je `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  ID klienta pro tento projekt. Použijte s `IndividualB2C`ověřováním `SingleOrg`, `MultiOrg` nebo. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Doména pro tenanta adresáře. Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` . Výchozí hodnota je `qualified.domain.name`.

- **`--tenant-id <ID>`**

  ID TenantId adresáře, ke kterému se má připojit. Použijte s `SingleOrg` ověřováním. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Cesta požadavku v základní cestě identifikátoru URI přesměrování. Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` . Výchozí hodnota je `/signin-oidc`.

- **`-r|--org-read-access`**

  Povolí této aplikaci přístup pro čtení k adresáři. Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.

- **`--exclude-launch-settings`**

  Vyloučí z vygenerované šablony *launchSettings. JSON* .

- **`--no-https`**

  Vypne protokol HTTPS. Tato možnost platí pouze v `Individual`případě `IndividualB2C`, `SingleOrg` `MultiOrg` že se nepoužívá pro `--auth`.

- **`-uld|--use-local-db`**

  Určuje, že se má místo SQLite použít LocalDB. Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

***

### <a name="web"></a>web

- **`--exclude-launch-settings`**

  Vyloučí z vygenerované šablony *launchSettings. JSON* .

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Možnost není dostupná v sadě .NET Core 2,2 SDK.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

- **`--no-https`**

  Vypne protokol HTTPS.

***

### <a name="mvc-webapp"></a><a name="web-options"></a>MVC, WebApp

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ ověřování, které se má použít. Možné hodnoty jsou:

  - `None`-Bez ověřování (výchozí).
  - `Individual`-Individuální ověřování.
  - `IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.
  - `SingleOrg`– Ověřování organizace pro jednoho tenanta.
  - `MultiOrg`– Ověřování organizace pro více tenantů.
  - `Windows`– Ověřování systému Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Instance Azure Active Directory B2C pro připojení. Použijte s `IndividualB2C` ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  ID zásad přihlášení a registrace pro tento projekt. Použijte s `IndividualB2C` ověřováním.

- **`-rp|--reset-password-policy-id <ID>`**

  ID zásad pro resetování hesla pro tento projekt. Použijte s `IndividualB2C` ověřováním.

- **`-ep|--edit-profile-policy-id <ID>`**

  Upravit ID zásad profilu pro tento projekt. Použijte s `IndividualB2C` ověřováním.

- **`--aad-instance <INSTANCE>`**

  Instance Azure Active Directory pro připojení. Použijte s `SingleOrg` ověřováním nebo `MultiOrg` . Výchozí hodnota je `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  ID klienta pro tento projekt. Použijte s `IndividualB2C`ověřováním `SingleOrg`, `MultiOrg` nebo. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Doména pro tenanta adresáře. Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` . Výchozí hodnota je `qualified.domain.name`.

- **`--tenant-id <ID>`**

  ID TenantId adresáře, ke kterému se má připojit. Použijte s `SingleOrg` ověřováním. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Cesta požadavku v základní cestě identifikátoru URI přesměrování. Použijte s `SingleOrg` ověřováním nebo `IndividualB2C` . Výchozí hodnota je `/signin-oidc`.

- **`-r|--org-read-access`**

  Povolí této aplikaci přístup pro čtení k adresáři. Platí jenom pro `SingleOrg` nebo `MultiOrg` ověřování.

- **`--exclude-launch-settings`**

  Vyloučí z vygenerované šablony *launchSettings. JSON* .

- **`--no-https`**

  Vypne protokol HTTPS. Tato možnost platí pouze v `Individual`případě `IndividualB2C`, `SingleOrg`že se `MultiOrg` nepoužívají, nebo.

- **`-uld|--use-local-db`**

  Určuje, že se má místo SQLite použít LocalDB. Platí jenom pro `Individual` nebo `IndividualB2C` ověřování.

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Možnost je k dispozici od verze .NET Core 3,0 SDK.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

- **`--use-browserlink`**

  Zahrnuje BrowserLink do projektu. V rozhraní .NET Core 2,2 a 3,1 SDK není dostupná možnost.

- **`-rrc|--razor-runtime-compilation`**

  Určuje, jestli je projekt nakonfigurovaný tak, aby používal [kompilaci za běhu Razor](/aspnet/core/mvc/views/view-compilation#runtime-compilation) v sestaveních ladění. Možnost je k dispozici od 3.1.201 sady .NET Core SDK.

***

### <a name="angular-react"></a><a name="spa"></a>Úhlová, reakce

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ ověřování, které se má použít. K dispozici od verze .NET Core 3,0 SDK.
  
  Možné hodnoty jsou:

  - `None`-Bez ověřování (výchozí).
  - `Individual`-Individuální ověřování.

- **`--exclude-launch-settings`**

  Vyloučí z vygenerované šablony *launchSettings. JSON* .

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

- **`--no-https`**

  Vypne protokol HTTPS. Tato možnost platí pouze v případě, `None`že je ověřování.

- **`-uld|--use-local-db`**

  Určuje, že se má místo SQLite použít LocalDB. Platí jenom pro `Individual` nebo `IndividualB2C` ověřování. K dispozici od verze .NET Core 3,0 SDK.

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Možnost není dostupná v sadě .NET Core 2,2 SDK.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

***

### <a name="reactredux"></a>reactredux

- **`--exclude-launch-settings`**

  Vyloučí z vygenerované šablony *launchSettings. JSON* .

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Možnost není dostupná v sadě .NET Core 2,2 SDK.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.0` |

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

- **`--no-https`**

  Vypne protokol HTTPS.

***

### <a name="razorclasslib"></a>razorclasslib

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

- **`-s|--support-pages-and-views`**

  Podporuje kromě součástí do této knihovny i tradiční zobrazení a stránky Razor. K dispozici od verze .NET Core 3,0 SDK.

***
  
### <a name="webapi"></a>WebApi

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ ověřování, které se má použít. Možné hodnoty jsou:

  - `None`-Bez ověřování (výchozí).
  - `IndividualB2C`-Jednotlivá ověřování pomocí Azure AD B2C.
  - `SingleOrg`– Ověřování organizace pro jednoho tenanta.
  - `Windows`– Ověřování systému Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Instance Azure Active Directory B2C pro připojení. Použijte s `IndividualB2C` ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  ID zásad přihlášení a registrace pro tento projekt. Použijte s `IndividualB2C` ověřováním.

- **`--aad-instance <INSTANCE>`**

  Instance Azure Active Directory pro připojení. Použijte s `SingleOrg` ověřováním. Výchozí hodnota je `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  ID klienta pro tento projekt. Použijte s `IndividualB2C` ověřováním nebo `SingleOrg` . Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Doména pro tenanta adresáře. Použijte s `IndividualB2C` ověřováním nebo `SingleOrg` . Výchozí hodnota je `qualified.domain.name`.

- **`--tenant-id <ID>`**

  ID TenantId adresáře, ke kterému se má připojit. Použijte s `SingleOrg` ověřováním. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

- **`-r|--org-read-access`**

  Povolí této aplikaci přístup pro čtení k adresáři. Platí jenom pro `SingleOrg` ověřování.

- **`--exclude-launch-settings`**

  Vyloučí z vygenerované šablony *launchSettings. JSON* .

- **`--no-https`**

  Vypne protokol HTTPS. `app.UseHsts`a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`. Tato možnost se vztahuje jenom `IndividualB2C` na `SingleOrg` to, jestli se nepoužívají pro ověřování.

- **`-uld|--use-local-db`**

  Určuje, že se má místo SQLite použít LocalDB. Platí jenom pro `IndividualB2C` ověřování.

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Možnost není dostupná v sadě .NET Core 2,2 SDK.

  V následující tabulce jsou uvedeny výchozí hodnoty podle čísla verze sady SDK, který používáte:

  | SDK version (Verze sady SDK) | Výchozí hodnota   |
  |-------------|-----------------|
  | 3.1         | `netcoreapp3.1` |
  | 3.0         | `netcoreapp3.0` |
  | 2.1         | `netcoreapp2.1` |

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

***

### <a name="globaljson"></a>globaljson

- **`--sdk-version <VERSION_NUMBER>`**

  Určuje verzi .NET Core SDK, která se má použít v souboru *Global. JSON* .

***

## <a name="examples"></a>Příklady

- Vytvořte projekt konzolové aplikace v jazyce C# zadáním názvu šablony:

  ```dotnetcli
  dotnet new "Console Application"
  ```

- Vytvořte projekt konzolové aplikace F # v aktuálním adresáři:

  ```dotnetcli
  dotnet new console -lang F#
  ```

- Vytvořte .NET Standard projekt knihovny tříd v zadaném adresáři:

  ```dotnetcli
  dotnet new classlib -lang VB -o MyLibrary
  ```

- Vytvoří nový projekt ASP.NET Core C# MVC v aktuálním adresáři bez ověřování:

  ```dotnetcli
  dotnet new mvc -au None
  ```

- Vytvořit nový projekt xUnit:

  ```dotnetcli
  dotnet new xunit
  ```

- Vypíše všechny šablony, které jsou k dispozici pro šablony jednostránkové aplikace (SPA):

  ```dotnetcli
  dotnet new spa -l
  ```

- Vypíše všechny šablony, které odpovídají podřetězci *My* . Nebyla nalezena žádná přesná shoda, takže porovnávání dílčích řetězců se shoduje se sloupci krátkého názvu a názvu.

  ```dotnetcli
  dotnet new we -l
  ```

- Došlo k pokusu o vyvolání šablony, která odpovídá *NG*. Pokud nelze určit jednu shodu, Seznamte se se šablonami, které jsou částečné shody.

  ```dotnetcli
  dotnet new ng
  ```

- Nainstalujte verzi 2,0 šablon SPA pro ASP.NET Core:

  ```dotnetcli
  dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.0.0
  ```

- Seznam nainstalovaných šablon a podrobností, včetně jejich odinstalace:

  ```dotnetcli
  dotnet new -u
  ```

- V aktuálním adresáři vytvořte *Global. JSON* s nastavením verze sady SDK na 3.1.101:

  ```dotnetcli
  dotnet new globaljson --sdk-version 3.1.101
  ```

## <a name="see-also"></a>Viz také

- [Vlastní šablony pro dotnet New](custom-templates.md)
- [Vytvoření vlastní šablony pro dotnet new](../tutorials/cli-templates-create-item-template.md)
- [dotnet/dotnet-Template-Samples – úložiště GitHub](https://github.com/dotnet/dotnet-template-samples)
- [Dostupné šablony pro dotnet New](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
