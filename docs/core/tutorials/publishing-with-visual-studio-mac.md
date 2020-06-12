---
title: Publikování konzolové aplikace .NET Core pomocí Visual Studio pro Mac
description: Publikování vytvoří sadu souborů, které jsou nutné ke spuštění aplikace .NET Core.
ms.date: 06/08/2020
ms.openlocfilehash: 67762481d3a56b8473e643f71b8df909b6e54fc6
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2020
ms.locfileid: "84713663"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="6ea46-103">Kurz: publikování konzolové aplikace .NET Core pomocí Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="6ea46-103">Tutorial: Publish a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="6ea46-104">V tomto kurzu se dozvíte, jak publikovat konzolovou aplikaci, aby ji ostatní uživatelé mohli spustit.</span><span class="sxs-lookup"><span data-stu-id="6ea46-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="6ea46-105">Publikování vytvoří sadu souborů, které jsou nutné ke spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ea46-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="6ea46-106">Chcete-li nasadit soubory, zkopírujte je do cílového počítače.</span><span class="sxs-lookup"><span data-stu-id="6ea46-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6ea46-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ea46-107">Prerequisites</span></span>

- <span data-ttu-id="6ea46-108">Tento kurz spolupracuje s konzolovou aplikací, kterou vytvoříte v části [Vytvoření konzolové aplikace .NET Core v Visual Studio pro Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="6ea46-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="6ea46-109">Publikování aplikace</span><span class="sxs-lookup"><span data-stu-id="6ea46-109">Publish the app</span></span>

1. <span data-ttu-id="6ea46-110">Spusťte Visual Studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="6ea46-110">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="6ea46-111">Otevřete projekt HelloWorld, který jste vytvořili v [části Vytvoření konzolové aplikace .NET Core v Visual Studio pro Mac](with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="6ea46-111">Open the HelloWorld project that you created in [Create a .NET Core console application in Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="6ea46-112">Ujistěte se, že Visual Studio sestavuje prodejní verzi vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ea46-112">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="6ea46-113">V případě potřeby změňte nastavení konfigurace sestavení na panelu nástrojů z části **ladit** na **verzi**.</span><span class="sxs-lookup"><span data-stu-id="6ea46-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/toolbar-release.png" alt-text="Panel nástrojů sady Visual Studio s vybraným sestavením pro vydání":::

1. <span data-ttu-id="6ea46-115">V hlavní nabídce vyberte **sestavení**  >  **publikovat do složky...**.</span><span class="sxs-lookup"><span data-stu-id="6ea46-115">From the main menu, choose **Build** > **Publish to Folder...**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-context-menu.png" alt-text="Místní nabídka publikování Visual studia":::

1. <span data-ttu-id="6ea46-117">V dialogovém okně **publikovat do složky** vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="6ea46-117">In the **Publish to Folder** dialog, select **Publish**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-to-folder-dialog.png" alt-text="Dialog publikovat do složky v aplikaci Visual Studio":::

   <span data-ttu-id="6ea46-119">Otevře se složka pro publikování zobrazující soubory, které byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="6ea46-119">The publish folder opens, showing the files that were created.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-folder.png" alt-text="Složka pro publikování":::

1. <span data-ttu-id="6ea46-121">Vyberte ikonu ozubeného kolečka a v místní nabídce vyberte **Kopírovat "publikovat" jako cestu** .</span><span class="sxs-lookup"><span data-stu-id="6ea46-121">Select the gear icon, and select **Copy "publish" as Pathname** from the context menu.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/copy-path.png" alt-text="Kopírovat cestu pro složku pro publikování":::

## <a name="inspect-the-files"></a><span data-ttu-id="6ea46-123">Kontrola souborů</span><span class="sxs-lookup"><span data-stu-id="6ea46-123">Inspect the files</span></span>

<span data-ttu-id="6ea46-124">Proces publikování vytvoří nasazení závislé na rozhraní, což je typ nasazení, ve kterém je publikovaná aplikace spuštěna na počítači s nainstalovanou modulem runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ea46-124">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="6ea46-125">Uživatelé mohou spustit publikovanou aplikaci spuštěním `dotnet HelloWorld.dll` příkazu z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="6ea46-125">Users can run the published app by running the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="6ea46-126">Jak ukazuje předchozí obrázek, publikovaný výstup obsahuje následující soubory:</span><span class="sxs-lookup"><span data-stu-id="6ea46-126">As the preceding image shows, the published output includes the following files:</span></span>

* <span data-ttu-id="6ea46-127">*HelloWorld.deps.jsna*</span><span class="sxs-lookup"><span data-stu-id="6ea46-127">*HelloWorld.deps.json*</span></span>

  <span data-ttu-id="6ea46-128">Toto je soubor závislostí modulu runtime aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ea46-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="6ea46-129">Definuje komponenty .NET Core a knihovny (včetně knihovny DLL, která obsahuje vaši aplikaci) potřebnou ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ea46-129">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="6ea46-130">Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="6ea46-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

* <span data-ttu-id="6ea46-131">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="6ea46-131">*HelloWorld.dll*</span></span>

   <span data-ttu-id="6ea46-132">Toto je verze [nasazení závislá na rozhraní](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ea46-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="6ea46-133">Chcete-li spustit tuto dynamickou knihovnu, zadejte `dotnet HelloWorld.dll` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="6ea46-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="6ea46-134">Tato metoda spuštění aplikace funguje na libovolné platformě, na které je nainstalovaný modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ea46-134">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

* <span data-ttu-id="6ea46-135">*HelloWorld. pdb* (volitelné pro nasazení)</span><span class="sxs-lookup"><span data-stu-id="6ea46-135">*HelloWorld.pdb* (optional for deployment)</span></span>

   <span data-ttu-id="6ea46-136">Toto je soubor se symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="6ea46-136">This is the debug symbols file.</span></span> <span data-ttu-id="6ea46-137">Nemusíte tento soubor nasazovat společně s vaší aplikací, i když byste ho měli uložit v události, kterou potřebujete k ladění publikované verze vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ea46-137">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

* <span data-ttu-id="6ea46-138">*HelloWorld.runtimeconfig.jsna*</span><span class="sxs-lookup"><span data-stu-id="6ea46-138">*HelloWorld.runtimeconfig.json*</span></span>

   <span data-ttu-id="6ea46-139">Toto je konfigurační soubor modulu runtime aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ea46-139">This is the application's run-time configuration file.</span></span> <span data-ttu-id="6ea46-140">Identifikuje verzi .NET Core, na které byla aplikace sestavena.</span><span class="sxs-lookup"><span data-stu-id="6ea46-140">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="6ea46-141">Můžete také přidat možnosti konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6ea46-141">You can also add configuration options to it.</span></span> <span data-ttu-id="6ea46-142">Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="6ea46-142">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="6ea46-143">Spuštění publikované aplikace</span><span class="sxs-lookup"><span data-stu-id="6ea46-143">Run the published app</span></span>

1. <span data-ttu-id="6ea46-144">Otevřete terminál a přejděte do složky pro *publikování* .</span><span class="sxs-lookup"><span data-stu-id="6ea46-144">Open a terminal and navigate to the *publish* folder.</span></span> <span data-ttu-id="6ea46-145">Provedete to tak, že zadáte `cd` a pak vložíte cestu, kterou jste zkopírovali dříve.</span><span class="sxs-lookup"><span data-stu-id="6ea46-145">To do that, enter `cd` and then paste the path that you copied earlier.</span></span> <span data-ttu-id="6ea46-146">Například:</span><span class="sxs-lookup"><span data-stu-id="6ea46-146">For example:</span></span>

   ```
   cd ~/Projects/HelloWorld/HelloWorld/bin/Release/netcoreapp3.1/publish/
   ```

1. <span data-ttu-id="6ea46-147">Spusťte aplikaci pomocí `dotnet` příkazu:</span><span class="sxs-lookup"><span data-stu-id="6ea46-147">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="6ea46-148">Zadejte `dotnet HelloWorld.dll` a stiskněte klávesu <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="6ea46-148">Enter `dotnet HelloWorld.dll` and press <kbd>enter</kbd>.</span></span>

   1. <span data-ttu-id="6ea46-149">Do příkazového řádku zadejte název a stiskněte libovolnou klávesu pro ukončení.</span><span class="sxs-lookup"><span data-stu-id="6ea46-149">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6ea46-150">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="6ea46-150">Additional resources</span></span>

- [<span data-ttu-id="6ea46-151">Nasazení aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ea46-151">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="6ea46-152">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6ea46-152">Next steps</span></span>

<span data-ttu-id="6ea46-153">V tomto kurzu jste publikovali konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6ea46-153">In this tutorial, you published a console app.</span></span> <span data-ttu-id="6ea46-154">V dalším kurzu vytvoříte knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="6ea46-154">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6ea46-155">Vytvoření knihovny .NET Standard v aplikaci Visual Studio pro Mac</span><span class="sxs-lookup"><span data-stu-id="6ea46-155">Create a .NET Standard library in Visual Studio for mac</span></span>](library-with-visual-studio-mac.md)
