---
title: příkaz DotNet nuget nabízených oznámení
description: Příkaz dotnet nuget nabízených odešle balíček na server a publikuje ji.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 4d5efa94c6a4494158aea447be98256d2a307cd6
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539135"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="46f33-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="46f33-103">dotnet nuget push</span></span>

<span data-ttu-id="46f33-104">**Toto téma platí pro: ✓** .NET Core 1.x sady SDK a novějších verzích</span><span class="sxs-lookup"><span data-stu-id="46f33-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="46f33-105">Name</span><span class="sxs-lookup"><span data-stu-id="46f33-105">Name</span></span>

<span data-ttu-id="46f33-106">`dotnet nuget push` -Odešle balíček na server a publikuje ji.</span><span class="sxs-lookup"><span data-stu-id="46f33-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="46f33-107">Souhrn</span><span class="sxs-lookup"><span data-stu-id="46f33-107">Synopsis</span></span>

```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="46f33-108">Popis</span><span class="sxs-lookup"><span data-stu-id="46f33-108">Description</span></span>

<span data-ttu-id="46f33-109">`dotnet nuget push` Příkaz odešle balíček na server a publikuje ji.</span><span class="sxs-lookup"><span data-stu-id="46f33-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="46f33-110">Příkaz nabízených oznámení pomocí serveru a přihlašovací údaje podrobnosti nacházející se v konfiguračním souboru systému NuGet nebo řetězec konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="46f33-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="46f33-111">Další informace o konfiguračních souborů naleznete v tématu [konfigurace chování Nugetu](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="46f33-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="46f33-112">Výchozí konfigurace NuGet se získá načítání *%AppData%\NuGet\NuGet.config* (Windows) nebo *$HOME/.local/share* (Linux/macOS), pak všechny načítání *nuget.config*nebo *.nuget\nuget.config* od kořenové jednotky a končí v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="46f33-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="46f33-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="46f33-113">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="46f33-114">Určuje cestu souboru pro balíček, který má být vložena.</span><span class="sxs-lookup"><span data-stu-id="46f33-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="46f33-115">Možnosti</span><span class="sxs-lookup"><span data-stu-id="46f33-115">Options</span></span>

* **`-d|--disable-buffering`**

  <span data-ttu-id="46f33-116">Zakáže ukládání do vyrovnávací paměti při odesílání na server HTTP (S) ke snížení využití paměti.</span><span class="sxs-lookup"><span data-stu-id="46f33-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="46f33-117">Přinutí aplikaci běžet v invariantní, základem je angličtina jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="46f33-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

<span data-ttu-id="46f33-118">Vytiskne krátký nápovědy pro příkaz.</span><span class="sxs-lookup"><span data-stu-id="46f33-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="46f33-119">Umožňuje příkazu blokování a vyžaduje ruční akci pro operace, jako je například ověřování.</span><span class="sxs-lookup"><span data-stu-id="46f33-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="46f33-120">Možnost dostupné od verze sady SDK 2.2 .NET Core.</span><span class="sxs-lookup"><span data-stu-id="46f33-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="46f33-121">Klíč rozhraní API pro server.</span><span class="sxs-lookup"><span data-stu-id="46f33-121">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="46f33-122">Nelze vložit symboly (i když je k dispozici).</span><span class="sxs-lookup"><span data-stu-id="46f33-122">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="46f33-123">"Api/v2/balíček" nemá připojení k zdrojová adresa URL.</span><span class="sxs-lookup"><span data-stu-id="46f33-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="46f33-124">Možnost dostupné od verze sady SDK .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="46f33-124">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="46f33-125">Určuje adresu URL serveru.</span><span class="sxs-lookup"><span data-stu-id="46f33-125">Specifies the server URL.</span></span> <span data-ttu-id="46f33-126">Tato možnost je vyžadována, pokud `DefaultPushSource` konfigurační hodnota je nastavena v konfiguračním souboru NuGet.</span><span class="sxs-lookup"><span data-stu-id="46f33-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="46f33-127">Klíč rozhraní API pro server symbolů.</span><span class="sxs-lookup"><span data-stu-id="46f33-127">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="46f33-128">Určuje adresu URL serveru symbolů.</span><span class="sxs-lookup"><span data-stu-id="46f33-128">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="46f33-129">Určuje časový limit pro odesílání na server v řádu sekund.</span><span class="sxs-lookup"><span data-stu-id="46f33-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="46f33-130">Výchozí hodnota je 300 sekund (5 minut).</span><span class="sxs-lookup"><span data-stu-id="46f33-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="46f33-131">Zadání 0 (nula sekund) použije výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="46f33-131">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="46f33-132">Příklady</span><span class="sxs-lookup"><span data-stu-id="46f33-132">Examples</span></span>

* <span data-ttu-id="46f33-133">Nabízených oznámení *foo.nupkg* nabízených oznámení na výchozí zdroj určení klíče rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="46f33-133">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="46f33-134">Push *foo.nupkg* ke zdroji vlastní nabízené `https://customsource`, určení klíče rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="46f33-134">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="46f33-135">Nabízených oznámení *foo.nupkg* pro výchozí zdroj nabízených oznámení:</span><span class="sxs-lookup"><span data-stu-id="46f33-135">Pushes *foo.nupkg* to the default push source:</span></span>

  ```console
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="46f33-136">Nabízených oznámení *foo.symbols.nupkg* pro výchozí zdroj symboly:</span><span class="sxs-lookup"><span data-stu-id="46f33-136">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```console
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="46f33-137">Nabízených oznámení *foo.nupkg* ke zdroji nabízené výchozí zadání časového limitu 360 druhé:</span><span class="sxs-lookup"><span data-stu-id="46f33-137">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```console
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="46f33-138">Nabízených oznámení všem *.nupkg* soubory v aktuálním adresáři pro výchozí zdroj nabízených oznámení:</span><span class="sxs-lookup"><span data-stu-id="46f33-138">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```console
  dotnet nuget push *.nupkg
  ```
  
  > [!NOTE]
  > <span data-ttu-id="46f33-139">Pokud tento příkaz nefunguje, může být z důvodu chyb, které existovaly ve starších verzích sady SDK (sady SDK .NET Core 2.1 a starší verze).</span><span class="sxs-lookup"><span data-stu-id="46f33-139">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="46f33-140">Tento problém můžete upgradovat vaše verze sady SDK nebo místo toho spuštěním následujícího příkazu: `dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="46f33-140">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>
