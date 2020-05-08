---
title: dotnet – příkaz push NuGet
description: Příkaz dotnet NuGet push odešle balíček na server a publikuje ho.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 1e7831de4c041591b3602e405418f89f1d1d27d1
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895460"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="150ef-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="150ef-103">dotnet nuget push</span></span>

<span data-ttu-id="150ef-104">**Tento článek se týká:** ✔️ .NET Core 2. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="150ef-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="150ef-105">Name</span><span class="sxs-lookup"><span data-stu-id="150ef-105">Name</span></span>

<span data-ttu-id="150ef-106">`dotnet nuget push`– Odešle balíček na server a publikuje ho.</span><span class="sxs-lookup"><span data-stu-id="150ef-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="150ef-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="150ef-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source <SOURCE>] [--skip-duplicate]
    [-sk|--symbol-api-key <API_KEY>] [-ss|--symbol-source <SOURCE>]
    [-t|--timeout <TIMEOUT>]

dotnet nuget push -h|--help
```

## <a name="description"></a><span data-ttu-id="150ef-108">Popis</span><span class="sxs-lookup"><span data-stu-id="150ef-108">Description</span></span>

<span data-ttu-id="150ef-109">`dotnet nuget push` Příkaz odešle balíček na server a publikuje ho.</span><span class="sxs-lookup"><span data-stu-id="150ef-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="150ef-110">Příkaz push používá podrobnosti serveru a přihlašovacích údajů, které se našly v konfiguračním souboru NuGet systému nebo v řetězci konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="150ef-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="150ef-111">Další informace o konfiguračních souborech najdete v tématu [Konfigurace chování NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="150ef-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="150ef-112">Výchozí konfigurace NuGet se získá tak, že se načtou *%AppData%\NuGet\NuGet.config* (Windows) nebo *$Home/.local/share* (Linux/MacOS) a pak se načte jakákoli soubor *NuGet. config* nebo *. NuGet\NuGet.config* počínaje kořenovým adresářem jednotky a končí aktuálním adresářem.</span><span class="sxs-lookup"><span data-stu-id="150ef-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

<span data-ttu-id="150ef-113">Příkaz vloží existující balíček.</span><span class="sxs-lookup"><span data-stu-id="150ef-113">The command pushes an existing package.</span></span> <span data-ttu-id="150ef-114">Nevytváří balíček.</span><span class="sxs-lookup"><span data-stu-id="150ef-114">It doesn't create a package.</span></span> <span data-ttu-id="150ef-115">K vytvoření balíčku použijte [`dotnet pack`](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="150ef-115">To create a package, use [`dotnet pack`](dotnet-pack.md).</span></span>

## <a name="arguments"></a><span data-ttu-id="150ef-116">Argumenty</span><span class="sxs-lookup"><span data-stu-id="150ef-116">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="150ef-117">Určuje cestu k balíčku, který má být vložen.</span><span class="sxs-lookup"><span data-stu-id="150ef-117">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="150ef-118">Možnosti</span><span class="sxs-lookup"><span data-stu-id="150ef-118">Options</span></span>

- **`-d|--disable-buffering`**

  <span data-ttu-id="150ef-119">Zakáže ukládání do vyrovnávací paměti při doručování na server HTTP (S), aby se snížilo využití paměti.</span><span class="sxs-lookup"><span data-stu-id="150ef-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

- **`--force-english-output`**

  <span data-ttu-id="150ef-120">Vynutí spuštění aplikace s využitím neutrální jazykové verze založené na angličtině.</span><span class="sxs-lookup"><span data-stu-id="150ef-120">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="150ef-121">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="150ef-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="150ef-122">Umožňuje příkazu blokovat a vyžadovat ruční akci pro operace, jako je ověřování.</span><span class="sxs-lookup"><span data-stu-id="150ef-122">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="150ef-123">Možnost je k dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="150ef-123">Option available since .NET Core 2.2 SDK.</span></span>

- **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="150ef-124">Klíč rozhraní API pro server</span><span class="sxs-lookup"><span data-stu-id="150ef-124">The API key for the server.</span></span>

- **`-n|--no-symbols`**

  <span data-ttu-id="150ef-125">Symboly nejsou nabízeny (i v případě, že jsou k dispozici).</span><span class="sxs-lookup"><span data-stu-id="150ef-125">Doesn't push symbols (even if present).</span></span>

- **`--no-service-endpoint`**

  <span data-ttu-id="150ef-126">Nepřipojí k zdrojové adrese URL rozhraní API/v2/Package.</span><span class="sxs-lookup"><span data-stu-id="150ef-126">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="150ef-127">Možnost je k dispozici od verze .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="150ef-127">Option available since .NET Core 2.1 SDK.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="150ef-128">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="150ef-128">Specifies the server URL.</span></span> <span data-ttu-id="150ef-129">Tato možnost je povinná, pokud `DefaultPushSource` konfigurační hodnota není nastavená v konfiguračním souboru NuGet.</span><span class="sxs-lookup"><span data-stu-id="150ef-129">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

- **`--skip-duplicate`**

  <span data-ttu-id="150ef-130">Při nahrávání více balíčků na server HTTP (S) zachází s každou odpovědí na 409 konfliktů jako s upozorněním, aby bylo možné pokračovat v nabízení.</span><span class="sxs-lookup"><span data-stu-id="150ef-130">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="150ef-131">K dispozici od verze .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="150ef-131">Available since .NET Core 3.1 SDK.</span></span>

- **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="150ef-132">Klíč rozhraní API pro server symbolů.</span><span class="sxs-lookup"><span data-stu-id="150ef-132">The API key for the symbol server.</span></span>

- **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="150ef-133">Určuje adresu URL serveru symbolů.</span><span class="sxs-lookup"><span data-stu-id="150ef-133">Specifies the symbol server URL.</span></span>

- **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="150ef-134">Určuje časový limit pro doručování na server během několika sekund.</span><span class="sxs-lookup"><span data-stu-id="150ef-134">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="150ef-135">Výchozí hodnota je 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="150ef-135">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="150ef-136">Zadáním hodnoty 0 (nula sekund) se použije výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="150ef-136">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="150ef-137">Příklady</span><span class="sxs-lookup"><span data-stu-id="150ef-137">Examples</span></span>

- <span data-ttu-id="150ef-138">Vložení *foo. nupkg* na výchozí zdroj nabízených oznámení a zadání klíče rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="150ef-138">Push *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- <span data-ttu-id="150ef-139">Vložení *foo. nupkg* do oficiálního serveru NuGet a zadání klíče rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="150ef-139">Push *foo.nupkg* to the official NuGet server, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * <span data-ttu-id="150ef-140">Vložení *foo. nupkg* do vlastního zdroje `https://customsource`nabízených oznámení zadání klíče rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="150ef-140">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- <span data-ttu-id="150ef-141">Vložení *foo. nupkg* na výchozí zdroj nabízených oznámení:</span><span class="sxs-lookup"><span data-stu-id="150ef-141">Push *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- <span data-ttu-id="150ef-142">Vložení *foo. Symbols. nupkg* do výchozího zdroje symbolů:</span><span class="sxs-lookup"><span data-stu-id="150ef-142">Push *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- <span data-ttu-id="150ef-143">Vložení *foo. nupkg* na výchozí zdroj nabízených oznámení a zadání časového limitu 360 sekund:</span><span class="sxs-lookup"><span data-stu-id="150ef-143">Push *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- <span data-ttu-id="150ef-144">Nahrajte všechny soubory *. nupkg* v aktuálním adresáři do výchozího zdroje nabízených oznámení:</span><span class="sxs-lookup"><span data-stu-id="150ef-144">Push all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > <span data-ttu-id="150ef-145">Pokud tento příkaz nefunguje, může to být způsobeno chybou, která existovala ve starších verzích sady SDK (.NET Core 2,1 SDK a starších verzích).</span><span class="sxs-lookup"><span data-stu-id="150ef-145">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="150ef-146">Pokud to chcete opravit, upgradujte verzi sady SDK nebo spusťte následující příkaz:`dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="150ef-146">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>

- <span data-ttu-id="150ef-147">Nahrajte všechny soubory *. nupkg* i v případě, že server http (S) vrátí odpověď na konflikt 409:</span><span class="sxs-lookup"><span data-stu-id="150ef-147">Push all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```

- <span data-ttu-id="150ef-148">Nahrajte všechny soubory *. nupkg* v aktuálním adresáři do místního adresáře informačního kanálu:</span><span class="sxs-lookup"><span data-stu-id="150ef-148">Push all *.nupkg* files in the current directory to a local feed directory:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg -s c:\mydir
  ```

  <span data-ttu-id="150ef-149">Tento příkaz neukládá balíčky do hierarchické struktury složek, což se doporučuje pro optimalizaci výkonu.</span><span class="sxs-lookup"><span data-stu-id="150ef-149">This command doesn't store packages in a hierarchical folder structure, which is recommended to optimize performance.</span></span> <span data-ttu-id="150ef-150">Další informace najdete v tématu [místní informační kanály](/nuget/hosting-packages/local-feeds).</span><span class="sxs-lookup"><span data-stu-id="150ef-150">For more information, see [Local feeds](/nuget/hosting-packages/local-feeds).</span></span>  
