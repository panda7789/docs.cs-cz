---
title: Publikování aplikace .NET Core Hello World pomocí sady Visual Studio
description: Publikování vytvoří sadu souborů, které jsou potřebné ke spuštění aplikace .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bdd6e28713bdece2bd144e6763bd84d719e91449
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156631"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a><span data-ttu-id="0e437-103">Publikování aplikace .NET Core Hello World pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0e437-103">Publish your .NET Core Hello World application with Visual Studio</span></span>

<span data-ttu-id="0e437-104">V [při vytváření aplikace Hello World s rozhraním .NET Core v sadě Visual Studio](with-visual-studio.md)jste vytvořili konzolovou aplikaci Hello World.</span><span class="sxs-lookup"><span data-stu-id="0e437-104">In [Create a Hello World application with .NET Core in Visual Studio](with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="0e437-105">V [ladění aplikace Hello World s Visual Studio](debugging-with-visual-studio.md), jste testovali pomocí ladicího programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0e437-105">In [Debug your Hello World application with Visual Studio](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="0e437-106">Nyní, když jste si jisti, že funguje podle očekávání, můžete publikovat tak, aby ostatní uživatelé mohli spustit.</span><span class="sxs-lookup"><span data-stu-id="0e437-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="0e437-107">Publikování vytvoří sadu souborů, které jsou potřebné ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e437-107">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="0e437-108">Chcete-li nasadit soubory, zkopírujte je do cílového počítače.</span><span class="sxs-lookup"><span data-stu-id="0e437-108">To deploy the files, copy them to the target machine.</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="0e437-109">Publikování aplikace</span><span class="sxs-lookup"><span data-stu-id="0e437-109">Publish the app</span></span>

1. <span data-ttu-id="0e437-110">Ujistěte se, že Visual Studio vytváří verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e437-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="0e437-111">V případě potřeby změňte nastavení konfigurace sestavení na panelu nástrojů z **Ladění** na **Uvolnit**.</span><span class="sxs-lookup"><span data-stu-id="0e437-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Panel nástrojů sady Visual Studio s vybranou verzí](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="0e437-113">Klikněte pravým tlačítkem myši na projekt **HelloWorld** (ne na řešení HelloWorld) a z nabídky vyberte **Publikovat.**</span><span class="sxs-lookup"><span data-stu-id="0e437-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="0e437-114">(Můžete také vybrat **Publikovat HelloWorld** z hlavní nabídky **sestavení.)**</span><span class="sxs-lookup"><span data-stu-id="0e437-114">(You can also select **Publish HelloWorld** from the main **Build** menu.)</span></span>

   ![Kontextová nabídka Publikování v sadě Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="0e437-116">Na stránce **Vybrat cílovou** publikování vyberte **Složku**a pak **vyberte Vytvořit profil**.</span><span class="sxs-lookup"><span data-stu-id="0e437-116">On the **Pick a publish target** page, select **Folder**, and then select **Create Profile**.</span></span>

   ![Výběr cíle publikování v Sadě Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="0e437-118">Na stránce **Publikovat** vyberte **Publikovat**.</span><span class="sxs-lookup"><span data-stu-id="0e437-118">On the **Publish** page, select **Publish**.</span></span>

   ![Okno Publikování v sadě Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="0e437-120">Kontrola souborů</span><span class="sxs-lookup"><span data-stu-id="0e437-120">Inspect the files</span></span>

<span data-ttu-id="0e437-121">Proces publikování vytvoří nasazení závislé na rozhraní, což je typ nasazení, kde publikovaná aplikace běží na libovolné platformě podporované rozhraním .NET Core s rozhraním .NET Core nainstalovaným v systému.</span><span class="sxs-lookup"><span data-stu-id="0e437-121">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="0e437-122">Uživatelé mohou publikovanou aplikaci spustit poklepáním na `dotnet HelloWorld.dll` spustitelný soubor nebo vydáním příkazu z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0e437-122">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="0e437-123">V následujících krocích se podíváte na soubory vytvořené procesem publikování.</span><span class="sxs-lookup"><span data-stu-id="0e437-123">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="0e437-124">Otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="0e437-124">Open a command prompt.</span></span>

   <span data-ttu-id="0e437-125">Jedním ze způsobů, jak otevřít příkazový řádek, je zadat **příkazový řádek** (nebo **zkráceně cmd)** do vyhledávacího pole na hlavním panelu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0e437-125">One way to open a command prompt is to enter **Command Prompt** (or **cmd** for short) in the search box on the Windows taskbar.</span></span> <span data-ttu-id="0e437-126">Vyberte aplikaci **Command Prompt** desktop nebo stiskněte **Enter,** pokud už je ve výsledcích hledání vybraná.</span><span class="sxs-lookup"><span data-stu-id="0e437-126">Select the **Command Prompt** desktop app, or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="0e437-127">Přejděte do publikované aplikace v *přihrádce\Release\netcoreapp3.1\publikovat* podadresář adresáře projektu aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e437-127">Navigate to the published application in the *bin\Release\netcoreapp3.1\publish* subdirectory of the application's project directory.</span></span>

   ![Okno konzoly zobrazující publikované soubory](media/publishing-with-visual-studio/published-files-output.png)

   <span data-ttu-id="0e437-129">Jak ukazuje obrázek, publikovaný výstup obsahuje následující soubory:</span><span class="sxs-lookup"><span data-stu-id="0e437-129">As the image shows, the published output includes the following files:</span></span>

      * <span data-ttu-id="0e437-130">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="0e437-130">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="0e437-131">Toto je soubor závislostí runtime aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e437-131">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="0e437-132">Definuje součásti .NET Core a knihovny (včetně knihovny dynamických odkazů, která obsahuje vaši aplikaci) potřebné ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e437-132">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="0e437-133">Další informace naleznete v [tématu Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="0e437-133">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

      * <span data-ttu-id="0e437-134">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="0e437-134">*HelloWorld.dll*</span></span>

         <span data-ttu-id="0e437-135">Toto je [verze nasazení závislé na rámci](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e437-135">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="0e437-136">Chcete-li spustit tuto `dotnet HelloWorld.dll` dynamickou knihovnu odkazů, zadejte na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="0e437-136">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span>

      * <span data-ttu-id="0e437-137">*HelloWorld.exe*</span><span class="sxs-lookup"><span data-stu-id="0e437-137">*HelloWorld.exe*</span></span>

         <span data-ttu-id="0e437-138">Toto je spustitelná verze aplikace [závislá na rozhraní.](../deploying/deploy-with-cli.md#framework-dependent-executable)</span><span class="sxs-lookup"><span data-stu-id="0e437-138">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="0e437-139">Chcete-li jej `HelloWorld.exe` spustit, zadejte příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="0e437-139">To run it, enter `HelloWorld.exe` at a command prompt.</span></span>

      * <span data-ttu-id="0e437-140">*HelloWorld.pdb* (volitelné pro nasazení)</span><span class="sxs-lookup"><span data-stu-id="0e437-140">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="0e437-141">Toto je soubor ladicí symboly.</span><span class="sxs-lookup"><span data-stu-id="0e437-141">This is the debug symbols file.</span></span> <span data-ttu-id="0e437-142">Není nutné nasadit tento soubor spolu s vaší aplikací, i když byste měli uložit v případě, že budete muset ladit publikovanou verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e437-142">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="0e437-143">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="0e437-143">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="0e437-144">Toto je konfigurační soubor aplikace za běhu.</span><span class="sxs-lookup"><span data-stu-id="0e437-144">This is the application's run-time configuration file.</span></span> <span data-ttu-id="0e437-145">Identifikuje verzi .NET Core, na které byla vaše aplikace vytvořena.</span><span class="sxs-lookup"><span data-stu-id="0e437-145">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="0e437-146">Můžete také přidat možnosti konfigurace.</span><span class="sxs-lookup"><span data-stu-id="0e437-146">You can also add configuration options to it.</span></span> <span data-ttu-id="0e437-147">Další informace naleznete v [tématu Nastavení konfigurace rozhraní .NET Core run-time](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="0e437-147">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0e437-148">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="0e437-148">Additional resources</span></span>

- [<span data-ttu-id="0e437-149">Nasazení aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="0e437-149">.NET Core application deployment</span></span>](../deploying/index.md)
