---
title: Struktura projektu pro Blazor aplikace
description: Přečtěte si, jak se ASP.NET struktury projektu webových formulářů a Blazor projektů.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 09/11/2019
ms.openlocfilehash: 473b708a9b58fa88844bc6f79a898943d5a7db71
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173039"
---
# <a name="project-structure-for-blazor-apps"></a>Struktura projektu pro Blazor aplikace

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Navzdory jejich významným rozdílům struktury projektů ASP.NET webové formuláře a Blazor sdílejí mnoho podobných konceptů. Tady se podíváme na strukturu Blazor projektu a porovnejte ji s projektem webových formulářů ASP.NET.

Pokud chcete vytvořit svoji první Blazor aplikaci, postupujte podle pokynů v části [ Blazor Začínáme](/aspnet/core/blazor/get-started). Můžete postupovat podle pokynů a vytvořit buď Blazor serverovou aplikaci, nebo Blazor WebAssembly aplikaci hostovanou v ASP.NET Core. S výjimkou logiky specifické pro model hostování je většina kódu v obou projektech stejná.

## <a name="project-file"></a>Soubor projektu

BlazorServerové aplikace jsou projekty .NET Core. Soubor projektu pro Blazor serverovou aplikaci je co nejjednodušší, protože může získat:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Soubor projektu pro aplikaci se Blazor WebAssembly trochu zabývají. (přesná čísla verze se můžou lišit):

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

BlazorWebAssemblyprojekty cílí .NET Standard místo .NET Core, protože jsou spouštěny v prohlížeči v WebAssembly prostředí .NET runtime na bázi. Rozhraní .NET nemůžete nainstalovat do webového prohlížeče, jako je to možné na serveru nebo v počítači pro vývojáře. V důsledku toho projekt odkazuje na Blazor rozhraní pomocí jednotlivých odkazů na balíčky.

Porovnáním, výchozí projekt webových formulářů ASP.NET obsahuje téměř 300 řádků XML v souboru *. csproj* , přičemž většina z nich explicitně uvádí různé soubory kódu a obsahu v projektu. Mnohé z zjednodušení v projektech .NET Core a .NET Standard pocházejí z výchozích cílů a vlastností importovaných odkazem na `Microsoft.NET.Sdk.Web` sadu SDK, která se často označuje jako jednoduše webová sada SDK. Webová sada SDK obsahuje zástupné znaky a další pohodlí, které zjednodušují zahrnutí kódu a souborů obsahu v projektu. Soubory není nutné explicitně vypisovat. Při cílení na .NET Core webová sada SDK také přidá odkazy na rozhraní do sdílených rozhraní .NET Core i ASP.NET Core. Rozhraní jsou viditelná v uzlu architektury **závislostí**  >  **Frameworks** v okně **Průzkumník řešení** . Sdílené architektury jsou kolekce sestavení, která byla nainstalována na počítači při instalaci rozhraní .NET Core.

I když jsou podporovány, jednotlivé odkazy na sestavení jsou méně běžné v projektech .NET Core. Většina závislostí projektu se zpracovává jako odkazy na balíčky NuGet. V projektech .NET Core musíte odkazovat jenom na závislosti balíčků nejvyšší úrovně. Přenosné závislosti jsou zahrnuty automaticky. Namísto použití *packages.config* souboru běžně nalezeného v projektech webových formulářů ASP.NET do referenčních balíčků, se odkazy na balíčky přidávají do souboru projektu pomocí `<PackageReference>` elementu.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>Vstupní bod

BlazorVstupní bod aplikace serveru je definovaný v souboru *program.cs* , jak vidíte v konzolové aplikaci. Když se aplikace spustí, vytvoří a spustí instanci webového hostitele s použitím výchozích hodnot specifických pro webové aplikace. Webový hostitel spravuje Blazor životní cyklus serverové aplikace a nastavuje služby na úrovni hostitele. Příklady takových služeb jsou konfigurace, protokolování, vkládání závislostí a HTTP Server. Tento kód je většinou často používaný a je často nezměněný.

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

BlazorWebAssemblyaplikace také definují vstupní bod v *program.cs*. Kód vypadá trochu jinak. Kód je podobný v tom, že nastavuje hostitele aplikace tak, aby poskytoval stejné služby na úrovni hostitele pro aplikaci. WebAssemblyHostitel aplikace ale nenastaví Server http, protože se spustí přímo v prohlížeči.

Blazoraplikace mají `Startup` třídu namísto souboru *Global. asax* k definování spouštěcí logiky pro aplikaci. `Startup`Třída se používá ke konfiguraci aplikace a všech služeb specifických pro aplikace. V Blazor serverové aplikaci se `Startup` Třída používá k nastavení koncového bodu pro připojení v reálném čase používané Blazor mezi klientskými prohlížeči a serverem. V Blazor WebAssembly aplikaci `Startup` Třída definuje kořenové součásti aplikace a tam, kde by měly být vykresleny. Podíváme se na `Startup` třídu v části [spuštění aplikace](./app-startup.md) .

## <a name="static-files"></a>Statické soubory

Na rozdíl od projektů webových formulářů ASP.NET ne všechny soubory v Blazor projektu mohou být požadovány jako statické soubory. Pouze soubory ve složce *wwwroot* jsou webové – adresovatelné. Tato složka je označována jako "webový kořenový adresář aplikace". Cokoli mimo webový kořenový adresář aplikace *není* webová adresa. Tato instalace poskytuje další úroveň zabezpečení, která brání nechtěnému vystavení souborů projektu na webu.

## <a name="configuration"></a>Konfigurace

Konfigurace v aplikacích webových formulářů ASP.NET se obvykle zpracovává pomocí jednoho nebo více *web.config* souborů. Blazoraplikace obvykle nemají *web.config* soubory. V takovém případě se soubor používá pouze ke konfiguraci nastavení specifických pro službu IIS, pokud je hostována službou IIS. Místo toho Blazor serverové aplikace používají abstrakce konfigurace ASP.NET Core ( Blazor WebAssembly aplikace momentálně nepodporují stejné konfigurační abstrakce, ale může se jednat o funkci přidanou v budoucnu). Výchozí Blazor Serverová aplikace například ukládá některá nastavení v *appsettings.js*.

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

Další informace o konfiguraci najdete v tématu ASP.NET Core projekty v oddílu [Konfigurace](./config.md) .

## <a name="razor-components"></a>Komponenty Razor

Většina souborů v Blazor projektech je soubory *. Razor* . Razor je šablonování jazyk založený na HTML a C#, který se používá k dynamickému generování webového uživatelského rozhraní. Soubory *. Razor* definují komponenty, které tvoří uživatelské rozhraní aplikace. Ve většině případů jsou komponenty pro Blazor Server i aplikace identické Blazor WebAssembly . Komponenty v Blazor jsou podobné uživatelským ovládacím prvkům v ASP.NET webových formulářů.

Každý soubor komponenty Razor je zkompilován do třídy .NET při sestavení projektu. Vygenerovaná třída zachytí stav komponenty, logiku vykreslování, metody životního cyklu, obslužné rutiny události a další logiku. Podíváme [se Blazor na vytváření komponent v části sestavování opakovaně použitelných komponent uživatelského rozhraní](./components.md) .

Soubory *_Imports. Razor* nejsou soubory komponenty Razor. Místo toho definují sadu direktiv Razor pro import do jiných souborů *. Razor* ve stejné složce a v jejích podsložkách. Například soubor *_Imports. Razor* je konvenčním způsobem, jak přidat `using` direktivy pro běžně používané obory názvů:

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

## <a name="pages"></a>Pages (Stránky)

Kde jsou stránky v Blazor aplikacích? Blazornedefinuje samostatnou příponu souboru pro adresovatelné stránky, například soubory *. aspx* v aplikacích webových formulářů ASP.NET. Místo toho jsou stránky definovány přiřazením tras k součástem. Trasa je obvykle přiřazena pomocí `@page` direktivy Razor. Například komponenta, která se `Counter` vytvořila v souboru *Pages/Counter. Razor* , definuje následující trasu:

```razor
@page "/counter"
```

Směrování v nástroji Blazor se zpracovává na straně klienta, nikoli na serveru. Když uživatel prochází v prohlížeči, Blazor zachycuje navigaci a potom vykresluje komponentu se stejnou trasou.

Trasy součástí nejsou aktuálně odvozeny z umístění souboru komponenty, jako jsou stránky *aspx* . Tato funkce může být v budoucnu přidána. Každou trasu musíte explicitně zadat na komponentě. Ukládání komponent s přísměrováním ve složce *Pages* nemá žádný zvláštní význam a je čistě konvencí.

Podrobněji podíváme se na téma směrování v Blazor části [stránky, směrování a rozložení](./pages-routing-layouts.md) .

## <a name="layout"></a>Rozložení

V aplikacích ASP.NET Web Forms se běžné rozložení stránky zpracovává pomocí stránek předlohy (*site. Master*). V Blazor aplikacích se rozložení stránky zpracovává pomocí součástí rozložení (*Shared/MainLayout. Razor*). Komponenty rozložení budou podrobněji popsány v části [Stránka, směrování a rozložení](./pages-routing-layouts.md) .

## <a name="bootstrap-blazor"></a>BootstrapBlazor

Aby bylo možné spustit zavádění Blazor , musí aplikace:

- Určete, kam má být vygenerována kořenová komponenta (*App. Razor*) na stránce.
- Přidejte odpovídající Blazor skript rozhraní.

V Blazor serverové aplikaci je stránka hostitele kořenové součásti definovaná v souboru *_Host. cshtml* . Tento soubor definuje stránku Razor, nikoli komponentu. Razor Pages použít syntaxe Razor k definování serverově adresované stránky, velmi podobně jako na stránce *aspx* . `Html.RenderComponentAsync<TComponent>(RenderMode)`Metoda slouží k definování, kde má být vykreslena komponenta na úrovni root. `RenderMode`Možnost určuje způsob, jakým má být komponenta vykreslena. Následující tabulka popisuje podporované `RenderMode` Možnosti.

|Možnost                        |Popis       |
|------------------------------|------------------|
|`RenderMode.Server`           |Po navázání spojení s prohlížečem se interaktivně vykreslovat.|
|`RenderMode.ServerPrerendered`|První předvykreslování a potom vykreslené interaktivně|
|`RenderMode.Static`           |Vykresleno jako statický obsah|

Odkaz na skript *_framework/blazor.server.js* vytváří připojení v reálném čase se serverem a pak se zabývá všemi interakcemi uživatelů a AKTUALIZACEMI uživatelského rozhraní.

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

Blazor WebAssembly Stránka hostitele v aplikaci je jednoduchý statický soubor HTML pod uzlem *wwwroot/index.html*. `<app>`Prvek slouží k označení, kde by měla být vykreslena kořenová komponenta.

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

Konkrétní komponenta pro vykreslení je nakonfigurována v `Startup.Configure` metodě aplikace s odpovídajícím Selektor šablon stylů CSS, který určuje, kde by měla být komponenta vykreslena.

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

## <a name="build-output"></a>Výstup sestavení

Při Blazor sestavení projektu jsou všechny komponenty a soubory kódu Razor zkompilovány do jediného sestavení. Na rozdíl od projektů webových formulářů ASP.NET Blazor nepodporuje kompilaci běhové logiky uživatelského rozhraní.

## <a name="run-the-app"></a>Spuštění aplikace

Pokud chcete spustit Blazor aplikaci serveru, stiskněte `F5` v aplikaci Visual Studio. Blazoraplikace nepodporují kompilaci za běhu. Chcete-li zobrazit výsledky kódu a změny kódu komponenty, sestavte a znovu spusťte aplikaci pomocí připojeného ladicího programu. Pokud spustíte program bez připojeného ladicího programu ( `Ctrl+F5` ), Visual Studio sleduje změny souborů a restartuje aplikaci, jakmile budou provedeny změny. Prohlížeč se aktualizuje ručně, protože se udělaly změny.

Pokud chcete Blazor WebAssembly aplikaci spustit, vyberte jeden z následujících přístupů:

- Spusťte klientský projekt přímo pomocí vývojového serveru.
- Spusťte serverový projekt při hostování aplikace pomocí ASP.NET Core.

BlazorWebAssemblyaplikace nepodporují ladění pomocí sady Visual Studio. Pokud chcete aplikaci spustit, použijte `Ctrl+F5` místo `F5` . Místo toho můžete ladit Blazor WebAssembly aplikace přímo v prohlížeči. Podrobnosti najdete v tématu [ladění ASP.NET Core Blazor ](/aspnet/core/blazor/debug) .

>[!div class="step-by-step"]
>[Předchozí](hosting-models.md) 
> [Další](app-startup.md)
