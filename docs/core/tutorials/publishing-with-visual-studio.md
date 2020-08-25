---
title: Publikování konzolové aplikace .NET Core pomocí sady Visual Studio
description: Publikování vytvoří sadu souborů, které jsou nutné ke spuštění aplikace .NET Core.
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: afbffa5dc8a620836ec1433a095face46c32df90
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811312"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="952a6-103">Kurz: publikování konzolové aplikace .NET Core pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="952a6-103">Tutorial: Publish a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="952a6-104">V tomto kurzu se dozvíte, jak publikovat konzolovou aplikaci, aby ji ostatní uživatelé mohli spustit.</span><span class="sxs-lookup"><span data-stu-id="952a6-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="952a6-105">Publikování vytvoří sadu souborů, které jsou nutné ke spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="952a6-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="952a6-106">Chcete-li nasadit soubory, zkopírujte je do cílového počítače.</span><span class="sxs-lookup"><span data-stu-id="952a6-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="952a6-107">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="952a6-107">Prerequisites</span></span>

- <span data-ttu-id="952a6-108">Tento kurz spolupracuje s konzolovou aplikací, kterou vytvoříte v části [Vytvoření konzolové aplikace .NET Core v sadě Visual Studio 2019](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="952a6-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="952a6-109">Publikování aplikace</span><span class="sxs-lookup"><span data-stu-id="952a6-109">Publish the app</span></span>

1. <span data-ttu-id="952a6-110">Spusťte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="952a6-110">Start Visual Studio.</span></span>

1. <span data-ttu-id="952a6-111">Otevřete projekt *HelloWorld* , který jste vytvořili v [části Vytvoření konzolové aplikace .NET Core v aplikaci Visual Studio](with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="952a6-111">Open the *HelloWorld* project that you created in [Create a .NET Core console application in Visual Studio](with-visual-studio.md).</span></span>

1. <span data-ttu-id="952a6-112">Ujistěte se, že aplikace Visual Studio používá konfiguraci sestavení pro vydání.</span><span class="sxs-lookup"><span data-stu-id="952a6-112">Make sure that Visual Studio is using the Release build configuration.</span></span> <span data-ttu-id="952a6-113">V případě potřeby změňte nastavení konfigurace sestavení na panelu nástrojů z části **ladit** na **verzi**.</span><span class="sxs-lookup"><span data-stu-id="952a6-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Panel nástrojů sady Visual Studio s vybraným sestavením pro vydání](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="952a6-115">Klikněte pravým tlačítkem na projekt **HelloWorld** (ne na řešení HelloWorld) a v nabídce vyberte **publikovat** .</span><span class="sxs-lookup"><span data-stu-id="952a6-115">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span>

   ![Místní nabídka publikování Visual studia](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="952a6-117">Na kartě **cíl** stránky **publikování** vyberte možnost **Složka**a potom vyberte možnost **Další**.</span><span class="sxs-lookup"><span data-stu-id="952a6-117">On the **Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   ![Výběr cíle publikování v aplikaci Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="952a6-119">Na kartě **umístění** stránky **publikovat** vyberte **Dokončit**.</span><span class="sxs-lookup"><span data-stu-id="952a6-119">On the **Location** tab of the **Publish** page, select **Finish**.</span></span>

   ![Karta umístění stránky pro publikování v aplikaci Visual Studio](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. <span data-ttu-id="952a6-121">Na kartě **publikovat** okna **publikovat** vyberte **publikovat**.</span><span class="sxs-lookup"><span data-stu-id="952a6-121">On the **Publish** tab of the **Publish** window, select **Publish**.</span></span>

   ![Okno pro publikování v aplikaci Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="952a6-123">Kontrola souborů</span><span class="sxs-lookup"><span data-stu-id="952a6-123">Inspect the files</span></span>

<span data-ttu-id="952a6-124">Ve výchozím nastavení vytvoří proces publikování nasazení závislé na rozhraní, což je typ nasazení, ve kterém je publikovaná aplikace spuštěna na počítači s nainstalovaným modulem runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="952a6-124">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="952a6-125">Uživatelé můžou publikovanou aplikaci spustit dvojitým kliknutím na spustitelný soubor nebo vyvoláním `dotnet HelloWorld.dll` příkazu z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="952a6-125">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="952a6-126">V následujících krocích se podíváte na soubory vytvořené procesem publikování.</span><span class="sxs-lookup"><span data-stu-id="952a6-126">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="952a6-127">V **Průzkumník řešení**vyberte možnost **Zobrazit všechny soubory**.</span><span class="sxs-lookup"><span data-stu-id="952a6-127">In **Solution Explorer**, select **Show all files**.</span></span>

1. <span data-ttu-id="952a6-128">Ve složce projektu rozbalte *přihrádku/Release/netcoreapp 3.1/Publish*.</span><span class="sxs-lookup"><span data-stu-id="952a6-128">In the project folder, expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Průzkumník řešení zobrazení publikovaných souborů":::

   <span data-ttu-id="952a6-130">Jak ukazuje obrázek, publikovaný výstup obsahuje následující soubory:</span><span class="sxs-lookup"><span data-stu-id="952a6-130">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="952a6-131">*HelloWorld.deps.jsna*</span><span class="sxs-lookup"><span data-stu-id="952a6-131">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="952a6-132">Toto je soubor závislostí modulu runtime aplikace.</span><span class="sxs-lookup"><span data-stu-id="952a6-132">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="952a6-133">Definuje komponenty .NET Core a knihovny (včetně knihovny DLL, která obsahuje vaši aplikaci) potřebnou ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="952a6-133">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="952a6-134">Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="952a6-134">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="952a6-135">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="952a6-135">*HelloWorld.dll*</span></span>

      <span data-ttu-id="952a6-136">Toto je verze [nasazení závislá na rozhraní](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikace.</span><span class="sxs-lookup"><span data-stu-id="952a6-136">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="952a6-137">Chcete-li spustit tuto dynamickou knihovnu, zadejte `dotnet HelloWorld.dll` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="952a6-137">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="952a6-138">Tato metoda spuštění aplikace funguje na libovolné platformě, na které je nainstalovaný modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="952a6-138">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="952a6-139">*HelloWorld.exe*</span><span class="sxs-lookup"><span data-stu-id="952a6-139">*HelloWorld.exe*</span></span>

      <span data-ttu-id="952a6-140">Toto je [spustitelná](../deploying/deploy-with-cli.md#framework-dependent-executable) verze aplikace závislá na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="952a6-140">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="952a6-141">Pokud ho chcete spustit, zadejte `HelloWorld.exe` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="952a6-141">To run it, enter `HelloWorld.exe` at a command prompt.</span></span> <span data-ttu-id="952a6-142">Soubor je specifický pro operační systém.</span><span class="sxs-lookup"><span data-stu-id="952a6-142">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="952a6-143">*HelloWorld. pdb* (volitelné pro nasazení)</span><span class="sxs-lookup"><span data-stu-id="952a6-143">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="952a6-144">Toto je soubor se symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="952a6-144">This is the debug symbols file.</span></span> <span data-ttu-id="952a6-145">Nemusíte tento soubor nasazovat společně s vaší aplikací, i když byste ho měli uložit v události, kterou potřebujete k ladění publikované verze vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="952a6-145">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="952a6-146">*HelloWorld.runtimeconfig.jsna*</span><span class="sxs-lookup"><span data-stu-id="952a6-146">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="952a6-147">Toto je konfigurační soubor modulu runtime aplikace.</span><span class="sxs-lookup"><span data-stu-id="952a6-147">This is the application's run-time configuration file.</span></span> <span data-ttu-id="952a6-148">Identifikuje verzi .NET Core, na které byla aplikace sestavena.</span><span class="sxs-lookup"><span data-stu-id="952a6-148">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="952a6-149">Můžete také přidat možnosti konfigurace.</span><span class="sxs-lookup"><span data-stu-id="952a6-149">You can also add configuration options to it.</span></span> <span data-ttu-id="952a6-150">Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="952a6-150">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="952a6-151">Spuštění publikované aplikace</span><span class="sxs-lookup"><span data-stu-id="952a6-151">Run the published app</span></span>

1. <span data-ttu-id="952a6-152">V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku pro *publikování* a vyberte možnost **Kopírovat úplnou cestu**.</span><span class="sxs-lookup"><span data-stu-id="952a6-152">In **Solution Explorer**, right-click the *publish* folder, and select **Copy Full Path**.</span></span>

1. <span data-ttu-id="952a6-153">Otevřete příkazový řádek a přejděte do složky pro *publikování* .</span><span class="sxs-lookup"><span data-stu-id="952a6-153">Open a command prompt and navigate to the *publish* folder.</span></span> <span data-ttu-id="952a6-154">Provedete to tak, že zadáte `cd` a pak vložíte úplnou cestu.</span><span class="sxs-lookup"><span data-stu-id="952a6-154">To do that, enter `cd` and then paste the full path.</span></span> <span data-ttu-id="952a6-155">Příklad:</span><span class="sxs-lookup"><span data-stu-id="952a6-155">For example:</span></span>

   ```console
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. <span data-ttu-id="952a6-156">Spusťte aplikaci pomocí spustitelného souboru:</span><span class="sxs-lookup"><span data-stu-id="952a6-156">Run the app by using the executable:</span></span>

   1. <span data-ttu-id="952a6-157">Zadejte `HelloWorld.exe` a stiskněte klávesu <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="952a6-157">Enter `HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="952a6-158">Do příkazového řádku zadejte název a stiskněte libovolnou klávesu pro ukončení.</span><span class="sxs-lookup"><span data-stu-id="952a6-158">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="952a6-159">Spusťte aplikaci pomocí `dotnet` příkazu:</span><span class="sxs-lookup"><span data-stu-id="952a6-159">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="952a6-160">Zadejte `dotnet HelloWorld.dll` a stiskněte klávesu <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="952a6-160">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="952a6-161">Do příkazového řádku zadejte název a stiskněte libovolnou klávesu pro ukončení.</span><span class="sxs-lookup"><span data-stu-id="952a6-161">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="952a6-162">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="952a6-162">Additional resources</span></span>

- [<span data-ttu-id="952a6-163">Nasazení aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="952a6-163">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="952a6-164">Další kroky</span><span class="sxs-lookup"><span data-stu-id="952a6-164">Next steps</span></span>

<span data-ttu-id="952a6-165">V tomto kurzu jste publikovali konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="952a6-165">In this tutorial, you published a console app.</span></span> <span data-ttu-id="952a6-166">V dalším kurzu vytvoříte knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="952a6-166">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="952a6-167">Vytvoření knihovny .NET Standard v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="952a6-167">Create a .NET Standard library in Visual Studio</span></span>](library-with-visual-studio.md)
