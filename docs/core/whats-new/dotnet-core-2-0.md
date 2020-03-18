---
title: Co je nového v .NET Core 2.0
description: Další informace o nových funkcích v rozhraní .NET Core.
ms.date: 08/13/2017
ms.openlocfilehash: 115b3adc72b6798c6a7bac9cc18044a8822808a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398830"
---
# <a name="whats-new-in-net-core-20"></a><span data-ttu-id="c4984-103">Co je nového v .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="c4984-103">What's new in .NET Core 2.0</span></span>

<span data-ttu-id="c4984-104">.NET Core 2.0 obsahuje vylepšení a nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="c4984-104">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="c4984-105">Nástroje</span><span class="sxs-lookup"><span data-stu-id="c4984-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="c4984-106">Podpora jazyků</span><span class="sxs-lookup"><span data-stu-id="c4984-106">Language support</span></span>](#language-support)
- [<span data-ttu-id="c4984-107">Vylepšení platformy</span><span class="sxs-lookup"><span data-stu-id="c4984-107">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="c4984-108">Změny rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c4984-108">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="c4984-109">Integrace se sadou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c4984-109">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="c4984-110">Vylepšení dokumentace</span><span class="sxs-lookup"><span data-stu-id="c4984-110">Documentation improvements</span></span>](#documentation-improvements)

## <a name="tooling"></a><span data-ttu-id="c4984-111">Nástroje</span><span class="sxs-lookup"><span data-stu-id="c4984-111">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="c4984-112">Dotnet restore běží implicitně</span><span class="sxs-lookup"><span data-stu-id="c4984-112">dotnet restore runs implicitly</span></span>

<span data-ttu-id="c4984-113">V předchozích verzích rozhraní .NET Core bylo možné spustit příkaz [dotnet restore](../tools/dotnet-restore.md) ke stažení závislostí ihned po vytvoření nového projektu s novým příkazem [dotnet](../tools/dotnet-new.md) a také vždy, když jste do projektu přidali novou závislost.</span><span class="sxs-lookup"><span data-stu-id="c4984-113">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="c4984-114">Automatické vyvolání `dotnet restore` můžete také zakázat `--no-restore` předáním `new`přepínače na příkazy , `run` `build`, `publish`, `pack`, a `test` příkazy.</span><span class="sxs-lookup"><span data-stu-id="c4984-114">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span>

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="c4984-115">Opětovné zacílení na rozhraní .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="c4984-115">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="c4984-116">Pokud je nainstalována sada .NET Core 2.0 SDK, projekty, které cílí na rozhraní .NET Core 1.x, lze znovu zacílit na .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="c4984-116">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span>

<span data-ttu-id="c4984-117">Chcete-li znovu zacílit na .NET Core 2.0, `<TargetFramework>` upravte `<TargetFrameworks>` soubor projektu změnou hodnoty prvku (nebo prvku, pokud máte v souboru projektu více než jeden cíl) z 1.x na 2.0:</span><span class="sxs-lookup"><span data-stu-id="c4984-117">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="c4984-118">Stejným způsobem můžete také znovu zacílit knihovny .NET Standard na rozhraní .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="c4984-118">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="c4984-119">Další informace o migraci projektu do rozhraní .NET Core 2.0 naleznete [v tématu Migrace z ASP.NET jádra 1.x na ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span><span class="sxs-lookup"><span data-stu-id="c4984-119">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="c4984-120">Podpora jazyků</span><span class="sxs-lookup"><span data-stu-id="c4984-120">Language support</span></span>

<span data-ttu-id="c4984-121">Kromě podpory Jazyka C# a F#podporuje jazyk Visual Basic také rozhraní .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="c4984-121">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="c4984-122">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4984-122">Visual Basic</span></span>

<span data-ttu-id="c4984-123">S verzí 2.0 rozhraní .NET Core nyní podporuje visual basic 2017.</span><span class="sxs-lookup"><span data-stu-id="c4984-123">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="c4984-124">Pomocí jazyka Visual Basic můžete vytvořit následující typy projektů:</span><span class="sxs-lookup"><span data-stu-id="c4984-124">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="c4984-125">Aplikace konzoly .NET Core</span><span class="sxs-lookup"><span data-stu-id="c4984-125">.NET Core console apps</span></span>
- <span data-ttu-id="c4984-126">Knihovny tříd .NET Core</span><span class="sxs-lookup"><span data-stu-id="c4984-126">.NET Core class libraries</span></span>
- <span data-ttu-id="c4984-127">Knihovny tříd .NET Standard</span><span class="sxs-lookup"><span data-stu-id="c4984-127">.NET Standard class libraries</span></span>
- <span data-ttu-id="c4984-128">Testovací projekty základní jednotky .NET</span><span class="sxs-lookup"><span data-stu-id="c4984-128">.NET Core unit test projects</span></span>
- <span data-ttu-id="c4984-129">Testovací projekty .NET Core xUnit</span><span class="sxs-lookup"><span data-stu-id="c4984-129">.NET Core xUnit test projects</span></span>

<span data-ttu-id="c4984-130">Chcete-li například vytvořit aplikaci "Hello World" jazyka Visual Basic, proveďte z příkazového řádku následující kroky:</span><span class="sxs-lookup"><span data-stu-id="c4984-130">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="c4984-131">Otevřete okno konzoly, vytvořte adresář pro projekt a vytvořte z něj aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="c4984-131">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="c4984-132">Zadejte `dotnet new console -lang vb`příkaz .</span><span class="sxs-lookup"><span data-stu-id="c4984-132">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="c4984-133">Příkaz vytvoří soubor projektu `.vbproj` s příponou souboru spolu se souborem zdrojového kódu jazyka Visual Basic s názvem *Program.vb*.</span><span class="sxs-lookup"><span data-stu-id="c4984-133">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="c4984-134">Tento soubor obsahuje zdrojový kód pro napsání řetězce "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c4984-134">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="c4984-135">do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="c4984-135">to the console window.</span></span>

1. <span data-ttu-id="c4984-136">Zadejte `dotnet run`příkaz .</span><span class="sxs-lookup"><span data-stu-id="c4984-136">Enter the command `dotnet run`.</span></span> <span data-ttu-id="c4984-137">Rozhraní [příkazového příkazu .NET Core](../tools/index.md) automaticky zkompiluje a spustí aplikaci, která zobrazí zprávu "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c4984-137">The [.NET Core CLI](../tools/index.md) automatically compiles and executes the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="c4984-138">v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="c4984-138">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="c4984-139">Podpora pro C# 7.1</span><span class="sxs-lookup"><span data-stu-id="c4984-139">Support for C# 7.1</span></span>

<span data-ttu-id="c4984-140">.NET Core 2.0 podporuje C# 7.1, který přidává řadu nových funkcí, včetně:</span><span class="sxs-lookup"><span data-stu-id="c4984-140">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="c4984-141">Metoda, `Main` vstupní bod aplikace, může být označena klíčovým slovem [async.](../../csharp/language-reference/keywords/async.md)</span><span class="sxs-lookup"><span data-stu-id="c4984-141">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="c4984-142">Odvozené názvy řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="c4984-142">Inferred tuple names.</span></span>
- <span data-ttu-id="c4984-143">Výchozí výrazy.</span><span class="sxs-lookup"><span data-stu-id="c4984-143">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="c4984-144">Vylepšení platformy</span><span class="sxs-lookup"><span data-stu-id="c4984-144">Platform improvements</span></span>

<span data-ttu-id="c4984-145">Rozhraní .NET Core 2.0 obsahuje řadu funkcí, které usnadňují instalaci rozhraní .NET Core a jeho použití v podporovaných operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="c4984-145">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="c4984-146">.NET Core pro Linux je jedna implementace</span><span class="sxs-lookup"><span data-stu-id="c4984-146">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="c4984-147">.NET Core 2.0 nabízí jednu implementaci Linuxu, která funguje na více linuxových distribucích.</span><span class="sxs-lookup"><span data-stu-id="c4984-147">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="c4984-148">.NET Core 1.x vyžaduje, abyste stáhli implementaci Linuxu specifickou pro distribuci.</span><span class="sxs-lookup"><span data-stu-id="c4984-148">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="c4984-149">Můžete také vyvíjet aplikace, které cílí na Linux jako jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="c4984-149">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="c4984-150">.NET Core 1.x vyžaduje, abyste cílili každou distribuci Linuxu samostatně.</span><span class="sxs-lookup"><span data-stu-id="c4984-150">.NET Core 1.x required that you target each Linux distribution separately.</span></span>

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="c4984-151">Podpora kryptografických knihoven Apple</span><span class="sxs-lookup"><span data-stu-id="c4984-151">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="c4984-152">.NET Core 1.x v macOS vyžadoval kryptografickou knihovnu OpenSSL toolkit.</span><span class="sxs-lookup"><span data-stu-id="c4984-152">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="c4984-153">.NET Core 2.0 používá kryptografické knihovny Apple a nevyžaduje OpenSSL, takže už ho nemusíte instalovat.</span><span class="sxs-lookup"><span data-stu-id="c4984-153">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span>

## <a name="api-changes-and-library-support"></a><span data-ttu-id="c4984-154">Změny rozhraní API a podpora knihovny</span><span class="sxs-lookup"><span data-stu-id="c4984-154">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="c4984-155">Podpora pro standard .NET 2.0</span><span class="sxs-lookup"><span data-stu-id="c4984-155">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="c4984-156">Standard .NET definuje sadu rozhraní API s verzí, která musí být k dispozici v implementacích .NET, které jsou v souladu s touto verzí standardu.</span><span class="sxs-lookup"><span data-stu-id="c4984-156">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="c4984-157">Standard .NET je určen pro vývojáře knihoven.</span><span class="sxs-lookup"><span data-stu-id="c4984-157">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="c4984-158">Jeho cílem je zaručit funkce, které jsou k dispozici pro knihovnu, která se zaměřuje na verzi standardu .NET na každé implementaci .NET.</span><span class="sxs-lookup"><span data-stu-id="c4984-158">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="c4984-159">Rozhraní .NET Core 1.x podporuje rozhraní .NET Standard verze 1.6; .NET Core 2.0 podporuje nejnovější verzi .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="c4984-159">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="c4984-160">Další informace naleznete v tématu [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="c4984-160">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="c4984-161">Standard .NET Standard 2.0 obsahuje více než 20 000 více rozhraní API, než bylo k dispozici ve standardu .NET Standard 1.6.</span><span class="sxs-lookup"><span data-stu-id="c4984-161">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="c4984-162">Velká část této rozšířené plochy je výsledkem začlenění rozhraní API, která jsou společná pro rozhraní .NET Framework a Xamarin do standardu .NET.</span><span class="sxs-lookup"><span data-stu-id="c4984-162">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="c4984-163">Knihovny tříd .NET Standard 2.0 mohou také odkazovat na knihovny tříd rozhraní .NET Framework za předpokladu, že volají rozhraní API, která jsou přítomna ve standardu .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="c4984-163">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="c4984-164">Není vyžadována žádná rekompilace knihoven rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4984-164">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="c4984-165">Seznam rozhraní API, která byla přidána do standardu .NET od jeho poslední verze, .NET Standard 1.6, naleznete [v tématu .NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="c4984-165">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="c4984-166">Rozbalené plochy</span><span class="sxs-lookup"><span data-stu-id="c4984-166">Expanded surface area</span></span>

<span data-ttu-id="c4984-167">Celkový počet rozhraní API dostupných na rozhraní .NET Core 2.0 se ve srovnání s rozhraním .NET Core 1.1 více než zdvojnásobil.</span><span class="sxs-lookup"><span data-stu-id="c4984-167">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span>

<span data-ttu-id="c4984-168">A s windows [compatibility pack](../porting/windows-compat-pack.md) portování z rozhraní .NET Framework se také stala mnohem jednodušší.</span><span class="sxs-lookup"><span data-stu-id="c4984-168">And with the [Windows Compatibility Pack](../porting/windows-compat-pack.md) porting from .NET Framework has also become much simpler.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="c4984-169">Podpora knihoven rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c4984-169">Support for .NET Framework libraries</span></span>

<span data-ttu-id="c4984-170">Základní kód rozhraní .NET může odkazovat na existující knihovny rozhraní .NET Framework, včetně existujících balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="c4984-170">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="c4984-171">Všimněte si, že knihovny musí používat rozhraní API, které se nacházejí v .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="c4984-171">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="c4984-172">Integrace se sadou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c4984-172">Visual Studio integration</span></span>

<span data-ttu-id="c4984-173">Visual Studio 2017 verze 15.3 a v některých případech Visual Studio pro Mac nabízejí řadu významných vylepšení pro vývojáře .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c4984-173">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="c4984-174">Opětovné cílení na aplikace .NET Core a knihovny .NET Standard</span><span class="sxs-lookup"><span data-stu-id="c4984-174">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="c4984-175">Pokud je nainstalována sada .NET Core 2.0 SDK, můžete znovu zacílit na projekty .NET Core 1.x na knihovny .NET Core 2.0 a .NET Standard 1.x na .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="c4984-175">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span>

<span data-ttu-id="c4984-176">Chcete-li znovu zacílit projekt v sadě Visual Studio, otevřete kartu **Aplikace** dialogového okna vlastností projektu a změňte hodnotu **cílového rozhraní** na **.NET Core 2.0** nebo **.NET Standard 2.0**.</span><span class="sxs-lookup"><span data-stu-id="c4984-176">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="c4984-177">Můžete jej také změnit kliknutím pravým tlačítkem myši na projekt a výběrem **možnosti Upravit \*soubor .csproj.**</span><span class="sxs-lookup"><span data-stu-id="c4984-177">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="c4984-178">Další informace naleznete v části [Nástroje](#tooling) dříve v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="c4984-178">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="c4984-179">Podpora Live Unit Testing pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="c4984-179">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="c4984-180">Kdykoli změníte kód, live testování částí automaticky spustí všechny testy ovlivněné jednotky na pozadí a zobrazí výsledky a pokrytí kódu živě v prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4984-180">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="c4984-181">.NET Core 2.0 nyní podporuje živé testování částí.</span><span class="sxs-lookup"><span data-stu-id="c4984-181">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="c4984-182">Dříve bylo živé testování částí k dispozici pouze pro aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4984-182">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span>

<span data-ttu-id="c4984-183">Další informace naleznete [v tématu Živé testování částí s Visual Studio](/visualstudio/test/live-unit-testing) a nejčastější dotazy k testování [živých částí](/visualstudio/test/live-unit-testing-faq).</span><span class="sxs-lookup"><span data-stu-id="c4984-183">For more information, see [Live Unit Testing with Visual Studio](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="c4984-184">Lepší podpora pro více cílových rámců</span><span class="sxs-lookup"><span data-stu-id="c4984-184">Better support for multiple target frameworks</span></span>

<span data-ttu-id="c4984-185">Pokud vytváříte projekt pro více cílových architektur, můžete nyní vybrat cílovou platformu z nabídky nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="c4984-185">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="c4984-186">Na následujícím obrázku projekt s názvem SCD1 cílí na 64bitový`osx.10.11-x64`macOS X 10.11 ( )`win10-x64`a 64bitový systém Windows 10/Windows Server 2016 ( ).</span><span class="sxs-lookup"><span data-stu-id="c4984-186">In the following figure, a project named SCD1 targets 64-bit macOS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="c4984-187">Můžete vybrat cílovou architekturu před výběrem tlačítka projektu, v tomto případě spustit sestavení ladění.</span><span class="sxs-lookup"><span data-stu-id="c4984-187">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![Snímek obrazovky zobrazující výběr cílového rozhraní při vytváření projektu](./media/dotnet-core-2-0/target-framework-selection.png)

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="c4984-189">Souběžná podpora sad SDK jádra .NET</span><span class="sxs-lookup"><span data-stu-id="c4984-189">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="c4984-190">Nyní můžete nainstalovat sdk jádra .NET nezávisle na sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4984-190">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="c4984-191">To umožňuje pro jednu verzi sady Visual Studio vytvářet projekty, které cílí na různé verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c4984-191">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="c4984-192">Dříve visual studio a sada .NET Core SDK byly pevně spojeny; konkrétní verze sady SDK doprovází konkrétní verzi sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4984-192">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="c4984-193">Vylepšení dokumentace</span><span class="sxs-lookup"><span data-stu-id="c4984-193">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="c4984-194">Architektura aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="c4984-194">.NET Application Architecture</span></span>

<span data-ttu-id="c4984-195">[Architektura aplikací .NET](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) umožňuje přístup k sadě e-knih, které poskytují pokyny, osvědčené postupy a ukázkové aplikace při vytváření rozhraní .NET:</span><span class="sxs-lookup"><span data-stu-id="c4984-195">[.NET Application Architecture](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) gives you access to a set of e-books that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- [<span data-ttu-id="c4984-196">Mikroslužeb a kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="c4984-196">Microservices and Docker containers</span></span>](../../architecture/microservices/index.md)
- [<span data-ttu-id="c4984-197">Webové aplikace s ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c4984-197">Web applications with ASP.NET</span></span>](../../architecture/modern-web-apps-azure/index.md)
- [<span data-ttu-id="c4984-198">Mobilní aplikace s Xamarinem</span><span class="sxs-lookup"><span data-stu-id="c4984-198">Mobile applications with Xamarin</span></span>](/xamarin/xamarin-forms/enterprise-application-patterns/index)
- [<span data-ttu-id="c4984-199">Aplikace, které jsou nasazené do cloudu s Azure</span><span class="sxs-lookup"><span data-stu-id="c4984-199">Applications that are deployed to the Cloud with Azure</span></span>](/azure/architecture/reference-architectures/index)

## <a name="see-also"></a><span data-ttu-id="c4984-200">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4984-200">See also</span></span>

- [<span data-ttu-id="c4984-201">Co je nového v ASP.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="c4984-201">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)
