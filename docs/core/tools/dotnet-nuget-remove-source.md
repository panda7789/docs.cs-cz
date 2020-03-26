---
title: dotnet nuget odebrat zdroj ový příkaz
description: Dotnet nuget odebrat zdroj příkaz odebere existující zdroj z konfiguračních souborů NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 65c97b98ab50121fb4ebc184da65f021c16e0634
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148538"
---
# <a name="dotnet-nuget-remove-source"></a><span data-ttu-id="42a23-103">dotnet nuget odebrat zdroj</span><span class="sxs-lookup"><span data-stu-id="42a23-103">dotnet nuget remove source</span></span>

<span data-ttu-id="42a23-104">**Tento článek se týká:** ✔️ .NET Core 3.1.200 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="42a23-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="42a23-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="42a23-105">Name</span></span>

<span data-ttu-id="42a23-106">`dotnet nuget remove source`- Odeberte zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="42a23-106">`dotnet nuget remove source` - Remove a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="42a23-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="42a23-107">Synopsis</span></span>

```dotnetcli
dotnet nuget remove source <NAME> [--configfile]
dotnet nuget remove source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="42a23-108">Popis</span><span class="sxs-lookup"><span data-stu-id="42a23-108">Description</span></span>

<span data-ttu-id="42a23-109">Příkaz `dotnet nuget remove source` odebere existující zdroj z konfiguračních souborů NuGet.</span><span class="sxs-lookup"><span data-stu-id="42a23-109">The `dotnet nuget remove source` command removes an existing source from your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="42a23-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="42a23-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="42a23-111">Název zdroje.</span><span class="sxs-lookup"><span data-stu-id="42a23-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="42a23-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="42a23-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="42a23-113">Konfigurační soubor NuGet.</span><span class="sxs-lookup"><span data-stu-id="42a23-113">The NuGet configuration file.</span></span> <span data-ttu-id="42a23-114">Pokud je zadán, budou použita pouze nastavení z tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="42a23-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="42a23-115">Pokud není zadán, bude použita hierarchie konfiguračních souborů z aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="42a23-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="42a23-116">Další informace naleznete [v tématu Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="42a23-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="42a23-117">Příklady</span><span class="sxs-lookup"><span data-stu-id="42a23-117">Examples</span></span>

- <span data-ttu-id="42a23-118">Odebrání zdroje s `mySource`názvem :</span><span class="sxs-lookup"><span data-stu-id="42a23-118">Remove a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="42a23-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="42a23-119">See also</span></span>

- [<span data-ttu-id="42a23-120">Zdrojové oddíly balíčku v souborech NuGet.config</span><span class="sxs-lookup"><span data-stu-id="42a23-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="42a23-121">příkaz zdroje (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="42a23-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
