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
# <a name="project-structure-for-blazor-apps"></a><span data-ttu-id="2180b-103">Struktura projektu pro aplikace Blazor</span><span class="sxs-lookup"><span data-stu-id="2180b-103">Project structure for Blazor apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="2180b-104">Navzdory jejich významným rozdílům struktury projektů ASP.NET webové formuláře a Blazor sdílejí mnoho podobných konceptů.</span><span class="sxs-lookup"><span data-stu-id="2180b-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="2180b-105">Tady se podíváme na strukturu projektu Blazor a porovnejte ji s projektem webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2180b-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="2180b-106">Pokud chcete vytvořit svoji první aplikaci pro Blazor, postupujte podle pokynů v tématu [Začínáme s Blazor](/aspnet/core/blazor/get-started).</span><span class="sxs-lookup"><span data-stu-id="2180b-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="2180b-107">Můžete postupovat podle pokynů k vytvoření aplikace Blazor serveru nebo aplikace Blazor WebAssembly hostované v ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2180b-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="2180b-108">S výjimkou logiky specifické pro model hostování je většina kódu v obou projektech stejná.</span><span class="sxs-lookup"><span data-stu-id="2180b-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="2180b-109">Soubor projektu</span><span class="sxs-lookup"><span data-stu-id="2180b-109">Project file</span></span>

<span data-ttu-id="2180b-110">Blazor serverové aplikace jsou projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2180b-110">Blazor Server apps are .NET Core projects.</span></span> <span data-ttu-id="2180b-111">Soubor projektu pro aplikaci Blazor Server je co nejjednodušší, protože může získat:</span><span class="sxs-lookup"><span data-stu-id="2180b-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="2180b-112">Soubor projektu pro aplikaci WebAssembly v Blazor se trochu zabývají. (přesná čísla verze se můžou lišit):</span><span class="sxs-lookup"><span data-stu-id="2180b-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

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

<span data-ttu-id="2180b-113">Blazor .NET Standard cíle projektů WebAssembly místo .NET Core, protože běží v prohlížeči v prostředí .NET runtime založeném na WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="2180b-113">Blazor WebAssembly projects target .NET Standard instead of .NET Core because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="2180b-114">Rozhraní .NET nemůžete nainstalovat do webového prohlížeče, jako je to možné na serveru nebo v počítači pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="2180b-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="2180b-115">V důsledku toho projekt odkazuje na rozhraní Blazor pomocí jednotlivých odkazů na balíčky.</span><span class="sxs-lookup"><span data-stu-id="2180b-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="2180b-116">Porovnáním, výchozí projekt webových formulářů ASP.NET obsahuje téměř 300 řádků XML v souboru *. csproj* , přičemž většina z nich explicitně uvádí různé soubory kódu a obsahu v projektu.</span><span class="sxs-lookup"><span data-stu-id="2180b-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="2180b-117">Mnohé z zjednodušení v projektech .NET Core a .NET Standard pocházejí z výchozích cílů a vlastností importovaných odkazem na `Microsoft.NET.Sdk.Web` sadu SDK, která se často označuje jako jednoduše webová sada SDK.</span><span class="sxs-lookup"><span data-stu-id="2180b-117">Many of the simplifications in the .NET Core- and .NET Standard-based projects come from the default targets and properties imported by referencing the `Microsoft.NET.Sdk.Web` SDK, often referred to as simply the Web SDK.</span></span> <span data-ttu-id="2180b-118">Webová sada SDK obsahuje zástupné znaky a další pohodlí, které zjednodušují zahrnutí kódu a souborů obsahu v projektu.</span><span class="sxs-lookup"><span data-stu-id="2180b-118">The Web SDK includes wildcards and other conveniences that simplify inclusion of code and content files in the project.</span></span> <span data-ttu-id="2180b-119">Soubory není nutné explicitně vypisovat.</span><span class="sxs-lookup"><span data-stu-id="2180b-119">You don't need to list the files explicitly.</span></span> <span data-ttu-id="2180b-120">Při cílení na .NET Core webová sada SDK také přidá odkazy na rozhraní do sdílených rozhraní .NET Core i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2180b-120">When targeting .NET Core, the Web SDK also adds framework references to both the .NET Core and ASP.NET Core shared frameworks.</span></span> <span data-ttu-id="2180b-121">Rozhraní jsou viditelná v uzlu**architektury** **závislostí** > v okně **Průzkumník řešení** .</span><span class="sxs-lookup"><span data-stu-id="2180b-121">The frameworks are visible from the **Dependencies** > **Frameworks** node in the **Solution Explorer** window.</span></span> <span data-ttu-id="2180b-122">Sdílené architektury jsou kolekce sestavení, která byla nainstalována na počítači při instalaci rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2180b-122">The shared frameworks are collections of assemblies that were installed on the machine when installing .NET Core.</span></span>

<span data-ttu-id="2180b-123">I když jsou podporovány, jednotlivé odkazy na sestavení jsou méně běžné v projektech .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2180b-123">Although they're supported, individual assembly references are less common in .NET Core projects.</span></span> <span data-ttu-id="2180b-124">Většina závislostí projektu se zpracovává jako odkazy na balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="2180b-124">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="2180b-125">V projektech .NET Core musíte odkazovat jenom na závislosti balíčků nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="2180b-125">You only need to reference top-level package dependencies in .NET Core projects.</span></span> <span data-ttu-id="2180b-126">Přenosné závislosti jsou zahrnuty automaticky.</span><span class="sxs-lookup"><span data-stu-id="2180b-126">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="2180b-127">Namísto použití souboru *Packages. config* , který se běžně našel v projektech webových formulářů ASP.NET, na referenční balíčky, se odkazy na balíčky přidávají do `<PackageReference>` souboru projektu pomocí elementu.</span><span class="sxs-lookup"><span data-stu-id="2180b-127">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="2180b-128">Vstupní bod</span><span class="sxs-lookup"><span data-stu-id="2180b-128">Entry point</span></span>

<span data-ttu-id="2180b-129">Vstupní bod aplikace serveru Blazor je definovaný v souboru *program.cs* , jak by se zobrazila v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2180b-129">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="2180b-130">Když se aplikace spustí, vytvoří a spustí instanci webového hostitele s použitím výchozích hodnot specifických pro webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="2180b-130">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="2180b-131">Webový hostitel spravuje životní cyklus aplikace serveru Blazor a nastavuje služby na úrovni hostitele.</span><span class="sxs-lookup"><span data-stu-id="2180b-131">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="2180b-132">Příklady takových služeb jsou konfigurace, protokolování, vkládání závislostí a HTTP Server.</span><span class="sxs-lookup"><span data-stu-id="2180b-132">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="2180b-133">Tento kód je většinou často používaný a je často nezměněný.</span><span class="sxs-lookup"><span data-stu-id="2180b-133">This code is mostly boilerplate and is often left unchanged.</span></span>

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

<span data-ttu-id="2180b-134">Blazor aplikace pro WebAssembly také definují vstupní bod v *program.cs*.</span><span class="sxs-lookup"><span data-stu-id="2180b-134">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="2180b-135">Kód vypadá trochu jinak.</span><span class="sxs-lookup"><span data-stu-id="2180b-135">The code looks slightly different.</span></span> <span data-ttu-id="2180b-136">Kód je podobný v tom, že nastavuje hostitele aplikace tak, aby poskytoval stejné služby na úrovni hostitele pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2180b-136">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="2180b-137">Hostitel aplikace pro WebAssembly ale nenastaví Server HTTP, protože se spustí přímo v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="2180b-137">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="2180b-138">Aplikace Blazor mají `Startup` třídu namísto souboru *Global. asax* k definování spouštěcí logiky pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2180b-138">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="2180b-139">`Startup` Třída se používá ke konfiguraci aplikace a všech služeb specifických pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="2180b-139">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="2180b-140">V aplikaci `Startup` Blazor serveru se třída používá k nastavení koncového bodu pro připojení v reálném čase, které používá Blazor mezi klientskými prohlížeči a serverem.</span><span class="sxs-lookup"><span data-stu-id="2180b-140">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="2180b-141">V aplikaci `Startup` Blazor WebAssembly třída definuje kořenové součásti pro aplikaci a tam, kde by měly být vykresleny.</span><span class="sxs-lookup"><span data-stu-id="2180b-141">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="2180b-142">Podíváme `Startup` se na třídu v části [spuštění aplikace](./app-startup.md) .</span><span class="sxs-lookup"><span data-stu-id="2180b-142">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="2180b-143">Statické soubory</span><span class="sxs-lookup"><span data-stu-id="2180b-143">Static files</span></span>

<span data-ttu-id="2180b-144">Na rozdíl od projektů webových formulářů ASP.NET ne všechny soubory v projektu Blazor mohou být požadovány jako statické soubory.</span><span class="sxs-lookup"><span data-stu-id="2180b-144">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="2180b-145">Pouze soubory ve složce *wwwroot* jsou webové – adresovatelné.</span><span class="sxs-lookup"><span data-stu-id="2180b-145">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="2180b-146">Tato složka je označována jako "webový kořenový adresář aplikace".</span><span class="sxs-lookup"><span data-stu-id="2180b-146">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="2180b-147">Cokoli mimo webový kořenový adresář aplikace *není* webová adresa.</span><span class="sxs-lookup"><span data-stu-id="2180b-147">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="2180b-148">Tato instalace poskytuje další úroveň zabezpečení, která brání nechtěnému vystavení souborů projektu na webu.</span><span class="sxs-lookup"><span data-stu-id="2180b-148">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="2180b-149">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="2180b-149">Configuration</span></span>

<span data-ttu-id="2180b-150">Konfigurace v aplikacích webových formulářů ASP.NET se obvykle zpracovává pomocí jednoho nebo více souborů *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="2180b-150">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="2180b-151">Aplikace Blazor obvykle nemají soubory *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="2180b-151">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="2180b-152">V takovém případě se soubor používá pouze ke konfiguraci nastavení specifických pro službu IIS, pokud je hostována službou IIS.</span><span class="sxs-lookup"><span data-stu-id="2180b-152">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="2180b-153">Místo toho aplikace serveru Blazor používají abstrakce konfigurace ASP.NET Core (aplikace Blazor WebAssembly v současné době nepodporuje stejné abstrakce konfigurace, ale může se jednat o funkci přidanou do budoucna).</span><span class="sxs-lookup"><span data-stu-id="2180b-153">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="2180b-154">Například výchozí aplikace serveru Blazor ukládá některá nastavení do souboru *appSettings. JSON*.</span><span class="sxs-lookup"><span data-stu-id="2180b-154">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

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

<span data-ttu-id="2180b-155">Další informace o konfiguraci najdete v tématu ASP.NET Core projekty v oddílu [Konfigurace](./config.md) .</span><span class="sxs-lookup"><span data-stu-id="2180b-155">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="2180b-156">Komponenty Razor</span><span class="sxs-lookup"><span data-stu-id="2180b-156">Razor components</span></span>

<span data-ttu-id="2180b-157">Většina souborů v projektech Blazor je soubory *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="2180b-157">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="2180b-158">Razor je šablonování jazyk založený na jazyce HTML a C# který slouží k dynamickému generování webového uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2180b-158">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="2180b-159">Soubory *. Razor* definují komponenty, které tvoří uživatelské rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="2180b-159">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="2180b-160">Ve většině případů jsou komponenty identické jak pro Blazor Server, tak pro aplikace Blazor pro WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="2180b-160">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="2180b-161">Komponenty v Blazor jsou podobné uživatelským ovládacím prvkům ve webových formulářích ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2180b-161">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="2180b-162">Každý soubor komponenty Razor je zkompilován do třídy .NET při sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="2180b-162">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="2180b-163">Vygenerovaná třída zachytí stav komponenty, logiku vykreslování, metody životního cyklu, obslužné rutiny události a další logiku.</span><span class="sxs-lookup"><span data-stu-id="2180b-163">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="2180b-164">Podíváme se na vytváření komponent v části [sestavování opakovaně použitelných komponent uživatelského rozhraní pomocí oddílu Blazor](./components.md) .</span><span class="sxs-lookup"><span data-stu-id="2180b-164">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="2180b-165">Soubory *_Imports. Razor* nejsou soubory komponenty Razor.</span><span class="sxs-lookup"><span data-stu-id="2180b-165">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="2180b-166">Místo toho definují sadu direktiv Razor pro import do jiných souborů *. Razor* ve stejné složce a v jejích podsložkách.</span><span class="sxs-lookup"><span data-stu-id="2180b-166">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="2180b-167">Například soubor *_Imports. Razor* je konvenční způsob, jak přidat `using` příkazy pro běžně používané obory názvů:</span><span class="sxs-lookup"><span data-stu-id="2180b-167">For example, a *_Imports.razor* file is a conventional way to add `using` statements for commonly used namespaces:</span></span>

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

## <a name="pages"></a><span data-ttu-id="2180b-168">Stránky</span><span class="sxs-lookup"><span data-stu-id="2180b-168">Pages</span></span>

<span data-ttu-id="2180b-169">Kde jsou stránky v aplikacích Blazor?</span><span class="sxs-lookup"><span data-stu-id="2180b-169">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="2180b-170">Blazor nedefinuje samostatnou příponu souboru pro adresovatelné stránky, jako jsou soubory *. aspx* v aplikacích ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="2180b-170">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="2180b-171">Místo toho jsou stránky definovány přiřazením tras k součástem.</span><span class="sxs-lookup"><span data-stu-id="2180b-171">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="2180b-172">Trasa je obvykle přiřazena pomocí `@page` direktivy Razor.</span><span class="sxs-lookup"><span data-stu-id="2180b-172">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="2180b-173">Například `Counter` komponenta, která se vytvořila v souboru *Pages/Counter. Razor* , definuje následující trasu:</span><span class="sxs-lookup"><span data-stu-id="2180b-173">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="2180b-174">Směrování v Blazor je zpracováváno na straně klienta, nikoli na serveru.</span><span class="sxs-lookup"><span data-stu-id="2180b-174">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="2180b-175">Když uživatel přejde v prohlížeči, Blazor zachytí navigaci a potom vykreslí komponentu se stejným směrováním.</span><span class="sxs-lookup"><span data-stu-id="2180b-175">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span> 

<span data-ttu-id="2180b-176">Trasy součástí nejsou aktuálně odvozeny z umístění souboru komponenty, jako jsou stránky *aspx* .</span><span class="sxs-lookup"><span data-stu-id="2180b-176">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="2180b-177">Tato funkce může být v budoucnu přidána.</span><span class="sxs-lookup"><span data-stu-id="2180b-177">This feature may be added in the future.</span></span> <span data-ttu-id="2180b-178">Každou trasu musíte explicitně zadat na komponentě.</span><span class="sxs-lookup"><span data-stu-id="2180b-178">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="2180b-179">Ukládání komponent s přísměrováním ve složce *Pages* nemá žádný zvláštní význam a je čistě konvencí.</span><span class="sxs-lookup"><span data-stu-id="2180b-179">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="2180b-180">Podrobněji se podrobněji podíváme na téma směrování v Blazor v části [stránky, směrování a rozložení](./pages-routing-layouts.md) .</span><span class="sxs-lookup"><span data-stu-id="2180b-180">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="2180b-181">Rozložení</span><span class="sxs-lookup"><span data-stu-id="2180b-181">Layout</span></span>

<span data-ttu-id="2180b-182">V aplikacích ASP.NET Web Forms se běžné rozložení stránky zpracovává pomocí stránek předlohy (*site. Master*).</span><span class="sxs-lookup"><span data-stu-id="2180b-182">In ASP.NET Web Forms apps, common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="2180b-183">V aplikacích Blazor se rozložení stránky zpracovává pomocí součástí rozložení (*Shared/MainLayout. Razor*).</span><span class="sxs-lookup"><span data-stu-id="2180b-183">In Blazor apps, page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="2180b-184">Komponenty rozložení budou podrobněji popsány v části [Stránka, směrování a rozložení](./pages-routing-layouts.md) .</span><span class="sxs-lookup"><span data-stu-id="2180b-184">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-blazor"></a><span data-ttu-id="2180b-185">Spouštěcí Blazor</span><span class="sxs-lookup"><span data-stu-id="2180b-185">Bootstrap Blazor</span></span>

<span data-ttu-id="2180b-186">K zavedení Blazor musí aplikace:</span><span class="sxs-lookup"><span data-stu-id="2180b-186">To bootstrap Blazor, the app must:</span></span>

* <span data-ttu-id="2180b-187">Určete, kam má být vygenerována kořenová komponenta (*App. Razor*) na stránce.</span><span class="sxs-lookup"><span data-stu-id="2180b-187">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
* <span data-ttu-id="2180b-188">Přidejte odpovídající skript Blazor Framework.</span><span class="sxs-lookup"><span data-stu-id="2180b-188">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="2180b-189">V aplikaci Blazor Server je v souboru *_Host. cshtml* definovaná stránka hostitele kořenové součásti.</span><span class="sxs-lookup"><span data-stu-id="2180b-189">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="2180b-190">Tento soubor definuje stránku Razor, nikoli komponentu.</span><span class="sxs-lookup"><span data-stu-id="2180b-190">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="2180b-191">Razor Pages použít syntaxe Razor k definování serverově adresované stránky, velmi podobně jako na stránce *aspx* .</span><span class="sxs-lookup"><span data-stu-id="2180b-191">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="2180b-192">`Html.RenderComponentAsync<TComponent>(RenderMode)` Metoda slouží k definování, kde má být vykreslena komponenta na úrovni root.</span><span class="sxs-lookup"><span data-stu-id="2180b-192">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="2180b-193">`RenderMode` Možnost určuje způsob, jakým má být komponenta vykreslena.</span><span class="sxs-lookup"><span data-stu-id="2180b-193">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="2180b-194">Následující tabulka popisuje podporované `RenderMode` možnosti.</span><span class="sxs-lookup"><span data-stu-id="2180b-194">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="2180b-195">Možnost</span><span class="sxs-lookup"><span data-stu-id="2180b-195">Option</span></span>                        |<span data-ttu-id="2180b-196">Popis</span><span class="sxs-lookup"><span data-stu-id="2180b-196">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="2180b-197">Po navázání spojení s prohlížečem se interaktivně vykreslovat.</span><span class="sxs-lookup"><span data-stu-id="2180b-197">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="2180b-198">První předvykreslování a potom vykreslené interaktivně</span><span class="sxs-lookup"><span data-stu-id="2180b-198">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="2180b-199">Vykresleno jako statický obsah</span><span class="sxs-lookup"><span data-stu-id="2180b-199">Rendered as static content</span></span>|

<span data-ttu-id="2180b-200">Odkaz na skript *_framework/blazor. Server. js* vytvoří připojení v reálném čase se serverem a pak bude pracovat se všemi interakcemi uživatelů a AKTUALIZACEMI uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2180b-200">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

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

<span data-ttu-id="2180b-201">V aplikaci Blazor WebAssembly je stránka hostitele jednoduchým statickým souborem HTML pod *wwwroot/index.html*.</span><span class="sxs-lookup"><span data-stu-id="2180b-201">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="2180b-202">`<app>` Prvek slouží k označení, kde by měla být vykreslena kořenová komponenta.</span><span class="sxs-lookup"><span data-stu-id="2180b-202">The `<app>` element is used to indicate where the root component should be rendered.</span></span>

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

<span data-ttu-id="2180b-203">Konkrétní komponenta pro vykreslení je nakonfigurována v `Startup.Configure` metodě aplikace s odpovídajícím Selektor šablon stylů CSS, který určuje, kde by měla být komponenta vykreslena.</span><span class="sxs-lookup"><span data-stu-id="2180b-203">The specific component to render is configured in the app's `Startup.Configure` method with a corresponding CSS selector indicating where the component should be rendered.</span></span>

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

## <a name="build-output"></a><span data-ttu-id="2180b-204">Výstup sestavení</span><span class="sxs-lookup"><span data-stu-id="2180b-204">Build output</span></span>

<span data-ttu-id="2180b-205">Při sestavení projektu Blazor jsou všechny komponenty a soubory kódu Razor zkompilovány do jediného sestavení.</span><span class="sxs-lookup"><span data-stu-id="2180b-205">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="2180b-206">Na rozdíl od projektů webových formulářů ASP.NET Blazor nepodporuje kompilaci běhové logiky uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2180b-206">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="2180b-207">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="2180b-207">Run the app</span></span>

<span data-ttu-id="2180b-208">Pokud chcete spustit aplikaci Blazor Server, stiskněte `F5` v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2180b-208">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="2180b-209">Aplikace Blazor nepodporují kompilaci za běhu.</span><span class="sxs-lookup"><span data-stu-id="2180b-209">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="2180b-210">Chcete-li zobrazit výsledky kódu a změny kódu komponenty, sestavte a znovu spusťte aplikaci pomocí připojeného ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="2180b-210">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="2180b-211">Pokud spustíte program bez připojeného ladicího`Ctrl+F5`programu (), Visual Studio sleduje změny souborů a restartuje aplikaci, jakmile budou provedeny změny.</span><span class="sxs-lookup"><span data-stu-id="2180b-211">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="2180b-212">Prohlížeč se aktualizuje ručně, protože se udělaly změny.</span><span class="sxs-lookup"><span data-stu-id="2180b-212">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="2180b-213">Chcete-li spustit aplikaci WebAssembly v Blazor, vyberte jeden z následujících přístupů:</span><span class="sxs-lookup"><span data-stu-id="2180b-213">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

* <span data-ttu-id="2180b-214">Spusťte klientský projekt přímo pomocí vývojového serveru.</span><span class="sxs-lookup"><span data-stu-id="2180b-214">Run the client project directly using the development server.</span></span>
* <span data-ttu-id="2180b-215">Spusťte serverový projekt při hostování aplikace pomocí ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2180b-215">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="2180b-216">Blazor aplikace WebAssembly nepodporují ladění pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2180b-216">Blazor WebAssembly apps don't support debugging using Visual Studio.</span></span> <span data-ttu-id="2180b-217">Pokud chcete aplikaci spustit, použijte `Ctrl+F5` `F5`místo.</span><span class="sxs-lookup"><span data-stu-id="2180b-217">To run the app, use `Ctrl+F5` instead of `F5`.</span></span> <span data-ttu-id="2180b-218">Místo toho můžete ladit aplikace Blazor WebAssembly přímo v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="2180b-218">You can instead debug Blazor WebAssembly apps directly in the browser.</span></span> <span data-ttu-id="2180b-219">Podrobnosti najdete v tématu [ladění ASP.NET Core Blazor](/aspnet/core/blazor/debug) .</span><span class="sxs-lookup"><span data-stu-id="2180b-219">See [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2180b-220">[Předchozí](hosting-models.md)
>[Další](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="2180b-220">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
