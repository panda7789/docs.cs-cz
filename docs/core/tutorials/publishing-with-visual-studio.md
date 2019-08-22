---
title: Publikování aplikace Hello World .NET Core pomocí sady Visual Studio 2017
description: Publikování vytvoří sadu souborů, které jsou nutné ke spuštění aplikace .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: f8c37f47cc8dfb999f2371773a50c2dd91e074a5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660478"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="4ce66-103">Publikování aplikace Hello World .NET Core pomocí sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="4ce66-103">Publish your .NET Core Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="4ce66-104">V [sestavování aplikace C# Hello World s .NET Core v aplikaci Visual Studio 2017](with-visual-studio.md) nebo [sestavení Visual Basic Hello World aplikace pomocí .NET core v aplikaci Visual Studio 2017](vb-with-visual-studio.md)jste vytvořili konzolovou aplikaci Hello World.</span><span class="sxs-lookup"><span data-stu-id="4ce66-104">In [Build a C# Hello World application with .NET Core in Visual Studio 2017](with-visual-studio.md) or [Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="4ce66-105">V části [ladění C# aplikace Hello World pomocí sady Visual Studio 2017](debugging-with-visual-studio.md)jste otestovali pomocí ladicího programu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4ce66-105">In [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="4ce66-106">Teď, když jste si jisti, že funguje podle očekávání, můžete ji publikovat, aby ji ostatní uživatelé mohli spustit.</span><span class="sxs-lookup"><span data-stu-id="4ce66-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="4ce66-107">Publikování vytvoří sadu souborů, které jsou potřeba ke spuštění vaší aplikace, a soubory můžete nasadit tak, že je zkopírujete do cílového počítače.</span><span class="sxs-lookup"><span data-stu-id="4ce66-107">Publishing creates the set of files that are needed to run your application, and you can deploy the files by copying them to a target machine.</span></span>

<span data-ttu-id="4ce66-108">Publikování a spuštění aplikace:</span><span class="sxs-lookup"><span data-stu-id="4ce66-108">To publish and run your application:</span></span> 

1. <span data-ttu-id="4ce66-109">Ujistěte se, že Visual Studio sestavuje prodejní verzi vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="4ce66-109">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="4ce66-110">V případě potřeby změňte nastavení konfigurace sestavení na panelu nástrojů z části **ladit** na **verzi**.</span><span class="sxs-lookup"><span data-stu-id="4ce66-110">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Panel nástrojů sady Visual Studio s vybraným sestavením pro vydání](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="4ce66-112">Klikněte pravým tlačítkem na projekt **HelloWorld** (ne na řešení HelloWorld) a v nabídce vyberte **publikovat** .</span><span class="sxs-lookup"><span data-stu-id="4ce66-112">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="4ce66-113">Můžete také vybrat **publikovat HelloWorld** z hlavní nabídky **sestavení** sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4ce66-113">You can also select **Publish HelloWorld** from the main Visual Studio **Build** menu.</span></span>

   ![Místní nabídka publikování Visual studia](media/publishing-with-visual-studio/publish-context-menu.png)

   ![Okno pro publikování v aplikaci Visual Studio](media/publishing-with-visual-studio/publish-settings-window.png)

1. <span data-ttu-id="4ce66-116">Otevřete okno konzoly.</span><span class="sxs-lookup"><span data-stu-id="4ce66-116">Open a console window.</span></span> <span data-ttu-id="4ce66-117">Například do textového pole **typ tady pro hledání** na hlavním panelu Windows zadejte `Command Prompt` (nebo `cmd` pro krátké) a otevřete okno konzoly. buď vyberte aplikaci desktopového **řádku** nebo stiskněte klávesu ENTER, pokud je vybraná na výsledky hledání</span><span class="sxs-lookup"><span data-stu-id="4ce66-117">For example in the **Type here to search** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="4ce66-118">Přejděte k publikované aplikaci v `bin\release\PublishOutput` podadresáři adresáře projektu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="4ce66-118">Navigate to the published application in the `bin\release\PublishOutput` subdirectory of your application's project directory.</span></span> <span data-ttu-id="4ce66-119">Jak ukazuje následující obrázek, publikovaný výstup obsahuje následující čtyři soubory:</span><span class="sxs-lookup"><span data-stu-id="4ce66-119">As the following figure shows, the published output includes the following four files:</span></span>

      * <span data-ttu-id="4ce66-120">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="4ce66-120">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="4ce66-121">Soubor závislostí modulu runtime aplikace</span><span class="sxs-lookup"><span data-stu-id="4ce66-121">The application's runtime dependencies file.</span></span> <span data-ttu-id="4ce66-122">Definuje součásti .NET Core a knihovny (včetně knihovny dynamického propojení, která obsahuje vaši aplikaci) potřebné ke spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="4ce66-122">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run your application.</span></span> <span data-ttu-id="4ce66-123">Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="4ce66-123">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>
 
      * <span data-ttu-id="4ce66-124">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="4ce66-124">*HelloWorld.dll*</span></span>

         <span data-ttu-id="4ce66-125">Soubor, který obsahuje vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4ce66-125">The file that contains your application.</span></span> <span data-ttu-id="4ce66-126">Je to dynamická knihovna, kterou lze spustit zadáním `dotnet HelloWorld.dll` příkazu v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="4ce66-126">It is a dynamic link library that can be executed by entering the `dotnet HelloWorld.dll` command in a console window.</span></span> 

      * <span data-ttu-id="4ce66-127">*HelloWorld. pdb* (volitelné pro nasazení)</span><span class="sxs-lookup"><span data-stu-id="4ce66-127">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="4ce66-128">Soubor, který obsahuje symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="4ce66-128">A file that contains debug symbols.</span></span> <span data-ttu-id="4ce66-129">Nemusíte tento soubor nasazovat společně s vaší aplikací, i když byste ho měli uložit v události, kterou potřebujete k ladění publikované verze vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="4ce66-129">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="4ce66-130">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="4ce66-130">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="4ce66-131">Konfigurační soubor modulu runtime aplikace</span><span class="sxs-lookup"><span data-stu-id="4ce66-131">The application's runtime configuration file.</span></span> <span data-ttu-id="4ce66-132">Identifikuje verzi .NET Core, na které byla aplikace sestavena.</span><span class="sxs-lookup"><span data-stu-id="4ce66-132">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="4ce66-133">Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="4ce66-133">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>  

   ![Okno konzoly zobrazující publikované soubory](media/publishing-with-visual-studio/published-files-output.png)

<span data-ttu-id="4ce66-135">Proces publikování vytvoří nasazení závislé na rozhraní, což je typ nasazení, ve kterém bude publikována aplikace na libovolné platformě podporované rozhraním .NET Core s nainstalovaným rozhraním .NET Core v systému.</span><span class="sxs-lookup"><span data-stu-id="4ce66-135">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application will run on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="4ce66-136">Uživatelé můžou aplikaci spustit vyvoláním `dotnet HelloWorld.dll` příkazu z okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="4ce66-136">Users can run your application by issuing the `dotnet HelloWorld.dll` command from a console window.</span></span>

<span data-ttu-id="4ce66-137">Další informace o publikování a nasazování aplikací .NET Core najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="4ce66-137">For more information on publishing and deploying .NET Core applications, see [.NET Core Application Deployment](../deploying/index.md).</span></span>
