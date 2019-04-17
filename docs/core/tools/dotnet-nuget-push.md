---
title: příkaz DotNet nuget nabízených oznámení
description: Příkaz dotnet nuget nabízených odešle balíček na server a publikuje ji.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: 9f38fb29ef5b802a5b7091dd1e9659c653cf04d0
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59610766"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="882c4-103">DotNet nuget push</span><span class="sxs-lookup"><span data-stu-id="882c4-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="882c4-104">Name</span><span class="sxs-lookup"><span data-stu-id="882c4-104">Name</span></span>

<span data-ttu-id="882c4-105">`dotnet nuget push` -Odešle balíček na server a publikuje ji.</span><span class="sxs-lookup"><span data-stu-id="882c4-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="882c4-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="882c4-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="882c4-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="882c4-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="882c4-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="882c4-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="882c4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="882c4-109">Description</span></span>

<span data-ttu-id="882c4-110">`dotnet nuget push` Příkaz odešle balíček na server a publikuje ji.</span><span class="sxs-lookup"><span data-stu-id="882c4-110">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="882c4-111">Příkaz nabízených oznámení pomocí serveru a přihlašovací údaje podrobnosti nacházející se v konfiguračním souboru systému NuGet nebo řetězec konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="882c4-111">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="882c4-112">Další informace o konfiguračních souborů naleznete v tématu [konfigurace chování Nugetu](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="882c4-112">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="882c4-113">Výchozí konfigurace NuGet se získá načítání *%AppData%\NuGet\NuGet.config* (Windows) nebo *$HOME/.local/share* (Linux/macOS), pak všechny načítání *nuget.config*nebo *.nuget\nuget.config* od kořenové jednotky a končí v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="882c4-113">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="882c4-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="882c4-114">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="882c4-115">Určuje cestu souboru pro balíček, který má být vložena.</span><span class="sxs-lookup"><span data-stu-id="882c4-115">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="882c4-116">Možnosti</span><span class="sxs-lookup"><span data-stu-id="882c4-116">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="882c4-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="882c4-117">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-d|--disable-buffering`**

  <span data-ttu-id="882c4-118">Zakáže ukládání do vyrovnávací paměti při odesílání na server HTTP (S) ke snížení využití paměti.</span><span class="sxs-lookup"><span data-stu-id="882c4-118">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="882c4-119">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="882c4-119">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

<span data-ttu-id="882c4-120">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="882c4-120">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="882c4-121">Umožňuje příkazu blokování a vyžaduje ruční akci pro operace, jako je například ověřování.</span><span class="sxs-lookup"><span data-stu-id="882c4-121">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="882c4-122">Možnost dostupné od verze sady SDK 2.2 .NET Core.</span><span class="sxs-lookup"><span data-stu-id="882c4-122">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="882c4-123">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="882c4-123">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="882c4-124">Nelze vložit symboly (i když je k dispozici).</span><span class="sxs-lookup"><span data-stu-id="882c4-124">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="882c4-125">"Api/v2/balíček" nemá připojení k zdrojová adresa URL.</span><span class="sxs-lookup"><span data-stu-id="882c4-125">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="882c4-126">Možnost dostupné od verze sady SDK .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="882c4-126">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="882c4-127">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="882c4-127">Specifies the server URL.</span></span> <span data-ttu-id="882c4-128">Tato možnost je vyžadována, pokud `DefaultPushSource` konfigurační hodnota je nastavena v konfiguračním souboru NuGet.</span><span class="sxs-lookup"><span data-stu-id="882c4-128">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="882c4-129">Klíč rozhraní API pro server symbolů.</span><span class="sxs-lookup"><span data-stu-id="882c4-129">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="882c4-130">Určuje adresu URL serveru symbolů.</span><span class="sxs-lookup"><span data-stu-id="882c4-130">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="882c4-131">Určuje časový limit pro odesílání na server v řádu sekund.</span><span class="sxs-lookup"><span data-stu-id="882c4-131">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="882c4-132">Výchozí hodnota je 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="882c4-132">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="882c4-133">Zadání 0 (nula sekund) použije výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="882c4-133">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="882c4-134">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="882c4-134">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-d|--disable-buffering`**

  <span data-ttu-id="882c4-135">Zakáže ukládání do vyrovnávací paměti při odesílání na server HTTP (S) ke snížení využití paměti.</span><span class="sxs-lookup"><span data-stu-id="882c4-135">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="882c4-136">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="882c4-136">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="882c4-137">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="882c4-137">Prints out a short help for the command.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="882c4-138">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="882c4-138">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="882c4-139">Nelze vložit symboly (i když je k dispozici).</span><span class="sxs-lookup"><span data-stu-id="882c4-139">Doesn't push symbols (even if present).</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="882c4-140">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="882c4-140">Specifies the server URL.</span></span> <span data-ttu-id="882c4-141">Tato možnost je vyžadována, pokud `DefaultPushSource` konfigurační hodnota je nastavena v konfiguračním souboru NuGet.</span><span class="sxs-lookup"><span data-stu-id="882c4-141">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="882c4-142">Klíč rozhraní API pro server symbolů.</span><span class="sxs-lookup"><span data-stu-id="882c4-142">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="882c4-143">Určuje adresu URL serveru symbolů.</span><span class="sxs-lookup"><span data-stu-id="882c4-143">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="882c4-144">Určuje časový limit pro odesílání na server v řádu sekund.</span><span class="sxs-lookup"><span data-stu-id="882c4-144">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="882c4-145">Výchozí hodnota je 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="882c4-145">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="882c4-146">Zadání 0 (nula sekund) použije výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="882c4-146">Specifying 0 (zero seconds) applies the default value.</span></span>

---

## <a name="examples"></a><span data-ttu-id="882c4-147">Příklady</span><span class="sxs-lookup"><span data-stu-id="882c4-147">Examples</span></span>

* <span data-ttu-id="882c4-148">Nabízených oznámení *foo.nupkg* nabízených oznámení na výchozí zdroj určení klíče rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="882c4-148">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="882c4-149">Push *foo.nupkg* ke zdroji vlastní nabízené `https://customsource`, určení klíče rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="882c4-149">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="882c4-150">Nabízených oznámení *foo.nupkg* pro výchozí zdroj nabízených oznámení:</span><span class="sxs-lookup"><span data-stu-id="882c4-150">Pushes *foo.nupkg* to the default push source:</span></span>

  ```console
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="882c4-151">Nabízených oznámení *foo.symbols.nupkg* pro výchozí zdroj symboly:</span><span class="sxs-lookup"><span data-stu-id="882c4-151">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```console
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="882c4-152">Nabízených oznámení *foo.nupkg* ke zdroji nabízené výchozí zadání časového limitu 360 druhé:</span><span class="sxs-lookup"><span data-stu-id="882c4-152">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```console
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="882c4-153">Nabízených oznámení všem *.nupkg* soubory v aktuálním adresáři pro výchozí zdroj nabízených oznámení:</span><span class="sxs-lookup"><span data-stu-id="882c4-153">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```console
  dotnet nuget push *.nupkg
  ```