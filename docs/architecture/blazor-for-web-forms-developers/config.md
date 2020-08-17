---
title: Konfigurace aplikací
description: Naučte se konfigurovat Blazor aplikace bez použití ConfigurationManager.
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 04/01/2020
ms.openlocfilehash: 6154b4f8c7a5bff42e603b12d5ef85468b80224e
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267500"
---
# <a name="app-configuration"></a><span data-ttu-id="efba0-103">Konfigurace aplikací</span><span class="sxs-lookup"><span data-stu-id="efba0-103">App configuration</span></span>

<span data-ttu-id="efba0-104">Hlavní způsob, jak načíst konfiguraci aplikace ve webových formulářích, je s položkami v \*web.configm \* souboru &mdash; buď na serveru, nebo v souvisejícím konfiguračním souboru, na který odkazuje *web.config*. Statický objekt můžete použít `ConfigurationManager` k interakci s nastavením aplikace, připojovacími řetězci úložiště dat a dalšími poskytovateli rozšířených konfigurací, které jsou přidány do aplikace.</span><span class="sxs-lookup"><span data-stu-id="efba0-104">The primary way to load app configuration in Web Forms is with entries in the *web.config* file&mdash;either on the server or a related configuration file referenced by *web.config*. You can use the static `ConfigurationManager` object to interact with app settings, data repository connection strings, and other extended configuration providers that are added into the app.</span></span> <span data-ttu-id="efba0-105">Je typický vidět interakce s konfigurací aplikace, jak je vidět v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="efba0-105">It's typical to see interactions with app configuration as seen in the following code:</span></span>

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

<span data-ttu-id="efba0-106">Při ASP.NET Core a na straně serveru Blazor může být k dispozici soubor *web.config* , pokud je vaše aplikace hostovaná na serveru Windows IIS.</span><span class="sxs-lookup"><span data-stu-id="efba0-106">With ASP.NET Core and server-side Blazor, the *web.config* file MAY be present if your app is hosted on a Windows IIS server.</span></span> <span data-ttu-id="efba0-107">Neexistuje ale žádná `ConfigurationManager` interakce s touto konfigurací a můžete získat více strukturovaných konfigurací aplikace z jiných zdrojů.</span><span class="sxs-lookup"><span data-stu-id="efba0-107">However, there's no `ConfigurationManager` interaction with this configuration, and you can receive more structured app configuration from other sources.</span></span> <span data-ttu-id="efba0-108">Pojďme se podívat na to, jak se bude shromažďovat konfigurace a jak pořád máte přístup k informacím o konfiguraci ze souboru *web.config* .</span><span class="sxs-lookup"><span data-stu-id="efba0-108">Let's take a look at how configuration is gathered and how you can still access configuration information from a *web.config* file.</span></span>

## <a name="configuration-sources"></a><span data-ttu-id="efba0-109">Zdroje konfigurace</span><span class="sxs-lookup"><span data-stu-id="efba0-109">Configuration sources</span></span>

<span data-ttu-id="efba0-110">ASP.NET Core rozpozná, že existuje mnoho zdrojů konfigurace, které můžete chtít použít pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="efba0-110">ASP.NET Core recognizes there are many configuration sources you may want to use for your app.</span></span> <span data-ttu-id="efba0-111">Rámec se ve výchozím nastavení pokusí nabídnout nejlepší z těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="efba0-111">The framework attempts to offer you the best of these features by default.</span></span> <span data-ttu-id="efba0-112">Konfigurace je čtená a agregovaná z těchto různých zdrojů ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="efba0-112">Configuration is read and aggregated from these various sources by ASP.NET Core.</span></span> <span data-ttu-id="efba0-113">Novější načtené hodnoty pro stejný konfigurační klíč mají přednost před předchozími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="efba0-113">Later loaded values for the same configuration key take precedence over earlier values.</span></span>

<span data-ttu-id="efba0-114">ASP.NET Core byla navržena jako cloudová a umožňuje snazší konfiguraci aplikací pro oba operátory i vývojáře.</span><span class="sxs-lookup"><span data-stu-id="efba0-114">ASP.NET Core was designed to be cloud-aware and to make configuration of apps easier for both operators and developers.</span></span> <span data-ttu-id="efba0-115">ASP.NET Core je s ohledem na prostředí a ví, jestli je spuštěný ve vašem `Production` `Development` prostředí nebo.</span><span class="sxs-lookup"><span data-stu-id="efba0-115">ASP.NET Core is environment-aware and knows if it's running in your `Production` or `Development` environment.</span></span> <span data-ttu-id="efba0-116">Indikátor prostředí je nastaven v `ASPNETCORE_ENVIRONMENT` proměnné prostředí systému.</span><span class="sxs-lookup"><span data-stu-id="efba0-116">The environment indicator is set in the `ASPNETCORE_ENVIRONMENT` system environment variable.</span></span> <span data-ttu-id="efba0-117">Pokud není nakonfigurovaná žádná hodnota, aplikace se ve výchozím nastavení spustí v `Production` prostředí.</span><span class="sxs-lookup"><span data-stu-id="efba0-117">If no value is configured, the app defaults to running in the `Production` environment.</span></span>

<span data-ttu-id="efba0-118">Vaše aplikace může aktivovat a přidat konfiguraci z několika zdrojů na základě názvu prostředí.</span><span class="sxs-lookup"><span data-stu-id="efba0-118">Your app can trigger and add configuration from several sources based on the environment's name.</span></span> <span data-ttu-id="efba0-119">Ve výchozím nastavení je konfigurace načtena z následujících zdrojů v uvedeném pořadí:</span><span class="sxs-lookup"><span data-stu-id="efba0-119">By default, configuration is loaded from the following resources in the order listed:</span></span>

1. <span data-ttu-id="efba0-120">*appsettings.jsv* souboru, pokud je k dispozici</span><span class="sxs-lookup"><span data-stu-id="efba0-120">*appsettings.json* file, if present</span></span>
1. <span data-ttu-id="efba0-121">*appSettings. Soubor {ENVIRONMENT_NAME}. JSON* (Pokud je k dispozici)</span><span class="sxs-lookup"><span data-stu-id="efba0-121">*appsettings.{ENVIRONMENT_NAME}.json* file, if present</span></span>
1. <span data-ttu-id="efba0-122">Soubor tajných klíčů uživatele na disku, pokud je k dispozici</span><span class="sxs-lookup"><span data-stu-id="efba0-122">User secrets file on disk, if present</span></span>
1. <span data-ttu-id="efba0-123">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="efba0-123">Environment variables</span></span>
1. <span data-ttu-id="efba0-124">Argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="efba0-124">Command-line arguments</span></span>

## <a name="appsettingsjson-format-and-access"></a><span data-ttu-id="efba0-125">appsettings.jspro formát a přístup</span><span class="sxs-lookup"><span data-stu-id="efba0-125">appsettings.json format and access</span></span>

<span data-ttu-id="efba0-126">*appsettings.js* souboru může být hierarchicky s hodnotami strukturovanými, jako je následující JSON:</span><span class="sxs-lookup"><span data-stu-id="efba0-126">The *appsettings.json* file can be hierarchical with values structured like the following JSON:</span></span>

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

<span data-ttu-id="efba0-127">Při předložení s předchozím JSON konfigurační systém sloučí podřízené hodnoty a odkazuje na jejich plně kvalifikované hierarchické cesty.</span><span class="sxs-lookup"><span data-stu-id="efba0-127">When presented with the preceding JSON, the configuration system flattens child values and references their fully qualified hierarchical paths.</span></span> <span data-ttu-id="efba0-128">Znak dvojtečky ( `:` ) odděluje každou vlastnost v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="efba0-128">A colon (`:`) character separates each property in the hierarchy.</span></span> <span data-ttu-id="efba0-129">Například konfigurační klíč `section1:key0` přistupuje k `section1` hodnotě literálu objektu `key0` .</span><span class="sxs-lookup"><span data-stu-id="efba0-129">For example, the configuration key `section1:key0` accesses the `section1` object literal's `key0` value.</span></span>

## <a name="user-secrets"></a><span data-ttu-id="efba0-130">Tajné klíče uživatele</span><span class="sxs-lookup"><span data-stu-id="efba0-130">User secrets</span></span>

<span data-ttu-id="efba0-131">Uživatelské tajné klíče:</span><span class="sxs-lookup"><span data-stu-id="efba0-131">User secrets are:</span></span>

* <span data-ttu-id="efba0-132">Hodnoty konfigurace, které jsou uloženy v souboru JSON pracovní stanice vývojáře, mimo složku pro vývoj aplikací.</span><span class="sxs-lookup"><span data-stu-id="efba0-132">Configuration values that are stored in a JSON file on the developer's workstation, outside of the app development folder.</span></span>
* <span data-ttu-id="efba0-133">Načte se jenom při spuštění v `Development` prostředí.</span><span class="sxs-lookup"><span data-stu-id="efba0-133">Only loaded when running in the `Development` environment.</span></span>
* <span data-ttu-id="efba0-134">Přidruženo ke konkrétní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="efba0-134">Associated with a specific app.</span></span>
* <span data-ttu-id="efba0-135">Spravované pomocí `user-secrets` příkazu .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="efba0-135">Managed with the .NET Core CLI's `user-secrets` command.</span></span>

<span data-ttu-id="efba0-136">Nakonfigurujte aplikaci pro tajné úložiště spuštěním `user-secrets` příkazu:</span><span class="sxs-lookup"><span data-stu-id="efba0-136">Configure your app for secrets storage by executing the `user-secrets` command:</span></span>

```dotnetcli
dotnet user-secrets init
```

<span data-ttu-id="efba0-137">Předchozí příkaz přidá `UserSecretsId` prvek do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="efba0-137">The preceding command adds a `UserSecretsId` element to the project file.</span></span> <span data-ttu-id="efba0-138">Element obsahuje identifikátor GUID, který se používá k přidružení tajných kódů k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="efba0-138">The element contains a GUID, which is used to associate secrets with the app.</span></span> <span data-ttu-id="efba0-139">Pak můžete pomocí příkazu definovat tajný klíč `set` .</span><span class="sxs-lookup"><span data-stu-id="efba0-139">You can then define a secret with the `set` command.</span></span> <span data-ttu-id="efba0-140">Příklad:</span><span class="sxs-lookup"><span data-stu-id="efba0-140">For example:</span></span>

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

<span data-ttu-id="efba0-141">Předchozí příkaz zpřístupní `Parent:ApiKey` konfigurační klíč v pracovní stanici vývojáře s hodnotou `12345` .</span><span class="sxs-lookup"><span data-stu-id="efba0-141">The preceding command makes the `Parent:ApiKey` configuration key available on a developer's workstation with the value `12345`.</span></span>

<span data-ttu-id="efba0-142">Další informace o vytváření, ukládání a správě uživatelských tajných klíčů najdete v [bezpečném úložišti tajných kódů aplikací ve vývoji v dokumentu ASP.NET Core](/aspnet/core/security/app-secrets) .</span><span class="sxs-lookup"><span data-stu-id="efba0-142">For more information about creating, storing, and managing user secrets, see the [Safe storage of app secrets in development in ASP.NET Core](/aspnet/core/security/app-secrets) document.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="efba0-143">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="efba0-143">Environment variables</span></span>

<span data-ttu-id="efba0-144">Další sadou hodnot načtených do vaší konfigurace aplikace jsou proměnné prostředí systému.</span><span class="sxs-lookup"><span data-stu-id="efba0-144">The next set of values loaded into your app configuration is the system's environment variables.</span></span> <span data-ttu-id="efba0-145">Všechna nastavení proměnných prostředí vašeho systému jsou teď přístupná prostřednictvím rozhraní API pro konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="efba0-145">All of your system's environment variable settings are now accessible to you through the configuration API.</span></span> <span data-ttu-id="efba0-146">Hierarchické hodnoty jsou shrnuty a odděleny čárkami při čtení v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="efba0-146">Hierarchical values are flattened and separated by colon characters when read inside your app.</span></span> <span data-ttu-id="efba0-147">Některé operační systémy však nepovolují názvy proměnných prostředí dvojtečky.</span><span class="sxs-lookup"><span data-stu-id="efba0-147">However, some operating systems don't allow the colon character environment variable names.</span></span> <span data-ttu-id="efba0-148">ASP.NET Core řeší toto omezení převedením hodnot, které mají dvojité podtržítka ( `__` ), do dvojtečky při jejich použití.</span><span class="sxs-lookup"><span data-stu-id="efba0-148">ASP.NET Core addresses this limitation by converting values that have double-underscores (`__`) into a colon when they're accessed.</span></span> <span data-ttu-id="efba0-149">`Parent:ApiKey`Hodnota výše uvedeného oddílu tajné klíče uživatele se dá přepsat proměnnou prostředí `Parent__ApiKey` .</span><span class="sxs-lookup"><span data-stu-id="efba0-149">The `Parent:ApiKey` value from the user secrets section above can be overridden with the environment variable `Parent__ApiKey`.</span></span>

## <a name="command-line-arguments"></a><span data-ttu-id="efba0-150">Argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="efba0-150">Command-line arguments</span></span>

<span data-ttu-id="efba0-151">Konfiguraci lze také zadat jako argumenty příkazového řádku při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="efba0-151">Configuration can also be provided as command-line arguments when your app is started.</span></span> <span data-ttu-id="efba0-152">Použijte notaci Double-spojovník ( `--` ) nebo lomítko ( `/` ) k označení názvu konfigurační hodnoty, kterou chcete nastavit a hodnotu, která má být nakonfigurována.</span><span class="sxs-lookup"><span data-stu-id="efba0-152">Use the double-dash (`--`) or forward-slash (`/`) notation to indicate the name of the configuration value to set and the value to be configured.</span></span> <span data-ttu-id="efba0-153">Syntaxe se podobá následujícím příkazům:</span><span class="sxs-lookup"><span data-stu-id="efba0-153">The syntax resembles the following commands:</span></span>

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a><span data-ttu-id="efba0-154">Vrácení web.config</span><span class="sxs-lookup"><span data-stu-id="efba0-154">The return of web.config</span></span>

<span data-ttu-id="efba0-155">Pokud jste aplikaci nasadili na Windows ve službě IIS, *web.config* soubor stále NAKONFIGURUJE službu IIS pro správu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="efba0-155">If you've deployed your app to Windows on IIS, the *web.config* file still configures IIS to manage your app.</span></span> <span data-ttu-id="efba0-156">Služba IIS ve výchozím nastavení přidá odkaz na modul ASP.NET Core (ANCM).</span><span class="sxs-lookup"><span data-stu-id="efba0-156">By default, IIS adds a reference to the ASP.NET Core Module (ANCM).</span></span> <span data-ttu-id="efba0-157">ANCM je nativní modul služby IIS, který hostuje vaši aplikaci místo webového serveru Kestrel.</span><span class="sxs-lookup"><span data-stu-id="efba0-157">ANCM is a native IIS module that hosts your app in place of the Kestrel web server.</span></span> <span data-ttu-id="efba0-158">Tento *web.config* oddíl se podobá následujícímu kódu XML:</span><span class="sxs-lookup"><span data-stu-id="efba0-158">This *web.config* section resembles the following XML markup:</span></span>

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

<span data-ttu-id="efba0-159">Konfiguraci specifickou pro aplikaci lze definovat vnořením `environmentVariables` elementu v `aspNetCore` elementu.</span><span class="sxs-lookup"><span data-stu-id="efba0-159">App-specific configuration can be defined by nesting an `environmentVariables` element in the `aspNetCore` element.</span></span> <span data-ttu-id="efba0-160">Hodnoty definované v této části se zobrazí ASP.NET Core aplikaci jako proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="efba0-160">The values defined in this section are presented to the ASP.NET Core app as environment variables.</span></span> <span data-ttu-id="efba0-161">Proměnné prostředí se při spuštění aplikace patřičně načítají.</span><span class="sxs-lookup"><span data-stu-id="efba0-161">The environment variables load appropriately during that segment of app startup.</span></span>

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

## <a name="read-configuration-in-the-app"></a><span data-ttu-id="efba0-162">Čtení konfigurace v aplikaci</span><span class="sxs-lookup"><span data-stu-id="efba0-162">Read configuration in the app</span></span>

<span data-ttu-id="efba0-163">ASP.NET Core poskytuje konfiguraci aplikace prostřednictvím <xref:Microsoft.Extensions.Configuration.IConfiguration> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="efba0-163">ASP.NET Core provides app configuration through the <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span></span> <span data-ttu-id="efba0-164">Toto konfigurační rozhraní by mělo požadovat vaše Blazor komponenty, Blazor stránky a všechny další ASP.NET Core spravované třídy, které potřebují přístup ke konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="efba0-164">This configuration interface should be requested by your Blazor components, Blazor pages, and any other ASP.NET Core-managed class that needs access to configuration.</span></span> <span data-ttu-id="efba0-165">Rozhraní ASP.NET Core Framework automaticky naplní toto rozhraní s vyřešenou konfigurací nakonfigurovanou dříve.</span><span class="sxs-lookup"><span data-stu-id="efba0-165">The ASP.NET Core framework will automatically populate this interface with the resolved configuration configured earlier.</span></span> <span data-ttu-id="efba0-166">Na Blazor stránce nebo v kódu Razor komponenty můžete vložit `IConfiguration` objekt s `@inject` direktivou v horní části souboru *. Razor* takto:</span><span class="sxs-lookup"><span data-stu-id="efba0-166">On a Blazor page or a component's Razor markup, you can inject the `IConfiguration` object with an `@inject` directive at the top of the *.razor* file like this:</span></span>

```razor
@inject IConfiguration Configuration
```

<span data-ttu-id="efba0-167">Tento předchozí příkaz zpřístupní `IConfiguration` objekt jako `Configuration` proměnnou v celé zbývající části šablony Razor.</span><span class="sxs-lookup"><span data-stu-id="efba0-167">This preceding statement makes the `IConfiguration` object available as the `Configuration` variable throughout the rest of the Razor template.</span></span>

<span data-ttu-id="efba0-168">Jednotlivá nastavení konfigurace je možné přečíst zadáním hierarchie nastavení konfigurace, kterou si můžete vyžádat jako parametr indexeru:</span><span class="sxs-lookup"><span data-stu-id="efba0-168">Individual configuration settings can be read by specifying the configuration setting hierarchy sought as an indexer parameter:</span></span>

```csharp
var mySetting = Configuration["section1:key0"];
```

<span data-ttu-id="efba0-169">Můžete načíst celé konfigurační oddíly pomocí <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> metody pro načtení kolekce klíčů v určitém umístění s syntaxí podobnou syntaxi pro `GetSection("section1")` načtení konfigurace pro Section1 z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="efba0-169">You can fetch entire configuration sections by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> method to retrieve a collection of keys at a specific location with a syntax similar to `GetSection("section1")` to retrieve the configuration for section1 from the earlier example.</span></span>

## <a name="strongly-typed-configuration"></a><span data-ttu-id="efba0-170">Konfigurace silného typu</span><span class="sxs-lookup"><span data-stu-id="efba0-170">Strongly typed configuration</span></span>

<span data-ttu-id="efba0-171">S webovými formuláři bylo možné vytvořit typ konfigurace silného typu, který je zděděný z <xref:System.Configuration.ConfigurationSection> typu a přidružených typů.</span><span class="sxs-lookup"><span data-stu-id="efba0-171">With Web Forms, it was possible to create a strongly typed configuration type that inherited from the <xref:System.Configuration.ConfigurationSection> type and associated types.</span></span> <span data-ttu-id="efba0-172">Umožňuje `ConfigurationSection` nakonfigurovat některá obchodní pravidla a zpracování pro tyto hodnoty konfigurace.</span><span class="sxs-lookup"><span data-stu-id="efba0-172">A `ConfigurationSection` allowed you to configure some business rules and processing for those configuration values.</span></span>

<span data-ttu-id="efba0-173">V ASP.NET Core můžete určit hierarchii tříd, která bude přijímat hodnoty konfigurace.</span><span class="sxs-lookup"><span data-stu-id="efba0-173">In ASP.NET Core, you can specify a class hierarchy that will receive the configuration values.</span></span> <span data-ttu-id="efba0-174">Tyto třídy:</span><span class="sxs-lookup"><span data-stu-id="efba0-174">These classes:</span></span>

* <span data-ttu-id="efba0-175">Není nutné dědit z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="efba0-175">Don't need to inherit from a parent class.</span></span>
* <span data-ttu-id="efba0-176">By měly obsahovat `public` vlastnosti, které odpovídají vlastnostem a odkazy na typy pro konfigurační strukturu, kterou chcete zachytit.</span><span class="sxs-lookup"><span data-stu-id="efba0-176">Should include `public` properties that match the properties and type references for the configuration structure you wish to capture.</span></span>

<span data-ttu-id="efba0-177">Pro předchozí *appsettings.jsv* ukázce můžete definovat následující třídy pro zachycení hodnot:</span><span class="sxs-lookup"><span data-stu-id="efba0-177">For the earlier *appsettings.json* sample, you could define the following classes to capture the values:</span></span>

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

<span data-ttu-id="efba0-178">Tuto hierarchii tříd lze naplnit přidáním následujícího řádku do `Startup.ConfigureServices` metody:</span><span class="sxs-lookup"><span data-stu-id="efba0-178">This class hierarchy can be populated by adding the following line to the `Startup.ConfigureServices` method:</span></span>

```csharp
services.Configure<MyConfig>(Configuration);
```

<span data-ttu-id="efba0-179">Ve zbývající části aplikace můžete přidat vstupní parametr do tříd nebo `@inject` direktivy v šablonách Razor typu `IOptions<MyConfig>` pro získání nastavení konfigurace silného typu.</span><span class="sxs-lookup"><span data-stu-id="efba0-179">In the rest of the app, you can add an input parameter to classes or an `@inject` directive in Razor templates of type `IOptions<MyConfig>` to receive the strongly typed configuration settings.</span></span> <span data-ttu-id="efba0-180">`IOptions<MyConfig>.Value`Vlastnost vrátí `MyConfig` hodnotu naplněnou z nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="efba0-180">The `IOptions<MyConfig>.Value` property will yield the `MyConfig` value populated from the configuration settings.</span></span>

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

<span data-ttu-id="efba0-181">Další informace o funkci Options najdete ve [vzoru možností v dokumentu ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) .</span><span class="sxs-lookup"><span data-stu-id="efba0-181">More information about the Options feature can be found in the [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="efba0-182">[Předchozí](middleware.md) 
> [Další](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="efba0-182">[Previous](middleware.md)
[Next](security-authentication-authorization.md)</span></span>
