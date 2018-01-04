---
title: "Co je nového v rozhraní .NET 2.0 jádra"
description: "Další informace o nových funkcích v .NET Core nalezen."
keywords: "Rozhraní .NET, .NET core"
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 749f0502b5c80ed3d6b81d2036e7591e3f1fe08a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="whats-new-in-net-core"></a><span data-ttu-id="15544-104">Co je nového v .NET Core</span><span class="sxs-lookup"><span data-stu-id="15544-104">What's new in .NET Core</span></span>

<span data-ttu-id="15544-105">.NET core 2.0 obsahuje vylepšení a nové funkce v těchto oblastech:</span><span class="sxs-lookup"><span data-stu-id="15544-105">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="15544-106">Nástrojů</span><span class="sxs-lookup"><span data-stu-id="15544-106">Tooling</span></span>](#tooling)
- [<span data-ttu-id="15544-107">Jazyková podpora</span><span class="sxs-lookup"><span data-stu-id="15544-107">Language support</span></span>](#language-support)
- [<span data-ttu-id="15544-108">Vylepšení platformy</span><span class="sxs-lookup"><span data-stu-id="15544-108">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="15544-109">Rozhraní API změny</span><span class="sxs-lookup"><span data-stu-id="15544-109">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="15544-110">Integrace aplikace Visual Studio</span><span class="sxs-lookup"><span data-stu-id="15544-110">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="15544-111">Dokumentace k vylepšení</span><span class="sxs-lookup"><span data-stu-id="15544-111">Documentation improvements</span></span>](#documentation-improvements)

## <a name="tooling"></a><span data-ttu-id="15544-112">Nástrojů</span><span class="sxs-lookup"><span data-stu-id="15544-112">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="15544-113">implicitně spouští obnovení DotNet.</span><span class="sxs-lookup"><span data-stu-id="15544-113">dotnet restore runs implicitly</span></span>

<span data-ttu-id="15544-114">V předchozích verzích .NET Core musely být spuštěné [dotnet obnovení](../tools/dotnet-restore.md) příkaz ke stažení závislostí ihned po vytvoření nového projektu s [dotnet nové](../tools/dotnet-new.md) příkaz, a také vždy, když jste Přidat nové závislosti do projektu.</span><span class="sxs-lookup"><span data-stu-id="15544-114">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="15544-115">Můžete také zakázat automatické vyvolání `dotnet restore` předáním `--no-restore` přepnout `new`, `run`, `build`, `publish`, `pack`, a `test` příkazy.</span><span class="sxs-lookup"><span data-stu-id="15544-115">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span> 

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="15544-116">Změna orientace na .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="15544-116">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="15544-117">Pokud je nainstalovaný .NET Core 2.0 SDK, projekty, cílí na .NET Core 1.x může být změnit cíl na necílené .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="15544-117">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span>

<span data-ttu-id="15544-118">Přesměrovat na rozhraní .NET 2.0 jádra, upravte svůj soubor projektu tak, že změníte hodnotu `<TargetFramework>` elementu (nebo `<TargetFrameworks>` elementu, pokud máte více než jeden cíl v souboru projektu) z 1.x k 2.0:</span><span class="sxs-lookup"><span data-stu-id="15544-118">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="15544-119">Můžete také změnit cíl .NET standardní knihovny pro rozhraní .NET 2.0 standardní stejným způsobem jako:</span><span class="sxs-lookup"><span data-stu-id="15544-119">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="15544-120">Další informace o migraci projektu na .NET Core 2.0 najdete v tématu [migrace z ASP.NET Core 1.x na technologii ASP.NET 2.0 základní](/aspnet/core/migration/1x-to-2x/index).</span><span class="sxs-lookup"><span data-stu-id="15544-120">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="15544-121">Jazyková podpora</span><span class="sxs-lookup"><span data-stu-id="15544-121">Language support</span></span>

<span data-ttu-id="15544-122">Vedle podpory jazyka C# a F #, rozhraní .NET 2.0 základní také podporuje jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="15544-122">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="15544-123">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15544-123">Visual Basic</span></span>

<span data-ttu-id="15544-124">Verze 2.0 .NET Core teď podporuje 2017 Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="15544-124">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="15544-125">Můžete vytvořit tyto typy projektů jazyka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="15544-125">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="15544-126">Aplikace konzoly .NET core</span><span class="sxs-lookup"><span data-stu-id="15544-126">.NET Core console apps</span></span>
- <span data-ttu-id="15544-127">Knihovny tříd .NET core</span><span class="sxs-lookup"><span data-stu-id="15544-127">.NET Core class libraries</span></span>
- <span data-ttu-id="15544-128">.NET standard knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="15544-128">.NET Standard class libraries</span></span>
- <span data-ttu-id="15544-129">.NET core projektů testování částí</span><span class="sxs-lookup"><span data-stu-id="15544-129">.NET Core unit test projects</span></span>
- <span data-ttu-id="15544-130">.NET core xUnit testovací projekty</span><span class="sxs-lookup"><span data-stu-id="15544-130">.NET Core xUnit test projects</span></span>

<span data-ttu-id="15544-131">Například pro vytvoření aplikace Visual Basic "Hello, World", proveďte následující kroky z příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="15544-131">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="15544-132">Otevřete okno konzoly, vytvořte adresář pro svůj projekt a nastavte jej aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="15544-132">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="15544-133">Zadejte příkaz `dotnet new console -lang vb`.</span><span class="sxs-lookup"><span data-stu-id="15544-133">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="15544-134">Příkaz vytvoří soubor projektu s `.vbproj` souboru příponu, společně s souboru zdrojového kódu jazyka Visual Basic, s názvem *soubor Program.vb*.</span><span class="sxs-lookup"><span data-stu-id="15544-134">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="15544-135">Tento soubor obsahuje zdrojový kód k zápisu řetězce "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="15544-135">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="15544-136">v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="15544-136">to the console window.</span></span>

1.  <span data-ttu-id="15544-137">Zadejte příkaz `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="15544-137">Enter the command `dotnet run`.</span></span> <span data-ttu-id="15544-138">[Nástrojů příkazového řádku .NET Core](../tools/index.md) automaticky zkompilování a spuštění aplikace, které zobrazí zprávu "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="15544-138">The [.NET Core CLI tools](../tools/index.md) automatically compile and execute the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="15544-139">v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="15544-139">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="15544-140">Podpora pro jazyk C# 7.1</span><span class="sxs-lookup"><span data-stu-id="15544-140">Support for C# 7.1</span></span>

<span data-ttu-id="15544-141">.NET core 2.0 podporuje 7.1 C#, který přidá číslo nové funkce, včetně:</span><span class="sxs-lookup"><span data-stu-id="15544-141">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="15544-142">`Main` Metoda, vstupní bod aplikace, může být označen [asynchronní](../../csharp/language-reference/keywords/async.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="15544-142">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="15544-143">Inferredname řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="15544-143">Inferred tuple names.</span></span>
- <span data-ttu-id="15544-144">Výchozí výrazy.</span><span class="sxs-lookup"><span data-stu-id="15544-144">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="15544-145">Vylepšení platformy</span><span class="sxs-lookup"><span data-stu-id="15544-145">Platform improvements</span></span>

<span data-ttu-id="15544-146">.NET core 2.0 obsahuje několik funkcí, které usnadňují instalaci .NET Core a používat na podporovaných operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="15544-146">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="15544-147">.NET core pro Linux je jediná implementace</span><span class="sxs-lookup"><span data-stu-id="15544-147">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="15544-148">Rozhraní .NET 2.0 základní nabízí jediná implementace Linux, který funguje na více Linuxových distribucích.</span><span class="sxs-lookup"><span data-stu-id="15544-148">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="15544-149">.NET core 1.x vyžaduje, abyste si stáhli na konkrétní distribuční Linux implementace.</span><span class="sxs-lookup"><span data-stu-id="15544-149">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="15544-150">Také můžete vyvíjet aplikace, které cílí na Linux jako jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="15544-150">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="15544-151">.NET core 1.x požadované cílové každý distribuční Linux samostatně.</span><span class="sxs-lookup"><span data-stu-id="15544-151">.NET Core 1.x required that you target each Linux distribution separately.</span></span>

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="15544-152">Podporu pro kryptografické knihovny Apple</span><span class="sxs-lookup"><span data-stu-id="15544-152">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="15544-153">.NET core 1.x v systému macOS požadované kryptografické knihovny OpenSSL toolkit.</span><span class="sxs-lookup"><span data-stu-id="15544-153">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="15544-154">Rozhraní .NET 2.0 základní využívá kryptografické knihovny Apple a nevyžaduje OpenSSL, takže potřebujete už ji nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="15544-154">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span>

## <a name="api-changes-and-library-support"></a><span data-ttu-id="15544-155">Rozhraní API změny a podpora knihovny</span><span class="sxs-lookup"><span data-stu-id="15544-155">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="15544-156">Podpora pro rozhraní .NET Standard 2.0</span><span class="sxs-lookup"><span data-stu-id="15544-156">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="15544-157">.NET Standard definuje sadu rozhraní API, která musí být k dispozici na implementace rozhraní .NET, které jsou v souladu s touto verzí standardní verzí.</span><span class="sxs-lookup"><span data-stu-id="15544-157">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="15544-158">.NET Standard je cílena na vývojáře knihovny.</span><span class="sxs-lookup"><span data-stu-id="15544-158">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="15544-159">Zaměřuje se na zaručit funkce, které jsou k dispozici pro knihovnu, která je cílena na verzi rozhraní .NET standardní na každou implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="15544-159">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="15544-160">.NET core 1.x podporuje .NET standardní verzi 1.6; na nejnovější verzi rozhraní .NET 2.0 standardní podporuje rozhraní .NET 2.0 jádra.</span><span class="sxs-lookup"><span data-stu-id="15544-160">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="15544-161">Další informace najdete v tématu [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="15544-161">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="15544-162">Standardní rozhraní .NET 2.0 obsahuje více než 20 000 další rozhraní API, než byly k dispozici v standardní 1.6 .NET.</span><span class="sxs-lookup"><span data-stu-id="15544-162">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="15544-163">Velká část to rozšířit útoku na výsledky z zařadit rozhraní API, které jsou společné pro rozhraní .NET Framework a Xamarin do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="15544-163">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="15544-164">Knihovny tříd rozhraní .NET 2.0 standardní lze také odkazovat knihovny tříd rozhraní .NET Framework, za předpokladu, že se volání rozhraní API, které jsou v rozhraní .NET 2.0 standardní.</span><span class="sxs-lookup"><span data-stu-id="15544-164">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="15544-165">Žádné rekompilace knihovny rozhraní .NET Framework je povinný.</span><span class="sxs-lookup"><span data-stu-id="15544-165">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="15544-166">Seznam rozhraní API, které byly přidány do .NET Standard od jeho poslední verze 1.6 standardní .NET, naleznete v části [vs standardní rozhraní .NET 2.0. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="15544-166">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="15544-167">Rozšířené útoku</span><span class="sxs-lookup"><span data-stu-id="15544-167">Expanded surface area</span></span>

<span data-ttu-id="15544-168">Celkový počet dostupných na rozhraní .NET 2.0 jádra rozhraní API obsahuje více než se používají ve srovnání s .NET Core 1.1.</span><span class="sxs-lookup"><span data-stu-id="15544-168">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span>

<span data-ttu-id="15544-169">A [Windows kompatibility Pack](../porting/windows-compat-pack.md) portování z rozhraní .NET Framework se staly také mnohem jednodušší.</span><span class="sxs-lookup"><span data-stu-id="15544-169">And with the [Windows Compatibility Pack](../porting/windows-compat-pack.md) porting from .NET Framework has also become much simpler.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="15544-170">Podporu pro knihovny rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="15544-170">Support for .NET Framework libraries</span></span>

<span data-ttu-id="15544-171">.NET core kód můžete odkazovat na existující knihovny rozhraní .NET Framework, včetně existující balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="15544-171">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="15544-172">Všimněte si, že v knihovnách musí používat rozhraní API, které se nacházejí v rozhraní .NET standardní.</span><span class="sxs-lookup"><span data-stu-id="15544-172">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="15544-173">integrace sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="15544-173">Visual Studio integration</span></span>

<span data-ttu-id="15544-174">Visual Studio 2017 verze 15.3 a v některých případech Visual Studio pro Mac nabízí několik významných vylepšení pro vývojáře .NET Core.</span><span class="sxs-lookup"><span data-stu-id="15544-174">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="15544-175">Změna orientace aplikace .NET Core a .NET Standard knihovny</span><span class="sxs-lookup"><span data-stu-id="15544-175">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="15544-176">Pokud je nainstalovaný .NET Core 2.0 SDK, můžete změnit cíl .NET Core 1.x projektů pro rozhraní .NET Core 2.0 a .NET standardní knihovny 1.x standardní rozhraní .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="15544-176">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span>

<span data-ttu-id="15544-177">Přesměrovat projektu v sadě Visual Studio, otevřete **aplikace** kartě dialogovém okně Vlastnosti projektu a změňte **cílové rozhraní** hodnotu **.NET Core 2.0** nebo **Rozhraní .NET 2.0 standardní**.</span><span class="sxs-lookup"><span data-stu-id="15544-177">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="15544-178">Můžete ji také změnit kliknutím pravým tlačítkem myši na projekt a výběrem možnosti **upravit \*souboru .csproj** možnost.</span><span class="sxs-lookup"><span data-stu-id="15544-178">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="15544-179">Další informace najdete v tématu [Tooling](#tooling) dříve v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="15544-179">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="15544-180">Podpora Live Unit Testing pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="15544-180">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="15544-181">Vždy, když upravíte kódu, Live testování částí automaticky spustí všechny testy ovlivněných jednotku na pozadí a zobrazí výsledky a pokrytí kódu v prostředí Visual Studio za provozu.</span><span class="sxs-lookup"><span data-stu-id="15544-181">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="15544-182">Rozhraní .NET 2.0 základní teď podporuje Live testování jednotky.</span><span class="sxs-lookup"><span data-stu-id="15544-182">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="15544-183">Dříve Live testování částí nebylo k dispozici pouze pro aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15544-183">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span>

<span data-ttu-id="15544-184">Další informace najdete v tématu [Live testování částí s Visual Studio 2017](/visualstudio/test/live-unit-testing) a [Live testování částí – nejčastější dotazy](/visualstudio/test/live-unit-testing-faq).</span><span class="sxs-lookup"><span data-stu-id="15544-184">For more information, see [Live Unit Testing with Visual Studio 2017](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="15544-185">Lepší podporu pro více rozhraní target</span><span class="sxs-lookup"><span data-stu-id="15544-185">Better support for multiple target frameworks</span></span>

<span data-ttu-id="15544-186">Pokud vytváříte projekt pro více cílové rozhraní, můžete nyní vybrat cílové platformy v nabídce nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="15544-186">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="15544-187">Na následujícím obrázku, projekt s názvem SCD1 cílem 64bitová verze Mac OS X 10.11 (`osx.10.11-x64`) a 64bitová verze Windows 10 a Windows Server 2016 (`win10-x64`).</span><span class="sxs-lookup"><span data-stu-id="15544-187">In the following figure, a project named SCD1 targets 64-bit Mac OS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="15544-188">Před výběrem tlačítko projektu v tomto případě spuštění sestavení ladicí verze, můžete vybrat cílové rozhraní.</span><span class="sxs-lookup"><span data-stu-id="15544-188">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![Výběr cílové rozhraní při sestavování projektu](media/multitarget.png)

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="15544-190">Souběžně sdílená podpory pro rozhraní .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="15544-190">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="15544-191">Nyní můžete nainstalovat rozhraní .NET Core SDK nezávisle na Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="15544-191">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="15544-192">To umožňuje jedna verze sady Visual Studio k vytvoření projektů, že cíl různé verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="15544-192">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="15544-193">Dříve Visual Studio a .NET Core SDK byly úzce párované; konkrétní verzi sady SDK spolu s konkrétní verze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="15544-193">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="15544-194">Dokumentace k vylepšení</span><span class="sxs-lookup"><span data-stu-id="15544-194">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="15544-195">Architektura aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="15544-195">.NET Application Architecture</span></span>

<span data-ttu-id="15544-196">[Architektura aplikace .NET](https://www.microsoft.com/net/learn/architecture) dává vám přístup k sadě e publikací, které obsahují pokyny, osvědčené postupy a ukázkové aplikace, při použití rozhraní .NET k sestavení:</span><span class="sxs-lookup"><span data-stu-id="15544-196">[.NET Application Architecture](https://www.microsoft.com/net/learn/architecture) gives you access to a set of e-books that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- <span data-ttu-id="15544-197">Mikroslužeb a Docker kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="15544-197">Microservices and Docker containers.</span></span>
- <span data-ttu-id="15544-198">Webové aplikace s ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="15544-198">Web applications with ASP.NET.</span></span>
- <span data-ttu-id="15544-199">Mobilní aplikace s funkcí Xamarin.</span><span class="sxs-lookup"><span data-stu-id="15544-199">Mobile applications with Xamarin.</span></span>
- <span data-ttu-id="15544-200">Aplikace, které jsou nasazeny do cloudu s Azure.</span><span class="sxs-lookup"><span data-stu-id="15544-200">Applications that are deployed to the Cloud with Azure.</span></span>

## <a name="see-also"></a><span data-ttu-id="15544-201">Viz také</span><span class="sxs-lookup"><span data-stu-id="15544-201">See also</span></span>
 [<span data-ttu-id="15544-202">Co je nového v technologii ASP.NET 2.0 jádra</span><span class="sxs-lookup"><span data-stu-id="15544-202">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)
