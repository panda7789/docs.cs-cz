---
title: dotnet nuget push, příkaz
description: Příkaz push dotnet nuget odešle balíček na server a publikuje jej.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: d4ef8e58908fe488c712debff3b313ac0908b43e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503658"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="f71f7-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="f71f7-103">dotnet nuget push</span></span>

<span data-ttu-id="f71f7-104">**Tento článek se týká:** ✔️ .NET Core 2.x SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="f71f7-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f71f7-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="f71f7-105">Name</span></span>

<span data-ttu-id="f71f7-106">`dotnet nuget push`- Odešle balíček na server a publikuje jej.</span><span class="sxs-lookup"><span data-stu-id="f71f7-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f71f7-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="f71f7-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [--skip-duplicate] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f71f7-108">Popis</span><span class="sxs-lookup"><span data-stu-id="f71f7-108">Description</span></span>

<span data-ttu-id="f71f7-109">Příkaz `dotnet nuget push` odešle balíček na server a publikuje jej.</span><span class="sxs-lookup"><span data-stu-id="f71f7-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="f71f7-110">Příkaz push používá podrobnosti o serveru a pověření, které se nacházejí v konfiguračním souboru nuget systému nebo v řetězci konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="f71f7-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="f71f7-111">Další informace o konfiguračních souborech naleznete [v tématu Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="f71f7-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="f71f7-112">Výchozí konfigurace nugetu je získána načtením *%AppData%\NuGet\NuGet.config* (Windows) nebo *$HOME/.local/share* (Linux/macOS), potom načtením *libovolného souboru nuget.config* nebo *.nuget\nuget.config* počínaje kořenem jednotky a končícím v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="f71f7-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="f71f7-113">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f71f7-113">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="f71f7-114">Určuje cestu k souboru, který má být posunut.</span><span class="sxs-lookup"><span data-stu-id="f71f7-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="f71f7-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="f71f7-115">Options</span></span>

- **`-d|--disable-buffering`**

  <span data-ttu-id="f71f7-116">Zakáže ukládání do vyrovnávací paměti při odesílání na server HTTP(S), aby se snížilo využití paměti.</span><span class="sxs-lookup"><span data-stu-id="f71f7-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

- **`--force-english-output`**

  <span data-ttu-id="f71f7-117">Vynutí spuštění aplikace pomocí invariantní jazykové verze založené na angličtině.</span><span class="sxs-lookup"><span data-stu-id="f71f7-117">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f71f7-118">Vytiskne krátkou nápovědu pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="f71f7-118">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="f71f7-119">Umožňuje příkaz blokovat a vyžaduje ruční akci pro operace, jako je ověřování.</span><span class="sxs-lookup"><span data-stu-id="f71f7-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="f71f7-120">Možnost je k dispozici od .NET Core 2.2 SDK.</span><span class="sxs-lookup"><span data-stu-id="f71f7-120">Option available since .NET Core 2.2 SDK.</span></span>

- **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="f71f7-121">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="f71f7-121">The API key for the server.</span></span>

- **`-n|--no-symbols`**

  <span data-ttu-id="f71f7-122">Netlačí symboly (i když jsou k dispozici).</span><span class="sxs-lookup"><span data-stu-id="f71f7-122">Doesn't push symbols (even if present).</span></span>

- **`--no-service-endpoint`**

  <span data-ttu-id="f71f7-123">Nepřipojí "api/v2/package" ke zdrojové adrese URL.</span><span class="sxs-lookup"><span data-stu-id="f71f7-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="f71f7-124">Možnost je k dispozici od .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="f71f7-124">Option available since .NET Core 2.1 SDK.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="f71f7-125">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="f71f7-125">Specifies the server URL.</span></span> <span data-ttu-id="f71f7-126">Tato možnost je `DefaultPushSource` vyžadována, pokud není v konfiguračním souboru NuGet nastavena hodnota konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f71f7-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

- **`--skip-duplicate`**

  <span data-ttu-id="f71f7-127">Při odesílání více balíčků na server HTTP(S) považuje všechny 409 konflikt odpověď jako upozornění tak, aby push může pokračovat.</span><span class="sxs-lookup"><span data-stu-id="f71f7-127">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="f71f7-128">K dispozici od .NET Core 3.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="f71f7-128">Available since .NET Core 3.1 SDK.</span></span>

- **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="f71f7-129">Klíč rozhraní API pro server symbolů.</span><span class="sxs-lookup"><span data-stu-id="f71f7-129">The API key for the symbol server.</span></span>

- **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="f71f7-130">Určuje adresu URL serveru symbolů.</span><span class="sxs-lookup"><span data-stu-id="f71f7-130">Specifies the symbol server URL.</span></span>

- **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="f71f7-131">Určuje časový limit pro odesílání na server v sekundách.</span><span class="sxs-lookup"><span data-stu-id="f71f7-131">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="f71f7-132">Výchozí hodnota je 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="f71f7-132">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="f71f7-133">Zadáním 0 (nula sekund) se použije výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="f71f7-133">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="f71f7-134">Příklady</span><span class="sxs-lookup"><span data-stu-id="f71f7-134">Examples</span></span>

- <span data-ttu-id="f71f7-135">Odešle *foo.nupkg* na výchozí zdroj nabízených oznámení a zadá klíč rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="f71f7-135">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- <span data-ttu-id="f71f7-136">Push *foo.nupkg* na oficiální server NuGet a zadejte klíč rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="f71f7-136">Push *foo.nupkg* to the official NuGet server, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * <span data-ttu-id="f71f7-137">Posuňte *foo.nupkg* na vlastní zdroj `https://customsource`nabízených síly a zadejte klíč rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="f71f7-137">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- <span data-ttu-id="f71f7-138">Posune *foo.nupkg* na výchozí zdroj push:</span><span class="sxs-lookup"><span data-stu-id="f71f7-138">Pushes *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- <span data-ttu-id="f71f7-139">Odešle *foo.symbols.nupkg* na výchozí zdroj symbolů:</span><span class="sxs-lookup"><span data-stu-id="f71f7-139">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- <span data-ttu-id="f71f7-140">Odešle *foo.nupkg* na výchozí zdroj nabízených oznámení a určí časový limit 360 sekund:</span><span class="sxs-lookup"><span data-stu-id="f71f7-140">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- <span data-ttu-id="f71f7-141">Odešle všechny soubory *NUPKG* v aktuálním adresáři na výchozí zdroj nabízených oznámení:</span><span class="sxs-lookup"><span data-stu-id="f71f7-141">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > <span data-ttu-id="f71f7-142">Pokud tento příkaz nefunguje, může to být způsobeno chybou, která existovala ve starších verzích sady SDK (.NET Core 2.1 SDK a starších verzích).</span><span class="sxs-lookup"><span data-stu-id="f71f7-142">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="f71f7-143">Chcete-li tento problém vyřešit, inovujte verzi sady SDK nebo spusťte místo toho následující příkaz:`dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="f71f7-143">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>

- <span data-ttu-id="f71f7-144">Odešle všechny soubory *.nupkg* i v případě, že server HTTP(S) vrátí odpověď konfliktu 409:</span><span class="sxs-lookup"><span data-stu-id="f71f7-144">Pushes all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
