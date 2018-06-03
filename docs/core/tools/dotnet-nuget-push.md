---
title: příkaz nabízené DotNet nuget - .NET Core rozhraní příkazového řádku
description: Příkaz dotnet nuget nabízené nabízených oznámení balíček na server a vydává je.
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: 8a64f9cdc11d03bed82a132265c3b4e1de290807
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728573"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="91139-103">nabízená nuget DotNet.</span><span class="sxs-lookup"><span data-stu-id="91139-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="91139-104">Název</span><span class="sxs-lookup"><span data-stu-id="91139-104">Name</span></span>

<span data-ttu-id="91139-105">`dotnet nuget push` -Sami balíček na server a vydává je.</span><span class="sxs-lookup"><span data-stu-id="91139-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="91139-106">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="91139-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="91139-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="91139-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="91139-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="91139-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="91139-109">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="91139-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="91139-110">Popis</span><span class="sxs-lookup"><span data-stu-id="91139-110">Description</span></span>

<span data-ttu-id="91139-111">`dotnet nuget push` Příkaz nabízených oznámení balíček na server a vydává je.</span><span class="sxs-lookup"><span data-stu-id="91139-111">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="91139-112">Příkaz nabízené používá server a podrobnosti o přihlašovacích údajích, které najde v konfiguračním souboru systému NuGet nebo řetězu konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="91139-112">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="91139-113">Další informace o konfigurační soubory, najdete v části [konfigurace chování NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="91139-113">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="91139-114">NuGet výchozí konfiguraci se získávají načtením *%AppData%\NuGet\NuGet.config* (Windows) nebo *$HOME/.local/share* (Linux/systému macOS), pak všechny načítání *nuget.config*nebo *.nuget\nuget.config* z kořene jednotky počáteční a koncovou v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="91139-114">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="91139-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="91139-115">Arguments</span></span>

`ROOT`

<span data-ttu-id="91139-116">Určuje cestu k souboru na balíček, který chcete poslat.</span><span class="sxs-lookup"><span data-stu-id="91139-116">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="91139-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="91139-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="91139-118">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="91139-118">.NET Core 2.1</span></span>](#tab/netcore21)

`-d|--disable-buffering`

<span data-ttu-id="91139-119">Zakáže ukládání do vyrovnávací paměti při nabízení do serveru protokolu HTTP (S) ke snížení využití paměti.</span><span class="sxs-lookup"><span data-stu-id="91139-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="91139-120">Vynutí spuštění pomocí invariantní, na základě angličtina jazykové verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="91139-120">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="91139-121">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="91139-121">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="91139-122">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="91139-122">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="91139-123">Není push symboly (i pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="91139-123">Doesn't push symbols (even if present).</span></span>

`--no-service-endpoint`

<span data-ttu-id="91139-124">Není připojit "v2/api/balíček" na adresu URL zdroje.</span><span class="sxs-lookup"><span data-stu-id="91139-124">Doesn't append "api/v2/package" to the source URL.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="91139-125">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="91139-125">Specifies the server URL.</span></span> <span data-ttu-id="91139-126">Tato možnost je povinná, pokud `DefaultPushSource` konfigurační hodnota je nastavena v konfiguračním souboru NuGet.</span><span class="sxs-lookup"><span data-stu-id="91139-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="91139-127">Klíč rozhraní API pro symbol server.</span><span class="sxs-lookup"><span data-stu-id="91139-127">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="91139-128">Určuje adresu URL serveru symbol.</span><span class="sxs-lookup"><span data-stu-id="91139-128">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="91139-129">Určuje časový limit pro vkládání na server v sekundách.</span><span class="sxs-lookup"><span data-stu-id="91139-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="91139-130">Výchozí hodnota je 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="91139-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="91139-131">Zadáním 0 (nula sekund) platí výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="91139-131">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="91139-132">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="91139-132">.NET Core 2.0</span></span>](#tab/netcore20)

`-d|--disable-buffering`

<span data-ttu-id="91139-133">Zakáže ukládání do vyrovnávací paměti při nabízení do serveru protokolu HTTP (S) ke snížení využití paměti.</span><span class="sxs-lookup"><span data-stu-id="91139-133">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="91139-134">Vynutí spuštění pomocí invariantní, na základě angličtina jazykové verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="91139-134">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="91139-135">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="91139-135">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="91139-136">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="91139-136">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="91139-137">Není push symboly (i pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="91139-137">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="91139-138">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="91139-138">Specifies the server URL.</span></span> <span data-ttu-id="91139-139">Tato možnost je povinná, pokud `DefaultPushSource` konfigurační hodnota je nastavena v konfiguračním souboru NuGet.</span><span class="sxs-lookup"><span data-stu-id="91139-139">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="91139-140">Klíč rozhraní API pro symbol server.</span><span class="sxs-lookup"><span data-stu-id="91139-140">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="91139-141">Určuje adresu URL serveru symbol.</span><span class="sxs-lookup"><span data-stu-id="91139-141">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="91139-142">Určuje časový limit pro vkládání na server v sekundách.</span><span class="sxs-lookup"><span data-stu-id="91139-142">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="91139-143">Výchozí hodnota je 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="91139-143">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="91139-144">Zadáním 0 (nula sekund) platí výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="91139-144">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="91139-145">.NET pro základní 1.x</span><span class="sxs-lookup"><span data-stu-id="91139-145">.NET Core 1.x</span></span>](#tab/netcore1x)

`-d|--disable-buffering`

<span data-ttu-id="91139-146">Zakáže ukládání do vyrovnávací paměti při nabízení do serveru protokolu HTTP (S) ke snížení využití paměti.</span><span class="sxs-lookup"><span data-stu-id="91139-146">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="91139-147">Vynutí spuštění pomocí invariantní, na základě angličtina jazykové verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="91139-147">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="91139-148">Vytiskne krátké nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="91139-148">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="91139-149">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="91139-149">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="91139-150">Není push symboly (i pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="91139-150">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="91139-151">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="91139-151">Specifies the server URL.</span></span> <span data-ttu-id="91139-152">Tato možnost je povinná, pokud `DefaultPushSource` konfigurační hodnota je nastavena v konfiguračním souboru NuGet.</span><span class="sxs-lookup"><span data-stu-id="91139-152">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="91139-153">Klíč rozhraní API pro symbol server.</span><span class="sxs-lookup"><span data-stu-id="91139-153">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="91139-154">Určuje adresu URL serveru symbol.</span><span class="sxs-lookup"><span data-stu-id="91139-154">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="91139-155">Určuje časový limit pro vkládání na server v sekundách.</span><span class="sxs-lookup"><span data-stu-id="91139-155">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="91139-156">Výchozí hodnota je 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="91139-156">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="91139-157">Zadáním 0 (nula sekund) platí výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="91139-157">Specifying 0 (zero seconds) applies the default value.</span></span>

---

## <a name="examples"></a><span data-ttu-id="91139-158">Příklady</span><span class="sxs-lookup"><span data-stu-id="91139-158">Examples</span></span>

<span data-ttu-id="91139-159">Nabízených oznámení *foo.nupkg* ke zdroji nabízené výchozí zadání klíč rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="91139-159">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="91139-160">Nabízená *foo.nupkg* ke zdroji vlastní nabízené `http://customsource`, zadání klíč rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="91139-160">Push *foo.nupkg* to the custom push source `http://customsource`, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="91139-161">Nabízených oznámení *foo.nupkg* ke zdroji nabízené výchozí:</span><span class="sxs-lookup"><span data-stu-id="91139-161">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="91139-162">Nabízených oznámení *foo.symbols.nupkg* ke zdroji výchozí symboly:</span><span class="sxs-lookup"><span data-stu-id="91139-162">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="91139-163">Nabízených oznámení *foo.nupkg* ke zdroji nabízené výchozí zadání vypršení časového limitu 360 sekundu:</span><span class="sxs-lookup"><span data-stu-id="91139-163">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="91139-164">Všechny sami *.nupkg* soubory v aktuálním adresáři ke zdroji nabízené výchozí:</span><span class="sxs-lookup"><span data-stu-id="91139-164">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`

<span data-ttu-id="91139-165">Všechny sami *.nupkg* soubory v aktuálním adresáři ke zdroji nabízené výchozí, zadáním souboru vlastní konfigurace *./config/My.Config*:</span><span class="sxs-lookup"><span data-stu-id="91139-165">Pushes all *.nupkg* files in the current directory to the default push source, specifying a custom config file *./config/My.Config*:</span></span>

`dotnet nuget push *.nupkg --config-file ./config/My.Config`
