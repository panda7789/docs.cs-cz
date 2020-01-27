---
title: Publikování aplikace Hello World .NET Core pomocí sady Visual Studio
description: Publikování vytvoří sadu souborů, které jsou nutné ke spuštění aplikace .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: a82934fd2ea9568681a3bec82c3b15513decc926
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741562"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a><span data-ttu-id="a8c64-103">Publikování aplikace Hello World .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a8c64-103">Publish your .NET Core Hello World application with Visual Studio</span></span>

<span data-ttu-id="a8c64-104">V části [vytvoření Hello World aplikace pomocí .NET Core v aplikaci Visual Studio](with-visual-studio.md)jste vytvořili konzolovou aplikaci Hello World.</span><span class="sxs-lookup"><span data-stu-id="a8c64-104">In [Create a Hello World application with .NET Core in Visual Studio](with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="a8c64-105">V části [ladění aplikace Hello World pomocí aplikace Visual Studio](debugging-with-visual-studio.md)jste otestovali pomocí ladicího programu sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a8c64-105">In [Debug your Hello World application with Visual Studio](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="a8c64-106">Teď, když jste si jisti, že funguje podle očekávání, můžete ji publikovat, aby ji ostatní uživatelé mohli spustit.</span><span class="sxs-lookup"><span data-stu-id="a8c64-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="a8c64-107">Publikování vytvoří sadu souborů, které jsou nutné ke spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8c64-107">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="a8c64-108">Chcete-li nasadit soubory, zkopírujte je do cílového počítače.</span><span class="sxs-lookup"><span data-stu-id="a8c64-108">To deploy the files, copy them to the target machine.</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="a8c64-109">Publikování aplikace</span><span class="sxs-lookup"><span data-stu-id="a8c64-109">Publish the app</span></span>

1. <span data-ttu-id="a8c64-110">Ujistěte se, že Visual Studio sestavuje prodejní verzi vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8c64-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="a8c64-111">V případě potřeby změňte nastavení konfigurace sestavení na panelu nástrojů z části **ladit** na **verzi**.</span><span class="sxs-lookup"><span data-stu-id="a8c64-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Panel nástrojů sady Visual Studio s vybraným sestavením pro vydání](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="a8c64-113">Klikněte pravým tlačítkem na projekt **HelloWorld** (ne na řešení HelloWorld) a v nabídce vyberte **publikovat** .</span><span class="sxs-lookup"><span data-stu-id="a8c64-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="a8c64-114">(Můžete také vybrat **publikovat HelloWorld** z hlavní nabídky **sestavení** .)</span><span class="sxs-lookup"><span data-stu-id="a8c64-114">(You can also select **Publish HelloWorld** from the main **Build** menu.)</span></span>

   ![Místní nabídka publikování Visual studia](media/publishing-with-visual-studio/publish-context-menu.png)
   
1. <span data-ttu-id="a8c64-116">Na stránce **Vyberte cíl publikování** vyberte **Složka**a pak vyberte **vytvořit profil**.</span><span class="sxs-lookup"><span data-stu-id="a8c64-116">On the **Pick a publish target** page, select **Folder**, and then select **Create Profile**.</span></span>

   ![Výběr cíle publikování v aplikaci Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)
   
1. <span data-ttu-id="a8c64-118">Na stránce **publikovat** vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="a8c64-118">On the **Publish** page, select **Publish**.</span></span>

   ![Okno pro publikování v aplikaci Visual Studio](media/publishing-with-visual-studio/publish-page.png)
   
## <a name="inspect-the-files"></a><span data-ttu-id="a8c64-120">Kontrola souborů</span><span class="sxs-lookup"><span data-stu-id="a8c64-120">Inspect the files</span></span>

<span data-ttu-id="a8c64-121">Proces publikování vytvoří nasazení závislé na rozhraní, což je typ nasazení, ve kterém je publikovaná aplikace spuštěna na libovolné platformě podporované rozhraním .NET Core s nainstalovaným rozhraním .NET Core v systému.</span><span class="sxs-lookup"><span data-stu-id="a8c64-121">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="a8c64-122">Uživatelé můžou publikovanou aplikaci spustit dvojitým kliknutím na spustitelný soubor nebo vyvoláním příkazu `dotnet HelloWorld.dll` z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a8c64-122">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="a8c64-123">V následujících krocích se podíváte na soubory vytvořené procesem publikování.</span><span class="sxs-lookup"><span data-stu-id="a8c64-123">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="a8c64-124">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="a8c64-124">Open a command prompt.</span></span>

   <span data-ttu-id="a8c64-125">Jedním ze způsobů, jak otevřít příkazový řádek, je zadat **příkazový řádek** (nebo program **cmd** pro krátké) do vyhledávacího pole na hlavním panelu Windows.</span><span class="sxs-lookup"><span data-stu-id="a8c64-125">One way to open a command prompt is to enter **Command Prompt** (or **cmd** for short) in the search box on the Windows taskbar.</span></span> <span data-ttu-id="a8c64-126">Vyberte desktopovou aplikaci na **příkazovém řádku** nebo stiskněte klávesu **ENTER** , pokud už je ve výsledcích hledání vybraná.</span><span class="sxs-lookup"><span data-stu-id="a8c64-126">Select the **Command Prompt** desktop app, or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="a8c64-127">Přejděte k publikované aplikaci v podadresáři *bin\Release\netcoreapp3.1\publish* adresáře projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8c64-127">Navigate to the published application in the *bin\Release\netcoreapp3.1\publish* subdirectory of the application's project directory.</span></span>

   ![Okno konzoly zobrazující publikované soubory](media/publishing-with-visual-studio/published-files-output.png)

   <span data-ttu-id="a8c64-129">Jak ukazuje obrázek, publikovaný výstup obsahuje následující soubory:</span><span class="sxs-lookup"><span data-stu-id="a8c64-129">As the image shows, the published output includes the following files:</span></span>

      * <span data-ttu-id="a8c64-130">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="a8c64-130">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="a8c64-131">Toto je soubor závislostí modulu runtime aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8c64-131">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="a8c64-132">Definuje komponenty .NET Core a knihovny (včetně knihovny DLL, která obsahuje vaši aplikaci) potřebnou ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8c64-132">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="a8c64-133">Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="a8c64-133">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

      * <span data-ttu-id="a8c64-134">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="a8c64-134">*HelloWorld.dll*</span></span>

         <span data-ttu-id="a8c64-135">Toto je verze [nasazení závislá na rozhraní](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8c64-135">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="a8c64-136">Chcete-li spustit tuto dynamickou knihovnu, zadejte `dotnet HelloWorld.dll` do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a8c64-136">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span>

      * <span data-ttu-id="a8c64-137">*Soubor HelloWorld. exe*</span><span class="sxs-lookup"><span data-stu-id="a8c64-137">*HelloWorld.exe*</span></span>
      
         <span data-ttu-id="a8c64-138">Toto je [spustitelná](../deploying/deploy-with-cli.md#framework-dependent-executable) verze aplikace závislá na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a8c64-138">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="a8c64-139">Pokud ho chcete spustit, zadejte `HelloWorld.exe` do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a8c64-139">To run it, enter `HelloWorld.exe` at a command prompt.</span></span>

      * <span data-ttu-id="a8c64-140">*HelloWorld. pdb* (volitelné pro nasazení)</span><span class="sxs-lookup"><span data-stu-id="a8c64-140">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="a8c64-141">Toto je soubor se symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="a8c64-141">This is the debug symbols file.</span></span> <span data-ttu-id="a8c64-142">Nemusíte tento soubor nasazovat společně s vaší aplikací, i když byste ho měli uložit v události, kterou potřebujete k ladění publikované verze vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8c64-142">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="a8c64-143">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="a8c64-143">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="a8c64-144">Toto je konfigurační soubor modulu runtime aplikace.</span><span class="sxs-lookup"><span data-stu-id="a8c64-144">This is the application's run-time configuration file.</span></span> <span data-ttu-id="a8c64-145">Identifikuje verzi .NET Core, na které byla aplikace sestavena.</span><span class="sxs-lookup"><span data-stu-id="a8c64-145">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="a8c64-146">Můžete také přidat možnosti konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a8c64-146">You can also add configuration options to it.</span></span> <span data-ttu-id="a8c64-147">Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="a8c64-147">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a8c64-148">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="a8c64-148">Additional resources</span></span>

- [<span data-ttu-id="a8c64-149">Nasazení aplikace .NET core</span><span class="sxs-lookup"><span data-stu-id="a8c64-149">.NET Core application deployment</span></span>](../deploying/index.md)
