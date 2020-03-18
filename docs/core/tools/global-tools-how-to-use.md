---
title: 'Kurz: Instalace a použití globálního nástroje .NET Core'
description: Přečtěte si, jak nainstalovat a používat nástroj .NET jako globální nástroj.
ms.date: 02/12/2020
ms.openlocfilehash: 9f8378e50fd2544eedbbaaeffb89d67800ec6880
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156735"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="bf461-103">Kurz: Instalace a použití globálního nástroje .NET Core pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="bf461-103">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>

<span data-ttu-id="bf461-104">**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="bf461-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="bf461-105">Tento kurz vás naučí, jak nainstalovat a používat globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="bf461-105">This tutorial teaches you how to install and use a global tool.</span></span> <span data-ttu-id="bf461-106">Nástroj, který vytvoříte v [prvním kurzu této řady](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="bf461-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bf461-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf461-107">Prerequisites</span></span>

* <span data-ttu-id="bf461-108">Dokončete [první kurz této série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="bf461-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="use-the-tool-as-a-global-tool"></a><span data-ttu-id="bf461-109">Použití nástroje jako globálního nástroje</span><span class="sxs-lookup"><span data-stu-id="bf461-109">Use the tool as a global tool</span></span>

1. <span data-ttu-id="bf461-110">Nainstalujte nástroj z balíčku spuštěním příkazu [instalace nástroje dotnet](dotnet-tool-install.md) ve složce projektu *Microsoft.botsay:*</span><span class="sxs-lookup"><span data-stu-id="bf461-110">Install the tool from the package by running the [dotnet tool install](dotnet-tool-install.md) command in the *microsoft.botsay* project folder:</span></span>

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="bf461-111">Parametr `--global` sděluje rozhraní .NET Core CLI k instalaci binárních souborů nástrojů do výchozího umístění, které je automaticky přidáno do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="bf461-111">The `--global` parameter tells the .NET Core CLI to install the tool binaries in a default location that is automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="bf461-112">Parametr `--add-source` říká rozhraní .NET Core CLI dočasně použít adresář *./nupkg* jako další zdrojový zdroj pro balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="bf461-112">The `--add-source` parameter tells the .NET Core CLI to temporarily use the *./nupkg* directory as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="bf461-113">Dali jste svému balíčku jedinečný název, abyste se ujistili, že bude nalezen pouze v adresáři *./nupkg,* nikoli na webu Nuget.org.</span><span class="sxs-lookup"><span data-stu-id="bf461-113">You gave your package a unique name to make sure that it will only be found in the *./nupkg* directory, not on the Nuget.org site.</span></span>

   <span data-ttu-id="bf461-114">Výstup zobrazuje příkaz použitý k volání nástroje a nainstalovanou verzi:</span><span class="sxs-lookup"><span data-stu-id="bf461-114">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="bf461-115">Vyvolat nástroj:</span><span class="sxs-lookup"><span data-stu-id="bf461-115">Invoke the tool:</span></span>

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > <span data-ttu-id="bf461-116">Pokud se tento příkaz nezdaří, bude pravděpodobně nutné otevřít nový terminál pro aktualizaci cesty.</span><span class="sxs-lookup"><span data-stu-id="bf461-116">If this command fails, you may need to open a new terminal to refresh the PATH.</span></span>

1. <span data-ttu-id="bf461-117">Nástroj odeberte spuštěním příkazu [odinstalovat nástroj dotnet:](dotnet-tool-uninstall.md)</span><span class="sxs-lookup"><span data-stu-id="bf461-117">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a><span data-ttu-id="bf461-118">Použití nástroje jako globálního nástroje nainstalovaného ve vlastním umístění</span><span class="sxs-lookup"><span data-stu-id="bf461-118">Use the tool as a global tool installed in a custom location</span></span>

1. <span data-ttu-id="bf461-119">Nainstalujte nástroj z balíčku.</span><span class="sxs-lookup"><span data-stu-id="bf461-119">Install the tool from the package.</span></span>

   <span data-ttu-id="bf461-120">Ve Windows:</span><span class="sxs-lookup"><span data-stu-id="bf461-120">On Windows:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="bf461-121">Na Linuxu nebo macOS:</span><span class="sxs-lookup"><span data-stu-id="bf461-121">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="bf461-122">Parametr `--tool-path` informuje rozhraní CLI jádra .NET k instalaci binárních souborů nástrojů do zadaného umístění.</span><span class="sxs-lookup"><span data-stu-id="bf461-122">The `--tool-path` parameter tells the .NET Core CLI to install the tool binaries in the specified location.</span></span> <span data-ttu-id="bf461-123">Pokud adresář neexistuje, je vytvořen.</span><span class="sxs-lookup"><span data-stu-id="bf461-123">If the directory doesn't exist, it is created.</span></span> <span data-ttu-id="bf461-124">Tento adresář není automaticky přidán do proměnné prostředí PATH.</span><span class="sxs-lookup"><span data-stu-id="bf461-124">This directory is not automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="bf461-125">Výstup zobrazuje příkaz použitý k volání nástroje a nainstalovanou verzi:</span><span class="sxs-lookup"><span data-stu-id="bf461-125">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="bf461-126">Vyvolat nástroj:</span><span class="sxs-lookup"><span data-stu-id="bf461-126">Invoke the tool:</span></span>

   <span data-ttu-id="bf461-127">Ve Windows:</span><span class="sxs-lookup"><span data-stu-id="bf461-127">On Windows:</span></span>

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   <span data-ttu-id="bf461-128">Na Linuxu nebo macOS:</span><span class="sxs-lookup"><span data-stu-id="bf461-128">On Linux or macOS:</span></span>

   ```console
   ~/bin/botsay hello from the bot
   ```

1. <span data-ttu-id="bf461-129">Nástroj odeberte spuštěním příkazu [odinstalovat nástroj dotnet:](dotnet-tool-uninstall.md)</span><span class="sxs-lookup"><span data-stu-id="bf461-129">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   <span data-ttu-id="bf461-130">Ve Windows:</span><span class="sxs-lookup"><span data-stu-id="bf461-130">On Windows:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   <span data-ttu-id="bf461-131">Na Linuxu nebo macOS:</span><span class="sxs-lookup"><span data-stu-id="bf461-131">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a><span data-ttu-id="bf461-132">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="bf461-132">Troubleshoot</span></span>

<span data-ttu-id="bf461-133">Pokud se při sledování kurzu zobrazí chybová zpráva, [přečtěte si článek Poradce při potížích s používáním nástroje .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="bf461-133">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="bf461-134">Další kroky</span><span class="sxs-lookup"><span data-stu-id="bf461-134">Next steps</span></span>

<span data-ttu-id="bf461-135">V tomto kurzu jste nainstalovali a použili nástroj jako globální nástroj.</span><span class="sxs-lookup"><span data-stu-id="bf461-135">In this tutorial, you installed and used a tool as a global tool.</span></span> <span data-ttu-id="bf461-136">Chcete-li nainstalovat a používat stejný nástroj jako místní nástroj, přejde meze k dalšímu kurzu.</span><span class="sxs-lookup"><span data-stu-id="bf461-136">To install and use the same tool as a local tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bf461-137">Instalace a používání místních nástrojů</span><span class="sxs-lookup"><span data-stu-id="bf461-137">Install and use local tools</span></span>](local-tools-how-to-use.md)
