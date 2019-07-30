---
title: Co je nového v .NET Core 2.0
description: Přečtěte si o nových funkcích, které najdete v .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.openlocfilehash: f48b8e88a716df0f07a5626bdc8f66000cfaeed8
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626358"
---
# <a name="whats-new-in-net-core-20"></a><span data-ttu-id="5b80f-103">Co je nového v .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5b80f-103">What's new in .NET Core 2.0</span></span>

<span data-ttu-id="5b80f-104">.NET Core 2,0 obsahuje vylepšení a nové funkce v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="5b80f-104">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="5b80f-105">Nástroje</span><span class="sxs-lookup"><span data-stu-id="5b80f-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="5b80f-106">Podpora jazyků</span><span class="sxs-lookup"><span data-stu-id="5b80f-106">Language support</span></span>](#language-support)
- [<span data-ttu-id="5b80f-107">Vylepšení platformy</span><span class="sxs-lookup"><span data-stu-id="5b80f-107">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="5b80f-108">Změny rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5b80f-108">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="5b80f-109">Integrace sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5b80f-109">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="5b80f-110">Vylepšení dokumentace</span><span class="sxs-lookup"><span data-stu-id="5b80f-110">Documentation improvements</span></span>](#documentation-improvements)

## <a name="tooling"></a><span data-ttu-id="5b80f-111">Nástroje</span><span class="sxs-lookup"><span data-stu-id="5b80f-111">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="5b80f-112">dotnet restore se spouští implicitně.</span><span class="sxs-lookup"><span data-stu-id="5b80f-112">dotnet restore runs implicitly</span></span>

<span data-ttu-id="5b80f-113">V předchozích verzích .NET Core jste museli spustit příkaz [dotnet Restore](../tools/dotnet-restore.md) pro stahování závislostí hned po vytvoření nového projektu pomocí příkazu [dotnet New](../tools/dotnet-new.md) a také při každém přidání nové závislosti do projektu.</span><span class="sxs-lookup"><span data-stu-id="5b80f-113">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="5b80f-114">Automatické `dotnet restore` vyvolání `test` můžete také zakázat `--no-restore` předáním přepínače `new` `run` dopříkazů`build`,, `pack`,, a. `publish`</span><span class="sxs-lookup"><span data-stu-id="5b80f-114">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span>

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="5b80f-115">Změna cílení na .NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="5b80f-115">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="5b80f-116">Pokud je nainstalovaná sada .NET Core 2,0 SDK, projekty, jejichž cílem je .NET Core 1. x, se dají změnit na .NET Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="5b80f-116">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span>

<span data-ttu-id="5b80f-117">Chcete-li změnit cílení na .NET Core 2,0, upravte soubor projektu změnou hodnoty `<TargetFramework>` elementu (nebo prvku, `<TargetFrameworks>` Pokud máte více než jeden cíl v souboru projektu) od 1. x do 2,0:</span><span class="sxs-lookup"><span data-stu-id="5b80f-117">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="5b80f-118">Můžete také změnit cílení knihoven .NET Standard .NET Standard 2,0 stejným způsobem:</span><span class="sxs-lookup"><span data-stu-id="5b80f-118">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="5b80f-119">Další informace o migraci projektu na rozhraní .NET Core 2,0 naleznete v tématu [migrace z ASP.NET Core 1. x na ASP.NET Core 2,0](/aspnet/core/migration/1x-to-2x/index).</span><span class="sxs-lookup"><span data-stu-id="5b80f-119">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="5b80f-120">Podpora jazyků</span><span class="sxs-lookup"><span data-stu-id="5b80f-120">Language support</span></span>

<span data-ttu-id="5b80f-121">Kromě podpory C# a F#podporuje .net Core 2,0 také Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5b80f-121">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="5b80f-122">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5b80f-122">Visual Basic</span></span>

<span data-ttu-id="5b80f-123">S verzí 2,0 teď .NET Core podporuje Visual Basic 2017.</span><span class="sxs-lookup"><span data-stu-id="5b80f-123">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="5b80f-124">Pomocí Visual Basic můžete vytvořit následující typy projektů:</span><span class="sxs-lookup"><span data-stu-id="5b80f-124">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="5b80f-125">Aplikace konzoly .NET Core</span><span class="sxs-lookup"><span data-stu-id="5b80f-125">.NET Core console apps</span></span>
- <span data-ttu-id="5b80f-126">Knihovny tříd .NET Core</span><span class="sxs-lookup"><span data-stu-id="5b80f-126">.NET Core class libraries</span></span>
- <span data-ttu-id="5b80f-127">.NET Standard knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="5b80f-127">.NET Standard class libraries</span></span>
- <span data-ttu-id="5b80f-128">Projekty testů jednotek .NET Core</span><span class="sxs-lookup"><span data-stu-id="5b80f-128">.NET Core unit test projects</span></span>
- <span data-ttu-id="5b80f-129">Projekty testů .NET Core xUnit</span><span class="sxs-lookup"><span data-stu-id="5b80f-129">.NET Core xUnit test projects</span></span>

<span data-ttu-id="5b80f-130">Chcete-li například vytvořit Visual Basic aplikaci "Hello World", proveďte následující kroky z příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="5b80f-130">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="5b80f-131">Otevřete okno konzoly, vytvořte adresář pro váš projekt a nastavte jej jako aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="5b80f-131">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="5b80f-132">Zadejte příkaz `dotnet new console -lang vb`.</span><span class="sxs-lookup"><span data-stu-id="5b80f-132">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="5b80f-133">Příkaz vytvoří soubor projektu s `.vbproj` příponou souboru společně se souborem zdrojového kódu Visual Basic s názvem *program. vb*.</span><span class="sxs-lookup"><span data-stu-id="5b80f-133">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="5b80f-134">Tento soubor obsahuje zdrojový kód pro zápis řetězce "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="5b80f-134">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="5b80f-135">do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="5b80f-135">to the console window.</span></span>

1. <span data-ttu-id="5b80f-136">Zadejte příkaz `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="5b80f-136">Enter the command `dotnet run`.</span></span> <span data-ttu-id="5b80f-137">[.NET Core CLI](../tools/index.md) automaticky zkompiluje a spustí aplikaci, která zobrazí zprávu "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="5b80f-137">The [.NET Core CLI](../tools/index.md) automatically compiles and executes the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="5b80f-138">v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="5b80f-138">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="5b80f-139">Podpora pro C# 7,1</span><span class="sxs-lookup"><span data-stu-id="5b80f-139">Support for C# 7.1</span></span>

<span data-ttu-id="5b80f-140">.NET Core 2,0 podporuje C# 7,1, který přidává řadu nových funkcí, včetně:</span><span class="sxs-lookup"><span data-stu-id="5b80f-140">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="5b80f-141">Metodu, vstupní bod aplikace, lze označit pomocí klíčového slova [Async.](../../csharp/language-reference/keywords/async.md) `Main`</span><span class="sxs-lookup"><span data-stu-id="5b80f-141">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="5b80f-142">Odvoditelné názvy řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="5b80f-142">Inferred tuple names.</span></span>
- <span data-ttu-id="5b80f-143">Výchozí výrazy.</span><span class="sxs-lookup"><span data-stu-id="5b80f-143">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="5b80f-144">Vylepšení platformy</span><span class="sxs-lookup"><span data-stu-id="5b80f-144">Platform improvements</span></span>

<span data-ttu-id="5b80f-145">.NET Core 2,0 obsahuje řadu funkcí, které usnadňují instalaci .NET Core a jejich použití v podporovaných operačních systémech.</span><span class="sxs-lookup"><span data-stu-id="5b80f-145">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="5b80f-146">.NET Core pro Linux je jediná implementace.</span><span class="sxs-lookup"><span data-stu-id="5b80f-146">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="5b80f-147">.NET Core 2,0 nabízí jednu implementaci Linux, která funguje na více distribucích systému Linux.</span><span class="sxs-lookup"><span data-stu-id="5b80f-147">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="5b80f-148">Rozhraní .NET Core 1. x vyžaduje stažení implementace Linux specifické pro distribuci.</span><span class="sxs-lookup"><span data-stu-id="5b80f-148">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="5b80f-149">Můžete také vyvíjet aplikace, které se zaměřují na Linux jako jeden operační systém.</span><span class="sxs-lookup"><span data-stu-id="5b80f-149">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="5b80f-150">.NET Core 1. x vyžaduje, abyste každou distribuci systému Linux zacíleni samostatně.</span><span class="sxs-lookup"><span data-stu-id="5b80f-150">.NET Core 1.x required that you target each Linux distribution separately.</span></span>

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="5b80f-151">Podpora pro knihovny šifrování Apple</span><span class="sxs-lookup"><span data-stu-id="5b80f-151">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="5b80f-152">.NET Core 1. x v macOS vyžadovala knihovnu kryptografických knihoven sady OpenSSL Toolkit.</span><span class="sxs-lookup"><span data-stu-id="5b80f-152">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="5b80f-153">.NET Core 2,0 používá kryptografické knihovny Apple a nevyžaduje OpenSSL, takže už je nemusíte instalovat.</span><span class="sxs-lookup"><span data-stu-id="5b80f-153">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span>

## <a name="api-changes-and-library-support"></a><span data-ttu-id="5b80f-154">Změny rozhraní API a podpora knihoven</span><span class="sxs-lookup"><span data-stu-id="5b80f-154">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="5b80f-155">Podpora pro .NET Standard 2,0</span><span class="sxs-lookup"><span data-stu-id="5b80f-155">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="5b80f-156">.NET Standard definuje sadu rozhraní API s verzí, která musí být k dispozici v implementacích .NET, které vyhovují této verzi standardu.</span><span class="sxs-lookup"><span data-stu-id="5b80f-156">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="5b80f-157">.NET Standard je cílena na vývojáře knihovny.</span><span class="sxs-lookup"><span data-stu-id="5b80f-157">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="5b80f-158">Cílem je zaručit funkčnost, která je k dispozici pro knihovnu, která cílí na verzi .NET Standard v každé implementaci rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="5b80f-158">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="5b80f-159">.NET Core 1. x podporuje .NET Standard verze 1,6; .NET Core 2,0 podporuje nejnovější verzi .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="5b80f-159">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="5b80f-160">Další informace najdete v tématu [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="5b80f-160">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="5b80f-161">.NET Standard 2,0 obsahuje více než 20 000 více rozhraní API, než bylo k dispozici v .NET Standard 1,6.</span><span class="sxs-lookup"><span data-stu-id="5b80f-161">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="5b80f-162">Většina této rozšířené oblasti plochy je výsledkem zahrnutí rozhraní API, která jsou společná pro .NET Framework a Xamarin do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5b80f-162">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="5b80f-163">Knihovny tříd .NET Standard 2,0 také mohou odkazovat .NET Framework knihovny tříd za předpokladu, že volají rozhraní API, která jsou přítomna v .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="5b80f-163">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="5b80f-164">Nevyžadují se žádná opětovná kompilace knihoven .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5b80f-164">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="5b80f-165">Seznam rozhraní API přidaných do .NET Standard od poslední verze .NET Standard 1,6 najdete v tématu [.NET Standard 2,0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="5b80f-165">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="5b80f-166">Rozbalená oblast povrchu</span><span class="sxs-lookup"><span data-stu-id="5b80f-166">Expanded surface area</span></span>

<span data-ttu-id="5b80f-167">Celkový počet rozhraní API dostupných v .NET Core 2,0 má více než dvojitou přesnost v porovnání s rozhraním .NET Core 1,1.</span><span class="sxs-lookup"><span data-stu-id="5b80f-167">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span>

<span data-ttu-id="5b80f-168">A se sadou [Windows Compatibility Pack](../porting/windows-compat-pack.md) pro přenos z .NET Framework se taky zjednodušilo mnohem jednodušší.</span><span class="sxs-lookup"><span data-stu-id="5b80f-168">And with the [Windows Compatibility Pack](../porting/windows-compat-pack.md) porting from .NET Framework has also become much simpler.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="5b80f-169">Podpora pro knihovny .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5b80f-169">Support for .NET Framework libraries</span></span>

<span data-ttu-id="5b80f-170">Kód .NET Core může odkazovat na existující knihovny .NET Framework, včetně existujících balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="5b80f-170">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="5b80f-171">Všimněte si, že knihovny musí používat rozhraní API, které najdete v .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="5b80f-171">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="5b80f-172">integrace sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5b80f-172">Visual Studio integration</span></span>

<span data-ttu-id="5b80f-173">Visual Studio 2017 verze 15,3 a v některých případech Visual Studio pro Mac nabízí řadu významných vylepšení pro vývojáře na platformě .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5b80f-173">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="5b80f-174">Změna cílení na aplikace .NET Core a knihovny .NET Standard</span><span class="sxs-lookup"><span data-stu-id="5b80f-174">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="5b80f-175">Pokud je nainstalovaná sada .NET Core 2,0 SDK, můžete změnit cílení na projekty .NET Core 1. x na rozhraní .NET Core 2,0 a .NET Standard 1. x .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="5b80f-175">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span>

<span data-ttu-id="5b80f-176">Chcete-li změnit cílení projektu v aplikaci Visual Studio, otevřete kartu **aplikace** v dialogovém okně Vlastnosti projektu a změňte **cílovou hodnotu rozhraní** **.net Core 2,0** nebo **.NET Standard 2,0**.</span><span class="sxs-lookup"><span data-stu-id="5b80f-176">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="5b80f-177">Můžete ji také změnit kliknutím pravým tlačítkem myši na projekt a výběrem možnosti **Upravit \*soubor. csproj** .</span><span class="sxs-lookup"><span data-stu-id="5b80f-177">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="5b80f-178">Další informace najdete v části [nástroje](#tooling) výše v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="5b80f-178">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="5b80f-179">Podpora Live Unit Testing pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="5b80f-179">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="5b80f-180">Kdykoli upravíte kód, Live Unit Testing automaticky spustí všechny ovlivněné testy jednotek na pozadí a zobrazí výsledky a pokrytí kódu živě v prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5b80f-180">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="5b80f-181">.NET Core 2,0 teď podporuje Live Unit Testing.</span><span class="sxs-lookup"><span data-stu-id="5b80f-181">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="5b80f-182">Dříve byla Live Unit Testing k dispozici pouze pro .NET Framework aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b80f-182">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span>

<span data-ttu-id="5b80f-183">Další informace najdete v tématu [Live Unit Testing se sadou Visual Studio 2017](/visualstudio/test/live-unit-testing) a v části [Live Unit Testing Nejčastější dotazy](/visualstudio/test/live-unit-testing-faq).</span><span class="sxs-lookup"><span data-stu-id="5b80f-183">For more information, see [Live Unit Testing with Visual Studio 2017](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="5b80f-184">Lepší podpora pro více cílových rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b80f-184">Better support for multiple target frameworks</span></span>

<span data-ttu-id="5b80f-185">Pokud vytváříte projekt pro více cílových rozhraní, můžete nyní vybrat cílovou platformu z nabídky nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="5b80f-185">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="5b80f-186">Na následujícím obrázku je projekt nazvaný SCD1 Targeting 64-bit MacOS X 10,11 (`osx.10.11-x64`) a 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span><span class="sxs-lookup"><span data-stu-id="5b80f-186">In the following figure, a project named SCD1 targets 64-bit macOS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="5b80f-187">Před výběrem tlačítka projekt můžete vybrat cílovou architekturu, a to v tomto případě pro spuštění sestavení ladění.</span><span class="sxs-lookup"><span data-stu-id="5b80f-187">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![Snímek obrazovky znázorňující výběr cílového rozhraní při sestavování projektu](./media/dotnet-core-2-0/target-framework-selection.png)

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="5b80f-189">Souběžná podpora pro sady SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="5b80f-189">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="5b80f-190">Nyní můžete nainstalovat .NET Core SDK nezávisle na aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5b80f-190">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="5b80f-191">Díky tomu může jediná verze sady Visual Studio vytvářet projekty, které cílí na různé verze rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5b80f-191">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="5b80f-192">Dříve byla aplikace Visual Studio a .NET Core SDK úzce spojena; konkrétní verze sady SDK se doprovází konkrétní verze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5b80f-192">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="5b80f-193">Vylepšení dokumentace</span><span class="sxs-lookup"><span data-stu-id="5b80f-193">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="5b80f-194">Architektura aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="5b80f-194">.NET Application Architecture</span></span>

<span data-ttu-id="5b80f-195">[Architektura aplikace .NET](https://www.microsoft.com/net/learn/architecture) poskytuje přístup k sadě elektronických knih, které poskytují pokyny, osvědčené postupy a ukázkové aplikace při použití .NET k sestavení:</span><span class="sxs-lookup"><span data-stu-id="5b80f-195">[.NET Application Architecture](https://www.microsoft.com/net/learn/architecture) gives you access to a set of e-books that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- [<span data-ttu-id="5b80f-196">Mikroslužby a kontejnery Docker</span><span class="sxs-lookup"><span data-stu-id="5b80f-196">Microservices and Docker containers</span></span>](../../architecture/microservices/index.md)
- [<span data-ttu-id="5b80f-197">Webové aplikace s ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5b80f-197">Web applications with ASP.NET</span></span>](../../architecture/modern-web-apps-azure/index.md)
- [<span data-ttu-id="5b80f-198">Mobilní aplikace s využitím Xamarin</span><span class="sxs-lookup"><span data-stu-id="5b80f-198">Mobile applications with Xamarin</span></span>](/xamarin/xamarin-forms/enterprise-application-patterns/index)
- [<span data-ttu-id="5b80f-199">Aplikace, které jsou nasazené do cloudu s Azure</span><span class="sxs-lookup"><span data-stu-id="5b80f-199">Applications that are deployed to the Cloud with Azure</span></span>](/azure/architecture/reference-architectures/index)

## <a name="see-also"></a><span data-ttu-id="5b80f-200">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b80f-200">See also</span></span>

- [<span data-ttu-id="5b80f-201">Co je nového v ASP.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="5b80f-201">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)
