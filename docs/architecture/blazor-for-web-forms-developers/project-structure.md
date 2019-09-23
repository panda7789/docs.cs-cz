---
title: Struktura projektu pro aplikace Blazor
description: Přečtěte si, jak porovnat struktury projektu webových formulářů ASP.NET a projektů Blazor.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: f9af8f88008ef45438a9104374d766cdbf8cc9a0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183817"
---
# <a name="project-structure-for-blazor-apps"></a>Struktura projektu pro aplikace Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Navzdory jejich významným rozdílům struktury projektů ASP.NET webové formuláře a Blazor sdílejí mnoho podobných konceptů. Tady se podíváme na strukturu projektu Blazor a porovnejte ji s projektem webových formulářů ASP.NET.

Pokud chcete vytvořit svoji první aplikaci pro Blazor, postupujte podle pokynů v tématu [Začínáme s Blazor](/aspnet/core/blazor/get-started). Můžete postupovat podle pokynů k vytvoření aplikace Blazor serveru nebo aplikace Blazor WebAssembly hostované v ASP.NET Core. S výjimkou logiky specifické pro model hostování je většina kódu v obou projektech stejná.

## <a name="project-file"></a>Soubor projektu

Blazor serverové aplikace jsou projekty .NET Core. Soubor projektu pro aplikaci Blazor Server je co nejjednodušší, protože může získat:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Soubor projektu pro aplikaci WebAssembly v Blazor se trochu zabývají. (přesná čísla verze se můžou lišit):

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

Blazor .NET Standard cíle projektů WebAssembly místo .NET Core, protože běží v prohlížeči v prostředí .NET runtime založeném na WebAssembly. Rozhraní .NET nemůžete nainstalovat do webového prohlížeče, jako je to možné na serveru nebo v počítači pro vývojáře. V důsledku toho projekt odkazuje na rozhraní Blazor pomocí jednotlivých odkazů na balíčky.

Porovnáním, výchozí projekt webových formulářů ASP.NET obsahuje téměř 300 řádků XML v souboru *. csproj* , přičemž většina z nich explicitně uvádí různé soubory kódu a obsahu v projektu. Mnohé z zjednodušení v projektech .NET Core a .NET Standard pocházejí z výchozích cílů a vlastností importovaných odkazem na `Microsoft.NET.Sdk.Web` sadu SDK, která se často označuje jako jednoduše webová sada SDK. Webová sada SDK obsahuje zástupné znaky a další pohodlí, které zjednodušují zahrnutí kódu a souborů obsahu v projektu. Soubory není nutné explicitně vypisovat. Při cílení na .NET Core webová sada SDK také přidá odkazy na rozhraní do sdílených rozhraní .NET Core i ASP.NET Core. Rozhraní jsou viditelná v uzlu**architektury** **závislostí** > v okně **Průzkumník řešení** . Sdílené architektury jsou kolekce sestavení, která byla nainstalována na počítači při instalaci rozhraní .NET Core.

I když jsou podporovány, jednotlivé odkazy na sestavení jsou méně běžné v projektech .NET Core. Většina závislostí projektu se zpracovává jako odkazy na balíčky NuGet. V projektech .NET Core musíte odkazovat jenom na závislosti balíčků nejvyšší úrovně. Přenosné závislosti jsou zahrnuty automaticky. Namísto použití souboru *Packages. config* , který se běžně našel v projektech webových formulářů ASP.NET, na referenční balíčky, se odkazy na balíčky přidávají do `<PackageReference>` souboru projektu pomocí elementu.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>Vstupní bod

Vstupní bod aplikace serveru Blazor je definovaný v souboru *program.cs* , jak by se zobrazila v konzolové aplikaci. Když se aplikace spustí, vytvoří a spustí instanci webového hostitele s použitím výchozích hodnot specifických pro webové aplikace. Webový hostitel spravuje životní cyklus aplikace serveru Blazor a nastavuje služby na úrovni hostitele. Příklady takových služeb jsou konfigurace, protokolování, vkládání závislostí a HTTP Server. Tento kód je většinou často používaný a je často nezměněný.

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

Blazor aplikace pro WebAssembly také definují vstupní bod v *program.cs*. Kód vypadá trochu jinak. Kód je podobný v tom, že nastavuje hostitele aplikace tak, aby poskytoval stejné služby na úrovni hostitele pro aplikaci. Hostitel aplikace pro WebAssembly ale nenastaví Server HTTP, protože se spustí přímo v prohlížeči.

Aplikace Blazor mají `Startup` třídu namísto souboru *Global. asax* k definování spouštěcí logiky pro aplikaci. `Startup` Třída se používá ke konfiguraci aplikace a všech služeb specifických pro aplikace. V aplikaci `Startup` Blazor serveru se třída používá k nastavení koncového bodu pro připojení v reálném čase, které používá Blazor mezi klientskými prohlížeči a serverem. V aplikaci `Startup` Blazor WebAssembly třída definuje kořenové součásti pro aplikaci a tam, kde by měly být vykresleny. Podíváme `Startup` se na třídu v části [spuštění aplikace](./app-startup.md) .

## <a name="static-files"></a>Statické soubory

Na rozdíl od projektů webových formulářů ASP.NET ne všechny soubory v projektu Blazor mohou být požadovány jako statické soubory. Pouze soubory ve složce *wwwroot* jsou webové – adresovatelné. Tato složka je označována jako "webový kořenový adresář aplikace". Cokoli mimo webový kořenový adresář aplikace *není* webová adresa. Tato instalace poskytuje další úroveň zabezpečení, která brání nechtěnému vystavení souborů projektu na webu.

## <a name="configuration"></a>Konfigurace

Konfigurace v aplikacích webových formulářů ASP.NET se obvykle zpracovává pomocí jednoho nebo více souborů *Web. config* . Aplikace Blazor obvykle nemají soubory *Web. config* . V takovém případě se soubor používá pouze ke konfiguraci nastavení specifických pro službu IIS, pokud je hostována službou IIS. Místo toho aplikace serveru Blazor používají abstrakce konfigurace ASP.NET Core (aplikace Blazor WebAssembly v současné době nepodporuje stejné abstrakce konfigurace, ale může se jednat o funkci přidanou do budoucna). Například výchozí aplikace serveru Blazor ukládá některá nastavení do souboru *appSettings. JSON*.

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

Většina souborů v projektech Blazor je soubory *. Razor* . Razor je šablonování jazyk založený na jazyce HTML a C# který slouží k dynamickému generování webového uživatelského rozhraní. Soubory *. Razor* definují komponenty, které tvoří uživatelské rozhraní aplikace. Ve většině případů jsou komponenty identické jak pro Blazor Server, tak pro aplikace Blazor pro WebAssembly. Komponenty v Blazor jsou podobné uživatelským ovládacím prvkům ve webových formulářích ASP.NET.

Každý soubor komponenty Razor je zkompilován do třídy .NET při sestavení projektu. Vygenerovaná třída zachytí stav komponenty, logiku vykreslování, metody životního cyklu, obslužné rutiny události a další logiku. Podíváme se na vytváření komponent v části [sestavování opakovaně použitelných komponent uživatelského rozhraní pomocí oddílu Blazor](./components.md) .

Soubory *_Imports. Razor* nejsou soubory komponenty Razor. Místo toho definují sadu direktiv Razor pro import do jiných souborů *. Razor* ve stejné složce a v jejích podsložkách. Například soubor *_Imports. Razor* je konvenční způsob, jak přidat `using` příkazy pro běžně používané obory názvů:

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

Kde jsou stránky v aplikacích Blazor? Blazor nedefinuje samostatnou příponu souboru pro adresovatelné stránky, jako jsou soubory *. aspx* v aplikacích ASP.NET Web Forms. Místo toho jsou stránky definovány přiřazením tras k součástem. Trasa je obvykle přiřazena pomocí `@page` direktivy Razor. Například `Counter` komponenta, která se vytvořila v souboru *Pages/Counter. Razor* , definuje následující trasu:

```razor
@page "/counter"
```

Směrování v Blazor je zpracováváno na straně klienta, nikoli na serveru. Když uživatel přejde v prohlížeči, Blazor zachytí navigaci a potom vykreslí komponentu se stejným směrováním. 

Trasy součástí nejsou aktuálně odvozeny z umístění souboru komponenty, jako jsou stránky *aspx* . Tato funkce může být v budoucnu přidána. Každou trasu musíte explicitně zadat na komponentě. Ukládání komponent s přísměrováním ve složce *Pages* nemá žádný zvláštní význam a je čistě konvencí.

Podrobněji se podrobněji podíváme na téma směrování v Blazor v části [stránky, směrování a rozložení](./pages-routing-layouts.md) .

## <a name="layout"></a>Rozložení

V aplikacích ASP.NET Web Forms se běžné rozložení stránky zpracovává pomocí stránek předlohy (*site. Master*). V aplikacích Blazor se rozložení stránky zpracovává pomocí součástí rozložení (*Shared/MainLayout. Razor*). Komponenty rozložení budou podrobněji popsány v části [Stránka, směrování a rozložení](./pages-routing-layouts.md) .

## <a name="bootstrap-blazor"></a>Spouštěcí Blazor

K zavedení Blazor musí aplikace:

* Určete, kam má být vygenerována kořenová komponenta (*App. Razor*) na stránce.
* Přidejte odpovídající skript Blazor Framework.

V aplikaci Blazor Server je v souboru *_Host. cshtml* definovaná stránka hostitele kořenové součásti. Tento soubor definuje stránku Razor, nikoli komponentu. Razor Pages použít syntaxe Razor k definování serverově adresované stránky, velmi podobně jako na stránce *aspx* . `Html.RenderComponentAsync<TComponent>(RenderMode)` Metoda slouží k definování, kde má být vykreslena komponenta na úrovni root. `RenderMode` Možnost určuje způsob, jakým má být komponenta vykreslena. Následující tabulka popisuje podporované `RenderMode` možnosti.

|Možnost                        |Popis       |
|------------------------------|------------------|
|`RenderMode.Server`           |Po navázání spojení s prohlížečem se interaktivně vykreslovat.|
|`RenderMode.ServerPrerendered`|První předvykreslování a potom vykreslené interaktivně|
|`RenderMode.Static`           |Vykresleno jako statický obsah|

Odkaz na skript *_framework/blazor. Server. js* vytvoří připojení v reálném čase se serverem a pak bude pracovat se všemi interakcemi uživatelů a AKTUALIZACEMI uživatelského rozhraní.

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

V aplikaci Blazor WebAssembly je stránka hostitele jednoduchým statickým souborem HTML pod *wwwroot/index.html*. `<app>` Prvek slouží k označení, kde by měla být vykreslena kořenová komponenta.

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

Při sestavení projektu Blazor jsou všechny komponenty a soubory kódu Razor zkompilovány do jediného sestavení. Na rozdíl od projektů webových formulářů ASP.NET Blazor nepodporuje kompilaci běhové logiky uživatelského rozhraní.

## <a name="run-the-app"></a>Spuštění aplikace

Pokud chcete spustit aplikaci Blazor Server, stiskněte `F5` v aplikaci Visual Studio. Aplikace Blazor nepodporují kompilaci za běhu. Chcete-li zobrazit výsledky kódu a změny kódu komponenty, sestavte a znovu spusťte aplikaci pomocí připojeného ladicího programu. Pokud spustíte program bez připojeného ladicího`Ctrl+F5`programu (), Visual Studio sleduje změny souborů a restartuje aplikaci, jakmile budou provedeny změny. Prohlížeč se aktualizuje ručně, protože se udělaly změny.

Chcete-li spustit aplikaci WebAssembly v Blazor, vyberte jeden z následujících přístupů:

* Spusťte klientský projekt přímo pomocí vývojového serveru.
* Spusťte serverový projekt při hostování aplikace pomocí ASP.NET Core.

Blazor aplikace WebAssembly nepodporují ladění pomocí sady Visual Studio. Pokud chcete aplikaci spustit, použijte `Ctrl+F5` `F5`místo. Místo toho můžete ladit aplikace Blazor WebAssembly přímo v prohlížeči. Podrobnosti najdete v tématu [ladění ASP.NET Core Blazor](/aspnet/core/blazor/debug) .

>[!div class="step-by-step"]
>[Předchozí](hosting-models.md)
>[Další](app-startup.md)
