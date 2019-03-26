---
title: Co je nového v .NET Core 2.0
description: Informace o nových funkcích v .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.openlocfilehash: 2d0f6a9faaec4d4438452054624751a40c96c8e5
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464070"
---
# <a name="whats-new-in-net-core-20"></a><span data-ttu-id="3282c-103">Co je nového v .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3282c-103">What's new in .NET Core 2.0</span></span>

<span data-ttu-id="3282c-104">.NET core 2.0 obsahuje vylepšení a nových funkcí v těchto oblastech:</span><span class="sxs-lookup"><span data-stu-id="3282c-104">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="3282c-105">Nástroje</span><span class="sxs-lookup"><span data-stu-id="3282c-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="3282c-106">Podpora jazyků</span><span class="sxs-lookup"><span data-stu-id="3282c-106">Language support</span></span>](#language-support)
- [<span data-ttu-id="3282c-107">Vylepšení platformy</span><span class="sxs-lookup"><span data-stu-id="3282c-107">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="3282c-108">Změny rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3282c-108">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="3282c-109">Integrace se sadou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3282c-109">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="3282c-110">Dokumentace k vylepšení</span><span class="sxs-lookup"><span data-stu-id="3282c-110">Documentation improvements</span></span>](#documentation-improvements)

## <a name="tooling"></a><span data-ttu-id="3282c-111">Nástroje</span><span class="sxs-lookup"><span data-stu-id="3282c-111">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="3282c-112">DotNet restore se implicitně spouští</span><span class="sxs-lookup"><span data-stu-id="3282c-112">dotnet restore runs implicitly</span></span>

<span data-ttu-id="3282c-113">V předchozích verzích .NET Core, musíte spustit [dotnet restore](../tools/dotnet-restore.md) příkazu stáhněte závislosti ihned poté, co jste vytvořili nový projekt s [dotnet nové](../tools/dotnet-new.md) příkazu, a také pokaždé, když jste do projektu přidá novou závislost.</span><span class="sxs-lookup"><span data-stu-id="3282c-113">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="3282c-114">Můžete také zakázat automatické vyvolání `dotnet restore` předáním `--no-restore` přepněte `new`, `run`, `build`, `publish`, `pack`, a `test` příkazy.</span><span class="sxs-lookup"><span data-stu-id="3282c-114">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span>

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="3282c-115">Mění se cílení na .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3282c-115">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="3282c-116">Pokud je nainstalovaná sada .NET Core 2.0 SDK, projekty, jejichž cílem .NET Core 1.x můžete měli změnit cílení na .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="3282c-116">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span>

<span data-ttu-id="3282c-117">Chcete-li změnit cílení na .NET Core 2.0, upravte soubor projektu tak, že změníte hodnotu `<TargetFramework>` elementu (nebo `<TargetFrameworks>` element, pokud máte více než jeden cíl v souboru projektu) z 1.x do 2.0:</span><span class="sxs-lookup"><span data-stu-id="3282c-117">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="3282c-118">Můžete také změnit cíl knihoven .NET Standard a .NET Standard 2.0 stejným způsobem jako:</span><span class="sxs-lookup"><span data-stu-id="3282c-118">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="3282c-119">Další informace o migraci vašich projektů .NET Core 2.0 najdete v tématu [migrace z ASP.NET Core 1.x do ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span><span class="sxs-lookup"><span data-stu-id="3282c-119">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="3282c-120">Podpora jazyků</span><span class="sxs-lookup"><span data-stu-id="3282c-120">Language support</span></span>

<span data-ttu-id="3282c-121">Kromě podpory C# a F#, .NET Core 2.0 podporuje i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3282c-121">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="3282c-122">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3282c-122">Visual Basic</span></span>

<span data-ttu-id="3282c-123">S verzí 2.0 .NET Core teď podporuje 2017 jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3282c-123">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="3282c-124">Můžete vytvořit následující typy projektů jazyka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="3282c-124">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="3282c-125">Aplikace konzoly .NET core</span><span class="sxs-lookup"><span data-stu-id="3282c-125">.NET Core console apps</span></span>
- <span data-ttu-id="3282c-126">Knihovny tříd .NET core</span><span class="sxs-lookup"><span data-stu-id="3282c-126">.NET Core class libraries</span></span>
- <span data-ttu-id="3282c-127">Knihovny tříd .NET standard</span><span class="sxs-lookup"><span data-stu-id="3282c-127">.NET Standard class libraries</span></span>
- <span data-ttu-id="3282c-128">Projekty testů jednotek .NET core</span><span class="sxs-lookup"><span data-stu-id="3282c-128">.NET Core unit test projects</span></span>
- <span data-ttu-id="3282c-129">Projekty testů xUnit .NET core</span><span class="sxs-lookup"><span data-stu-id="3282c-129">.NET Core xUnit test projects</span></span>

<span data-ttu-id="3282c-130">Například k vytvoření aplikace v jazyce Visual Basic "Hello World", proveďte následující kroky z příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="3282c-130">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="3282c-131">Otevřete okno konzole, vytvořte adresář pro váš projekt a usnadnit aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="3282c-131">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="3282c-132">Zadejte příkaz `dotnet new console -lang vb`.</span><span class="sxs-lookup"><span data-stu-id="3282c-132">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="3282c-133">Příkaz vytvoří soubor projektu s `.vbproj` příponou spolu s názvem souboru zdrojového kódu jazyka Visual Basic *soubor Program.vb*.</span><span class="sxs-lookup"><span data-stu-id="3282c-133">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="3282c-134">Tento soubor obsahuje zdrojový kód k zápisu řetězce "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3282c-134">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="3282c-135">v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="3282c-135">to the console window.</span></span>

1. <span data-ttu-id="3282c-136">Zadejte příkaz `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="3282c-136">Enter the command `dotnet run`.</span></span> <span data-ttu-id="3282c-137">[Rozhraní příkazového řádku .NET Core](../tools/index.md) automaticky zkompiluje a spustí aplikaci, které zobrazí zprávu "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3282c-137">The [.NET Core CLI](../tools/index.md) automatically compiles and executes the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="3282c-138">v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="3282c-138">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="3282c-139">Podpora pro jazyk C# 7.1</span><span class="sxs-lookup"><span data-stu-id="3282c-139">Support for C# 7.1</span></span>

<span data-ttu-id="3282c-140">.NET core 2.0 podporuje C# 7.1, který přidává řadu nových funkcí, včetně:</span><span class="sxs-lookup"><span data-stu-id="3282c-140">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="3282c-141">`Main` Metoda vstupní bod aplikace, může být označena [asynchronní](../../csharp/language-reference/keywords/async.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="3282c-141">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="3282c-142">Inferredname řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="3282c-142">Inferred tuple names.</span></span>
- <span data-ttu-id="3282c-143">Výchozí výrazy.</span><span class="sxs-lookup"><span data-stu-id="3282c-143">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="3282c-144">Vylepšení platformy</span><span class="sxs-lookup"><span data-stu-id="3282c-144">Platform improvements</span></span>

<span data-ttu-id="3282c-145">.NET core 2.0 obsahuje několik funkcí, které usnadňují nainstalovat sadu .NET Core a používat na podporovaných operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="3282c-145">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="3282c-146">.NET core pro Linux je jedna implementace</span><span class="sxs-lookup"><span data-stu-id="3282c-146">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="3282c-147">.NET core 2.0 nabízí jedna implementace systému Linux, která funguje v několika Linuxových distribucích.</span><span class="sxs-lookup"><span data-stu-id="3282c-147">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="3282c-148">.NET core 1.x vyžaduje, stáhněte si distribuce Linuxu je implementace.</span><span class="sxs-lookup"><span data-stu-id="3282c-148">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="3282c-149">Můžete také vyvíjet aplikace, které cílí na Linux jako jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="3282c-149">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="3282c-150">.NET core 1.x požadované cílové samostatně každá distribuce Linuxu.</span><span class="sxs-lookup"><span data-stu-id="3282c-150">.NET Core 1.x required that you target each Linux distribution separately.</span></span>

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="3282c-151">Podpora pro kryptografické knihovny Apple</span><span class="sxs-lookup"><span data-stu-id="3282c-151">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="3282c-152">.NET core 1.x v systému macOS vyžaduje kryptografické knihovny OpenSSL toolkit.</span><span class="sxs-lookup"><span data-stu-id="3282c-152">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="3282c-153">.NET core 2.0 využívá kryptografické knihovny Apple a nevyžaduje, aby OpenSSL, takže už nemusíte jej nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="3282c-153">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span>

## <a name="api-changes-and-library-support"></a><span data-ttu-id="3282c-154">Změny rozhraní API a podpora knihovny</span><span class="sxs-lookup"><span data-stu-id="3282c-154">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="3282c-155">Podpora pro .NET Standard 2.0</span><span class="sxs-lookup"><span data-stu-id="3282c-155">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="3282c-156">.NET Standard definuje sadu rozhraní API, která musí být k dispozici na implementace .NET, které jsou v souladu s touto verzí standardu systémovou správou verzí.</span><span class="sxs-lookup"><span data-stu-id="3282c-156">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="3282c-157">.NET Standard je cílena na vývojáře knihovny.</span><span class="sxs-lookup"><span data-stu-id="3282c-157">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="3282c-158">Cílem je zajistit funkce, které jsou k dispozici pro knihovnu, která cílí na verzi .NET Standard na každá implementace .NET.</span><span class="sxs-lookup"><span data-stu-id="3282c-158">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="3282c-159">.NET core 1.x podporuje .NET Standard verzi 1.6, .NET Core 2.0 podporuje nejnovější verzi rozhraní .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="3282c-159">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="3282c-160">Další informace najdete v tématu [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="3282c-160">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="3282c-161">Rozhraní .NET standard 2.0 obsahuje více než 20 000 další rozhraní API, než byly k dispozici v rozhraní .NET Standard 1.6.</span><span class="sxs-lookup"><span data-stu-id="3282c-161">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="3282c-162">Velká část to rozšířit styčné plochy výsledky z využívá rozhraní API, které jsou společné pro rozhraní .NET Framework a Xamarin do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3282c-162">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="3282c-163">Knihovny tříd .NET standard 2.0 lze také odkazovat knihovny tříd rozhraní .NET Framework, za předpokladu, že volání rozhraní API, která jsou k dispozici v rozhraní .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="3282c-163">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="3282c-164">Žádné rekompilace knihovny rozhraní .NET Framework je povinný.</span><span class="sxs-lookup"><span data-stu-id="3282c-164">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="3282c-165">Seznam rozhraní API, která byla přidána do .NET Standard od jeho poslední verze rozhraní .NET Standard 1.6, najdete v části [vs .NET Standard 2.0. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="3282c-165">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="3282c-166">Rozšířené plochy</span><span class="sxs-lookup"><span data-stu-id="3282c-166">Expanded surface area</span></span>

<span data-ttu-id="3282c-167">Celkový počet rozhraní API na .NET Core 2.0 k dispozici více než zdvojnásobil ve srovnání s .NET Core 1.1.</span><span class="sxs-lookup"><span data-stu-id="3282c-167">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span>

<span data-ttu-id="3282c-168">A [Windows Compatibility Pack](../porting/windows-compat-pack.md) přenos z rozhraní .NET Framework se stal také mnohem jednodušší.</span><span class="sxs-lookup"><span data-stu-id="3282c-168">And with the [Windows Compatibility Pack](../porting/windows-compat-pack.md) porting from .NET Framework has also become much simpler.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="3282c-169">Podporu pro knihovny rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3282c-169">Support for .NET Framework libraries</span></span>

<span data-ttu-id="3282c-170">Kód .NET core může odkazovat na existující knihovny rozhraní .NET Framework, včetně existujících balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="3282c-170">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="3282c-171">Všimněte si, že tyto knihovny musí používat rozhraní API, která se nacházejí v .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3282c-171">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="3282c-172">integrace sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3282c-172">Visual Studio integration</span></span>

<span data-ttu-id="3282c-173">Visual Studio 2017 verze 15.3 a v některých případech Visual Studio for Mac nabízí řadu významných vylepšení pro vývojáře v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3282c-173">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="3282c-174">Mění se cílení aplikace .NET Core a knihovny .NET Standard</span><span class="sxs-lookup"><span data-stu-id="3282c-174">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="3282c-175">Pokud je nainstalovaná sada .NET Core 2.0 SDK, můžete změnit cíl projektů .NET Core 1.x do 1.x knihoven .NET Core 2.0 a .NET Standard a .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="3282c-175">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span>

<span data-ttu-id="3282c-176">Chcete-li změnit cíl projektu v sadě Visual Studio, otevřete **aplikace** kartu dialogové okno Vlastnosti projektu a změňte **Cílová architektura** hodnota, která se **.NET Core 2.0** nebo **.NET standard 2.0**.</span><span class="sxs-lookup"><span data-stu-id="3282c-176">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="3282c-177">Můžete ho můžete změnit tak, že kliknete pravým tlačítkem na projekt a vyberete **upravit \*soubor .csproj** možnost.</span><span class="sxs-lookup"><span data-stu-id="3282c-177">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="3282c-178">Další informace najdete v tématu [nástrojů](#tooling) dříve v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="3282c-178">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="3282c-179">Podpora Live Unit Testing pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="3282c-179">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="3282c-180">Pokaždé, když se váš kód upravíte, Live Unit Testing automaticky spustí všechny testy ovlivněné jednotek na pozadí a zobrazí výsledky a pokrytí kódu živě v prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3282c-180">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="3282c-181">Live Unit Testing nyní podporuje .NET core 2.0.</span><span class="sxs-lookup"><span data-stu-id="3282c-181">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="3282c-182">Live Unit Testing byla dříve k dispozici pouze u aplikací využívajících rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3282c-182">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span>

<span data-ttu-id="3282c-183">Další informace najdete v tématu [Live Unit Testing v sadě Visual Studio 2017](/visualstudio/test/live-unit-testing) a [Live Unit Testing – nejčastější dotazy](/visualstudio/test/live-unit-testing-faq).</span><span class="sxs-lookup"><span data-stu-id="3282c-183">For more information, see [Live Unit Testing with Visual Studio 2017](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="3282c-184">Lepší podporu pro více cílových platforem</span><span class="sxs-lookup"><span data-stu-id="3282c-184">Better support for multiple target frameworks</span></span>

<span data-ttu-id="3282c-185">Pokud vytváříte projekt pro více cílových platforem, teď můžete vybrat cílovou platformu z nabídek nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="3282c-185">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="3282c-186">Na následujícím obrázku, projekt s názvem SCD1 cíle 64bitová verze macOS X 10.11 (`osx.10.11-x64`) a 64bitová verze Windows 10/Windows Server 2016 (`win10-x64`).</span><span class="sxs-lookup"><span data-stu-id="3282c-186">In the following figure, a project named SCD1 targets 64-bit macOS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="3282c-187">Před výběrem tlačítka projektu, v tomto případě ke spuštění sestavení pro ladění, můžete vybrat cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="3282c-187">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![Snímek obrazovky výběru cílového rozhraní framework při sestavování projektu.](./media/dotnet-core-2-0/target-framework-selection.png)

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="3282c-189">Podpora .NET Core SDK vedle sebe</span><span class="sxs-lookup"><span data-stu-id="3282c-189">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="3282c-190">Nyní můžete nainstalovat sadu .NET Core SDK nezávisle na Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3282c-190">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="3282c-191">Díky tomu je možné pro jednu verzi sady Visual Studio k sestavení projektů zaměřené na různé verze rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3282c-191">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="3282c-192">Dříve Visual Studio a .NET Core SDK byly úzce párované; konkrétní verze sady SDK spolu s konkrétní verzí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3282c-192">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="3282c-193">Dokumentace k vylepšení</span><span class="sxs-lookup"><span data-stu-id="3282c-193">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="3282c-194">Architektura aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="3282c-194">.NET Application Architecture</span></span>

<span data-ttu-id="3282c-195">[Architektura aplikace .NET](https://www.microsoft.com/net/learn/architecture) vám umožní přístup k sadě elektronické knihy, které obsahují pokyny, osvědčené postupy a ukázkové aplikace při používání technologie .NET k sestavení:</span><span class="sxs-lookup"><span data-stu-id="3282c-195">[.NET Application Architecture](https://www.microsoft.com/net/learn/architecture) gives you access to a set of e-books that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- [<span data-ttu-id="3282c-196">Mikroslužby a kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="3282c-196">Microservices and Docker containers</span></span>](../../standard/microservices-architecture/index.md)
- [<span data-ttu-id="3282c-197">Webové aplikace s ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3282c-197">Web applications with ASP.NET</span></span>](../../standard/modern-web-apps-azure-architecture/index.md)
- [<span data-ttu-id="3282c-198">Mobilní aplikace s využitím kódu Xamarin</span><span class="sxs-lookup"><span data-stu-id="3282c-198">Mobile applications with Xamarin</span></span>](/xamarin/xamarin-forms/enterprise-application-patterns/index)
- [<span data-ttu-id="3282c-199">Aplikace, které jsou nasazeny do cloudu s Azure</span><span class="sxs-lookup"><span data-stu-id="3282c-199">Applications that are deployed to the Cloud with Azure</span></span>](/azure/architecture/reference-architectures/index)

## <a name="see-also"></a><span data-ttu-id="3282c-200">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3282c-200">See also</span></span>

- [<span data-ttu-id="3282c-201">Co je nového v ASP.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3282c-201">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)
