---
title: dotnet nuget povolit zdrojový příkaz
description: Dotnet nuget povolit zdrojový příkaz umožňuje existující zdroj v konfiguračních souborech NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 38fb5917361bd7952fef9c31ed897fb81f005155
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463563"
---
# <a name="dotnet-nuget-enable-source"></a><span data-ttu-id="314da-103">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="314da-103">dotnet nuget enable source</span></span>

<span data-ttu-id="314da-104">**Tento článek se týká:** ✔️ .NET Core 3.1.200 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="314da-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="314da-105">Název</span><span class="sxs-lookup"><span data-stu-id="314da-105">Name</span></span>

<span data-ttu-id="314da-106">`dotnet nuget enable source`- Povolte zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="314da-106">`dotnet nuget enable source` - Enable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="314da-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="314da-107">Synopsis</span></span>

```dotnetcli
dotnet nuget enable source <NAME> [--configfile <FILE>]

dotnet nuget enable source -h|--help
```

## <a name="description"></a><span data-ttu-id="314da-108">Popis</span><span class="sxs-lookup"><span data-stu-id="314da-108">Description</span></span>

<span data-ttu-id="314da-109">Příkaz `dotnet nuget enable source` povolí existující zdroj v konfiguračních souborech NuGet.</span><span class="sxs-lookup"><span data-stu-id="314da-109">The `dotnet nuget enable source` command enables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="314da-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="314da-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="314da-111">Název zdroje.</span><span class="sxs-lookup"><span data-stu-id="314da-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="314da-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="314da-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="314da-113">Konfigurační soubor NuGet.</span><span class="sxs-lookup"><span data-stu-id="314da-113">The NuGet configuration file.</span></span> <span data-ttu-id="314da-114">Pokud je zadán, budou použita pouze nastavení z tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="314da-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="314da-115">Pokud není zadán, bude použita hierarchie konfiguračních souborů z aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="314da-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="314da-116">Další informace naleznete [v tématu Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="314da-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="314da-117">Příklady</span><span class="sxs-lookup"><span data-stu-id="314da-117">Examples</span></span>

- <span data-ttu-id="314da-118">Povolit zdroj s `mySource`názvem :</span><span class="sxs-lookup"><span data-stu-id="314da-118">Enable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="314da-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="314da-119">See also</span></span>

- [<span data-ttu-id="314da-120">Zdrojové oddíly balíčku v souborech NuGet.config</span><span class="sxs-lookup"><span data-stu-id="314da-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="314da-121">příkaz zdroje (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="314da-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
