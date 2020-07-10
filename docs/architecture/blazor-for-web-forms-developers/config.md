---
title: Konfigurace aplikací
description: Naučte se konfigurovat Blazor aplikace bez použití ConfigurationManager.
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 04/01/2020
ms.openlocfilehash: a13f663c2c6908ba906e42cb939c3b8707b8cccd
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173312"
---
# <a name="app-configuration"></a>Konfigurace aplikací

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Hlavní způsob, jak načíst konfiguraci aplikace ve webových formulářích, je s položkami v *web.configm* souboru &mdash; buď na serveru, nebo v souvisejícím konfiguračním souboru, na který odkazuje *web.config*. Statický objekt můžete použít `ConfigurationManager` k interakci s nastavením aplikace, připojovacími řetězci úložiště dat a dalšími poskytovateli rozšířených konfigurací, které jsou přidány do aplikace. Je typický vidět interakce s konfigurací aplikace, jak je vidět v následujícím kódu:

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

Při ASP.NET Core a na straně serveru Blazor může být k dispozici soubor *web.config* , pokud je vaše aplikace hostovaná na serveru Windows IIS. Neexistuje ale žádná `ConfigurationManager` interakce s touto konfigurací a můžete získat více strukturovaných konfigurací aplikace z jiných zdrojů. Pojďme se podívat na to, jak se bude shromažďovat konfigurace a jak pořád máte přístup k informacím o konfiguraci ze souboru *web.config* .

## <a name="configuration-sources"></a>Zdroje konfigurace

ASP.NET Core rozpozná, že existuje mnoho zdrojů konfigurace, které můžete chtít použít pro vaši aplikaci. Rámec se ve výchozím nastavení pokusí nabídnout nejlepší z těchto funkcí. Konfigurace je čtená a agregovaná z těchto různých zdrojů ASP.NET Core. Novější načtené hodnoty pro stejný konfigurační klíč mají přednost před předchozími hodnotami.

ASP.NET Core byla navržena jako cloudová a umožňuje snazší konfiguraci aplikací pro oba operátory i vývojáře. ASP.NET Core je s ohledem na prostředí a ví, jestli je spuštěný ve vašem `Production` `Development` prostředí nebo. Indikátor prostředí je nastaven v `ASPNETCORE_ENVIRONMENT` proměnné prostředí systému. Pokud není nakonfigurovaná žádná hodnota, aplikace se ve výchozím nastavení spustí v `Production` prostředí.

Vaše aplikace může aktivovat a přidat konfiguraci z několika zdrojů na základě názvu prostředí. Ve výchozím nastavení je konfigurace načtena z následujících zdrojů v uvedeném pořadí:

1. *appsettings.jsv* souboru, pokud je k dispozici
1. *appSettings. Soubor {ENVIRONMENT_NAME}. JSON* (Pokud je k dispozici)
1. Soubor tajných klíčů uživatele na disku, pokud je k dispozici
1. Proměnné prostředí
1. Argumenty příkazového řádku

## <a name="appsettingsjson-format-and-access"></a>appsettings.jspro formát a přístup

*appsettings.js* souboru může být hierarchicky s hodnotami strukturovanými, jako je následující JSON:

```json
{
  "section0": {
    "key0": "value",
    "key1": "value"
  },
  "section1": {
    "key0": "value",
    "key1": "value"
  }
}
```

Při předložení s předchozím JSON konfigurační systém sloučí podřízené hodnoty a odkazuje na jejich plně kvalifikované hierarchické cesty. Znak dvojtečky ( `:` ) odděluje každou vlastnost v hierarchii. Například konfigurační klíč `section1:key0` přistupuje k `section1` hodnotě literálu objektu `key0` .

## <a name="user-secrets"></a>Tajné klíče uživatele

Uživatelské tajné klíče:

* Hodnoty konfigurace, které jsou uloženy v souboru JSON pracovní stanice vývojáře, mimo složku pro vývoj aplikací.
* Načte se jenom při spuštění v `Development` prostředí.
* Přidruženo ke konkrétní aplikaci.
* Spravované pomocí `user-secrets` příkazu .NET Core CLI.

Nakonfigurujte aplikaci pro tajné úložiště spuštěním `user-secrets` příkazu:

```dotnetcli
dotnet user-secrets init
```

Předchozí příkaz přidá `UserSecretsId` prvek do souboru projektu. Element obsahuje identifikátor GUID, který se používá k přidružení tajných kódů k aplikaci. Pak můžete pomocí příkazu definovat tajný klíč `set` . Příklad:

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

Předchozí příkaz zpřístupní `Parent:ApiKey` konfigurační klíč v pracovní stanici vývojáře s hodnotou `12345` .

Další informace o vytváření, ukládání a správě uživatelských tajných klíčů najdete v [bezpečném úložišti tajných kódů aplikací ve vývoji v dokumentu ASP.NET Core](/aspnet/core/security/app-secrets) .

## <a name="environment-variables"></a>Proměnné prostředí

Další sadou hodnot načtených do vaší konfigurace aplikace jsou proměnné prostředí systému. Všechna nastavení proměnných prostředí vašeho systému jsou teď přístupná prostřednictvím rozhraní API pro konfiguraci. Hierarchické hodnoty jsou shrnuty a odděleny čárkami při čtení v aplikaci. Některé operační systémy však nepovolují názvy proměnných prostředí dvojtečky. ASP.NET Core řeší toto omezení převedením hodnot, které mají dvojité podtržítka ( `__` ), do dvojtečky při jejich použití. `Parent:ApiKey`Hodnota výše uvedeného oddílu tajné klíče uživatele se dá přepsat proměnnou prostředí `Parent__ApiKey` .

## <a name="command-line-arguments"></a>Argumenty příkazového řádku

Konfiguraci lze také zadat jako argumenty příkazového řádku při spuštění aplikace. Použijte notaci Double-spojovník ( `--` ) nebo lomítko ( `/` ) k označení názvu konfigurační hodnoty, kterou chcete nastavit a hodnotu, která má být nakonfigurována. Syntaxe se podobá následujícím příkazům:

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a>Vrácení web.config

Pokud jste aplikaci nasadili na Windows ve službě IIS, *web.config* soubor stále NAKONFIGURUJE službu IIS pro správu vaší aplikace. Služba IIS ve výchozím nastavení přidá odkaz na modul ASP.NET Core (ANCM). ANCM je nativní modul služby IIS, který hostuje vaši aplikaci místo webového serveru Kestrel. Tento *web.config* oddíl se podobá následujícímu kódu XML:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\MyApp.exe"
                  stdoutLogEnabled="false"
                  stdoutLogFile=".\logs\stdout"
                  hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

Konfiguraci specifickou pro aplikaci lze definovat vnořením `environmentVariables` elementu v `aspNetCore` elementu. Hodnoty definované v této části se zobrazí ASP.NET Core aplikaci jako proměnné prostředí. Proměnné prostředí se při spuštění aplikace patřičně načítají.

```xml
<aspNetCore processPath="dotnet"
      arguments=".\MyApp.dll"
      stdoutLogEnabled="false"
      stdoutLogFile=".\logs\stdout"
      hostingModel="inprocess">
  <environmentVariables>
    <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Development" />
    <environmentVariable name="Parent:ApiKey" value="67890" />
  </environmentVariables>
</aspNetCore>
```

## <a name="read-configuration-in-the-app"></a>Čtení konfigurace v aplikaci

ASP.NET Core poskytuje konfiguraci aplikace prostřednictvím <xref:Microsoft.Extensions.Configuration.IConfiguration> rozhraní. Toto konfigurační rozhraní by mělo požadovat vaše Blazor komponenty, Blazor stránky a všechny další ASP.NET Core spravované třídy, které potřebují přístup ke konfiguraci. Rozhraní ASP.NET Core Framework automaticky naplní toto rozhraní s vyřešenou konfigurací nakonfigurovanou dříve. Na Blazor stránce nebo v kódu Razor komponenty můžete vložit `IConfiguration` objekt s `@inject` direktivou v horní části souboru *. Razor* takto:

```razor
@inject IConfiguration Configuration
```

Tento předchozí příkaz zpřístupní `IConfiguration` objekt jako `Configuration` proměnnou v celé zbývající části šablony Razor.

Jednotlivá nastavení konfigurace je možné přečíst zadáním hierarchie nastavení konfigurace, kterou si můžete vyžádat jako parametr indexeru:

```csharp
var mySetting = Configuration["section1:key0"];
```

Můžete načíst celé konfigurační oddíly pomocí <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> metody pro načtení kolekce klíčů v určitém umístění s syntaxí podobnou syntaxi pro `GetSection("section1")` načtení konfigurace pro Section1 z předchozího příkladu.

## <a name="strongly-typed-configuration"></a>Konfigurace silného typu

S webovými formuláři bylo možné vytvořit typ konfigurace silného typu, který je zděděný z <xref:System.Configuration.ConfigurationSection> typu a přidružených typů. Umožňuje `ConfigurationSection` nakonfigurovat některá obchodní pravidla a zpracování pro tyto hodnoty konfigurace.

V ASP.NET Core můžete určit hierarchii tříd, která bude přijímat hodnoty konfigurace. Tyto třídy:

* Není nutné dědit z nadřazené třídy.
* By měly obsahovat `public` vlastnosti, které odpovídají vlastnostem a odkazy na typy pro konfigurační strukturu, kterou chcete zachytit.

Pro předchozí *appsettings.jsv* ukázce můžete definovat následující třídy pro zachycení hodnot:

```csharp
public class MyConfig
{
    public MyConfigSection section0 { get; set;}

    public MyConfigSection section1 { get; set;}
}

public class MyConfigSection
{
    public string key0 { get; set; }

    public string key1 { get; set; }
}
```

Tuto hierarchii tříd lze naplnit přidáním následujícího řádku do `Startup.ConfigureServices` metody:

```csharp
services.Configure<MyConfig>(Configuration);
```

Ve zbývající části aplikace můžete přidat vstupní parametr do tříd nebo `@inject` direktivy v šablonách Razor typu `IOptions<MyConfig>` pro získání nastavení konfigurace silného typu. `IOptions<MyConfig>.Value`Vlastnost vrátí `MyConfig` hodnotu naplněnou z nastavení konfigurace.

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

Další informace o funkci Options najdete ve [vzoru možností v dokumentu ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) .

>[!div class="step-by-step"]
>[Předchozí](middleware.md) 
> [Další](security-authentication-authorization.md)
