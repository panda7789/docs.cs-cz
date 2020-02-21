---
title: 'Kurz: Vytvoření nástroje .NET Core'
description: Naučte se vytvořit nástroj .NET Core. Nástroj je Konzolová aplikace, která je nainstalována pomocí .NET Core CLI.
ms.date: 02/12/2020
ms.openlocfilehash: 558bf9e37efc8de68a61f1384fababe342ab7d66
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543401"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a><span data-ttu-id="098c9-104">Kurz: Vytvoření nástroje .NET Core pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="098c9-104">Tutorial: Create a .NET Core tool using the .NET Core CLI</span></span>

<span data-ttu-id="098c9-105">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="098c9-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="098c9-106">V tomto kurzu se naučíte, jak vytvořit a zabalit nástroj .NET Core.</span><span class="sxs-lookup"><span data-stu-id="098c9-106">This tutorial teaches you how to create and package a .NET Core tool.</span></span> <span data-ttu-id="098c9-107">.NET Core CLI umožňuje vytvořit konzolovou aplikaci jako nástroj, který mohou nainstalovat a spustit další.</span><span class="sxs-lookup"><span data-stu-id="098c9-107">The .NET Core CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="098c9-108">Nástroje .NET Core jsou balíčky NuGet, které jsou nainstalované z .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="098c9-108">.NET Core tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="098c9-109">Další informace o nástrojích najdete v tématu [Přehled nástrojů .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="098c9-109">For more information about tools, see [.NET Core tools overview](global-tools.md).</span></span>

<span data-ttu-id="098c9-110">Nástroj, který vytvoříte, je Konzolová aplikace, která jako vstup převezme zprávu, a zobrazí zprávu spolu s řádky textu, které vytvoří obrázek robota.</span><span class="sxs-lookup"><span data-stu-id="098c9-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="098c9-111">Toto je první v sérii tří kurzů.</span><span class="sxs-lookup"><span data-stu-id="098c9-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="098c9-112">V tomto kurzu vytvoříte a zabalíte nástroj.</span><span class="sxs-lookup"><span data-stu-id="098c9-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="098c9-113">V následujících dvou kurzech používáte [Nástroj jako globální nástroj](global-tools-how-to-use.md) a [nástroj použijete jako místní nástroj](local-tools-how-to-use.md).</span><span class="sxs-lookup"><span data-stu-id="098c9-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="098c9-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="098c9-114">Prerequisites</span></span>

- <span data-ttu-id="098c9-115">[.NET Core SDK 3,1](https://dotnet.microsoft.com/download) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="098c9-115">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="098c9-116">Tento kurz a následující [kurz pro globální nástroje](global-tools-how-to-use.md) se vztahují na .NET Core SDK 2,1 a novější verze, protože v této verzi jsou dostupné globální nástroje.</span><span class="sxs-lookup"><span data-stu-id="098c9-116">This tutorial and the following [tutorial for global tools](global-tools-how-to-use.md) apply to .NET Core SDK 2.1 and later versions because global tools are available starting in that version.</span></span> <span data-ttu-id="098c9-117">Ale v tomto kurzu se předpokládá, že máte nainstalovaný 3,1 nebo novější, abyste měli možnost pokračovat na [místní kurzy k nástrojům](local-tools-how-to-use.md).</span><span class="sxs-lookup"><span data-stu-id="098c9-117">But this tutorial assumes you have installed 3.1 or later so that you have the option of continuing on to the [local tools tutorial](local-tools-how-to-use.md).</span></span> <span data-ttu-id="098c9-118">K dispozici jsou místní nástroje od .NET Core SDK 3,0.</span><span class="sxs-lookup"><span data-stu-id="098c9-118">Local tools are available starting in .NET Core SDK 3.0.</span></span> <span data-ttu-id="098c9-119">Postupy pro vytvoření nástroje jsou stejné, ať už používáte jako globální nástroj, nebo jako místní nástroj.</span><span class="sxs-lookup"><span data-stu-id="098c9-119">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>
  
- <span data-ttu-id="098c9-120">Textový editor nebo editor kódu podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="098c9-120">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="098c9-121">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="098c9-121">Create a project</span></span>

1. <span data-ttu-id="098c9-122">Otevřete příkazový řádek a vytvořte složku s názvem *úložiště*.</span><span class="sxs-lookup"><span data-stu-id="098c9-122">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="098c9-123">Přejděte do složky *úložiště* a zadejte následující příkaz, kde nahraďte `<name>` jedinečnou hodnotou, aby byl název projektu jedinečný.</span><span class="sxs-lookup"><span data-stu-id="098c9-123">Navigate to the *repository* folder and enter the following command, replacing `<name>` with a unique value to make the project name unique.</span></span> 

   ```dotnetcli
   dotnet new console -n botsay-<name>
   ```

   <span data-ttu-id="098c9-124">Můžete například spustit následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="098c9-124">For example, you could run the following command:</span></span>

   ```dotnetcli
   dotnet new console -n botsay-nancydavolio
   ```

   <span data-ttu-id="098c9-125">Příkaz vytvoří novou složku s názvem *botsay-\<název >* ve složce *úložiště* .</span><span class="sxs-lookup"><span data-stu-id="098c9-125">The command creates a new folder named *botsay-\<name>* under the *repository* folder.</span></span>

1. <span data-ttu-id="098c9-126">Přejděte do složky *botsay-\<název >* .</span><span class="sxs-lookup"><span data-stu-id="098c9-126">Navigate to the *botsay-\<name>* folder.</span></span>

   ```console
   cd botsay-<name>
   ```

## <a name="add-the-code"></a><span data-ttu-id="098c9-127">Přidání kódu</span><span class="sxs-lookup"><span data-stu-id="098c9-127">Add the code</span></span>

1. <span data-ttu-id="098c9-128">Otevřete `Program.cs` soubor pomocí editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="098c9-128">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="098c9-129">Do horní části souboru přidejte následující direktivu `using`:</span><span class="sxs-lookup"><span data-stu-id="098c9-129">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="098c9-130">Nahraďte metodu `Main` následujícím kódem pro zpracování argumentů příkazového řádku pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="098c9-130">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

   ```csharp
   static void Main(string[] args)
   {
       if (args.Length == 0)
       {
           var versionString = Assembly.GetEntryAssembly()
                                   .GetCustomAttribute<AssemblyInformationalVersionAttribute>()
                                   .InformationalVersion
                                   .ToString();

           Console.WriteLine($"botsay v{versionString}");
           Console.WriteLine("-------------");
           Console.WriteLine("\nUsage:");
           Console.WriteLine("  botsay <message>");
           return;
       }

       ShowBot(string.Join(' ', args));
   }
   ```

   <span data-ttu-id="098c9-131">Pokud nejsou předány žádné argumenty, zobrazí se krátká zpráva help.</span><span class="sxs-lookup"><span data-stu-id="098c9-131">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="098c9-132">V opačném případě jsou všechny argumenty zřetězeny do jednoho řetězce a vytištěny voláním metody `ShowBot`, kterou vytvoříte v následujícím kroku.</span><span class="sxs-lookup"><span data-stu-id="098c9-132">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="098c9-133">Přidejte novou metodu s názvem `ShowBot`, která přijímá řetězcový parametr.</span><span class="sxs-lookup"><span data-stu-id="098c9-133">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="098c9-134">Metoda vytiskne zprávu a obrázek robota s použitím řádků textu.</span><span class="sxs-lookup"><span data-stu-id="098c9-134">The method prints out the message and an image of a robot using lines of text.</span></span>

   ```csharp
   static void ShowBot(string message)
   {
       string bot = $"\n        {message}";
       bot += @"
       __________________
                         \
                          \
                             ....
                             ....'
                              ....
                           ..........
                       .............'..'..
                    ................'..'.....
                  .......'..........'..'..'....
                 ........'..........'..'..'.....
                .'....'..'..........'..'.......'.
                .'..................'...   ......
                .  ......'.........         .....
                .    _            __        ......
               ..    #            ##        ......
              ....       .                 .......
              ......  .......          ............
               ................  ......................
               ........................'................
              ......................'..'......    .......
           .........................'..'.....       .......
        ........    ..'.............'..'....      ..........
      ..'..'...      ...............'.......      ..........
     ...'......     ...... ..........  ......         .......
    ...........   .......              ........        ......
   .......        '...'.'.              '.'.'.'         ....
   .......       .....'..               ..'.....
      ..       ..........               ..'........
             ............               ..............
            .............               '..............
           ...........'..              .'.'............
          ...............              .'.'.............
         .............'..               ..'..'...........
         ...............                 .'..............
          .........                        ..............
           .....
   ";
       Console.WriteLine(bot);
   }
   ```

1. <span data-ttu-id="098c9-135">Uložte provedené změny.</span><span class="sxs-lookup"><span data-stu-id="098c9-135">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="098c9-136">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="098c9-136">Test the application</span></span>

<span data-ttu-id="098c9-137">Spusťte projekt a podívejte se na výstup.</span><span class="sxs-lookup"><span data-stu-id="098c9-137">Run the project and see the output.</span></span> <span data-ttu-id="098c9-138">Zkuste tyto variace na příkazovém řádku pro zobrazení různých výsledků:</span><span class="sxs-lookup"><span data-stu-id="098c9-138">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="098c9-139">Všechny argumenty po `--` oddělovači jsou předány do aplikace.</span><span class="sxs-lookup"><span data-stu-id="098c9-139">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="098c9-140">Zabalení nástroje</span><span class="sxs-lookup"><span data-stu-id="098c9-140">Package the tool</span></span>

<span data-ttu-id="098c9-141">Předtím, než budete moci zabalit a distribuovat aplikaci jako nástroj, je nutné upravit soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="098c9-141">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span> 

1. <span data-ttu-id="098c9-142">Otevřete *název botsay-\<> soubor. csproj* a přidejte na konec `<PropertyGroup>` uzlu tři nové uzly XML:</span><span class="sxs-lookup"><span data-stu-id="098c9-142">Open the *botsay-\<name>.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="098c9-143">`<ToolCommandName>` je volitelný prvek, který určuje příkaz, který nástroj vyvolá po jeho instalaci.</span><span class="sxs-lookup"><span data-stu-id="098c9-143">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="098c9-144">Pokud tento prvek není k dispozici, název příkazu pro nástroj je název souboru projektu bez přípony *. csproj* .</span><span class="sxs-lookup"><span data-stu-id="098c9-144">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="098c9-145">`<PackageOutputPath>` je volitelný prvek, který určuje, kde bude vytvořen balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="098c9-145">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="098c9-146">Balíček NuGet je to, co .NET Core CLI používá k instalaci nástroje.</span><span class="sxs-lookup"><span data-stu-id="098c9-146">The NuGet package is what the .NET Core CLI uses to install your tool.</span></span>

   <span data-ttu-id="098c9-147">Soubor projektu teď vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="098c9-147">The project file now looks like the following example:</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">
  
     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>netcoreapp3.1</TargetFramework>
  
       <PackAsTool>true</PackAsTool>
       <ToolCommandName>botsay</ToolCommandName>
       <PackageOutputPath>./nupkg</PackageOutputPath>
  
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="098c9-148">Vytvořte balíček NuGet spuštěním příkazu [dotnet Pack](dotnet-pack.md) :</span><span class="sxs-lookup"><span data-stu-id="098c9-148">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="098c9-149">*Název botsay-\<>. 1.0.0. nupkg* se vytvoří ve složce určené hodnotou `<PackageOutputPath>` ze souboru *botsay-\<Name >. csproj* , který je v tomto příkladu složkou *./nupkg* .</span><span class="sxs-lookup"><span data-stu-id="098c9-149">The *botsay-\<name>.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *botsay-\<name>.csproj* file, which in this example is the *./nupkg* folder.</span></span>
  
   <span data-ttu-id="098c9-150">Pokud chcete veřejně vydávat nástroj, můžete ho nahrát na `https://www.nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="098c9-150">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="098c9-151">Jakmile je nástroj k dispozici v NuGet, mohou vývojáři nainstalovat nástroj pomocí příkazu pro [instalaci nástroje dotnet](dotnet-tool-install.md) .</span><span class="sxs-lookup"><span data-stu-id="098c9-151">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="098c9-152">V tomto kurzu nainstalujete balíček přímo z místní složky *nupkg* , takže není potřeba balíček nahrát do NuGet.</span><span class="sxs-lookup"><span data-stu-id="098c9-152">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="098c9-153">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="098c9-153">Troubleshoot</span></span>

<span data-ttu-id="098c9-154">Pokud se vám zobrazí chybová zpráva s postupem v tomto kurzu, přečtěte si téma [řešení potíží s používáním nástrojů .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="098c9-154">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="098c9-155">Další kroky</span><span class="sxs-lookup"><span data-stu-id="098c9-155">Next steps</span></span>

<span data-ttu-id="098c9-156">V tomto kurzu jste vytvořili konzolovou aplikaci a zabalíte ji jako nástroj.</span><span class="sxs-lookup"><span data-stu-id="098c9-156">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="098c9-157">Pokud se chcete dozvědět, jak nástroj používat jako globální nástroj, přejděte k dalšímu kurzu.</span><span class="sxs-lookup"><span data-stu-id="098c9-157">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="098c9-158">Instalace a použití globálního nástroje</span><span class="sxs-lookup"><span data-stu-id="098c9-158">Install and use a global tool</span></span>](global-tools-how-to-use.md)

<span data-ttu-id="098c9-159">Pokud chcete, můžete přeskočit kurz globálních nástrojů a přejít přímo do kurzu místních nástrojů.</span><span class="sxs-lookup"><span data-stu-id="098c9-159">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="098c9-160">Instalace a použití místního nástroje</span><span class="sxs-lookup"><span data-stu-id="098c9-160">Install and use a local tool</span></span>](local-tools-how-to-use.md)
