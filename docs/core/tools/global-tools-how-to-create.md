---
title: Postup vytvoření globálního nástroje .NET Core
description: Popisuje, jak vytvořit globální nástroj. Globální nástroj je Konzolová aplikace, která je nainstalována prostřednictvím .NET Core CLI.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 5c2b1e459f0308f5f96eb041c10f4d7a7ae0ca20
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117445"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="3b40c-104">Vytvoření globálního nástroje .NET Core pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="3b40c-104">Create a .NET Core Global Tool using the .NET Core CLI</span></span>

<span data-ttu-id="3b40c-105">V tomto článku se naučíte, jak vytvořit a zabalit globální nástroj .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3b40c-105">This article teaches you how to create and package a .NET Core Global Tool.</span></span> <span data-ttu-id="3b40c-106">.NET Core CLI umožňuje vytvořit konzolovou aplikaci jako globální nástroj, který mohou uživatelé snadno nainstalovat a spustit.</span><span class="sxs-lookup"><span data-stu-id="3b40c-106">The .NET Core CLI allows you to create a console application as a Global Tool, which others can easily install and run.</span></span> <span data-ttu-id="3b40c-107">Globální nástroje .NET Core jsou balíčky NuGet, které jsou nainstalované z .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="3b40c-107">.NET Core Global Tools are NuGet packages that are installed from the .NET Core CLI.</span></span> <span data-ttu-id="3b40c-108">Další informace o globálních nástrojích najdete v tématu [Přehled globálních nástrojů .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="3b40c-108">For more information about Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a><span data-ttu-id="3b40c-109">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="3b40c-109">Create a project</span></span>

<span data-ttu-id="3b40c-110">Tento článek používá .NET Core CLI k vytvoření a správě projektu.</span><span class="sxs-lookup"><span data-stu-id="3b40c-110">This article uses the .NET Core CLI to create and manage a project.</span></span>

<span data-ttu-id="3b40c-111">Náš ukázkový nástroj bude Konzolová aplikace, která generuje robota ASCII a vytiskne zprávu.</span><span class="sxs-lookup"><span data-stu-id="3b40c-111">Our example tool will be a console application that generates an ASCII bot and prints a message.</span></span> <span data-ttu-id="3b40c-112">Nejprve vytvořte novou konzolovou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3b40c-112">First, create a new .NET Core Console Application.</span></span>

```dotnetcli
dotnet new console -o botsay
```

<span data-ttu-id="3b40c-113">Přejděte do `botsay` adresáře vytvořeného předchozím příkazem.</span><span class="sxs-lookup"><span data-stu-id="3b40c-113">Navigate to the `botsay` directory created by the previous command.</span></span>

## <a name="add-the-code"></a><span data-ttu-id="3b40c-114">Přidat kód</span><span class="sxs-lookup"><span data-stu-id="3b40c-114">Add the code</span></span>

<span data-ttu-id="3b40c-115">Otevřete soubor v oblíbeném textovém editoru, jako je `vim` například nebo [Visual Studio Code](https://code.visualstudio.com/). `Program.cs`</span><span class="sxs-lookup"><span data-stu-id="3b40c-115">Open the `Program.cs` file with your favorite text editor, such as `vim` or [Visual Studio Code](https://code.visualstudio.com/).</span></span>

<span data-ttu-id="3b40c-116">Do horní části `using` souboru přidejte následující direktivu, což pomůže zkrátit kód a zobrazit informace o verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="3b40c-116">Add the following `using` directive to the top of the file, this helps shorten the code to display the version information of the application.</span></span>

```csharp
using System.Reflection;
```

<span data-ttu-id="3b40c-117">Potom přejděte dolů k `Main` metodě.</span><span class="sxs-lookup"><span data-stu-id="3b40c-117">Next, move down to the `Main` method.</span></span> <span data-ttu-id="3b40c-118">Nahraďte metodu následujícím kódem pro zpracování argumentů příkazového řádku pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b40c-118">Replace the method with the following code to process the command-line arguments for your application.</span></span> <span data-ttu-id="3b40c-119">Pokud nebyly předány žádné argumenty, zobrazí se krátká zpráva help.</span><span class="sxs-lookup"><span data-stu-id="3b40c-119">If no arguments were passed, a short help message is displayed.</span></span> <span data-ttu-id="3b40c-120">V opačném případě jsou všechny tyto argumenty transformovány do řetězce a vytištěny s robotem.</span><span class="sxs-lookup"><span data-stu-id="3b40c-120">Otherwise, all of those arguments are transformed into a string and printed with the bot.</span></span>

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

### <a name="create-the-bot"></a><span data-ttu-id="3b40c-121">Vytvoření robota</span><span class="sxs-lookup"><span data-stu-id="3b40c-121">Create the bot</span></span>

<span data-ttu-id="3b40c-122">Dále přidejte novou metodu s názvem `ShowBot` , která přijímá řetězcový parametr.</span><span class="sxs-lookup"><span data-stu-id="3b40c-122">Next, add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="3b40c-123">Tato metoda vytiskne zprávy a robota ASCII.</span><span class="sxs-lookup"><span data-stu-id="3b40c-123">This method prints out the message and the ASCII bot.</span></span> <span data-ttu-id="3b40c-124">Z ukázky [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) byl vytvořen kód bot standardu ASCII.</span><span class="sxs-lookup"><span data-stu-id="3b40c-124">The ASCII bot code was taken from the [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) sample.</span></span>

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

### <a name="test-the-tool"></a><span data-ttu-id="3b40c-125">Otestování nástroje</span><span class="sxs-lookup"><span data-stu-id="3b40c-125">Test the tool</span></span>

<span data-ttu-id="3b40c-126">Spusťte projekt a podívejte se na výstup.</span><span class="sxs-lookup"><span data-stu-id="3b40c-126">Run the project and see the output.</span></span> <span data-ttu-id="3b40c-127">Zkuste tyto variace příkazového řádku pro zobrazení různých výsledků:</span><span class="sxs-lookup"><span data-stu-id="3b40c-127">Try these variations of the command-line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

<span data-ttu-id="3b40c-128">Všechny argumenty za `--` oddělovačem jsou předány do aplikace.</span><span class="sxs-lookup"><span data-stu-id="3b40c-128">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="setup-the-global-tool"></a><span data-ttu-id="3b40c-129">Nastavení globálního nástroje</span><span class="sxs-lookup"><span data-stu-id="3b40c-129">Setup the global tool</span></span>

<span data-ttu-id="3b40c-130">Předtím, než budete moci zabalit a distribuovat aplikaci jako globální nástroj, je nutné upravit soubor projektu.</span><span class="sxs-lookup"><span data-stu-id="3b40c-130">Before you can pack and distribute the application as a Global Tool, you need to modify the project file.</span></span> <span data-ttu-id="3b40c-131">Otevřete soubor a přidejte do uzlu tři nové uzly XML: `<Project><PropertyGroup>` `botsay.csproj`</span><span class="sxs-lookup"><span data-stu-id="3b40c-131">Open the `botsay.csproj` file and add three new XML nodes to the `<Project><PropertyGroup>` node:</span></span>

- `<PackAsTool>`\
<span data-ttu-id="3b40c-132">POŽADOVANOU Označuje, že aplikace bude zabalena pro instalaci jako globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="3b40c-132">[REQUIRED] Indicates that the application will be packaged for install as a Global Tool.</span></span>

- `<ToolCommandName>`\
<span data-ttu-id="3b40c-133">VOLITELNÉ Alternativní název nástroje, jinak bude název příkazu pro nástroj pojmenován za souborem projektu.</span><span class="sxs-lookup"><span data-stu-id="3b40c-133">[OPTIONAL] An alternative name for the tool, otherwise the command name for the tool will be named after the project file.</span></span> <span data-ttu-id="3b40c-134">V balíčku můžete mít několik nástrojů, přičemž volba jedinečného a popisného názvu pomůže odlišit od ostatních nástrojů ve stejném balíčku.</span><span class="sxs-lookup"><span data-stu-id="3b40c-134">You can have multiple tools in a package, choosing a unique and friendly name helps differentiate from other tools in the same package.</span></span>

- `<PackageOutputPath>`\
<span data-ttu-id="3b40c-135">VOLITELNÉ Kde bude vytvořen balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="3b40c-135">[OPTIONAL] Where the NuGet package will be produced.</span></span> <span data-ttu-id="3b40c-136">Balíček NuGet je to, co .NET Core CLI globální nástroje používají k instalaci vašeho nástroje.</span><span class="sxs-lookup"><span data-stu-id="3b40c-136">The NuGet package is what the .NET Core CLI Global Tools uses to install your tool.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>

    <PackAsTool>true</PackAsTool>
    <ToolCommandName>botsay</ToolCommandName>
    <PackageOutputPath>./nupkg</PackageOutputPath>

  </PropertyGroup>

</Project>
```

<span data-ttu-id="3b40c-137">I když `<PackageOutputPath>` je volitelný, použijte ho v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="3b40c-137">Even though `<PackageOutputPath>` is optional, use it in this example.</span></span> <span data-ttu-id="3b40c-138">Ujistěte se, že jste ji `<PackageOutputPath>./nupkg</PackageOutputPath>`nastavili:.</span><span class="sxs-lookup"><span data-stu-id="3b40c-138">Make sure you set it: `<PackageOutputPath>./nupkg</PackageOutputPath>`.</span></span>

<span data-ttu-id="3b40c-139">Dále vytvořte balíček NuGet pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b40c-139">Next, create a NuGet package for your application.</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="3b40c-140">Soubor je vytvořen ve složce identifikované `<PackageOutputPath>` hodnotou XML ze `botsay.csproj` `./nupkg` souboru, který je v tomto příkladu složkou. `botsay.1.0.0.nupkg`</span><span class="sxs-lookup"><span data-stu-id="3b40c-140">The `botsay.1.0.0.nupkg` file is created in the folder identified by the `<PackageOutputPath>` XML value from the `botsay.csproj` file, which in this example is the `./nupkg` folder.</span></span> <span data-ttu-id="3b40c-141">To usnadňuje instalaci a testování.</span><span class="sxs-lookup"><span data-stu-id="3b40c-141">This makes it easy to install and test.</span></span> <span data-ttu-id="3b40c-142">Pokud chcete veřejně vydávat nástroj, nahrajte ho do <https://www.nuget.org>.</span><span class="sxs-lookup"><span data-stu-id="3b40c-142">When you want to release a tool publicly, upload it to <https://www.nuget.org>.</span></span> <span data-ttu-id="3b40c-143">Jakmile je nástroj k dispozici v NuGet, vývojáři můžou provést instalaci nástroje pro všechny uživatele pomocí `--global` možnosti [instalačního příkazu nástroje dotnet](dotnet-tool-install.md) .</span><span class="sxs-lookup"><span data-stu-id="3b40c-143">Once the tool is available on NuGet, developers can perform a user-wide installation of the tool using the `--global` option of the [dotnet tool install](dotnet-tool-install.md) command.</span></span>

<span data-ttu-id="3b40c-144">Teď, když máte balíček, nainstalujte nástroj z tohoto balíčku:</span><span class="sxs-lookup"><span data-stu-id="3b40c-144">Now that you have a package, install the tool from that package:</span></span>

```dotnetcli
dotnet tool install --global --add-source ./nupkg botsay
```

<span data-ttu-id="3b40c-145">Parametr oznamuje .NET Core CLI dočasné `./nupkg` použití složky (naší `<PackageOutputPath>` složky) jako dalšího zdrojového kanálu pro balíčky NuGet. `--add-source`</span><span class="sxs-lookup"><span data-stu-id="3b40c-145">The `--add-source` parameter tells the .NET Core CLI to temporarily use the `./nupkg` folder (our `<PackageOutputPath>` folder) as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="3b40c-146">Další informace o instalaci globálních nástrojů najdete v tématu [Přehled globálních nástrojů .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="3b40c-146">For more information about installing Global Tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

<span data-ttu-id="3b40c-147">Pokud je instalace úspěšná, zobrazí se zpráva s příkazem použitým pro volání nástroje a nainstalované verze, podobně jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3b40c-147">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

<span data-ttu-id="3b40c-148">Nyní byste měli být schopni zadat `botsay` a získat odpověď z nástroje.</span><span class="sxs-lookup"><span data-stu-id="3b40c-148">You should now be able to type `botsay` and get a response from the tool.</span></span>

> [!NOTE]
> <span data-ttu-id="3b40c-149">Pokud byla instalace úspěšná, ale nemůžete použít `botsay` příkaz, možná budete muset otevřít nový terminál, aby se cesta aktualizovala.</span><span class="sxs-lookup"><span data-stu-id="3b40c-149">If the install was successful, but you cannot use the `botsay` command, you may need to open a new terminal to refresh the PATH.</span></span>

## <a name="remove-the-tool"></a><span data-ttu-id="3b40c-150">Odebrat nástroj</span><span class="sxs-lookup"><span data-stu-id="3b40c-150">Remove the tool</span></span>

<span data-ttu-id="3b40c-151">Až budete s nástrojem hotovi, můžete ho odebrat pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="3b40c-151">Once you're done experimenting with the tool, you can remove it with the following command:</span></span>

```dotnetcli
dotnet tool uninstall -g botsay
```
