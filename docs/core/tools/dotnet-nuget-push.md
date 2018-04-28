---
title: příkaz nabízené DotNet nuget - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet nuget nabízené nabízených oznámení balíček na server a vydává je.
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 29bc05c42bff9ace3fac2328ba44e15e4746e10e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="c3bbb-103">nabízená nuget DotNet.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c3bbb-104">Název</span><span class="sxs-lookup"><span data-stu-id="c3bbb-104">Name</span></span>

<span data-ttu-id="c3bbb-105">`dotnet nuget push` -Sami balíček na server a vydává je.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c3bbb-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="c3bbb-106">Synopsis</span></span>

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="c3bbb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c3bbb-107">Description</span></span>

<span data-ttu-id="c3bbb-108">`dotnet nuget push` Příkaz nabízených oznámení balíček na server a vydává je.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-108">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="c3bbb-109">Příkaz nabízené používá server a podrobnosti o přihlašovacích údajích, které najde v konfiguračním souboru systému NuGet nebo řetězu konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-109">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="c3bbb-110">Další informace o konfigurační soubory, najdete v části [konfigurace chování NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="c3bbb-110">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="c3bbb-111">NuGet výchozí konfiguraci se získávají načtením *%AppData%\NuGet\NuGet.config* (Windows) nebo *$HOME/.local/share* (Linux/systému macOS), pak všechny načítání *nuget.config*nebo *.nuget\nuget.config* z kořene jednotky počáteční a koncovou v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-111">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="c3bbb-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="c3bbb-112">Arguments</span></span>

`ROOT`

<span data-ttu-id="c3bbb-113">Určuje cestu k souboru na balíček, který chcete poslat.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-113">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="c3bbb-114">Možnosti</span><span class="sxs-lookup"><span data-stu-id="c3bbb-114">Options</span></span>

`-h|--help`

<span data-ttu-id="c3bbb-115">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-115">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="c3bbb-116">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-116">Specifies the server URL.</span></span> <span data-ttu-id="c3bbb-117">Tato možnost je povinná, pokud `DefaultPushSource` konfigurační hodnota je nastavena v konfiguračním souboru NuGet.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-117">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`--symbol-source <SOURCE>`

<span data-ttu-id="c3bbb-118">Určuje adresu URL serveru symbol.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-118">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="c3bbb-119">Určuje časový limit pro vkládání na server v sekundách.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-119">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="c3bbb-120">Výchozí hodnota je 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="c3bbb-120">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="c3bbb-121">Zadáním 0 (nula sekund) platí výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-121">Specifying 0 (zero seconds) applies the default value.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="c3bbb-122">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-122">The API key for the server.</span></span>

`--symbol-api-key <API_KEY>`

<span data-ttu-id="c3bbb-123">Klíč rozhraní API pro symbol server.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-123">The API key for the symbol server.</span></span>

`-d|--disable-buffering`

<span data-ttu-id="c3bbb-124">Zakáže ukládání do vyrovnávací paměti při nabízení do serveru protokolu HTTP (S), jak snížit využití paměti.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-124">Disables buffering when pushing to an HTTP(S) server to decrease memory usage.</span></span>

`-n|--no-symbols`

<span data-ttu-id="c3bbb-125">Není push symboly (i pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="c3bbb-125">Doesn't push symbols (even if present).</span></span>

`--force-english-output`

<span data-ttu-id="c3bbb-126">Vynutí protokolovat výstup v angličtině.</span><span class="sxs-lookup"><span data-stu-id="c3bbb-126">Forces all logged output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="c3bbb-127">Příklady</span><span class="sxs-lookup"><span data-stu-id="c3bbb-127">Examples</span></span>

<span data-ttu-id="c3bbb-128">Nabízených oznámení *foo.nupkg* ke zdroji nabízené výchozí poskytování klíč rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="c3bbb-128">Pushes *foo.nupkg* to the default push source, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="c3bbb-129">Nabízená *foo.nupkg* ke zdroji vlastní nabízené `http://customsource`, poskytuje klíč rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="c3bbb-129">Push *foo.nupkg* to the custom push source `http://customsource`, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="c3bbb-130">Nabízených oznámení *foo.nupkg* ke zdroji nabízené výchozí:</span><span class="sxs-lookup"><span data-stu-id="c3bbb-130">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="c3bbb-131">Nabízených oznámení *foo.symbols.nupkg* ke zdroji výchozí symboly:</span><span class="sxs-lookup"><span data-stu-id="c3bbb-131">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="c3bbb-132">Nabízených oznámení *foo.nupkg* ke zdroji nabízené výchozí zadání 360 druhý vypršení časového limitu:</span><span class="sxs-lookup"><span data-stu-id="c3bbb-132">Pushes *foo.nupkg* to the default push source, specifying a 360 second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="c3bbb-133">Všechny sami *.nupkg* soubory v aktuálním adresáři ke zdroji nabízené výchozí:</span><span class="sxs-lookup"><span data-stu-id="c3bbb-133">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`

<span data-ttu-id="c3bbb-134">Všechny sami *.nupkg* soubory v aktuálním adresáři ke zdroji nabízené výchozí, zadáním souboru vlastní konfigurace *./config/My.Config*:</span><span class="sxs-lookup"><span data-stu-id="c3bbb-134">Pushes all *.nupkg* files in the current directory to the default push source, specifying a custom config file *./config/My.Config*:</span></span>

`dotnet nuget push *.nupkg --config-file ./config/My.Config`
