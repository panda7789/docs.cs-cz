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
# <a name="app-configuration"></a><span data-ttu-id="6626f-103">Konfigurace aplikací</span><span class="sxs-lookup"><span data-stu-id="6626f-103">App configuration</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="6626f-104">Primární způsob načtení konfigurace aplikace ve webových formulářích je&mdash;s položkami v souboru *web.config* buď na serveru, nebo souvisejícím konfiguračním souborem, na který odkazuje *web.config*. Statický `ConfigurationManager` objekt můžete použít k interakci s nastavením aplikace, připojovacími řetězci úložiště dat a dalšími poskytovateli rozšířené konfigurace, kteří se přidají do aplikace.</span><span class="sxs-lookup"><span data-stu-id="6626f-104">The primary way to load app configuration in Web Forms is with entries in the *web.config* file&mdash;either on the server or a related configuration file referenced by *web.config*. You can use the static `ConfigurationManager` object to interact with app settings, data repository connection strings, and other extended configuration providers that are added into the app.</span></span> <span data-ttu-id="6626f-105">Je typické vidět interakce s konfigurací aplikace, jak je vidět v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="6626f-105">It's typical to see interactions with app configuration as seen in the following code:</span></span>

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

<span data-ttu-id="6626f-106">Pokud je aplikace hostována na serveru IIS systému Windows, může být soubor web.config v případě, že je ASP.NET Core a server Blazor, k dispozici může být soubor *web.config.*</span><span class="sxs-lookup"><span data-stu-id="6626f-106">With ASP.NET Core and server-side Blazor, the *web.config* file MAY be present if your app is hosted on a Windows IIS server.</span></span> <span data-ttu-id="6626f-107">S touto konfigurací `ConfigurationManager` však neexistuje žádná interakce a můžete získat strukturovanější konfiguraci aplikace z jiných zdrojů.</span><span class="sxs-lookup"><span data-stu-id="6626f-107">However, there's no `ConfigurationManager` interaction with this configuration, and you can receive more structured app configuration from other sources.</span></span> <span data-ttu-id="6626f-108">Podívejme se na to, jak se shromažďuje konfigurace a jak můžete stále přistupovat k informacím o konfiguraci ze souboru *web.config.*</span><span class="sxs-lookup"><span data-stu-id="6626f-108">Let's take a look at how configuration is gathered and how you can still access configuration information from a *web.config* file.</span></span>

## <a name="configuration-sources"></a><span data-ttu-id="6626f-109">Zdroje konfigurace</span><span class="sxs-lookup"><span data-stu-id="6626f-109">Configuration sources</span></span>

<span data-ttu-id="6626f-110">ASP.NET Core rozpozná, že existuje mnoho konfiguračních zdrojů, které můžete chtít použít pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6626f-110">ASP.NET Core recognizes there are many configuration sources you may want to use for your app.</span></span> <span data-ttu-id="6626f-111">Rozhraní Framework se pokusí nabídnout nejlepší z těchto funkcí ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="6626f-111">The framework attempts to offer you the best of these features by default.</span></span> <span data-ttu-id="6626f-112">Konfigurace je čtena a agregována z těchto různých zdrojů ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6626f-112">Configuration is read and aggregated from these various sources by ASP.NET Core.</span></span> <span data-ttu-id="6626f-113">Později načtené hodnoty pro stejný konfigurační klíč mají přednost před dřívějšími hodnotami.</span><span class="sxs-lookup"><span data-stu-id="6626f-113">Later loaded values for the same configuration key take precedence over earlier values.</span></span>

<span data-ttu-id="6626f-114">ASP.NET Core byl navržen tak, aby byl zhotoven s cloudem a zjednodušil konfiguraci aplikací pro operátory i vývojáře.</span><span class="sxs-lookup"><span data-stu-id="6626f-114">ASP.NET Core was designed to be cloud-aware and to make configuration of apps easier for both operators and developers.</span></span> <span data-ttu-id="6626f-115">ASP.NET Core je zhotoveno prostředí a `Production` `Development` ví, jestli běží ve vašem prostředí.</span><span class="sxs-lookup"><span data-stu-id="6626f-115">ASP.NET Core is environment-aware and knows if it's running in your `Production` or `Development` environment.</span></span> <span data-ttu-id="6626f-116">Indikátor prostředí je nastaven `ASPNETCORE_ENVIRONMENT` v systémové proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="6626f-116">The environment indicator is set in the `ASPNETCORE_ENVIRONMENT` system environment variable.</span></span> <span data-ttu-id="6626f-117">Pokud není nakonfigurována žádná hodnota, aplikace `Production` výchozí spuštění v prostředí.</span><span class="sxs-lookup"><span data-stu-id="6626f-117">If no value is configured, the app defaults to running in the `Production` environment.</span></span>

<span data-ttu-id="6626f-118">Vaše aplikace může aktivovat a přidat konfiguraci z několika zdrojů na základě názvu prostředí.</span><span class="sxs-lookup"><span data-stu-id="6626f-118">Your app can trigger and add configuration from several sources based on the environment's name.</span></span> <span data-ttu-id="6626f-119">Ve výchozím nastavení je konfigurace načtena z následujících prostředků v uvedeném pořadí:</span><span class="sxs-lookup"><span data-stu-id="6626f-119">By default, configuration is loaded from the following resources in the order listed:</span></span>

1. <span data-ttu-id="6626f-120">*appsettings.json* soubor, pokud je k dispozici</span><span class="sxs-lookup"><span data-stu-id="6626f-120">*appsettings.json* file, if present</span></span>
1. <span data-ttu-id="6626f-121">*nastavení aplikace. {ENVIRONMENT_NAME}.json,* je-li k dispozici</span><span class="sxs-lookup"><span data-stu-id="6626f-121">*appsettings.{ENVIRONMENT_NAME}.json* file, if present</span></span>
1. <span data-ttu-id="6626f-122">Soubor tajných klíčů uživatelů na disku, pokud je k dispozici</span><span class="sxs-lookup"><span data-stu-id="6626f-122">User secrets file on disk, if present</span></span>
1. <span data-ttu-id="6626f-123">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="6626f-123">Environment variables</span></span>
1. <span data-ttu-id="6626f-124">Argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="6626f-124">Command-line arguments</span></span>

## <a name="appsettingsjson-format-and-access"></a><span data-ttu-id="6626f-125">appsettings.json formát a přístup</span><span class="sxs-lookup"><span data-stu-id="6626f-125">appsettings.json format and access</span></span>

<span data-ttu-id="6626f-126">Soubor *appsettings.json* může být hierarchický s hodnotami strukturovanými jako následující JSON:</span><span class="sxs-lookup"><span data-stu-id="6626f-126">The *appsettings.json* file can be hierarchical with values structured like the following JSON:</span></span>

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

<span data-ttu-id="6626f-127">Při předložení s předchozí JSON, konfigurační systém sloučí podřízené hodnoty a odkazuje na jejich plně kvalifikované hierarchické cesty.</span><span class="sxs-lookup"><span data-stu-id="6626f-127">When presented with the preceding JSON, the configuration system flattens child values and references their fully qualified hierarchical paths.</span></span> <span data-ttu-id="6626f-128">Znak dvojtečky (`:`) odděluje každou vlastnost v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="6626f-128">A colon (`:`) character separates each property in the hierarchy.</span></span> <span data-ttu-id="6626f-129">Například konfigurační `section1:key0` klíč `section1` přistupuje k `key0` hodnotě literálu objektu.</span><span class="sxs-lookup"><span data-stu-id="6626f-129">For example, the configuration key `section1:key0` accesses the `section1` object literal's `key0` value.</span></span>

## <a name="user-secrets"></a><span data-ttu-id="6626f-130">Tajné klíče uživatelů</span><span class="sxs-lookup"><span data-stu-id="6626f-130">User secrets</span></span>

<span data-ttu-id="6626f-131">Uživatelské tajemství jsou:</span><span class="sxs-lookup"><span data-stu-id="6626f-131">User secrets are:</span></span>

* <span data-ttu-id="6626f-132">Hodnoty konfigurace, které jsou uloženy v souboru JSON na pracovní stanici vývojáře mimo složku pro vývoj aplikací.</span><span class="sxs-lookup"><span data-stu-id="6626f-132">Configuration values that are stored in a JSON file on the developer's workstation, outside of the app development folder.</span></span>
* <span data-ttu-id="6626f-133">Načteno pouze při `Development` spuštění v prostředí.</span><span class="sxs-lookup"><span data-stu-id="6626f-133">Only loaded when running in the `Development` environment.</span></span>
* <span data-ttu-id="6626f-134">Přidruženo k konkrétní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6626f-134">Associated with a specific app.</span></span>
* <span data-ttu-id="6626f-135">Spravováno pomocí `user-secrets` příkazu rozhraní PŘÍKAZU .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="6626f-135">Managed with the .NET Core CLI's `user-secrets` command.</span></span>

<span data-ttu-id="6626f-136">Nakonfigurujte aplikaci pro `user-secrets` ukládání tajných klíčů spuštěním příkazu:</span><span class="sxs-lookup"><span data-stu-id="6626f-136">Configure your app for secrets storage by executing the `user-secrets` command:</span></span>

```dotnetcli
dotnet user-secrets init
```

<span data-ttu-id="6626f-137">Předchozí příkaz přidá `UserSecretsId` prvek do souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="6626f-137">The preceding command adds a `UserSecretsId` element to the project file.</span></span> <span data-ttu-id="6626f-138">Prvek obsahuje identifikátor GUID, který se používá k přidružení tajných kódů k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6626f-138">The element contains a GUID, which is used to associate secrets with the app.</span></span> <span data-ttu-id="6626f-139">Potom můžete definovat tajný `set` klíč pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="6626f-139">You can then define a secret with the `set` command.</span></span> <span data-ttu-id="6626f-140">Například:</span><span class="sxs-lookup"><span data-stu-id="6626f-140">For example:</span></span>

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

<span data-ttu-id="6626f-141">Předchozí příkaz zpřístupní `Parent:ApiKey` konfigurační klíč na pracovní `12345`stanici vývojáře s hodnotou .</span><span class="sxs-lookup"><span data-stu-id="6626f-141">The preceding command makes the `Parent:ApiKey` configuration key available on a developer's workstation with the value `12345`.</span></span>

<span data-ttu-id="6626f-142">Další informace o vytváření, ukládání a správě tajných kódů uživatelů najdete v tématu [bezpečné ukládání tajných kódů aplikací ve vývoji ASP.NET základnídokument.](/aspnet/core/security/app-secrets)</span><span class="sxs-lookup"><span data-stu-id="6626f-142">For more information about creating, storing, and managing user secrets, see the [Safe storage of app secrets in development in ASP.NET Core](/aspnet/core/security/app-secrets) document.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="6626f-143">Proměnné prostředí</span><span class="sxs-lookup"><span data-stu-id="6626f-143">Environment variables</span></span>

<span data-ttu-id="6626f-144">Další sadou hodnot načtených do konfigurace aplikace jsou proměnné prostředí systému.</span><span class="sxs-lookup"><span data-stu-id="6626f-144">The next set of values loaded into your app configuration is the system's environment variables.</span></span> <span data-ttu-id="6626f-145">Všechna nastavení proměnných prostředí systému jsou nyní přístupná prostřednictvím konfiguračního rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="6626f-145">All of your system's environment variable settings are now accessible to you through the configuration API.</span></span> <span data-ttu-id="6626f-146">Hierarchické hodnoty jsou sloučí a odděleny znaky dvojtečky při čtení uvnitř aplikace.</span><span class="sxs-lookup"><span data-stu-id="6626f-146">Hierarchical values are flattened and separated by colon characters when read inside your app.</span></span> <span data-ttu-id="6626f-147">Některé operační systémy však neumožňují názvy proměnných znakdvoje písmene.</span><span class="sxs-lookup"><span data-stu-id="6626f-147">However, some operating systems don't allow the colon character environment variable names.</span></span> <span data-ttu-id="6626f-148">ASP.NET Jádro řeší toto omezení převodem hodnot,`__`které mají dvojité podtržítko ( ) do dvojtečky, když jsou přístupné.</span><span class="sxs-lookup"><span data-stu-id="6626f-148">ASP.NET Core addresses this limitation by converting values that have double-underscores (`__`) into a colon when they're accessed.</span></span> <span data-ttu-id="6626f-149">Hodnota `Parent:ApiKey` z části uživatelské housečné kódy `Parent__ApiKey`výše může být přepsána proměnnou prostředí .</span><span class="sxs-lookup"><span data-stu-id="6626f-149">The `Parent:ApiKey` value from the user secrets section above can be overridden with the environment variable `Parent__ApiKey`.</span></span>

## <a name="command-line-arguments"></a><span data-ttu-id="6626f-150">Argumenty příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="6626f-150">Command-line arguments</span></span>

<span data-ttu-id="6626f-151">Konfiguraci lze také poskytnout jako argumenty příkazového řádku při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="6626f-151">Configuration can also be provided as command-line arguments when your app is started.</span></span> <span data-ttu-id="6626f-152">Pomocí zápisu dvojité`--`pomlčky (`/`) nebo lomítka ( ) označte název nastavené hodnoty konfigurace a hodnotu, která má být nakonfigurována.</span><span class="sxs-lookup"><span data-stu-id="6626f-152">Use the double-dash (`--`) or forward-slash (`/`) notation to indicate the name of the configuration value to set and the value to be configured.</span></span> <span data-ttu-id="6626f-153">Syntaxe se podobá následujícím příkazům:</span><span class="sxs-lookup"><span data-stu-id="6626f-153">The syntax resembles the following commands:</span></span>

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a><span data-ttu-id="6626f-154">Návrat web.config</span><span class="sxs-lookup"><span data-stu-id="6626f-154">The return of web.config</span></span>

<span data-ttu-id="6626f-155">Pokud jste aplikaci nasadili do Windows ve službě IIS, soubor *web.config* stále konfiguruje službu IIS pro správu aplikace.</span><span class="sxs-lookup"><span data-stu-id="6626f-155">If you've deployed your app to Windows on IIS, the *web.config* file still configures IIS to manage your app.</span></span> <span data-ttu-id="6626f-156">Ve výchozím nastavení přidá iis odkaz na ASP.NET základní modul (ANCM).</span><span class="sxs-lookup"><span data-stu-id="6626f-156">By default, IIS adds a reference to the ASP.NET Core Module (ANCM).</span></span> <span data-ttu-id="6626f-157">ANCM je nativní modul služby IIS, který hostuje vaši aplikaci místo webového serveru Kestrel.</span><span class="sxs-lookup"><span data-stu-id="6626f-157">ANCM is a native IIS module that hosts your app in place of the Kestrel web server.</span></span> <span data-ttu-id="6626f-158">Tento oddíl *web.config* se podobá následujícím značkám XML:</span><span class="sxs-lookup"><span data-stu-id="6626f-158">This *web.config* section resembles the following XML markup:</span></span>

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

<span data-ttu-id="6626f-159">Konfigurace specifické pro aplikaci lze `environmentVariables` definovat vnořením prvku v elementu. `aspNetCore`</span><span class="sxs-lookup"><span data-stu-id="6626f-159">App-specific configuration can be defined by nesting an `environmentVariables` element in the `aspNetCore` element.</span></span> <span data-ttu-id="6626f-160">Hodnoty definované v této části jsou prezentovány aplikaci ASP.NET Core jako proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="6626f-160">The values defined in this section are presented to the ASP.NET Core app as environment variables.</span></span> <span data-ttu-id="6626f-161">Proměnné prostředí se během spuštění aplikace načítají odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="6626f-161">The environment variables load appropriately during that segment of app startup.</span></span>

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

## <a name="read-configuration-in-the-app"></a><span data-ttu-id="6626f-162">Čtení konfigurace v aplikaci</span><span class="sxs-lookup"><span data-stu-id="6626f-162">Read configuration in the app</span></span>

<span data-ttu-id="6626f-163">ASP.NET Core poskytuje konfiguraci aplikace prostřednictvím <xref:Microsoft.Extensions.Configuration.IConfiguration> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6626f-163">ASP.NET Core provides app configuration through the <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span></span> <span data-ttu-id="6626f-164">Toto konfigurační rozhraní by mělo být požadováno komponenty Blazor, Blazor stránky a všechny ostatní ASP.NET třídy spravované jádrem, která potřebuje přístup ke konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="6626f-164">This configuration interface should be requested by your Blazor components, Blazor pages, and any other ASP.NET Core-managed class that needs access to configuration.</span></span> <span data-ttu-id="6626f-165">Rozhraní ASP.NET Core framework automaticky naplní toto rozhraní dříve nakonfigurovanou konfigurací.</span><span class="sxs-lookup"><span data-stu-id="6626f-165">The ASP.NET Core framework will automatically populate this interface with the resolved configuration configured earlier.</span></span> <span data-ttu-id="6626f-166">Na stránce Blazor nebo značky Razor komponenty můžete `IConfiguration` objekt `@inject` vložit direktivou v horní části souboru *.razor* takto:</span><span class="sxs-lookup"><span data-stu-id="6626f-166">On a Blazor page or a component's Razor markup, you can inject the `IConfiguration` object with an `@inject` directive at the top of the *.razor* file like this:</span></span>

```razor
@inject IConfiguration Configuration
```

<span data-ttu-id="6626f-167">Tento předchozí příkaz `IConfiguration` zpřístupní `Configuration` objekt jako proměnnou ve zbytku šablony Razor.</span><span class="sxs-lookup"><span data-stu-id="6626f-167">This preceding statement makes the `IConfiguration` object available as the `Configuration` variable throughout the rest of the Razor template.</span></span>

<span data-ttu-id="6626f-168">Jednotlivá nastavení konfigurace lze číst zadáním hierarchie nastavení konfigurace jako parametrindexeru:</span><span class="sxs-lookup"><span data-stu-id="6626f-168">Individual configuration settings can be read by specifying the configuration setting hierarchy sought as an indexer parameter:</span></span>

```csharp
var mySetting = Configuration["section1:key0"];
```

<span data-ttu-id="6626f-169">Můžete načíst celé části <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> konfigurace pomocí metody k načtení kolekce klíčů v `GetSection("section1")` určitém umístění se syntaxí podobnou načíst konfiguraci pro section1 z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="6626f-169">You can fetch entire configuration sections by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> method to retrieve a collection of keys at a specific location with a syntax similar to `GetSection("section1")` to retrieve the configuration for section1 from the earlier example.</span></span>

## <a name="strongly-typed-configuration"></a><span data-ttu-id="6626f-170">Konfigurace silného typu</span><span class="sxs-lookup"><span data-stu-id="6626f-170">Strongly typed configuration</span></span>

<span data-ttu-id="6626f-171">S webovými formuláři bylo možné vytvořit typ konfigurace silného <xref:System.Configuration.ConfigurationSection> typu, který byl zděděn z typu a přidružených typů.</span><span class="sxs-lookup"><span data-stu-id="6626f-171">With Web Forms, it was possible to create a strongly typed configuration type that inherited from the <xref:System.Configuration.ConfigurationSection> type and associated types.</span></span> <span data-ttu-id="6626f-172">A `ConfigurationSection` umožňuje nakonfigurovat některá obchodní pravidla a zpracování pro tyto hodnoty konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6626f-172">A `ConfigurationSection` allowed you to configure some business rules and processing for those configuration values.</span></span>

<span data-ttu-id="6626f-173">V ASP.NET Core můžete určit hierarchii tříd, která obdrží hodnoty konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6626f-173">In ASP.NET Core, you can specify a class hierarchy that will receive the configuration values.</span></span> <span data-ttu-id="6626f-174">Tyto třídy:</span><span class="sxs-lookup"><span data-stu-id="6626f-174">These classes:</span></span>

* <span data-ttu-id="6626f-175">Není nutné dědit z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="6626f-175">Don't need to inherit from a parent class.</span></span>
* <span data-ttu-id="6626f-176">By `public` měl obsahovat vlastnosti, které odpovídají vlastnosti a typ odkazy na strukturu konfigurace, kterou chcete zachytit.</span><span class="sxs-lookup"><span data-stu-id="6626f-176">Should include `public` properties that match the properties and type references for the configuration structure you wish to capture.</span></span>

<span data-ttu-id="6626f-177">Pro předchozí ukázku *appsettings.json* můžete definovat následující třídy pro zachycení hodnot:</span><span class="sxs-lookup"><span data-stu-id="6626f-177">For the earlier *appsettings.json* sample, you could define the following classes to capture the values:</span></span>

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

<span data-ttu-id="6626f-178">Tato hierarchie tříd může být naplněna `Startup.ConfigureServices` přidáním následujícího řádku k metodě:</span><span class="sxs-lookup"><span data-stu-id="6626f-178">This class hierarchy can be populated by adding the following line to the `Startup.ConfigureServices` method:</span></span>

```csharp
services.Configure<MyConfig>(Configuration);
```

<span data-ttu-id="6626f-179">Ve zbytku aplikace můžete přidat vstupní parametr do `@inject` tříd nebo direktivu v šablonách Razor typu, `IOptions<MyConfig>` abyste získali nastavení konfigurace silného typu.</span><span class="sxs-lookup"><span data-stu-id="6626f-179">In the rest of the app, you can add an input parameter to classes or an `@inject` directive in Razor templates of type `IOptions<MyConfig>` to receive the strongly typed configuration settings.</span></span> <span data-ttu-id="6626f-180">Vlastnost `IOptions<MyConfig>.Value` přinese hodnotu `MyConfig` naplněnou z nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6626f-180">The `IOptions<MyConfig>.Value` property will yield the `MyConfig` value populated from the configuration settings.</span></span>

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

<span data-ttu-id="6626f-181">Další informace o funkci Možnosti naleznete ve [vzoru Možnosti v dokumentu ASP.NET Core.](/aspnet/core/fundamentals/configuration/options#options-interfaces)</span><span class="sxs-lookup"><span data-stu-id="6626f-181">More information about the Options feature can be found in the [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6626f-182">[Předchozí](middleware.md)
>[další](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="6626f-182">[Previous](middleware.md)
[Next](security-authentication-authorization.md)</span></span>
