---
title: příkaz push DotNet nuget – rozhraní příkazového řádku .NET Core
description: Příkaz dotnet nuget nabízených odešle balíček na server a publikuje ji.
author: karann-msft
ms.author: mairaw
ms.date: 09/04/2018
ms.openlocfilehash: 23d27cef29008955850f9ed9f4a8baed9e7ad982
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45609999"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="d31c7-103">DotNet nuget push</span><span class="sxs-lookup"><span data-stu-id="d31c7-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d31c7-104">Název</span><span class="sxs-lookup"><span data-stu-id="d31c7-104">Name</span></span>

<span data-ttu-id="d31c7-105">`dotnet nuget push` -Odešle balíček na server a publikuje ji.</span><span class="sxs-lookup"><span data-stu-id="d31c7-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d31c7-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="d31c7-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d31c7-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="d31c7-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d31c7-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="d31c7-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d31c7-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="d31c7-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="d31c7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d31c7-110">Description</span></span>

<span data-ttu-id="d31c7-111">`dotnet nuget push` Příkaz odešle balíček na server a publikuje ji.</span><span class="sxs-lookup"><span data-stu-id="d31c7-111">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="d31c7-112">Příkaz nabízených oznámení pomocí serveru a přihlašovací údaje podrobnosti nacházející se v konfiguračním souboru systému NuGet nebo řetězec konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="d31c7-112">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="d31c7-113">Další informace o konfiguračních souborů naleznete v tématu [konfigurace chování Nugetu](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="d31c7-113">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="d31c7-114">Výchozí konfigurace NuGet se získá načítání *%AppData%\NuGet\NuGet.config* (Windows) nebo *$HOME/.local/share* (Linux/macOS), pak všechny načítání *nuget.config*nebo *.nuget\nuget.config* od kořenové jednotky a končí v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="d31c7-114">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="d31c7-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="d31c7-115">Arguments</span></span>

`ROOT`

<span data-ttu-id="d31c7-116">Určuje cestu souboru pro balíček, který má být vložena.</span><span class="sxs-lookup"><span data-stu-id="d31c7-116">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="d31c7-117">Možnosti</span><span class="sxs-lookup"><span data-stu-id="d31c7-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="d31c7-118">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="d31c7-118">.NET Core 2.1</span></span>](#tab/netcore21)

`-d|--disable-buffering`

<span data-ttu-id="d31c7-119">Zakáže ukládání do vyrovnávací paměti při odesílání na server HTTP (S) ke snížení využití paměti.</span><span class="sxs-lookup"><span data-stu-id="d31c7-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="d31c7-120">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="d31c7-120">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="d31c7-121">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="d31c7-121">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="d31c7-122">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="d31c7-122">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="d31c7-123">Nelze vložit symboly (i když je k dispozici).</span><span class="sxs-lookup"><span data-stu-id="d31c7-123">Doesn't push symbols (even if present).</span></span>

`--no-service-endpoint`

<span data-ttu-id="d31c7-124">"Api/v2/balíček" nemá připojení k zdrojová adresa URL.</span><span class="sxs-lookup"><span data-stu-id="d31c7-124">Doesn't append "api/v2/package" to the source URL.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="d31c7-125">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="d31c7-125">Specifies the server URL.</span></span> <span data-ttu-id="d31c7-126">Tato možnost je vyžadována, pokud `DefaultPushSource` konfigurační hodnota je nastavena v konfiguračním souboru NuGet.</span><span class="sxs-lookup"><span data-stu-id="d31c7-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="d31c7-127">Klíč rozhraní API pro server symbolů.</span><span class="sxs-lookup"><span data-stu-id="d31c7-127">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="d31c7-128">Určuje adresu URL serveru symbolů.</span><span class="sxs-lookup"><span data-stu-id="d31c7-128">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="d31c7-129">Určuje časový limit pro odesílání na server v řádu sekund.</span><span class="sxs-lookup"><span data-stu-id="d31c7-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="d31c7-130">Výchozí hodnota je 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="d31c7-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="d31c7-131">Zadání 0 (nula sekund) použije výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d31c7-131">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="d31c7-132">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="d31c7-132">.NET Core 2.0</span></span>](#tab/netcore20)

`-d|--disable-buffering`

<span data-ttu-id="d31c7-133">Zakáže ukládání do vyrovnávací paměti při odesílání na server HTTP (S) ke snížení využití paměti.</span><span class="sxs-lookup"><span data-stu-id="d31c7-133">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="d31c7-134">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="d31c7-134">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="d31c7-135">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="d31c7-135">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="d31c7-136">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="d31c7-136">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="d31c7-137">Nelze vložit symboly (i když je k dispozici).</span><span class="sxs-lookup"><span data-stu-id="d31c7-137">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="d31c7-138">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="d31c7-138">Specifies the server URL.</span></span> <span data-ttu-id="d31c7-139">Tato možnost je vyžadována, pokud `DefaultPushSource` konfigurační hodnota je nastavena v konfiguračním souboru NuGet.</span><span class="sxs-lookup"><span data-stu-id="d31c7-139">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="d31c7-140">Klíč rozhraní API pro server symbolů.</span><span class="sxs-lookup"><span data-stu-id="d31c7-140">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="d31c7-141">Určuje adresu URL serveru symbolů.</span><span class="sxs-lookup"><span data-stu-id="d31c7-141">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="d31c7-142">Určuje časový limit pro odesílání na server v řádu sekund.</span><span class="sxs-lookup"><span data-stu-id="d31c7-142">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="d31c7-143">Výchozí hodnota je 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="d31c7-143">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="d31c7-144">Zadání 0 (nula sekund) použije výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d31c7-144">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d31c7-145">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="d31c7-145">.NET Core 1.x</span></span>](#tab/netcore1x)

`-d|--disable-buffering`

<span data-ttu-id="d31c7-146">Zakáže ukládání do vyrovnávací paměti při odesílání na server HTTP (S) ke snížení využití paměti.</span><span class="sxs-lookup"><span data-stu-id="d31c7-146">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="d31c7-147">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="d31c7-147">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="d31c7-148">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="d31c7-148">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="d31c7-149">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="d31c7-149">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="d31c7-150">Nelze vložit symboly (i když je k dispozici).</span><span class="sxs-lookup"><span data-stu-id="d31c7-150">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="d31c7-151">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="d31c7-151">Specifies the server URL.</span></span> <span data-ttu-id="d31c7-152">Tato možnost je vyžadována, pokud `DefaultPushSource` konfigurační hodnota je nastavena v konfiguračním souboru NuGet.</span><span class="sxs-lookup"><span data-stu-id="d31c7-152">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="d31c7-153">Klíč rozhraní API pro server symbolů.</span><span class="sxs-lookup"><span data-stu-id="d31c7-153">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="d31c7-154">Určuje adresu URL serveru symbolů.</span><span class="sxs-lookup"><span data-stu-id="d31c7-154">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="d31c7-155">Určuje časový limit pro odesílání na server v řádu sekund.</span><span class="sxs-lookup"><span data-stu-id="d31c7-155">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="d31c7-156">Výchozí hodnota je 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="d31c7-156">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="d31c7-157">Zadání 0 (nula sekund) použije výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d31c7-157">Specifying 0 (zero seconds) applies the default value.</span></span>

---

## <a name="examples"></a><span data-ttu-id="d31c7-158">Příklady</span><span class="sxs-lookup"><span data-stu-id="d31c7-158">Examples</span></span>

<span data-ttu-id="d31c7-159">Nabízených oznámení *foo.nupkg* nabízených oznámení na výchozí zdroj určení klíče rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="d31c7-159">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="d31c7-160">Push *foo.nupkg* ke zdroji vlastní nabízené `http://customsource`, určení klíče rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="d31c7-160">Push *foo.nupkg* to the custom push source `http://customsource`, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="d31c7-161">Nabízených oznámení *foo.nupkg* pro výchozí zdroj nabízených oznámení:</span><span class="sxs-lookup"><span data-stu-id="d31c7-161">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="d31c7-162">Nabízených oznámení *foo.symbols.nupkg* pro výchozí zdroj symboly:</span><span class="sxs-lookup"><span data-stu-id="d31c7-162">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="d31c7-163">Nabízených oznámení *foo.nupkg* ke zdroji nabízené výchozí zadání časového limitu 360 druhé:</span><span class="sxs-lookup"><span data-stu-id="d31c7-163">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="d31c7-164">Nabízených oznámení všem *.nupkg* soubory v aktuálním adresáři pro výchozí zdroj nabízených oznámení:</span><span class="sxs-lookup"><span data-stu-id="d31c7-164">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`
