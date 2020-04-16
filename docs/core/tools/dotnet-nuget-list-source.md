---
title: dotnet nuget zdroj seznamu, příkaz
description: Dotnet nuget seznam zdroj příkaz uvede všechny existující zdroje z konfiguračních souborů NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 8b14413949bd60ddeed977d19eec9bb99982da70
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463539"
---
# <a name="dotnet-nuget-list-source"></a><span data-ttu-id="e7226-103">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="e7226-103">dotnet nuget list source</span></span>

<span data-ttu-id="e7226-104">**Tento článek se týká:** ✔️ .NET Core 3.1.200 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="e7226-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e7226-105">Název</span><span class="sxs-lookup"><span data-stu-id="e7226-105">Name</span></span>

<span data-ttu-id="e7226-106">`dotnet nuget list source`- Zobrazí seznam všech nakonfigurovaných zdrojů NuGet.</span><span class="sxs-lookup"><span data-stu-id="e7226-106">`dotnet nuget list source` - Lists all configured NuGet sources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e7226-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="e7226-107">Synopsis</span></span>

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a><span data-ttu-id="e7226-108">Popis</span><span class="sxs-lookup"><span data-stu-id="e7226-108">Description</span></span>

<span data-ttu-id="e7226-109">Příkaz `dotnet nuget list source` obsahuje seznam všech existujících zdrojů z konfiguračních souborů NuGet.</span><span class="sxs-lookup"><span data-stu-id="e7226-109">The `dotnet nuget list source` command lists all existing sources from your NuGet configuration files.</span></span>

## <a name="options"></a><span data-ttu-id="e7226-110">Možnosti</span><span class="sxs-lookup"><span data-stu-id="e7226-110">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="e7226-111">Konfigurační soubor NuGet.</span><span class="sxs-lookup"><span data-stu-id="e7226-111">The NuGet configuration file.</span></span> <span data-ttu-id="e7226-112">Pokud je zadán, budou použita pouze nastavení z tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="e7226-112">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="e7226-113">Pokud není zadán, bude použita hierarchie konfiguračních souborů z aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="e7226-113">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="e7226-114">Další informace naleznete [v tématu Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="e7226-114">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--format [Detailed|Short]`**

  <span data-ttu-id="e7226-115">Formát výstupu příkazu seznamu: `Detailed` (výchozí) `Short`a .</span><span class="sxs-lookup"><span data-stu-id="e7226-115">The format of the list command output: `Detailed` (the default) and `Short`.</span></span>

## <a name="examples"></a><span data-ttu-id="e7226-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="e7226-116">Examples</span></span>

- <span data-ttu-id="e7226-117">Seznam nakonfigurovaných zdrojů z aktuálního adresáře:</span><span class="sxs-lookup"><span data-stu-id="e7226-117">List configured sources from the current directory:</span></span>

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a><span data-ttu-id="e7226-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7226-118">See also</span></span>

- [<span data-ttu-id="e7226-119">Zdrojové oddíly balíčku v souborech NuGet.config</span><span class="sxs-lookup"><span data-stu-id="e7226-119">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="e7226-120">příkaz zdroje (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="e7226-120">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
