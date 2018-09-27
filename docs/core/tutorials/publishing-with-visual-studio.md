---
title: Publikování aplikace Hello World pomocí sady Visual Studio 2017
description: Publikování vytvoří sadu souborů, které jsou potřeba ke spuštění aplikace.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.custom: vs-dotnet
ms.openlocfilehash: e44ae69c9cd8f0767e369791737cef9b4c33f963
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399791"
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="fc79c-103">Publikování aplikace Hello World pomocí sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="fc79c-103">Publish your Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="fc79c-104">V [sestavení C# aplikace Hello World pomocí .NET Core v sadě Visual Studio 2017](with-visual-studio.md) nebo [vytvořit aplikaci Hello World jazyka Visual Basic pomocí .NET Core v sadě Visual Studio 2017](vb-with-visual-studio.md), jste vytvořili konzolovou aplikaci Hello World .</span><span class="sxs-lookup"><span data-stu-id="fc79c-104">In [Build a C# Hello World application with .NET Core in Visual Studio 2017](with-visual-studio.md) or [Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="fc79c-105">V [ladění jazyka C# aplikace Hello World pomocí sady Visual Studio 2017](debugging-with-visual-studio.md), můžete otestovat pomocí ladicího programu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fc79c-105">In [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="fc79c-106">Teď, když jste si jisti, že funguje podle očekávání, můžete publikovat tak, aby mohli ostatní uživatelé spouštět.</span><span class="sxs-lookup"><span data-stu-id="fc79c-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="fc79c-107">Publikování vytvoří sadu souborů, které jsou potřeba ke spuštění aplikace a soubory můžete nasadit zkopírováním do cílového počítače.</span><span class="sxs-lookup"><span data-stu-id="fc79c-107">Publishing creates the set of files that are needed to run your application, and you can deploy the files by copying them to a target machine.</span></span>

<span data-ttu-id="fc79c-108">K publikování a spuštění aplikace:</span><span class="sxs-lookup"><span data-stu-id="fc79c-108">To publish and run your application:</span></span> 

1. <span data-ttu-id="fc79c-109">Ujistěte se, že Visual Studio sestavuje verzi vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="fc79c-109">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="fc79c-110">V případě potřeby změnit nastavení konfigurace sestavení na panelu nástrojů z **ladění** k **vydání**.</span><span class="sxs-lookup"><span data-stu-id="fc79c-110">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Panel nástrojů Visual Studio](media/publishing-with-visual-studio/toolbar.png)

1. <span data-ttu-id="fc79c-112">Klikněte pravým tlačítkem na **HelloWorld** projektu (nikoli řešení HelloWorld) a vyberte **publikovat** z nabídky.</span><span class="sxs-lookup"><span data-stu-id="fc79c-112">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="fc79c-113">Můžete také vybrat **publikovat HelloWorld** z hlavní aplikace Visual Studio **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="fc79c-113">You can also select **Publish HelloWorld** from the main Visual Studio **Build** menu.</span></span>

   ![Panel nástrojů Visual Studio](media/publishing-with-visual-studio/publish1.png)


   ![Panel nástrojů Visual Studio](media/publishing-with-visual-studio/publishwindow.png)

1. <span data-ttu-id="fc79c-116">Otevřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="fc79c-116">Open a console window.</span></span> <span data-ttu-id="fc79c-117">Například v **typ hledání** textové pole na hlavním panelu Windows, zadejte `Command Prompt` (nebo `cmd` zkráceně) a otevřete okno konzoly tak, že vyberete **příkazového řádku** desktop aplikace nebo stisknutím klávesy Enter, pokud je vybrána ve výsledcích hledání.</span><span class="sxs-lookup"><span data-stu-id="fc79c-117">For example in the **Type here to search** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="fc79c-118">Přejděte k publikované aplikaci v `bin\release\PublishOutput` podadresáři adresáře projektu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="fc79c-118">Navigate to the published application in the `bin\release\PublishOutput` subdirectory of your application's project directory.</span></span> <span data-ttu-id="fc79c-119">Jak ukazuje následující obrázek, publikovaný výstup zahrnuje následující čtyři soubory:</span><span class="sxs-lookup"><span data-stu-id="fc79c-119">As the following figure shows, the published output includes the following four files:</span></span>

      * <span data-ttu-id="fc79c-120">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="fc79c-120">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="fc79c-121">Soubor závislosti modulu runtime aplikace.</span><span class="sxs-lookup"><span data-stu-id="fc79c-121">The application's runtime dependencies file.</span></span> <span data-ttu-id="fc79c-122">Definuje komponenty .NET Core a knihovny (včetně knihovny DLL, která obsahuje vaše aplikace) potřebných ke spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="fc79c-122">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run your application.</span></span> <span data-ttu-id="fc79c-123">Další informace najdete v tématu [konfigurační soubory modulu Runtime](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="fc79c-123">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>
 
      * <span data-ttu-id="fc79c-124">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="fc79c-124">*HelloWorld.dll*</span></span>

         <span data-ttu-id="fc79c-125">Soubor, který obsahuje vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fc79c-125">The file that contains your application.</span></span> <span data-ttu-id="fc79c-126">Je dynamické knihovny DLL, které můžete provést tak, že zadáte `dotnet HelloWorld.dll` příkazu v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="fc79c-126">It is a dynamic link library that can be executed by entering the `dotnet HelloWorld.dll` command in a console window.</span></span> 

      * <span data-ttu-id="fc79c-127">*HelloWorld.pdb* (volitelné pro nasazení)</span><span class="sxs-lookup"><span data-stu-id="fc79c-127">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="fc79c-128">Soubor, který obsahuje symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="fc79c-128">A file that contains debug symbols.</span></span> <span data-ttu-id="fc79c-129">Není nutné k nasazení tohoto souboru spolu s vaší aplikace, i když byste ji uložíte, v případě, že budete muset ladění publikované verze vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="fc79c-129">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="fc79c-130">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="fc79c-130">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="fc79c-131">Konfigurační soubor běhu aplikace.</span><span class="sxs-lookup"><span data-stu-id="fc79c-131">The application's runtime configuration file.</span></span> <span data-ttu-id="fc79c-132">Určuje verzi .NET Core, vaše aplikace byla vytvořena pro spuštění na.</span><span class="sxs-lookup"><span data-stu-id="fc79c-132">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="fc79c-133">Další informace najdete v tématu [konfigurační soubory modulu Runtime](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="fc79c-133">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>  

   ![Okno konzoly publikované soubory](media/publishing-with-visual-studio/publishedfiles.png)

<span data-ttu-id="fc79c-135">Proces publikování vytvoří nasazení závisí na architektuře, které je typ nasazení, ve kterém se spustí publikovanou aplikaci na žádnou platformu podporovanou nástrojem .NET Core s .NET Core v systému nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="fc79c-135">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application will run on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="fc79c-136">Uživatelé můžou spouštět aplikace vydáním `dotnet HelloWorld.dll` příkazu z okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="fc79c-136">Users can run your application by issuing the `dotnet HelloWorld.dll` command from a console window.</span></span>

<span data-ttu-id="fc79c-137">Další informace o publikování a nasazení aplikací .NET Core najdete v tématu [nasazení aplikace .NET Core](../../core/deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="fc79c-137">For more information on publishing and deploying .NET Core applications, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>
