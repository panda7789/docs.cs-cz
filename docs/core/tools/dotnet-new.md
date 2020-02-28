---
title: dotnet – nový příkaz
description: Příkaz dotnet New vytvoří nové projekty .NET Core založené na zadané šabloně.
ms.date: 02/13/2020
ms.openlocfilehash: d3c609419596b123f5bfb3ca85cf292a61154a70
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157216"
---
# <a name="dotnet-new"></a>dotnet new

**Tento článek se týká:** ✔️ .net Core 2,0 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet new` – vytvoří nový projekt, konfigurační soubor nebo řešení na základě zadané šablony.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet new <TEMPLATE> [--dry-run] [--force] [-i|--install] [-lang|--language] [-n|--name]
    [--nuget-source] [-o|--output] [-u|--uninstall] [--update-apply] [--update-check] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```

## <a name="description"></a>Popis

Příkaz `dotnet new` vytvoří projekt .NET Core nebo jiné artefakty založené na šabloně.

Příkaz volá [modul šablony](https://github.com/dotnet/templating) a vytvoří artefakty na disku na základě zadané šablony a možností.

## <a name="arguments"></a>Argumenty

- **`TEMPLATE`**

  Šablona, která se má vytvořit při vyvolání příkazu Každá šablona může mít konkrétní možnosti, které můžete předat. Další informace najdete v tématu [Možnosti šablony](#template-options).

  Můžete spustit `dotnet new --list`, abyste zobrazili seznam všech nainstalovaných šablon. Pokud hodnota `TEMPLATE` není přesná shoda na textu v **šablonách** nebo ve sloupci **krátký název** z vrácené tabulky, provede se shoda podřetězce na těchto dvou sloupcích.

  Počínaje verzí .NET Core 3,0 SDK vyhledává CLI šablony v NuGet.org při vyvolání příkazu `dotnet new` v následujících podmínkách:

  - Pokud rozhraní příkazového řádku nemůže najít shodu šablony při vyvolání `dotnet new`, a ne i částečně.
  - Pokud je k dispozici novější verze šablony. V tomto případě se vytvoří projekt nebo artefakt, ale rozhraní příkazového řádku vás upozorní na aktualizovanou verzi šablony.

  Příkaz obsahuje výchozí seznam šablon. Seznam dostupných šablon můžete získat pomocí `dotnet new -l`. Následující tabulka obsahuje šablony, které jsou předinstalované s .NET Core SDK. Výchozí jazyk pro šablonu se zobrazí v závorkách. Kliknutím na odkaz krátké jméno zobrazíte konkrétní možnosti šablony.

| Šablony                                    | Krátký název                      | Jazyk     | Značky                                  | Vedou |
|----------------------------------------------|---------------------------------|--------------|---------------------------------------|------------|
| Konzolová aplikace                          | [stromu](#console)             | [C#], F#, VB | Společná/konzola                        | 1.0        |
| Knihovna tříd                                | [že knihovna tříd](#classlib)           | [C#], F#, VB | Společné/knihovny                        | 1.0        |
| Aplikace WPF                              | [subsystém](#wpf)                     | [C#]         | Common/WPF                            | 3.0        |
| WPF – knihovna tříd                            | [wpflib](#wpf)                  | [C#]         | Common/WPF                            | 3.0        |
| Knihovna vlastních ovládacích prvků WPF                   | [wpfcustomcontrollib](#wpf)     | [C#]         | Common/WPF                            | 3.0        |
| Knihovna uživatelských ovládacích prvků WPF                     | [wpfusercontrollib](#wpf)       | [C#]         | Common/WPF                            | 3.0        |
| Aplikace model Windows Forms (WinForms)         | [WinForms](#winforms)           | [C#]         | Common/WinForms                       | 3.0        |
| Knihovna tříd model Windows Forms (WinForms)       | [winformslib](#winforms)        | [C#]         | Common/WinForms                       | 3.0        |
| Služba pracovního procesu                               | [zaměstnanec](#web-others)           | [C#]         | Common/Work/Web                     | 3.0        |
| Projekt testu jednotek                            | [MSTest](#test)                 | [C#], F#, VB | Test/MSTest                           | 1.0        |
| Projekt testů NUnit 3                         | [nunit](#nunit)                  | [C#], F#, VB | Test/NUnit                            | 2.1.400    |
| NUnit 3 položka testu                            | `nunit-test`                    | [C#], F#, VB | Test/NUnit                            | 2.2        |
| Projekt testů xUnit                           | [xUnit](#test)                  | [C#], F#, VB | Test/xUnit                            | 1.0        |
| Komponenta Razor                              | `razorcomponent`                | [C#]         | Web/ASP.NET                           | 3.0        |
| Stránka Razor                                   | [Page](#page)                   | [C#]         | Web/ASP.NET                           | 2.0        |
| ViewImports MVC                              | [viewimports](#namespace)       | [C#]         | Web/ASP.NET                           | 2.0        |
| ViewStart MVC                                | `viewstart`                     | [C#]         | Web/ASP.NET                           | 2.0        |
| Aplikace serveru Blazor                            | [blazorserver](#blazorserver)   | [C#]         | Web/Blazor                            | 3.0        |
| ASP.NET Core prázdné                           | [webovém](#web)                     | [C#], F#     | Web/prázdné                             | 1.0        |
| ASP.NET Core webová aplikace (model-zobrazení-kontroler) | [Návrhový](#web-options)             | [C#], F#     | Web/MVC                               | 1.0        |
| ASP.NET Core webové aplikace                         | [WebApp, Razor](#web-options)   | [C#]         | Web/MVC/Razor Pages                   | 2,2, 2,0   |
| ASP.NET Core s úhlovým                    | [Angular](#spa)                 | [C#]         | Web/MVC/SPA                           | 2.0        |
| ASP.NET Core s reagují. js                   | [reaguje](#spa)                   | [C#]         | Web/MVC/SPA                           | 2.0        |
| ASP.NET Core s využitím reagují. js a Redux         | [reactredux](#reactredux)       | [C#]         | Web/MVC/SPA                           | 2.0        |
| Knihovna tříd Razor                          | [razorclasslib](#razorclasslib) | [C#]         | Knihovna tříd web/Razor/Library/Razor | 2.1        |
| Webové rozhraní API ASP.NET Core                         | [WebApi](#webapi)               | [C#], F#     | Web/WebAPI                            | 1.0        |
| Služba ASP.NET Core gRPC                    | [grpc](#web-others)             | [C#]         | Web/gRPC                              | 3.0        |
| Soubor vyrovnávací paměti protokolu                         | [Proto](#namespace)             |              | Web/gRPC                              | 3.0        |
| soubor dotnet gitignore                        | `gitignore`                     |              | Config                                | 3.0        |
| global.json file                             | [globaljson](#globaljson)       |              | Config                                | 2.0        |
| Konfigurace NuGet                                 | `nugetconfig`                   |              | Config                                | 1.0        |
| dotnet – místní nástroj soubor manifestu              | `tool-manifest`                 |              | Config                                | 3.0        |
| Webová konfigurace                                   | `webconfig`                     |              | Config                                | 1.0        |
| Soubor řešení                                | `sln`                           |              | Řešení                              | 1.0        |

## <a name="options"></a>Možnosti

- **`--dry-run`**

  Zobrazí souhrn toho, co se stane, když se spustí daný příkaz. K dispozici od verze .NET Core 2,2 SDK.

- **`--force`**

  Vynutí vygenerování obsahu i v případě, že změní existující soubory. Tato možnost je vyžadována, pokud by vybraná šablona přepsala existující soubory ve výstupním adresáři.

- **`-h|--help`**

  Vytiskne nápovědu k příkazu. Dá se vyvolat pro samotný příkaz `dotnet new` nebo pro libovolnou šablonu. například `dotnet new mvc --help`.

- **`-i|--install <PATH|NUGET_ID>`**

  Nainstaluje balíček šablon z `PATH` nebo `NUGET_ID` poskytnutý. Pokud chcete nainstalovat předprodejní verzi balíčku šablony, je nutné zadat verzi ve formátu `<package-name>::<package-version>`. Ve výchozím nastavení `dotnet new` předá verze \*, která představuje nejnovější stabilní verzi balíčku. Podívejte se na příklad v části [Příklady](#examples) .
  
  Pokud byla verze šablony již nainstalována při spuštění tohoto příkazu, šablona bude aktualizována na určenou verzi nebo na nejnovější stabilní verzi, pokud nebyla zadána žádná verze.

  Informace o vytváření vlastních šablon najdete v tématu [vlastní šablony pro dotnet New](custom-templates.md).

- **`-l|--list`**

  Vypíše seznam šablon, které obsahují zadaný název. Pokud není zadán žádný název, vypíše všechny šablony.

- **`-lang|--language {C#|F#|VB}`**

  Jazyk šablony, která se má vytvořit Přijatý jazyk se liší podle šablony (viz výchozí hodnoty v oddílu [argumenty](#arguments) ). Pro některé šablony není platná.

  > [!NOTE]
  > Některá prostředí interpretují `#` jako speciální znak. V těchto případech uveďte hodnotu parametru Language v uvozovkách. například `dotnet new console -lang "F#"`.

- **`-n|--name <OUTPUT_NAME>`**

  Název vytvořeného výstupu. Pokud název nezadáte, použije se název aktuálního adresáře.

- **`--nuget-source`**

  Určuje zdroj NuGet, který se použije při instalaci. K dispozici od verze .NET Core 2,1 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Umístění, do kterého se má vygenerovaný výstup umístit. Výchozí je aktuální adresář.

- **`--type`**

  Filtruje šablony založené na dostupných typech. Předdefinované hodnoty jsou "projekt", "položka" nebo "jiné".

- **`-u|--uninstall [PATH|NUGET_ID]`**

  Odinstaluje balíček šablon na `PATH` nebo `NUGET_ID` poskytnutý. Pokud není zadána hodnota `<PATH|NUGET_ID>`, zobrazí se všechny aktuálně nainstalované sady šablon a jejich přidružené šablony. Při zadávání `NUGET_ID`nezahrnujte číslo verze.

  Pokud neurčíte parametr této možnosti, příkaz zobrazí seznam nainstalovaných šablon a podrobností.

  > [!NOTE]
  > Chcete-li odinstalovat šablonu pomocí `PATH`, je nutné cestu plně kvalifikovat. Například *C:/uživatelé/\<USER >/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* budou fungovat, ale *./GarciaSoftware.ConsoleTemplate.CSharp* z nadřazené složky to nebude.
  > Do cesty k šabloně nezahrnujte konečné koncové lomítko adresáře.

- **`--update-apply`**

  Kontroluje, zda jsou k dispozici aktualizace pro sady šablon, které jsou aktuálně nainstalovány a instalovány. K dispozici od verze .NET Core 3,0 SDK.

- **`--update-check`**

  Kontroluje, zda jsou k dispozici aktualizace pro sady šablon, které jsou aktuálně nainstalovány. K dispozici od verze .NET Core 3,0 SDK.

## <a name="template-options"></a>Možnosti šablony

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

  Nastaví vlastnost `LangVersion` v souboru vytvořeného projektu. Například použijte `--langVersion 7.3` k použití C# 7,3. Nepodporuje se pro F#. K dispozici od verze .NET Core 2,2 SDK.

  Seznam výchozích C# verzí najdete v tématu [výchozí](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Je-li tento parametr zadán, nespustí při vytváření projektu implicitní obnovení. K dispozici od verze .NET Core 2,2 SDK.

***

### <a name="classlib"></a>že knihovna tříd

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Hodnoty: `netcoreapp<version>` pro vytvoření knihovny tříd .NET Core nebo `netstandard<version>` k vytvoření knihovny tříd .NET Standard. Výchozí hodnota je `netstandard2.0`.

- **`--langVersion <VERSION_NUMBER>`**

  Nastaví vlastnost `LangVersion` v souboru vytvořeného projektu. Například použijte `--langVersion 7.3` k použití C# 7,3. Nepodporuje se pro F#. K dispozici od verze .NET Core 2,2 SDK.

  Seznam výchozích C# verzí najdete v tématu [výchozí](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

***

### <a name="wpf"></a>WPF, wpflib, wpfcustomcontrollib, wpfusercontrollib

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Výchozí hodnota je `netcoreapp3.1`. K dispozici od verze .NET Core 3,1 SDK.

- **`--langVersion <VERSION_NUMBER>`**

  Nastaví vlastnost `LangVersion` v souboru vytvořeného projektu. Například použijte `--langVersion 7.3` k použití C# 7,3.

  Seznam výchozích C# verzí najdete v tématu [výchozí](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

***

### <a name="winforms"></a>WinForms, winformslib

- **`--langVersion <VERSION_NUMBER>`**

  Nastaví vlastnost `LangVersion` v souboru vytvořeného projektu. Například použijte `--langVersion 7.3` k použití C# 7,3.

  Seznam výchozích C# verzí najdete v tématu [výchozí](../../csharp/language-reference/configure-language-version.md#defaults).

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

***

### <a name="web-others"></a>pracovní proces, grpc

- **`-f|--framework <FRAMEWORK>`**

  Určuje [rozhraní](../../standard/frameworks.md) , které se má cílit. Výchozí hodnota je `netcoreapp3.1`. K dispozici od verze .NET Core 3,1 SDK.

- **`--exclude-launch-settings`**

  Vyloučí z vygenerované šablony *launchSettings. JSON* .

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

***

### <a name="test"></a>MSTest, xUnit

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
  | 2.2         | `netcoreapp2.2` |
  | 2.1         | `netcoreapp2.1` |

- **`-p|--enable-pack`**

  Umožňuje sbalení pro projekt pomocí [sady dotnet Pack](dotnet-pack.md).

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

***

### <a name="page"></a>stránka

- **`-na|--namespace <NAMESPACE_NAME>`**

  Obor názvů pro vygenerovaný kód. Výchozí hodnota je `MyApp.Namespace`.

- **`-np|--no-pagemodel`**

  Vytvoří stránku bez PageModel.

***

### <a name="namespace"></a>viewimports, a proto

- **`-na|--namespace <NAMESPACE_NAME>`**

  Obor názvů pro vygenerovaný kód. Výchozí hodnota je `MyApp.Namespace`.

***

### <a name="blazorserver"></a>blazorserver

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ ověřování, který má být použit. Možné hodnoty jsou:

  - `None` – bez ověřování (výchozí).
  - `Individual` – individuální ověřování.
  - `IndividualB2C` – individuální ověřování pomocí Azure AD B2C.
  - `SingleOrg` – ověřování organizace pro jednoho tenanta.
  - `MultiOrg` – ověřování organizace pro více tenantů.
  - `Windows` – ověřování systému Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Instance Azure Active Directory B2C pro připojení. Použijte s ověřováním `IndividualB2C`. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  ID zásad přihlášení a registrace pro tento projekt. Použijte s ověřováním `IndividualB2C`.

- **`-rp|--reset-password-policy-id <ID>`**

  ID zásad pro resetování hesla pro tento projekt. Použijte s ověřováním `IndividualB2C`.

- **`-ep|--edit-profile-policy-id <ID>`**

  Upravit ID zásad profilu pro tento projekt. Použijte s ověřováním `IndividualB2C`.

- **`--aad-instance <INSTANCE>`**

  Instance Azure Active Directory pro připojení. Použijte s ověřováním `SingleOrg` nebo `MultiOrg`. Výchozí hodnota je `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  ID klienta pro tento projekt. Použijte s ověřováním `IndividualB2C`, `SingleOrg`nebo `MultiOrg`. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Doména pro tenanta adresáře. Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`. Výchozí hodnota je `qualified.domain.name`.

- **`--tenant-id <ID>`**

  ID TenantId adresáře, ke kterému se má připojit. Použijte s ověřováním `SingleOrg`. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Cesta požadavku v základní cestě identifikátoru URI přesměrování. Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`. Výchozí hodnota je `/signin-oidc`.

- **`-r|--org-read-access`**

  Povolí této aplikaci přístup pro čtení k adresáři. Platí jenom pro ověřování `SingleOrg` nebo `MultiOrg`.

- **`--exclude-launch-settings`**

  Vyloučí z vygenerované šablony *launchSettings. JSON* .

- **`--no-https`**

  Vypne protokol HTTPS. Tato možnost se použije jenom v případě, že se pro `--auth`nepoužívají `Individual`, `IndividualB2C`, `SingleOrg`nebo `MultiOrg`.

- **`-uld|--use-local-db`**

  Určuje, že se má místo SQLite použít LocalDB. Platí jenom pro ověřování `Individual` nebo `IndividualB2C`.

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

### <a name="web-options"></a>MVC, WebApp

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ ověřování, který má být použit. Možné hodnoty jsou:

  - `None` – bez ověřování (výchozí).
  - `Individual` – individuální ověřování.
  - `IndividualB2C` – individuální ověřování pomocí Azure AD B2C.
  - `SingleOrg` – ověřování organizace pro jednoho tenanta.
  - `MultiOrg` – ověřování organizace pro více tenantů.
  - `Windows` – ověřování systému Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Instance Azure Active Directory B2C pro připojení. Použijte s ověřováním `IndividualB2C`. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  ID zásad přihlášení a registrace pro tento projekt. Použijte s ověřováním `IndividualB2C`.

- **`-rp|--reset-password-policy-id <ID>`**

  ID zásad pro resetování hesla pro tento projekt. Použijte s ověřováním `IndividualB2C`.

- **`-ep|--edit-profile-policy-id <ID>`**

  Upravit ID zásad profilu pro tento projekt. Použijte s ověřováním `IndividualB2C`.

- **`--aad-instance <INSTANCE>`**

  Instance Azure Active Directory pro připojení. Použijte s ověřováním `SingleOrg` nebo `MultiOrg`. Výchozí hodnota je `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  ID klienta pro tento projekt. Použijte s ověřováním `IndividualB2C`, `SingleOrg`nebo `MultiOrg`. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Doména pro tenanta adresáře. Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`. Výchozí hodnota je `qualified.domain.name`.

- **`--tenant-id <ID>`**

  ID TenantId adresáře, ke kterému se má připojit. Použijte s ověřováním `SingleOrg`. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

- **`--callback-path <PATH>`**

  Cesta požadavku v základní cestě identifikátoru URI přesměrování. Použijte s ověřováním `SingleOrg` nebo `IndividualB2C`. Výchozí hodnota je `/signin-oidc`.

- **`-r|--org-read-access`**

  Povolí této aplikaci přístup pro čtení k adresáři. Platí jenom pro ověřování `SingleOrg` nebo `MultiOrg`.

- **`--exclude-launch-settings`**

  Vyloučí z vygenerované šablony *launchSettings. JSON* .

- **`--no-https`**

  Vypne protokol HTTPS. Tato možnost se vztahuje jenom v případě, že se nepoužívají `Individual`, `IndividualB2C`, `SingleOrg`nebo `MultiOrg`.

- **`-uld|--use-local-db`**

  Určuje, že se má místo SQLite použít LocalDB. Platí jenom pro ověřování `Individual` nebo `IndividualB2C`.

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

***

### <a name="spa"></a>Úhlová, reakce

- **`-au|--auth <AUTHENTICATION_TYPE>`**

  Typ ověřování, který má být použit. K dispozici od verze .NET Core 3,0 SDK.
  
  Možné hodnoty jsou:

  - `None` – bez ověřování (výchozí).
  - `Individual` – individuální ověřování.

- **`--exclude-launch-settings`**

  Vyloučí z vygenerované šablony *launchSettings. JSON* .

- **`--no-restore`**

  Při vytváření projektu neprovede implicitní obnovení.

- **`--no-https`**

  Vypne protokol HTTPS. Tato možnost se vztahuje pouze v případě, že je ověřování `None`.

- **`-uld|--use-local-db`**

  Určuje, že se má místo SQLite použít LocalDB. Platí jenom pro ověřování `Individual` nebo `IndividualB2C`. K dispozici od verze .NET Core 3,0 SDK.

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

  Typ ověřování, který má být použit. Možné hodnoty jsou:

  - `None` – bez ověřování (výchozí).
  - `IndividualB2C` – individuální ověřování pomocí Azure AD B2C.
  - `SingleOrg` – ověřování organizace pro jednoho tenanta.
  - `Windows` – ověřování systému Windows.

- **`--aad-b2c-instance <INSTANCE>`**

  Instance Azure Active Directory B2C pro připojení. Použijte s ověřováním `IndividualB2C`. Výchozí hodnota je `https://login.microsoftonline.com/tfp/`.

- **`-ssp|--susi-policy-id <ID>`**

  ID zásad přihlášení a registrace pro tento projekt. Použijte s ověřováním `IndividualB2C`.

- **`--aad-instance <INSTANCE>`**

  Instance Azure Active Directory pro připojení. Použijte s ověřováním `SingleOrg`. Výchozí hodnota je `https://login.microsoftonline.com/`.

- **`--client-id <ID>`**

  ID klienta pro tento projekt. Použijte s ověřováním `IndividualB2C` nebo `SingleOrg`. Výchozí hodnota je `11111111-1111-1111-11111111111111111`.

- **`--domain <DOMAIN>`**

  Doména pro tenanta adresáře. Použijte s ověřováním `IndividualB2C` nebo `SingleOrg`. Výchozí hodnota je `qualified.domain.name`.

- **`--tenant-id <ID>`**

  ID TenantId adresáře, ke kterému se má připojit. Použijte s ověřováním `SingleOrg`. Výchozí hodnota je `22222222-2222-2222-2222-222222222222`.

- **`-r|--org-read-access`**

  Povolí této aplikaci přístup pro čtení k adresáři. Platí jenom pro ověřování `SingleOrg`.

- **`--exclude-launch-settings`**

  Vyloučí z vygenerované šablony *launchSettings. JSON* .

- **`--no-https`**

  Vypne protokol HTTPS. `app.UseHsts` a `app.UseHttpsRedirection` nejsou přidány do `Startup.Configure`. Tato možnost platí pouze v případě, že se pro ověřování nepoužívá `IndividualB2C` nebo `SingleOrg`.

- **`-uld|--use-local-db`**

  Určuje, že se má místo SQLite použít LocalDB. Platí jenom pro ověřování `IndividualB2C`.

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

- Vytvořte projekt C# konzolové aplikace zadáním názvu šablony:

  ```dotnetcli
  dotnet new "Console Application"
  ```

- Vytvořte projekt F# konzolové aplikace v aktuálním adresáři:

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
