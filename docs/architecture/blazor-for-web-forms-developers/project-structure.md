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
# <a name="project-structure-for-blazor-apps"></a><span data-ttu-id="9344d-103">Struktura projektu pro aplikace Blazor</span><span class="sxs-lookup"><span data-stu-id="9344d-103">Project structure for Blazor apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="9344d-104">Navzdory svým významným rozdílům ve struktuře projektů sdílejí ASP.NET Web Forms a Blazor mnoho podobných konceptů.</span><span class="sxs-lookup"><span data-stu-id="9344d-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="9344d-105">Zde se podíváme na strukturu projektu Blazor a porovnáme jej s projektem ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="9344d-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="9344d-106">Chcete-li vytvořit první aplikaci Blazor, postupujte podle pokynů v [krocích pro zahájení začínání v aplikaci Blazor](/aspnet/core/blazor/get-started).</span><span class="sxs-lookup"><span data-stu-id="9344d-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="9344d-107">Podle pokynů můžete vytvořit aplikaci Blazor Server nebo aplikaci Blazor WebAssembly hostovoci v ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9344d-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="9344d-108">S výjimkou logiky specifické pro hostování modelu je většina kódu v obou projektech stejná.</span><span class="sxs-lookup"><span data-stu-id="9344d-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="9344d-109">Soubor projektu</span><span class="sxs-lookup"><span data-stu-id="9344d-109">Project file</span></span>

<span data-ttu-id="9344d-110">Aplikace Blazor Server jsou projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9344d-110">Blazor Server apps are .NET Core projects.</span></span> <span data-ttu-id="9344d-111">Soubor projektu pro aplikaci Blazor Server je asi tak jednoduchý, jak to může dostat:</span><span class="sxs-lookup"><span data-stu-id="9344d-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="9344d-112">Soubor projektu pro aplikaci Blazor WebAssembly vypadá o něco více (přesná čísla verzí se mohou lišit):</span><span class="sxs-lookup"><span data-stu-id="9344d-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

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

<span data-ttu-id="9344d-113">Projekty Blazor WebAssembly cílí na standard .NET místo .NET Core, protože jsou spuštěny v prohlížeči v době runtime .NET založené na webové sestavě.</span><span class="sxs-lookup"><span data-stu-id="9344d-113">Blazor WebAssembly projects target .NET Standard instead of .NET Core because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="9344d-114">Rozhraní .NET nelze nainstalovat do webového prohlížeče jako na serveru nebo na vývojářském počítači.</span><span class="sxs-lookup"><span data-stu-id="9344d-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="9344d-115">Projekt proto odkazuje na rámec Blazor pomocí jednotlivých odkazů na balíčky.</span><span class="sxs-lookup"><span data-stu-id="9344d-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="9344d-116">Pro srovnání, výchozí ASP.NET projektu Webových formulářů obsahuje téměř 300 řádků XML ve svém souboru *.csproj,* z nichž většina je explicitně výpis různých souborů kódu a obsahu v projektu.</span><span class="sxs-lookup"><span data-stu-id="9344d-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="9344d-117">Mnoho zjednodušení v projektech založených na standardu .NET a .NET standard pochází z výchozích cílů a vlastností importovaných odkazem na sadu `Microsoft.NET.Sdk.Web` SDK, často označované jako jednoduše webová sada SDK.</span><span class="sxs-lookup"><span data-stu-id="9344d-117">Many of the simplifications in the .NET Core- and .NET Standard-based projects come from the default targets and properties imported by referencing the `Microsoft.NET.Sdk.Web` SDK, often referred to as simply the Web SDK.</span></span> <span data-ttu-id="9344d-118">Sada Web SDK obsahuje zástupné znaky a další vymoženosti, které zjednodušují zahrnutí souborů kódu a obsahu do projektu.</span><span class="sxs-lookup"><span data-stu-id="9344d-118">The Web SDK includes wildcards and other conveniences that simplify inclusion of code and content files in the project.</span></span> <span data-ttu-id="9344d-119">Soubory není nutné uvádět explicitně.</span><span class="sxs-lookup"><span data-stu-id="9344d-119">You don't need to list the files explicitly.</span></span> <span data-ttu-id="9344d-120">Při cílení na .NET Core, Web SDK také přidává odkazy na rozhraní rozhraní .NET Core a ASP.NET základní sdílené architektury.</span><span class="sxs-lookup"><span data-stu-id="9344d-120">When targeting .NET Core, the Web SDK also adds framework references to both the .NET Core and ASP.NET Core shared frameworks.</span></span> <span data-ttu-id="9344d-121">Rámce jsou viditelné z uzlu **Architektury** > **závislostí** v okně **Průzkumník řešení.**</span><span class="sxs-lookup"><span data-stu-id="9344d-121">The frameworks are visible from the **Dependencies** > **Frameworks** node in the **Solution Explorer** window.</span></span> <span data-ttu-id="9344d-122">Sdílené architektury jsou kolekce sestavení, které byly nainstalovány v počítači při instalaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9344d-122">The shared frameworks are collections of assemblies that were installed on the machine when installing .NET Core.</span></span>

<span data-ttu-id="9344d-123">I když jsou podporovány, jednotlivé odkazy na sestavení jsou méně běžné v projektech .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9344d-123">Although they're supported, individual assembly references are less common in .NET Core projects.</span></span> <span data-ttu-id="9344d-124">Většina závislostí projektu jsou zpracovány jako odkazy na balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="9344d-124">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="9344d-125">Jetřeba odkazovat pouze na závislosti balíčků nejvyšší úrovně v projektech .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9344d-125">You only need to reference top-level package dependencies in .NET Core projects.</span></span> <span data-ttu-id="9344d-126">Přenosité závislosti jsou zahrnuty automaticky.</span><span class="sxs-lookup"><span data-stu-id="9344d-126">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="9344d-127">Namísto použití souboru *packages.config,* který se běžně vyskytuje v projektech ASP.NET webových `<PackageReference>` formulářů, jsou odkazy na balíčky přidány do souboru projektu pomocí prvku.</span><span class="sxs-lookup"><span data-stu-id="9344d-127">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="9344d-128">Vstupní bod</span><span class="sxs-lookup"><span data-stu-id="9344d-128">Entry point</span></span>

<span data-ttu-id="9344d-129">Vstupní bod aplikace Blazor Server je definován v *souboru Program.cs,* jak byste viděli v aplikaci Console.</span><span class="sxs-lookup"><span data-stu-id="9344d-129">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="9344d-130">Když se aplikace spustí, vytvoří a spustí instanci webového hostitele pomocí výchozích hodnot specifických pro webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="9344d-130">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="9344d-131">Webový hostitel spravuje životní cyklus aplikace Blazor Server a nastavuje služby na úrovni hostitele.</span><span class="sxs-lookup"><span data-stu-id="9344d-131">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="9344d-132">Příklady těchto služeb jsou konfigurace, protokolování, vkládání závislostí a http server.</span><span class="sxs-lookup"><span data-stu-id="9344d-132">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="9344d-133">Tento kód je většinou často standardní a je často ponechánbeze změny.</span><span class="sxs-lookup"><span data-stu-id="9344d-133">This code is mostly boilerplate and is often left unchanged.</span></span>

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

<span data-ttu-id="9344d-134">Aplikace Blazor WebAssembly také definují vstupní bod v *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="9344d-134">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="9344d-135">Kód vypadá trochu jinak.</span><span class="sxs-lookup"><span data-stu-id="9344d-135">The code looks slightly different.</span></span> <span data-ttu-id="9344d-136">Kód je podobný v tom, že nastavuje hostitele aplikace tak, aby poskytoval stejnou službu na úrovni hostitele.</span><span class="sxs-lookup"><span data-stu-id="9344d-136">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="9344d-137">Hostitel aplikace WebAssembly však nenastavuje http server, protože se spouští přímo v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="9344d-137">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="9344d-138">Aplikace Blazor `Startup` mají třídu namísto souboru *Global.asax,* která definuje logiku spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="9344d-138">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="9344d-139">Třída `Startup` se používá ke konfiguraci aplikace a všechny služby specifické pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9344d-139">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="9344d-140">V aplikaci Blazor `Startup` Server se třída používá k nastavení koncového bodu pro připojení v reálném čase používaného Blazorem mezi klientskými prohlížeči a serverem.</span><span class="sxs-lookup"><span data-stu-id="9344d-140">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="9344d-141">V aplikaci Blazor WebAssembly `Startup` třída definuje kořenové součásti aplikace a kde by měly být vykresleny.</span><span class="sxs-lookup"><span data-stu-id="9344d-141">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="9344d-142">Podíváme se hlouběji na `Startup` třídu v části [spuštění aplikace.](./app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="9344d-142">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="9344d-143">Statické soubory</span><span class="sxs-lookup"><span data-stu-id="9344d-143">Static files</span></span>

<span data-ttu-id="9344d-144">Na rozdíl od projektů ASP.NET webových formulářů nelze jako statické soubory požadovat všechny soubory v projektu Blazor.</span><span class="sxs-lookup"><span data-stu-id="9344d-144">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="9344d-145">Pouze soubory ve složce *wwwroot* jsou webové adresovatelné.</span><span class="sxs-lookup"><span data-stu-id="9344d-145">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="9344d-146">Tato složka je odkazována na "kořen ový web" aplikace.</span><span class="sxs-lookup"><span data-stu-id="9344d-146">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="9344d-147">Nic mimo kořen webu aplikace *není* adresovatelné na webu.</span><span class="sxs-lookup"><span data-stu-id="9344d-147">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="9344d-148">Toto nastavení poskytuje další úroveň zabezpečení, která zabraňuje náhodnému vystavení souborů projektu přes web.</span><span class="sxs-lookup"><span data-stu-id="9344d-148">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="9344d-149">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9344d-149">Configuration</span></span>

<span data-ttu-id="9344d-150">Konfigurace v aplikacích ASP.NET webových formulářů se obvykle zpracovává pomocí jednoho nebo více souborů *web.config.*</span><span class="sxs-lookup"><span data-stu-id="9344d-150">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="9344d-151">Aplikace Blazor obvykle nemají soubory *web.config.*</span><span class="sxs-lookup"><span data-stu-id="9344d-151">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="9344d-152">Pokud ano, soubor se používá pouze ke konfiguraci nastavení specifických pro službu IIS, pokud jsou hostována ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="9344d-152">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="9344d-153">Místo toho aplikace Blazor Server používají ASP.NET abstrakce konfigurace Core (aplikace Blazor WebAssembly v současné době nepodporují stejné abstrakce konfigurace, ale to může být funkce přidaná v budoucnu).</span><span class="sxs-lookup"><span data-stu-id="9344d-153">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="9344d-154">Například výchozí aplikace Blazor Server ukládá některá nastavení v *souboru appsettings.json*.</span><span class="sxs-lookup"><span data-stu-id="9344d-154">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

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

<span data-ttu-id="9344d-155">Další informace o konfiguraci v ASP.NET základních projektech najdete v části [Konfigurace.](./config.md)</span><span class="sxs-lookup"><span data-stu-id="9344d-155">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="9344d-156">Komponenty pro břitvy</span><span class="sxs-lookup"><span data-stu-id="9344d-156">Razor components</span></span>

<span data-ttu-id="9344d-157">Většina souborů v blazorprojektech jsou *.razor* soubory.</span><span class="sxs-lookup"><span data-stu-id="9344d-157">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="9344d-158">Razor je šablonovací jazyk založený na HTML a C#, který se používá k dynamickému generování webového uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9344d-158">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="9344d-159">Soubory *.razor* definují součásti, které tvoří ui aplikace.</span><span class="sxs-lookup"><span data-stu-id="9344d-159">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="9344d-160">Součásti jsou většinou identické jak pro aplikace Blazor Server, tak pro aplikace Blazor WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="9344d-160">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="9344d-161">Komponenty v Blazoru jsou obdobou uživatelských ovládacích prvků v ASP.NET Webových formulářích.</span><span class="sxs-lookup"><span data-stu-id="9344d-161">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="9344d-162">Každý soubor komponenty Razor je zkompilován do třídy .NET při sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="9344d-162">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="9344d-163">Vygenerovaná třída zachycuje stav komponenty, logiku vykreslování, metody životního cyklu, obslužné rutiny událostí a další logiku.</span><span class="sxs-lookup"><span data-stu-id="9344d-163">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="9344d-164">Podíváme se na vytváření komponent v [opakovaně použitelných komponentách ui budovy s částí Blazor.](./components.md)</span><span class="sxs-lookup"><span data-stu-id="9344d-164">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="9344d-165">Soubory *_Imports.razor* nejsou soubory komponent razor.</span><span class="sxs-lookup"><span data-stu-id="9344d-165">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="9344d-166">Místo toho definují sadu direktiv razor pro import do jiných souborů *.razor* ve stejné složce a v jejích podsložkách.</span><span class="sxs-lookup"><span data-stu-id="9344d-166">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="9344d-167">Například soubor *_Imports.razor* je konvenční způsob `using` přidání příkazů pro běžně používané obory názvů:</span><span class="sxs-lookup"><span data-stu-id="9344d-167">For example, a *_Imports.razor* file is a conventional way to add `using` statements for commonly used namespaces:</span></span>

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

## <a name="pages"></a><span data-ttu-id="9344d-168">Stránky</span><span class="sxs-lookup"><span data-stu-id="9344d-168">Pages</span></span>

<span data-ttu-id="9344d-169">Kde jsou stránky v aplikacích Blazor?</span><span class="sxs-lookup"><span data-stu-id="9344d-169">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="9344d-170">Blazor nedefinuje samostatnou příponu souborů pro adresovatelné stránky, jako jsou soubory *ASPX* v aplikacích ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="9344d-170">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="9344d-171">Místo toho jsou stránky definovány přiřazením tras k komponentám.</span><span class="sxs-lookup"><span data-stu-id="9344d-171">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="9344d-172">Trasa je obvykle přiřazena pomocí `@page` razor směrnice.</span><span class="sxs-lookup"><span data-stu-id="9344d-172">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="9344d-173">Například komponenta `Counter` vytvořená v souboru *Pages/Counter.razor* definuje následující trasu:</span><span class="sxs-lookup"><span data-stu-id="9344d-173">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="9344d-174">Směrování v Blazoru je zpracováno na straně klienta, nikoli na serveru.</span><span class="sxs-lookup"><span data-stu-id="9344d-174">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="9344d-175">Jak uživatel naviguje v prohlížeči, Blazor zachytí navigaci a pak vykreslí komponentu s odpovídající trasou.</span><span class="sxs-lookup"><span data-stu-id="9344d-175">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="9344d-176">Trasy komponent nejsou aktuálně odvozeny umístěním souboru komponenty, jako jsou u stránek *ASPX.*</span><span class="sxs-lookup"><span data-stu-id="9344d-176">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="9344d-177">Tato funkce může být přidána v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="9344d-177">This feature may be added in the future.</span></span> <span data-ttu-id="9344d-178">Každý postup musí být určen explicitně na komponentě.</span><span class="sxs-lookup"><span data-stu-id="9344d-178">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="9344d-179">Ukládání směrovatelných součástí do složky *Stránky* nemá žádný zvláštní význam a je čistě konvence.</span><span class="sxs-lookup"><span data-stu-id="9344d-179">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="9344d-180">Podrobněji se podíváme na směrování v Blazoru v sekci [Stránky, směrování a rozložení.](./pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="9344d-180">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="9344d-181">Rozložení</span><span class="sxs-lookup"><span data-stu-id="9344d-181">Layout</span></span>

<span data-ttu-id="9344d-182">V aplikacích ASP.NET Webových formulářů se společné rozložení stránky zpracovává pomocí vzorových stránek *(Site.Master).*</span><span class="sxs-lookup"><span data-stu-id="9344d-182">In ASP.NET Web Forms apps, common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="9344d-183">V aplikacích Blazor je rozložení stránky zpracováno pomocí komponent rozložení (*Shared/MainLayout.razor*).</span><span class="sxs-lookup"><span data-stu-id="9344d-183">In Blazor apps, page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="9344d-184">Součásti rozložení budou podrobněji popsány v části [Stránka, směrování a rozložení.](./pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="9344d-184">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-blazor"></a><span data-ttu-id="9344d-185">Bootstrap Blazor</span><span class="sxs-lookup"><span data-stu-id="9344d-185">Bootstrap Blazor</span></span>

<span data-ttu-id="9344d-186">Chcete-li zavést Blazor, aplikace musí:</span><span class="sxs-lookup"><span data-stu-id="9344d-186">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="9344d-187">Určete, kde na stránce má být vykreslena kořenová komponenta (*App.Razor*).</span><span class="sxs-lookup"><span data-stu-id="9344d-187">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="9344d-188">Přidejte odpovídající blazor framework skript.</span><span class="sxs-lookup"><span data-stu-id="9344d-188">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="9344d-189">V aplikaci Blazor Server je hostitelská stránka kořenové komponenty definována v souboru *_Host.cshtml.*</span><span class="sxs-lookup"><span data-stu-id="9344d-189">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="9344d-190">Tento soubor definuje stránku razor, nikoli součást.</span><span class="sxs-lookup"><span data-stu-id="9344d-190">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="9344d-191">Razor Pages používají syntaxi Razor k definování stránky adresovatelné serveru, velmi podobně jako stránka *ASPX.*</span><span class="sxs-lookup"><span data-stu-id="9344d-191">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="9344d-192">Metoda `Html.RenderComponentAsync<TComponent>(RenderMode)` se používá k definování, kde by měla být komponenta kořenové úrovně vykreslena.</span><span class="sxs-lookup"><span data-stu-id="9344d-192">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="9344d-193">Tato `RenderMode` možnost označuje způsob, jakým má být komponenta vykreslena.</span><span class="sxs-lookup"><span data-stu-id="9344d-193">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="9344d-194">Následující tabulka popisuje podporované `RenderMode` možnosti.</span><span class="sxs-lookup"><span data-stu-id="9344d-194">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="9344d-195">Možnost</span><span class="sxs-lookup"><span data-stu-id="9344d-195">Option</span></span>                        |<span data-ttu-id="9344d-196">Popis</span><span class="sxs-lookup"><span data-stu-id="9344d-196">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="9344d-197">Vykresleno interaktivně po navázání spojení s prohlížečem</span><span class="sxs-lookup"><span data-stu-id="9344d-197">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="9344d-198">Nejprve předvykreslena a poté vykreslena interaktivně</span><span class="sxs-lookup"><span data-stu-id="9344d-198">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="9344d-199">Vykresleno jako statický obsah</span><span class="sxs-lookup"><span data-stu-id="9344d-199">Rendered as static content</span></span>|

<span data-ttu-id="9344d-200">Odkaz na skript *_framework/blazor.server.js* vytvoří spojení se serverem v reálném čase a poté se zabývá všemi interakcemi uživatele a aktualizacemi uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9344d-200">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

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

<span data-ttu-id="9344d-201">V aplikaci Blazor WebAssembly je hostitelská stránka jednoduchý statický soubor HTML pod *wwwroot/index.html*.</span><span class="sxs-lookup"><span data-stu-id="9344d-201">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="9344d-202">Prvek `<app>` se používá k označení, kde má být kořenová komponenta vykreslena.</span><span class="sxs-lookup"><span data-stu-id="9344d-202">The `<app>` element is used to indicate where the root component should be rendered.</span></span>

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

<span data-ttu-id="9344d-203">Konkrétní komponenta, která má být `Startup.Configure` vykreslena, je konfigurována v metodě aplikace s odpovídajícím voličem CSS, který označuje, kde má být komponenta vykreslena.</span><span class="sxs-lookup"><span data-stu-id="9344d-203">The specific component to render is configured in the app's `Startup.Configure` method with a corresponding CSS selector indicating where the component should be rendered.</span></span>

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

## <a name="build-output"></a><span data-ttu-id="9344d-204">Vytvořit výstup</span><span class="sxs-lookup"><span data-stu-id="9344d-204">Build output</span></span>

<span data-ttu-id="9344d-205">Při sestavení projektu Blazor jsou všechny komponenty Razor a soubory kódu zkompilovány do jednoho sestavení.</span><span class="sxs-lookup"><span data-stu-id="9344d-205">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="9344d-206">Na rozdíl od ASP.NET projekty webových formulářů Blazor nepodporuje runtime kompilaci logiky uživatelského nastavení.</span><span class="sxs-lookup"><span data-stu-id="9344d-206">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="9344d-207">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="9344d-207">Run the app</span></span>

<span data-ttu-id="9344d-208">Chcete-li spustit aplikaci Blazor Server, stiskněte v `F5` sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9344d-208">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="9344d-209">Aplikace Blazor nepodporují kompilaci za běhu.</span><span class="sxs-lookup"><span data-stu-id="9344d-209">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="9344d-210">Chcete-li zobrazit výsledky změn kódu a značek komponent, znovu sestavte a restartujte aplikaci s připojeným ladicím programem.</span><span class="sxs-lookup"><span data-stu-id="9344d-210">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="9344d-211">Pokud spustíte bez připojenéladicí`Ctrl+F5`program ( ), Visual Studio hodinky pro změny souborů a restartuje aplikaci jako změny jsou prováděny.</span><span class="sxs-lookup"><span data-stu-id="9344d-211">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="9344d-212">Při provádění změn prohlížeč ručně aktualizujete.</span><span class="sxs-lookup"><span data-stu-id="9344d-212">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="9344d-213">Chcete-li spustit aplikaci Blazor WebAssembly, zvolte jeden z následujících přístupů:</span><span class="sxs-lookup"><span data-stu-id="9344d-213">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="9344d-214">Spusťte projekt klienta přímo pomocí vývojového serveru.</span><span class="sxs-lookup"><span data-stu-id="9344d-214">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="9344d-215">Spusťte serverový projekt při hostování aplikace s ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9344d-215">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="9344d-216">Aplikace Blazor WebAssembly nepodporují ladění pomocí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9344d-216">Blazor WebAssembly apps don't support debugging using Visual Studio.</span></span> <span data-ttu-id="9344d-217">Chcete-li aplikaci `Ctrl+F5` spustit, použijte místo `F5`aplikace .</span><span class="sxs-lookup"><span data-stu-id="9344d-217">To run the app, use `Ctrl+F5` instead of `F5`.</span></span> <span data-ttu-id="9344d-218">Místo toho můžete ladit aplikace Blazor WebAssembly přímo v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="9344d-218">You can instead debug Blazor WebAssembly apps directly in the browser.</span></span> <span data-ttu-id="9344d-219">Podrobnosti najdete [v tématu Ladění ASP.NET Core Blazor.](/aspnet/core/blazor/debug)</span><span class="sxs-lookup"><span data-stu-id="9344d-219">See [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9344d-220">[Předchozí](hosting-models.md)
>[další](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="9344d-220">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
