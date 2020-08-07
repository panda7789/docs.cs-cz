---
title: Spuštění aplikace
description: Naučte se definovat logiku spouštění vaší aplikace.
author: csharpfritz
ms.author: jefritz
ms.date: 02/25/2020
ms.openlocfilehash: 3d460750c36f64b8ad343755bd63b47af5c310d9
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87914877"
---
# <a name="app-startup"></a>Spuštění aplikace

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Aplikace napsané pro ASP.NET mají typicky `global.asax.cs` soubor, který definuje `Application_Start` událost, která řídí, které služby jsou nakonfigurovány a zpřístupněny pro vykreslování HTML i pro zpracování .NET. V této kapitole najdete informace o tom, jak se trochu liší od ASP.NET Core a Blazor serveru.

## <a name="application_start-and-web-forms"></a>Application_Start a webové formuláře

Výchozí metoda webových formulářů `Application_Start` vzrostla za několik let a zpracovává mnoho úloh konfigurace.  Nový projekt webových formulářů s výchozí šablonou v aplikaci Visual Studio 2019 teď obsahuje následující logiku konfigurace:

- `RouteConfig`– Směrování adres URL aplikace
- `BundleConfig`– Sdružování CSS a JavaScriptu a minifikace

Každý z těchto jednotlivých souborů se nachází ve `App_Start` složce a spouští se pouze jednou na začátku naší aplikace.  `RouteConfig`ve výchozí šabloně projektu přidá `FriendlyUrlSettings` webové formuláře, které umožní adresám URL aplikace vynechat `.ASPX` příponu souboru.  Výchozí šablona obsahuje také direktivu, která poskytuje trvalé stavové kódy přesměrování HTTP (HTTP 301) pro `.ASPX` stránky popisné adresy URL s názvem souboru, který toto rozšíření vynechává.

Pomocí ASP.NET Core a Blazor jsou tyto metody buď zjednodušené, konsoliduje do `Startup` třídy, nebo jsou z hlediska běžných webových technologií eliminovány.

## <a name="blazor-server-startup-structure"></a>Spouštěcí struktura serveru Blazor

Blazor serverové aplikace jsou umístěné na ASP.NET Core 3,0 nebo novějším.  ASP.NET Core webové aplikace jsou konfigurovány prostřednictvím páru metod ve třídě v `Startup.cs` kořenové složce aplikace.  Výchozí obsah spouštěcí třídy je uveden níže.

```csharp
public class Startup
{
  public Startup(IConfiguration configuration)
  {
    Configuration = configuration;
  }

  public IConfiguration Configuration { get; }

  // This method gets called by the runtime. Use this method to add services to the container.
  // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
  public void ConfigureServices(IServiceCollection services)
  {
    services.AddRazorPages();
    services.AddServerSideBlazor();
    services.AddSingleton<WeatherForecastService>();
  }

  // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
  public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
  {
    if (env.IsDevelopment())
    {
      app.UseDeveloperExceptionPage();
    }
    else
    {
      app.UseExceptionHandler("/Error");
      // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
      app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
      endpoints.MapBlazorHub();
      endpoints.MapFallbackToPage("/_Host");
   });
  }
 }
```

Podobně jako u ostatních ASP.NET Core je třída po spuštění vytvořena se zásadami injektáže závislostí.  `IConfiguration`Je k dispozici pro konstruktor a v případě pozdějšího přístupu během konfigurace může být dočasně vydaný ve vlastnosti Public.

`ConfigureServices`Metoda zavedená v ASP.NET Core umožňuje nakonfigurovat různé služby ASP.NET Core Framework pro integrovaný kontejner injektáže závislosti rozhraní.  Mezi různé `services.Add*` metody patří služby, které umožňují používat funkce, jako je ověřování, stránky Razor, směrování kontroléru MVC, signál a interakce Blazor serveru mezi mnoha ostatními.  Tato metoda není ve webových formulářích nutná, protože analýza a zpracování souborů ASPX, ASCX, ASHX a ASMX byly definovány odkazem na ASP.NET v konfiguračním souboru web.config.  Další informace o vkládání závislostí v ASP.NET Core najdete v [online dokumentaci](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection).

`Configure`Metoda zavádí koncept kanálu HTTP na ASP.NET Core.  V této metodě deklarujeme shora dolů [middleware](middleware.md) , který zpracuje všechny požadavky odeslané do naší aplikace. Většina těchto funkcí ve výchozí konfiguraci byla rozptýlená napříč konfiguračními soubory webových formulářů a teď je na jednom místě pro snadné použití reference.

Již není konfigurací vlastní chybové stránky umístěné v `web.config` souboru, ale nyní je nakonfigurována tak, aby se vždy zobrazila, pokud není v prostředí aplikace označeno `Development` .  Kromě toho ASP.NET Core aplikace teď nakonfigurované tak, aby ve výchozím nastavení sloužily zabezpečené stránky s protokolem TLS, a to prostřednictvím `UseHttpsRedirection` volání metody.

V dalším kroku je neočekávaná metoda konfigurace uvedená jako `UseStaticFiles` .  V ASP.NET Core musí být podpora žádostí o statické soubory (například JavaScript, CSS a obrázkové soubory) explicitně povolená a ve výchozím nastavení budou mít veřejné i jenom soubory ve složce *wwwroot* této aplikace.

Další řádek je první, který replikuje jednu z možností konfigurace z webových formulářů: `UseRouting` .  Tato metoda přidá směrovač ASP.NET Core do kanálu a může být buď nakonfigurován zde, nebo v jednotlivých souborech, na které může zvážit směrování.  Další informace o konfiguraci směrování najdete v [části směrování](pages-routing-layouts.md).

Poslední příkaz v této metodě definuje koncové body, na kterých ASP.NET Core naslouchá.  Jedná se o dostupná umístění webu, ke kterým můžete přistupovat na webovém serveru a získat nějaký obsah zpracovaný rozhraním .NET a vrátit se na vás.  První položka `MapBlazorHub` nakonfiguruje centrum signalizace pro použití v reálném čase a trvalé připojení k serveru, kde je zpracováván stav a vykreslování komponent Blazor.  `MapFallbackToPage`Volání metody indikuje umístění stránky přístupné pro web, které spouští aplikaci Blazor, a také nakonfiguruje aplikaci tak, aby zpracovávala požadavky na důkladné propojení od klienta.  Tato funkce se zobrazí v práci, pokud otevřete prohlížeč a přejdete přímo na Blazor zpracovávaný postup ve vaší aplikaci, například `/counter` ve výchozí šabloně projektu. Požadavek se zpracuje pomocí stránky *_Host. cshtml* Fallback, která pak spustí směrovač Blazor a vykreslí stránku čítače.

## <a name="upgrading-the-bundleconfig-process"></a>Upgrade procesu BundleConfig

Technologie pro sdružování prostředků, jako jsou šablony stylů CSS a soubory JavaScriptu, se významně vyvinuly s dalšími technologiemi, které poskytují rychlé vývoj nástrojů a technik pro správu těchto prostředků.  K tomuto účelu doporučujeme použít pro zabalení statických prostředků nástroj příkazového řádku Node, jako je Grunt/Gulp/Webpack.

Nástroje příkazového řádku grunt, Gulp a Webpack a jejich přidružené konfigurace je možné do vaší aplikace přidat a ASP.NET Core je během procesu sestavení aplikace tyto soubory v tichém režimu ignorovat.  Můžete přidat volání ke spouštění svých úkolů přidáním `Target` v rámci souboru projektu s syntaxí podobnou následující, která by aktivovala skript Gulp a `min` cíl uvnitř tohoto skriptu.

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

Další podrobnosti o obou strategiích pro správu souborů CSS a JavaScript jsou k dispozici v sadě [prostředků a statické prostředky minimalizuje v dokumentaci ASP.NET Core](https://docs.microsoft.com/aspnet/core/client-side/bundling-and-minification) .

>[!div class="step-by-step"]
>[Předchozí](project-structure.md) 
> [Další](components.md)
