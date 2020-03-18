---
title: Struktura projektu pro aplikace Blazor
description: Zjistěte, jak se porovnávají struktury projektů ASP.NET webových formulářů a blazorů.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 2c383e86ff22f5a3460476998992b66e9417cc11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401576"
---
# <a name="project-structure-for-blazor-apps"></a>Struktura projektu pro aplikace Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Navzdory svým významným rozdílům ve struktuře projektů sdílejí ASP.NET Web Forms a Blazor mnoho podobných konceptů. Zde se podíváme na strukturu projektu Blazor a porovnáme jej s projektem ASP.NET Web Forms.

Chcete-li vytvořit první aplikaci Blazor, postupujte podle pokynů v [krocích pro zahájení začínání v aplikaci Blazor](/aspnet/core/blazor/get-started). Podle pokynů můžete vytvořit aplikaci Blazor Server nebo aplikaci Blazor WebAssembly hostovoci v ASP.NET Core. S výjimkou logiky specifické pro hostování modelu je většina kódu v obou projektech stejná.

## <a name="project-file"></a>Soubor projektu

Aplikace Blazor Server jsou projekty .NET Core. Soubor projektu pro aplikaci Blazor Server je asi tak jednoduchý, jak to může dostat:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Soubor projektu pro aplikaci Blazor WebAssembly vypadá o něco více (přesná čísla verzí se mohou lišit):

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <RazorLangVersion>3.0</RazorLangVersion>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Blazor" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.Build" Version="3.1.0" PrivateAssets="all" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.HttpClient" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.DevServer" Version="3.1.0" PrivateAssets="all" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include="..\Shared\BlazorWebAssemblyApp1.Shared.csproj" />
  </ItemGroup>

</Project>
```

Projekty Blazor WebAssembly cílí na standard .NET místo .NET Core, protože jsou spuštěny v prohlížeči v době runtime .NET založené na webové sestavě. Rozhraní .NET nelze nainstalovat do webového prohlížeče jako na serveru nebo na vývojářském počítači. Projekt proto odkazuje na rámec Blazor pomocí jednotlivých odkazů na balíčky.

Pro srovnání, výchozí ASP.NET projektu Webových formulářů obsahuje téměř 300 řádků XML ve svém souboru *.csproj,* z nichž většina je explicitně výpis různých souborů kódu a obsahu v projektu. Mnoho zjednodušení v projektech založených na standardu .NET a .NET standard pochází z výchozích cílů a vlastností importovaných odkazem na sadu `Microsoft.NET.Sdk.Web` SDK, často označované jako jednoduše webová sada SDK. Sada Web SDK obsahuje zástupné znaky a další vymoženosti, které zjednodušují zahrnutí souborů kódu a obsahu do projektu. Soubory není nutné uvádět explicitně. Při cílení na .NET Core, Web SDK také přidává odkazy na rozhraní rozhraní .NET Core a ASP.NET základní sdílené architektury. Rámce jsou viditelné z uzlu **Architektury** > **závislostí** v okně **Průzkumník řešení.** Sdílené architektury jsou kolekce sestavení, které byly nainstalovány v počítači při instalaci .NET Core.

I když jsou podporovány, jednotlivé odkazy na sestavení jsou méně běžné v projektech .NET Core. Většina závislostí projektu jsou zpracovány jako odkazy na balíček NuGet. Jetřeba odkazovat pouze na závislosti balíčků nejvyšší úrovně v projektech .NET Core. Přenosité závislosti jsou zahrnuty automaticky. Namísto použití souboru *packages.config,* který se běžně vyskytuje v projektech ASP.NET webových `<PackageReference>` formulářů, jsou odkazy na balíčky přidány do souboru projektu pomocí prvku.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>Vstupní bod

Vstupní bod aplikace Blazor Server je definován v *souboru Program.cs,* jak byste viděli v aplikaci Console. Když se aplikace spustí, vytvoří a spustí instanci webového hostitele pomocí výchozích hodnot specifických pro webové aplikace. Webový hostitel spravuje životní cyklus aplikace Blazor Server a nastavuje služby na úrovni hostitele. Příklady těchto služeb jsou konfigurace, protokolování, vkládání závislostí a http server. Tento kód je většinou často standardní a je často ponechánbeze změny.

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

Aplikace Blazor WebAssembly také definují vstupní bod v *Program.cs*. Kód vypadá trochu jinak. Kód je podobný v tom, že nastavuje hostitele aplikace tak, aby poskytoval stejnou službu na úrovni hostitele. Hostitel aplikace WebAssembly však nenastavuje http server, protože se spouští přímo v prohlížeči.

Aplikace Blazor `Startup` mají třídu namísto souboru *Global.asax,* která definuje logiku spuštění aplikace. Třída `Startup` se používá ke konfiguraci aplikace a všechny služby specifické pro aplikaci. V aplikaci Blazor `Startup` Server se třída používá k nastavení koncového bodu pro připojení v reálném čase používaného Blazorem mezi klientskými prohlížeči a serverem. V aplikaci Blazor WebAssembly `Startup` třída definuje kořenové součásti aplikace a kde by měly být vykresleny. Podíváme se hlouběji na `Startup` třídu v části [spuštění aplikace.](./app-startup.md)

## <a name="static-files"></a>Statické soubory

Na rozdíl od projektů ASP.NET webových formulářů nelze jako statické soubory požadovat všechny soubory v projektu Blazor. Pouze soubory ve složce *wwwroot* jsou webové adresovatelné. Tato složka je odkazována na "kořen ový web" aplikace. Nic mimo kořen webu aplikace *není* adresovatelné na webu. Toto nastavení poskytuje další úroveň zabezpečení, která zabraňuje náhodnému vystavení souborů projektu přes web.

## <a name="configuration"></a>Konfigurace

Konfigurace v aplikacích ASP.NET webových formulářů se obvykle zpracovává pomocí jednoho nebo více souborů *web.config.* Aplikace Blazor obvykle nemají soubory *web.config.* Pokud ano, soubor se používá pouze ke konfiguraci nastavení specifických pro službu IIS, pokud jsou hostována ve službě IIS. Místo toho aplikace Blazor Server používají ASP.NET abstrakce konfigurace Core (aplikace Blazor WebAssembly v současné době nepodporují stejné abstrakce konfigurace, ale to může být funkce přidaná v budoucnu). Například výchozí aplikace Blazor Server ukládá některá nastavení v *souboru appsettings.json*.

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

Další informace o konfiguraci v ASP.NET základních projektech najdete v části [Konfigurace.](./config.md)

## <a name="razor-components"></a>Komponenty pro břitvy

Většina souborů v blazorprojektech jsou *.razor* soubory. Razor je šablonovací jazyk založený na HTML a C#, který se používá k dynamickému generování webového uživatelského rozhraní. Soubory *.razor* definují součásti, které tvoří ui aplikace. Součásti jsou většinou identické jak pro aplikace Blazor Server, tak pro aplikace Blazor WebAssembly. Komponenty v Blazoru jsou obdobou uživatelských ovládacích prvků v ASP.NET Webových formulářích.

Každý soubor komponenty Razor je zkompilován do třídy .NET při sestavení projektu. Vygenerovaná třída zachycuje stav komponenty, logiku vykreslování, metody životního cyklu, obslužné rutiny událostí a další logiku. Podíváme se na vytváření komponent v [opakovaně použitelných komponentách ui budovy s částí Blazor.](./components.md)

Soubory *_Imports.razor* nejsou soubory komponent razor. Místo toho definují sadu direktiv razor pro import do jiných souborů *.razor* ve stejné složce a v jejích podsložkách. Například soubor *_Imports.razor* je konvenční způsob `using` přidání příkazů pro běžně používané obory názvů:

```razor
@using System.Net.Http
@using Microsoft.AspNetCore.Authorization
@using Microsoft.AspNetCore.Components.Authorization
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using Microsoft.JSInterop
@using BlazorApp1
@using BlazorApp1.Shared
```

## <a name="pages"></a>Stránky

Kde jsou stránky v aplikacích Blazor? Blazor nedefinuje samostatnou příponu souborů pro adresovatelné stránky, jako jsou soubory *ASPX* v aplikacích ASP.NET Web Forms. Místo toho jsou stránky definovány přiřazením tras k komponentám. Trasa je obvykle přiřazena pomocí `@page` razor směrnice. Například komponenta `Counter` vytvořená v souboru *Pages/Counter.razor* definuje následující trasu:

```razor
@page "/counter"
```

Směrování v Blazoru je zpracováno na straně klienta, nikoli na serveru. Jak uživatel naviguje v prohlížeči, Blazor zachytí navigaci a pak vykreslí komponentu s odpovídající trasou.

Trasy komponent nejsou aktuálně odvozeny umístěním souboru komponenty, jako jsou u stránek *ASPX.* Tato funkce může být přidána v budoucnu. Každý postup musí být určen explicitně na komponentě. Ukládání směrovatelných součástí do složky *Stránky* nemá žádný zvláštní význam a je čistě konvence.

Podrobněji se podíváme na směrování v Blazoru v sekci [Stránky, směrování a rozložení.](./pages-routing-layouts.md)

## <a name="layout"></a>Rozložení

V aplikacích ASP.NET Webových formulářů se společné rozložení stránky zpracovává pomocí vzorových stránek *(Site.Master).* V aplikacích Blazor je rozložení stránky zpracováno pomocí komponent rozložení (*Shared/MainLayout.razor*). Součásti rozložení budou podrobněji popsány v části [Stránka, směrování a rozložení.](./pages-routing-layouts.md)

## <a name="bootstrap-blazor"></a>Bootstrap Blazor

Chcete-li zavést Blazor, aplikace musí:

- Určete, kde na stránce má být vykreslena kořenová komponenta (*App.Razor*).
- Přidejte odpovídající blazor framework skript.

V aplikaci Blazor Server je hostitelská stránka kořenové komponenty definována v souboru *_Host.cshtml.* Tento soubor definuje stránku razor, nikoli součást. Razor Pages používají syntaxi Razor k definování stránky adresovatelné serveru, velmi podobně jako stránka *ASPX.* Metoda `Html.RenderComponentAsync<TComponent>(RenderMode)` se používá k definování, kde by měla být komponenta kořenové úrovně vykreslena. Tato `RenderMode` možnost označuje způsob, jakým má být komponenta vykreslena. Následující tabulka popisuje podporované `RenderMode` možnosti.

|Možnost                        |Popis       |
|------------------------------|------------------|
|`RenderMode.Server`           |Vykresleno interaktivně po navázání spojení s prohlížečem|
|`RenderMode.ServerPrerendered`|Nejprve předvykreslena a poté vykreslena interaktivně|
|`RenderMode.Static`           |Vykresleno jako statický obsah|

Odkaz na skript *_framework/blazor.server.js* vytvoří spojení se serverem v reálném čase a poté se zabývá všemi interakcemi uživatele a aktualizacemi uživatelského rozhraní.

```razor
@page "/"
@namespace BlazorApp1.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BlazorApp1</title>
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>
        @(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))
    </app>

    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

V aplikaci Blazor WebAssembly je hostitelská stránka jednoduchý statický soubor HTML pod *wwwroot/index.html*. Prvek `<app>` se používá k označení, kde má být kořenová komponenta vykreslena.

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>Loading...</app>

    <script src="_framework/blazor.webassembly.js"></script>
</body>
</html>
```

Konkrétní komponenta, která má být `Startup.Configure` vykreslena, je konfigurována v metodě aplikace s odpovídajícím voličem CSS, který označuje, kde má být komponenta vykreslena.

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IComponentsApplicationBuilder app)
    {
        app.AddComponent<App>("app");
    }
}
```

## <a name="build-output"></a>Vytvořit výstup

Při sestavení projektu Blazor jsou všechny komponenty Razor a soubory kódu zkompilovány do jednoho sestavení. Na rozdíl od ASP.NET projekty webových formulářů Blazor nepodporuje runtime kompilaci logiky uživatelského nastavení.

## <a name="run-the-app"></a>Spuštění aplikace

Chcete-li spustit aplikaci Blazor Server, stiskněte v `F5` sadě Visual Studio. Aplikace Blazor nepodporují kompilaci za běhu. Chcete-li zobrazit výsledky změn kódu a značek komponent, znovu sestavte a restartujte aplikaci s připojeným ladicím programem. Pokud spustíte bez připojenéladicí`Ctrl+F5`program ( ), Visual Studio hodinky pro změny souborů a restartuje aplikaci jako změny jsou prováděny. Při provádění změn prohlížeč ručně aktualizujete.

Chcete-li spustit aplikaci Blazor WebAssembly, zvolte jeden z následujících přístupů:

- Spusťte projekt klienta přímo pomocí vývojového serveru.
- Spusťte serverový projekt při hostování aplikace s ASP.NET Core.

Aplikace Blazor WebAssembly nepodporují ladění pomocí sady Visual Studio. Chcete-li aplikaci `Ctrl+F5` spustit, použijte místo `F5`aplikace . Místo toho můžete ladit aplikace Blazor WebAssembly přímo v prohlížeči. Podrobnosti najdete [v tématu Ladění ASP.NET Core Blazor.](/aspnet/core/blazor/debug)

>[!div class="step-by-step"]
>[Předchozí](hosting-models.md)
>[další](app-startup.md)
