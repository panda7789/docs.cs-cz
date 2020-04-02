---
title: Konfigurace aplikací
description: Přečtěte si, jak nakonfigurovat aplikace Blazor bez použití ConfigurationManageru.
author: csharpfritz
ms.author: jefritz
ms.date: 04/01/2020
ms.openlocfilehash: c780a395f72e2520af86c20c7f6618953a528ff7
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588250"
---
# <a name="app-configuration"></a>Konfigurace aplikací

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Primární způsob načtení konfigurace aplikace ve webových formulářích je&mdash;s položkami v souboru *web.config* buď na serveru, nebo souvisejícím konfiguračním souborem, na který odkazuje *web.config*. Statický `ConfigurationManager` objekt můžete použít k interakci s nastavením aplikace, připojovacími řetězci úložiště dat a dalšími poskytovateli rozšířené konfigurace, kteří se přidají do aplikace. Je typické vidět interakce s konfigurací aplikace, jak je vidět v následujícím kódu:

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

Pokud je aplikace hostována na serveru IIS systému Windows, může být soubor web.config v případě, že je ASP.NET Core a server Blazor, k dispozici může být soubor *web.config.* S touto konfigurací `ConfigurationManager` však neexistuje žádná interakce a můžete získat strukturovanější konfiguraci aplikace z jiných zdrojů. Podívejme se na to, jak se shromažďuje konfigurace a jak můžete stále přistupovat k informacím o konfiguraci ze souboru *web.config.*

## <a name="configuration-sources"></a>Zdroje konfigurace

ASP.NET Core rozpozná, že existuje mnoho konfiguračních zdrojů, které můžete chtít použít pro vaši aplikaci. Rozhraní Framework se pokusí nabídnout nejlepší z těchto funkcí ve výchozím nastavení. Konfigurace je čtena a agregována z těchto různých zdrojů ASP.NET Core. Později načtené hodnoty pro stejný konfigurační klíč mají přednost před dřívějšími hodnotami.

ASP.NET Core byl navržen tak, aby byl zhotoven s cloudem a zjednodušil konfiguraci aplikací pro operátory i vývojáře. ASP.NET Core je zhotoveno prostředí a `Production` `Development` ví, jestli běží ve vašem prostředí. Indikátor prostředí je nastaven `ASPNETCORE_ENVIRONMENT` v systémové proměnné prostředí. Pokud není nakonfigurována žádná hodnota, aplikace `Production` výchozí spuštění v prostředí.

Vaše aplikace může aktivovat a přidat konfiguraci z několika zdrojů na základě názvu prostředí. Ve výchozím nastavení je konfigurace načtena z následujících prostředků v uvedeném pořadí:

1. *appsettings.json* soubor, pokud je k dispozici
1. *nastavení aplikace. {ENVIRONMENT_NAME}.json,* je-li k dispozici
1. Soubor tajných klíčů uživatelů na disku, pokud je k dispozici
1. Proměnné prostředí
1. Argumenty příkazového řádku

## <a name="appsettingsjson-format-and-access"></a>appsettings.json formát a přístup

Soubor *appsettings.json* může být hierarchický s hodnotami strukturovanými jako následující JSON:

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

Při předložení s předchozí JSON, konfigurační systém sloučí podřízené hodnoty a odkazuje na jejich plně kvalifikované hierarchické cesty. Znak dvojtečky (`:`) odděluje každou vlastnost v hierarchii. Například konfigurační `section1:key0` klíč `section1` přistupuje k `key0` hodnotě literálu objektu.

## <a name="user-secrets"></a>Tajné klíče uživatelů

Uživatelské tajemství jsou:

* Hodnoty konfigurace, které jsou uloženy v souboru JSON na pracovní stanici vývojáře mimo složku pro vývoj aplikací.
* Načteno pouze při `Development` spuštění v prostředí.
* Přidruženo k konkrétní aplikaci.
* Spravováno pomocí `user-secrets` příkazu rozhraní PŘÍKAZU .NET Core CLI.

Nakonfigurujte aplikaci pro `user-secrets` ukládání tajných klíčů spuštěním příkazu:

```dotnetcli
dotnet user-secrets init
```

Předchozí příkaz přidá `UserSecretsId` prvek do souboru projektu. Prvek obsahuje identifikátor GUID, který se používá k přidružení tajných kódů k aplikaci. Potom můžete definovat tajný `set` klíč pomocí příkazu. Například:

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

Předchozí příkaz zpřístupní `Parent:ApiKey` konfigurační klíč na pracovní `12345`stanici vývojáře s hodnotou .

Další informace o vytváření, ukládání a správě tajných kódů uživatelů najdete v tématu [bezpečné ukládání tajných kódů aplikací ve vývoji ASP.NET základnídokument.](/aspnet/core/security/app-secrets)

## <a name="environment-variables"></a>Proměnné prostředí

Další sadou hodnot načtených do konfigurace aplikace jsou proměnné prostředí systému. Všechna nastavení proměnných prostředí systému jsou nyní přístupná prostřednictvím konfiguračního rozhraní API. Hierarchické hodnoty jsou sloučí a odděleny znaky dvojtečky při čtení uvnitř aplikace. Některé operační systémy však neumožňují názvy proměnných znakdvoje písmene. ASP.NET Jádro řeší toto omezení převodem hodnot,`__`které mají dvojité podtržítko ( ) do dvojtečky, když jsou přístupné. Hodnota `Parent:ApiKey` z části uživatelské housečné kódy `Parent__ApiKey`výše může být přepsána proměnnou prostředí .

## <a name="command-line-arguments"></a>Argumenty příkazového řádku

Konfiguraci lze také poskytnout jako argumenty příkazového řádku při spuštění aplikace. Pomocí zápisu dvojité`--`pomlčky (`/`) nebo lomítka ( ) označte název nastavené hodnoty konfigurace a hodnotu, která má být nakonfigurována. Syntaxe se podobá následujícím příkazům:

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a>Návrat web.config

Pokud jste aplikaci nasadili do Windows ve službě IIS, soubor *web.config* stále konfiguruje službu IIS pro správu aplikace. Ve výchozím nastavení přidá iis odkaz na ASP.NET základní modul (ANCM). ANCM je nativní modul služby IIS, který hostuje vaši aplikaci místo webového serveru Kestrel. Tento oddíl *web.config* se podobá následujícím značkám XML:

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

Konfigurace specifické pro aplikaci lze `environmentVariables` definovat vnořením prvku v elementu. `aspNetCore` Hodnoty definované v této části jsou prezentovány aplikaci ASP.NET Core jako proměnné prostředí. Proměnné prostředí se během spuštění aplikace načítají odpovídajícím způsobem.

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

ASP.NET Core poskytuje konfiguraci aplikace prostřednictvím <xref:Microsoft.Extensions.Configuration.IConfiguration> rozhraní. Toto konfigurační rozhraní by mělo být požadováno komponenty Blazor, Blazor stránky a všechny ostatní ASP.NET třídy spravované jádrem, která potřebuje přístup ke konfiguraci. Rozhraní ASP.NET Core framework automaticky naplní toto rozhraní dříve nakonfigurovanou konfigurací. Na stránce Blazor nebo značky Razor komponenty můžete `IConfiguration` objekt `@inject` vložit direktivou v horní části souboru *.razor* takto:

```razor
@inject IConfiguration Configuration
```

Tento předchozí příkaz `IConfiguration` zpřístupní `Configuration` objekt jako proměnnou ve zbytku šablony Razor.

Jednotlivá nastavení konfigurace lze číst zadáním hierarchie nastavení konfigurace jako parametrindexeru:

```csharp
var mySetting = Configuration["section1:key0"];
```

Můžete načíst celé části <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> konfigurace pomocí metody k načtení kolekce klíčů v `GetSection("section1")` určitém umístění se syntaxí podobnou načíst konfiguraci pro section1 z předchozího příkladu.

## <a name="strongly-typed-configuration"></a>Konfigurace silného typu

S webovými formuláři bylo možné vytvořit typ konfigurace silného <xref:System.Configuration.ConfigurationSection> typu, který byl zděděn z typu a přidružených typů. A `ConfigurationSection` umožňuje nakonfigurovat některá obchodní pravidla a zpracování pro tyto hodnoty konfigurace.

V ASP.NET Core můžete určit hierarchii tříd, která obdrží hodnoty konfigurace. Tyto třídy:

* Není nutné dědit z nadřazené třídy.
* By `public` měl obsahovat vlastnosti, které odpovídají vlastnosti a typ odkazy na strukturu konfigurace, kterou chcete zachytit.

Pro předchozí ukázku *appsettings.json* můžete definovat následující třídy pro zachycení hodnot:

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

Tato hierarchie tříd může být naplněna `Startup.ConfigureServices` přidáním následujícího řádku k metodě:

```csharp
services.Configure<MyConfig>(Configuration);
```

Ve zbytku aplikace můžete přidat vstupní parametr do `@inject` tříd nebo direktivu v šablonách Razor typu, `IOptions<MyConfig>` abyste získali nastavení konfigurace silného typu. Vlastnost `IOptions<MyConfig>.Value` přinese hodnotu `MyConfig` naplněnou z nastavení konfigurace.

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

Další informace o funkci Možnosti naleznete ve [vzoru Možnosti v dokumentu ASP.NET Core.](/aspnet/core/fundamentals/configuration/options#options-interfaces)

>[!div class="step-by-step"]
>[Předchozí](middleware.md)
>[další](security-authentication-authorization.md)
