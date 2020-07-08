---
title: Publikování konzolové aplikace .NET Core pomocí Visual Studio Code
description: Publikování vytvoří sadu souborů, které jsou nutné ke spuštění aplikace .NET Core.
ms.date: 07/04/2020
ms.openlocfilehash: 8fd9975e8a88704b9dea45b40127c8dc03f7d09f
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051880"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="73130-103">Kurz: publikování konzolové aplikace .NET Core pomocí Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="73130-103">Tutorial: Publish a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="73130-104">V tomto kurzu se dozvíte, jak publikovat konzolovou aplikaci, aby ji ostatní uživatelé mohli spustit.</span><span class="sxs-lookup"><span data-stu-id="73130-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="73130-105">Publikování vytvoří sadu souborů, které jsou nutné ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="73130-105">Publishing creates the set of files that are needed to run an application.</span></span> <span data-ttu-id="73130-106">Chcete-li nasadit soubory, zkopírujte je do cílového počítače.</span><span class="sxs-lookup"><span data-stu-id="73130-106">To deploy the files, copy them to the target machine.</span></span>

<span data-ttu-id="73130-107">.NET Core CLI slouží k publikování aplikace, takže můžete postupovat podle tohoto kurzu s jiným editorem kódu, než Visual Studio Code, pokud dáváte přednost.</span><span class="sxs-lookup"><span data-stu-id="73130-107">The .NET Core CLI is used to publish the app, so you can follow this tutorial with a code editor other than Visual Studio Code if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="73130-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73130-108">Prerequisites</span></span>

- <span data-ttu-id="73130-109">Tento kurz spolupracuje s konzolovou aplikací, kterou vytvoříte v části [Vytvoření konzolové aplikace .NET Core v Visual Studio Code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="73130-109">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="73130-110">Publikování aplikace</span><span class="sxs-lookup"><span data-stu-id="73130-110">Publish the app</span></span>

1. <span data-ttu-id="73130-111">Spusťte Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="73130-111">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="73130-112">Otevřete složku projektu *HelloWorld* , kterou jste vytvořili v [části Vytvoření konzolové aplikace .net Core v Visual Studio Code](with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="73130-112">Open the *HelloWorld* project folder that you created in [Create a .NET Core console application in Visual Studio Code](with-visual-studio-code.md).</span></span>

1. <span data-ttu-id="73130-113">V hlavní nabídce vyberte **Zobrazit**  >  **terminál** .</span><span class="sxs-lookup"><span data-stu-id="73130-113">Choose **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="73130-114">Terminál se otevře ve složce *HelloWorld* .</span><span class="sxs-lookup"><span data-stu-id="73130-114">The terminal opens in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="73130-115">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="73130-115">Run the following command:</span></span>

   ```dotnetcli
   dotnet publish --configuration Release
   ```

   <span data-ttu-id="73130-116">Výchozí konfigurace sestavení je *ladění*, takže tento příkaz určuje konfiguraci sestavení pro *vydání* .</span><span class="sxs-lookup"><span data-stu-id="73130-116">The default build configuration is *Debug*, so this command specifies the *Release* build configuration.</span></span> <span data-ttu-id="73130-117">Výstup konfigurace sestavení verze obsahuje minimální symbolické informace o ladění a je plně optimalizován.</span><span class="sxs-lookup"><span data-stu-id="73130-117">The output from the Release build configuration has minimal symbolic debug information and is fully optimized.</span></span>

   <span data-ttu-id="73130-118">Výstup příkazu je podobný následujícímu příkladu:</span><span class="sxs-lookup"><span data-stu-id="73130-118">The command output is similar to the following example:</span></span>

   ```
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

   Determining projects to restore...
   All projects are up-to-date for restore.
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\HelloWorld.dll
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

## <a name="inspect-the-files"></a><span data-ttu-id="73130-119">Kontrola souborů</span><span class="sxs-lookup"><span data-stu-id="73130-119">Inspect the files</span></span>

<span data-ttu-id="73130-120">Ve výchozím nastavení vytvoří proces publikování nasazení závislé na rozhraní, což je typ nasazení, ve kterém je publikovaná aplikace spuštěna na počítači s nainstalovanou modulem runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="73130-120">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="73130-121">Pokud chcete spustit publikovanou aplikaci, můžete použít spustitelný soubor nebo spustit `dotnet HelloWorld.dll` příkaz z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="73130-121">To run the published app you can use the executable file or run the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="73130-122">V následujících krocích se podíváte na soubory vytvořené procesem publikování.</span><span class="sxs-lookup"><span data-stu-id="73130-122">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="73130-123">Vyberte **Průzkumníka** v levém navigačním panelu.</span><span class="sxs-lookup"><span data-stu-id="73130-123">Select the **Explorer** in the left navigation bar.</span></span>

1. <span data-ttu-id="73130-124">Rozbalte položku *Přihrádka/Release/netcoreapp 3.1/Publish*.</span><span class="sxs-lookup"><span data-stu-id="73130-124">Expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/published-files-output.png" alt-text="Průzkumník zobrazující publikované soubory":::

   <span data-ttu-id="73130-126">Jak ukazuje obrázek, publikovaný výstup obsahuje následující soubory:</span><span class="sxs-lookup"><span data-stu-id="73130-126">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="73130-127">*HelloWorld.deps.jsna*</span><span class="sxs-lookup"><span data-stu-id="73130-127">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="73130-128">Toto je soubor závislostí modulu runtime aplikace.</span><span class="sxs-lookup"><span data-stu-id="73130-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="73130-129">Definuje komponenty .NET Core a knihovny (včetně knihovny DLL, která obsahuje vaši aplikaci) potřebnou ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="73130-129">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="73130-130">Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="73130-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="73130-131">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="73130-131">*HelloWorld.dll*</span></span>

      <span data-ttu-id="73130-132">Toto je verze [nasazení závislá na rozhraní](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikace.</span><span class="sxs-lookup"><span data-stu-id="73130-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="73130-133">Chcete-li spustit tuto dynamickou knihovnu, zadejte `dotnet HelloWorld.dll` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="73130-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="73130-134">Tato metoda spuštění aplikace funguje na libovolné platformě, na které je nainstalovaný modul runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="73130-134">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="73130-135">*HelloWorld.exe* (*HelloWorld* v systému Linux, nevytvoří se v MacOS.)</span><span class="sxs-lookup"><span data-stu-id="73130-135">*HelloWorld.exe* (*HelloWorld* on Linux, not created on macOS.)</span></span>

      <span data-ttu-id="73130-136">Toto je [spustitelná](../deploying/deploy-with-cli.md#framework-dependent-executable) verze aplikace závislá na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="73130-136">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="73130-137">Soubor je specifický pro operační systém.</span><span class="sxs-lookup"><span data-stu-id="73130-137">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="73130-138">*HelloWorld. pdb* (volitelné pro nasazení)</span><span class="sxs-lookup"><span data-stu-id="73130-138">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="73130-139">Toto je soubor se symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="73130-139">This is the debug symbols file.</span></span> <span data-ttu-id="73130-140">Nemusíte tento soubor nasazovat společně s vaší aplikací, i když byste ho měli uložit v události, kterou potřebujete k ladění publikované verze vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="73130-140">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="73130-141">*HelloWorld.runtimeconfig.jsna*</span><span class="sxs-lookup"><span data-stu-id="73130-141">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="73130-142">Toto je konfigurační soubor modulu runtime aplikace.</span><span class="sxs-lookup"><span data-stu-id="73130-142">This is the application's run-time configuration file.</span></span> <span data-ttu-id="73130-143">Identifikuje verzi .NET Core, na které byla aplikace sestavena.</span><span class="sxs-lookup"><span data-stu-id="73130-143">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="73130-144">Můžete také přidat možnosti konfigurace.</span><span class="sxs-lookup"><span data-stu-id="73130-144">You can also add configuration options to it.</span></span> <span data-ttu-id="73130-145">Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="73130-145">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="73130-146">Spuštění publikované aplikace</span><span class="sxs-lookup"><span data-stu-id="73130-146">Run the published app</span></span>

1. <span data-ttu-id="73130-147">V **Průzkumníkovi**klikněte pravým tlačítkem na složku pro *publikování* (<kbd>stisknutím klávesy CTRL</kbd>a kliknutím na MacOS) a vyberte **otevřít v terminálu**.</span><span class="sxs-lookup"><span data-stu-id="73130-147">In **Explorer**, right-click the *publish* folder (<kbd>Ctrl</kbd>-click on macOS), and select **Open in Terminal**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/open-in-terminal.png" alt-text="Místní nabídka, která zobrazuje otevření v terminálu":::

1. <span data-ttu-id="73130-149">V systému Windows nebo Linux spusťte aplikaci pomocí spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="73130-149">On Windows or Linux, run the app by using the executable.</span></span>

   1. <span data-ttu-id="73130-150">V systému Windows zadejte `.\HelloWorld.exe` a stiskněte klávesu <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="73130-150">On Windows, enter `.\HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="73130-151">V systému Linux zadejte `./HelloWorld` a stiskněte klávesu <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="73130-151">On Linux, enter `./HelloWorld` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="73130-152">Do příkazového řádku zadejte název a stiskněte libovolnou klávesu pro ukončení.</span><span class="sxs-lookup"><span data-stu-id="73130-152">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="73130-153">Na libovolné platformě spusťte aplikaci pomocí [`dotnet`](../tools/dotnet.md) příkazu:</span><span class="sxs-lookup"><span data-stu-id="73130-153">On any platform, run the app by using the  [`dotnet`](../tools/dotnet.md) command:</span></span>

   1. <span data-ttu-id="73130-154">Zadejte `dotnet HelloWorld.dll` a stiskněte klávesu <kbd>ENTER</kbd>.</span><span class="sxs-lookup"><span data-stu-id="73130-154">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="73130-155">Do příkazového řádku zadejte název a stiskněte libovolnou klávesu pro ukončení.</span><span class="sxs-lookup"><span data-stu-id="73130-155">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="73130-156">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="73130-156">Additional resources</span></span>

- [<span data-ttu-id="73130-157">Nasazení aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="73130-157">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="73130-158">Další kroky</span><span class="sxs-lookup"><span data-stu-id="73130-158">Next steps</span></span>

<span data-ttu-id="73130-159">V tomto kurzu jste publikovali konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="73130-159">In this tutorial, you published a console app.</span></span> <span data-ttu-id="73130-160">V dalším kurzu vytvoříte knihovnu tříd.</span><span class="sxs-lookup"><span data-stu-id="73130-160">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="73130-161">Vytvoření knihovny .NET Standard v Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="73130-161">Create a .NET Standard library in Visual Studio Code</span></span>](library-with-visual-studio-code.md)
