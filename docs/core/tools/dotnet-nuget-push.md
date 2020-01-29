---
title: dotnet – příkaz push NuGet
description: Příkaz dotnet NuGet push odešle balíček na server a publikuje ho.
author: karann-msft
ms.date: 12/04/2019
ms.openlocfilehash: a483c559dee8b4a82cc2c792f5c2c5e4a8ff3f87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733106"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="97564-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="97564-103">dotnet nuget push</span></span>

<span data-ttu-id="97564-104">**Tento článek se týká:** ✔️ .NET Core 1. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="97564-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="97564-105">Name</span><span class="sxs-lookup"><span data-stu-id="97564-105">Name</span></span>

<span data-ttu-id="97564-106">`dotnet nuget push` – odešle balíček na server a publikuje ho.</span><span class="sxs-lookup"><span data-stu-id="97564-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="97564-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="97564-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [--skip-duplicate] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="97564-108">Popis</span><span class="sxs-lookup"><span data-stu-id="97564-108">Description</span></span>

<span data-ttu-id="97564-109">Příkaz `dotnet nuget push` odešle balíček na server a publikuje ho.</span><span class="sxs-lookup"><span data-stu-id="97564-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="97564-110">Příkaz push používá podrobnosti serveru a přihlašovacích údajů, které se našly v konfiguračním souboru NuGet systému nebo v řetězci konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="97564-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="97564-111">Další informace o konfiguračních souborech najdete v tématu [Konfigurace chování NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="97564-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="97564-112">Výchozí konfigurace NuGet se získá tak, že se načtou *%AppData%\NuGet\NuGet.config* (Windows) nebo *$Home/.local/share* (Linux/MacOS) a pak se načte jakákoli soubor *NuGet. config* nebo *. NuGet\NuGet.config* počínaje kořenovým adresářem jednotky a končí aktuálním adresářem.</span><span class="sxs-lookup"><span data-stu-id="97564-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="97564-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="97564-113">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="97564-114">Určuje cestu k balíčku, který má být vložen.</span><span class="sxs-lookup"><span data-stu-id="97564-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="97564-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="97564-115">Options</span></span>

* **`-d|--disable-buffering`**

  <span data-ttu-id="97564-116">Zakáže ukládání do vyrovnávací paměti při doručování na server HTTP (S), aby se snížilo využití paměti.</span><span class="sxs-lookup"><span data-stu-id="97564-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="97564-117">Vynutí spuštění aplikace s využitím neutrální jazykové verze založené na angličtině.</span><span class="sxs-lookup"><span data-stu-id="97564-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="97564-118">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="97564-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="97564-119">Umožňuje příkazu blokovat a vyžadovat ruční akci pro operace, jako je ověřování.</span><span class="sxs-lookup"><span data-stu-id="97564-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="97564-120">Možnost je k dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="97564-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="97564-121">Klíč rozhraní API pro server</span><span class="sxs-lookup"><span data-stu-id="97564-121">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="97564-122">Symboly nejsou nabízeny (i v případě, že jsou k dispozici).</span><span class="sxs-lookup"><span data-stu-id="97564-122">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="97564-123">Nepřipojí k zdrojové adrese URL rozhraní API/v2/Package.</span><span class="sxs-lookup"><span data-stu-id="97564-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="97564-124">Možnost je k dispozici od verze .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="97564-124">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="97564-125">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="97564-125">Specifies the server URL.</span></span> <span data-ttu-id="97564-126">Tato možnost je povinná, pokud v konfiguračním souboru NuGet není nastavená hodnota `DefaultPushSource` config.</span><span class="sxs-lookup"><span data-stu-id="97564-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`--skip-duplicate`**

  <span data-ttu-id="97564-127">Při nahrávání více balíčků na server HTTP (S) zachází s každou odpovědí na 409 konfliktů jako s upozorněním, aby bylo možné pokračovat v nabízení.</span><span class="sxs-lookup"><span data-stu-id="97564-127">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="97564-128">K dispozici od verze .NET Core 3,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="97564-128">Available since .NET Core 3.1 SDK.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="97564-129">Klíč rozhraní API pro server symbolů.</span><span class="sxs-lookup"><span data-stu-id="97564-129">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="97564-130">Určuje adresu URL serveru symbolů.</span><span class="sxs-lookup"><span data-stu-id="97564-130">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="97564-131">Určuje časový limit pro doručování na server během několika sekund.</span><span class="sxs-lookup"><span data-stu-id="97564-131">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="97564-132">Výchozí hodnota je 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="97564-132">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="97564-133">Zadáním hodnoty 0 (nula sekund) se použije výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="97564-133">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="97564-134">Příklady</span><span class="sxs-lookup"><span data-stu-id="97564-134">Examples</span></span>

* <span data-ttu-id="97564-135">Vloží *foo. nupkg* na výchozí zdroj nabízených oznámení a určí klíč rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="97564-135">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="97564-136">Vložení *foo. nupkg* do vlastního `https://customsource`zdroje nabízených oznámení zadání klíče rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="97564-136">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="97564-137">Vloží *foo. nupkg* na výchozí zdroj nabízených oznámení:</span><span class="sxs-lookup"><span data-stu-id="97564-137">Pushes *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="97564-138">Vloží *foo. Symbols. nupkg* na výchozí zdroj symbolů:</span><span class="sxs-lookup"><span data-stu-id="97564-138">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="97564-139">Vloží *foo. nupkg* na výchozí zdroj nabízených oznámení a určí časový limit 360 sekund:</span><span class="sxs-lookup"><span data-stu-id="97564-139">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="97564-140">Vloží všechny soubory *. nupkg* v aktuálním adresáři do výchozího zdroje nabízených oznámení:</span><span class="sxs-lookup"><span data-stu-id="97564-140">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > <span data-ttu-id="97564-141">Pokud tento příkaz nefunguje, může to být způsobeno chybou, která existovala ve starších verzích sady SDK (.NET Core 2,1 SDK a starších verzích).</span><span class="sxs-lookup"><span data-stu-id="97564-141">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="97564-142">Pokud to chcete opravit, upgradujte verzi sady SDK nebo spusťte následující příkaz: `dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="97564-142">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>

* <span data-ttu-id="97564-143">Vloží všechny soubory *. nupkg* i v případě, že server http (S) vrátí odpověď na konflikt 409:</span><span class="sxs-lookup"><span data-stu-id="97564-143">Pushes all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
