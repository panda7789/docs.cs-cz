---
title: 'Kurz: instalace a použití globálního nástroje .NET Core'
description: Naučte se instalovat a používat nástroj .NET jako globální nástroj.
ms.date: 02/12/2020
ms.openlocfilehash: 65047af9d8a7f2fd4c1a07f65af3a6ddbf870c5d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543871"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="05b01-103">Kurz: instalace a použití globálního nástroje .NET Core pomocí .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="05b01-103">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>

<span data-ttu-id="05b01-104">**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="05b01-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="05b01-105">V tomto kurzu se naučíte, jak nainstalovat a používat globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="05b01-105">This tutorial teaches you how to install and use a global tool.</span></span> <span data-ttu-id="05b01-106">Použijete nástroj, který vytvoříte v [prvním kurzu této série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="05b01-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="05b01-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05b01-107">Prerequisites</span></span>

* <span data-ttu-id="05b01-108">Dokončete [první kurz této série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="05b01-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="use-the-tool-as-a-global-tool"></a><span data-ttu-id="05b01-109">Použití nástroje jako globálního nástroje</span><span class="sxs-lookup"><span data-stu-id="05b01-109">Use the tool as a global tool</span></span>

1. <span data-ttu-id="05b01-110">Nainstalujte nástroj z balíčku spuštěním příkazu pro [instalaci nástroje dotnet](dotnet-tool-install.md) ve složce *botsay-\<název >* projektu:</span><span class="sxs-lookup"><span data-stu-id="05b01-110">Install the tool from the package by running the [dotnet tool install](dotnet-tool-install.md) command in the *botsay-\<name>* project folder:</span></span>

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="05b01-111">Parametr `--global` přikáže .NET Core CLI k instalaci binárních souborů nástroje ve výchozím umístění, které je automaticky přidáno do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="05b01-111">The `--global` parameter tells the .NET Core CLI to install the tool binaries in a default location that is automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="05b01-112">Parametr `--add-source` instruuje .NET Core CLI, aby dočasně používal adresář *./nupkg* jako další zdrojový kanál pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="05b01-112">The `--add-source` parameter tells the .NET Core CLI to temporarily use the *./nupkg* directory as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="05b01-113">Váš balíček jste přiřadili k jedinečnému názvu, abyste se ujistili, že bude nalezen pouze v adresáři *./nupkg* , nikoli na webu NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="05b01-113">You gave your package a unique name to make sure that it will only be found in the *./nupkg* directory, not on the Nuget.org site.</span></span> 

   <span data-ttu-id="05b01-114">Výstup ukazuje příkaz použitý pro volání nástroje a nainstalovanou verzi:</span><span class="sxs-lookup"><span data-stu-id="05b01-114">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="05b01-115">Vyvolat nástroj:</span><span class="sxs-lookup"><span data-stu-id="05b01-115">Invoke the tool:</span></span>

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > <span data-ttu-id="05b01-116">Pokud se tento příkaz nepovede, možná budete muset otevřít nový terminál, aby se cesta aktualizovala.</span><span class="sxs-lookup"><span data-stu-id="05b01-116">If this command fails, you may need to open a new terminal to refresh the PATH.</span></span>

1. <span data-ttu-id="05b01-117">Odeberte nástroj spuštěním příkazu pro [odinstalaci nástroje dotnet](dotnet-tool-uninstall.md) :</span><span class="sxs-lookup"><span data-stu-id="05b01-117">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   ```dotnetcli
   dotnet tool uninstall -g botsay-<name>
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a><span data-ttu-id="05b01-118">Použití nástroje jako globálního nástroje nainstalovaného ve vlastním umístění</span><span class="sxs-lookup"><span data-stu-id="05b01-118">Use the tool as a global tool installed in a custom location</span></span>

1. <span data-ttu-id="05b01-119">Nainstalujte nástroj z balíčku.</span><span class="sxs-lookup"><span data-stu-id="05b01-119">Install the tool from the package.</span></span>

   <span data-ttu-id="05b01-120">Ve Windows:</span><span class="sxs-lookup"><span data-stu-id="05b01-120">On Windows:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="05b01-121">V systému Linux nebo macOS:</span><span class="sxs-lookup"><span data-stu-id="05b01-121">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="05b01-122">Parametr `--tool-path` oznamuje .NET Core CLI instalaci binárních souborů nástroje v zadaném umístění.</span><span class="sxs-lookup"><span data-stu-id="05b01-122">The `--tool-path` parameter tells the .NET Core CLI to install the tool binaries in the specified location.</span></span> <span data-ttu-id="05b01-123">Pokud adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="05b01-123">If the directory doesn't exist, it is created.</span></span> <span data-ttu-id="05b01-124">Tento adresář není automaticky přidán do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="05b01-124">This directory is not automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="05b01-125">Výstup ukazuje příkaz použitý pro volání nástroje a nainstalovanou verzi:</span><span class="sxs-lookup"><span data-stu-id="05b01-125">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="05b01-126">Vyvolat nástroj:</span><span class="sxs-lookup"><span data-stu-id="05b01-126">Invoke the tool:</span></span>

   <span data-ttu-id="05b01-127">Ve Windows:</span><span class="sxs-lookup"><span data-stu-id="05b01-127">On Windows:</span></span>

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   <span data-ttu-id="05b01-128">V systému Linux nebo macOS:</span><span class="sxs-lookup"><span data-stu-id="05b01-128">On Linux or macOS:</span></span>

   ```console
   ~/bin/botsay hello from the bot
   ```

1. <span data-ttu-id="05b01-129">Odeberte nástroj spuštěním příkazu pro [odinstalaci nástroje dotnet](dotnet-tool-uninstall.md) :</span><span class="sxs-lookup"><span data-stu-id="05b01-129">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   <span data-ttu-id="05b01-130">Ve Windows:</span><span class="sxs-lookup"><span data-stu-id="05b01-130">On Windows:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools botsay --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="05b01-131">V systému Linux nebo macOS:</span><span class="sxs-lookup"><span data-stu-id="05b01-131">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin botsay-<name>
   ```

## <a name="troubleshoot"></a><span data-ttu-id="05b01-132">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="05b01-132">Troubleshoot</span></span>

<span data-ttu-id="05b01-133">Pokud se vám zobrazí chybová zpráva s postupem v tomto kurzu, přečtěte si téma [řešení potíží s používáním nástrojů .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="05b01-133">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="05b01-134">Další kroky</span><span class="sxs-lookup"><span data-stu-id="05b01-134">Next steps</span></span>

<span data-ttu-id="05b01-135">V tomto kurzu jste nainstalovali a použili nástroj jako globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="05b01-135">In this tutorial, you installed and used a tool as a global tool.</span></span> <span data-ttu-id="05b01-136">Pokud chcete nainstalovat a používat stejný nástroj jako místní nástroj, přejděte k dalšímu kurzu.</span><span class="sxs-lookup"><span data-stu-id="05b01-136">To install and use the same tool as a local tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="05b01-137">Instalace a použití místních nástrojů</span><span class="sxs-lookup"><span data-stu-id="05b01-137">Install and use local tools</span></span>](local-tools-how-to-use.md)
