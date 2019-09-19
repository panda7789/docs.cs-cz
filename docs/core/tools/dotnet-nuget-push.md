---
title: dotnet – příkaz push NuGet
description: Příkaz dotnet NuGet push odešle balíček na server a publikuje ho.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 3299f79ec62aebdcdbef38f1e8b09a2dc5529ec4
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117489"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="a653f-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="a653f-103">dotnet nuget push</span></span>

<span data-ttu-id="a653f-104">**Toto téma se týká: ✓** .NET Core 1. x SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="a653f-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="a653f-105">Name</span><span class="sxs-lookup"><span data-stu-id="a653f-105">Name</span></span>

<span data-ttu-id="a653f-106">`dotnet nuget push`– Odešle balíček na server a publikuje ho.</span><span class="sxs-lookup"><span data-stu-id="a653f-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a653f-107">Stručný obsah</span><span class="sxs-lookup"><span data-stu-id="a653f-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="a653f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="a653f-108">Description</span></span>

<span data-ttu-id="a653f-109">`dotnet nuget push` Příkaz odešle balíček na server a publikuje ho.</span><span class="sxs-lookup"><span data-stu-id="a653f-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="a653f-110">Příkaz push používá podrobnosti serveru a přihlašovacích údajů, které se našly v konfiguračním souboru NuGet systému nebo v řetězci konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="a653f-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="a653f-111">Další informace o konfiguračních souborech najdete v tématu [Konfigurace chování NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="a653f-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="a653f-112">Výchozí konfigurace NuGet se získá načtením *%AppData%\NuGet\NuGet.config* (Windows) nebo *$Home/.local/share* (Linux/MacOS) a následným načtením jakékoli sady *NuGet. config* nebo *. NuGet\NuGet.config* počínaje kořenem jednotka a končí v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="a653f-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="a653f-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="a653f-113">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="a653f-114">Určuje cestu k balíčku, který má být vložen.</span><span class="sxs-lookup"><span data-stu-id="a653f-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="a653f-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="a653f-115">Options</span></span>

* **`-d|--disable-buffering`**

  <span data-ttu-id="a653f-116">Zakáže ukládání do vyrovnávací paměti při doručování na server HTTP (S), aby se snížilo využití paměti.</span><span class="sxs-lookup"><span data-stu-id="a653f-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="a653f-117">Vynutí spuštění aplikace s využitím neutrální jazykové verze založené na angličtině.</span><span class="sxs-lookup"><span data-stu-id="a653f-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

<span data-ttu-id="a653f-118">Vypíše krátkou nápovědu k příkazu.</span><span class="sxs-lookup"><span data-stu-id="a653f-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="a653f-119">Umožňuje příkazu blokovat a vyžadovat ruční akci pro operace, jako je ověřování.</span><span class="sxs-lookup"><span data-stu-id="a653f-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="a653f-120">Možnost je k dispozici od verze .NET Core 2,2 SDK.</span><span class="sxs-lookup"><span data-stu-id="a653f-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="a653f-121">Klíč rozhraní API pro server</span><span class="sxs-lookup"><span data-stu-id="a653f-121">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="a653f-122">Symboly nejsou nabízeny (i v případě, že jsou k dispozici).</span><span class="sxs-lookup"><span data-stu-id="a653f-122">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="a653f-123">Nepřipojí k zdrojové adrese URL rozhraní API/v2/Package.</span><span class="sxs-lookup"><span data-stu-id="a653f-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="a653f-124">Možnost je k dispozici od verze .NET Core 2,1 SDK.</span><span class="sxs-lookup"><span data-stu-id="a653f-124">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="a653f-125">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="a653f-125">Specifies the server URL.</span></span> <span data-ttu-id="a653f-126">Tato možnost je povinná, pokud `DefaultPushSource` konfigurační hodnota není nastavená v konfiguračním souboru NuGet.</span><span class="sxs-lookup"><span data-stu-id="a653f-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="a653f-127">Klíč rozhraní API pro server symbolů.</span><span class="sxs-lookup"><span data-stu-id="a653f-127">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="a653f-128">Určuje adresu URL serveru symbolů.</span><span class="sxs-lookup"><span data-stu-id="a653f-128">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="a653f-129">Určuje časový limit pro doručování na server během několika sekund.</span><span class="sxs-lookup"><span data-stu-id="a653f-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="a653f-130">Výchozí hodnota je 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="a653f-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="a653f-131">Zadáním hodnoty 0 (nula sekund) se použije výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="a653f-131">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="a653f-132">Příklady</span><span class="sxs-lookup"><span data-stu-id="a653f-132">Examples</span></span>

* <span data-ttu-id="a653f-133">Vloží *foo. nupkg* na výchozí zdroj nabízených oznámení a určí klíč rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="a653f-133">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="a653f-134">Vložení *foo. nupkg* do vlastního zdroje `https://customsource`nabízených oznámení zadání klíče rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="a653f-134">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="a653f-135">Vloží *foo. nupkg* na výchozí zdroj nabízených oznámení:</span><span class="sxs-lookup"><span data-stu-id="a653f-135">Pushes *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="a653f-136">Vloží *foo. Symbols. nupkg* na výchozí zdroj symbolů:</span><span class="sxs-lookup"><span data-stu-id="a653f-136">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="a653f-137">Vloží *foo. nupkg* na výchozí zdroj nabízených oznámení a určí časový limit 360 sekund:</span><span class="sxs-lookup"><span data-stu-id="a653f-137">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="a653f-138">Vloží všechny soubory *. nupkg* v aktuálním adresáři do výchozího zdroje nabízených oznámení:</span><span class="sxs-lookup"><span data-stu-id="a653f-138">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```
  
  > [!NOTE]
  > <span data-ttu-id="a653f-139">Pokud tento příkaz nefunguje, může to být způsobeno chybou, která existovala ve starších verzích sady SDK (.NET Core 2,1 SDK a starších verzích).</span><span class="sxs-lookup"><span data-stu-id="a653f-139">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="a653f-140">Pokud to chcete opravit, upgradujte verzi sady SDK nebo spusťte následující příkaz:`dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="a653f-140">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>
