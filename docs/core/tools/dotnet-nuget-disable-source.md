---
title: dotnet nuget zakázat zdrojový příkaz
description: Dotnet nuget zakázat zdrojový příkaz zakáže existující zdroj v konfiguračních souborech NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 54acb40b1944eaff347107e8f3439578ec8e0f3c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463571"
---
# <a name="dotnet-nuget-disable-source"></a><span data-ttu-id="4a0b7-103">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="4a0b7-103">dotnet nuget disable source</span></span>

<span data-ttu-id="4a0b7-104">**Tento článek se týká:** ✔️ .NET Core 3.1.200 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="4a0b7-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="4a0b7-105">Název</span><span class="sxs-lookup"><span data-stu-id="4a0b7-105">Name</span></span>

<span data-ttu-id="4a0b7-106">`dotnet nuget disable source`- Zakázat zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="4a0b7-106">`dotnet nuget disable source` - Disable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4a0b7-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="4a0b7-107">Synopsis</span></span>

```dotnetcli
dotnet nuget disable source <NAME> [--configfile <FILE>]

dotnet nuget disable source -h|--help
```

## <a name="description"></a><span data-ttu-id="4a0b7-108">Popis</span><span class="sxs-lookup"><span data-stu-id="4a0b7-108">Description</span></span>

<span data-ttu-id="4a0b7-109">Příkaz `dotnet nuget disable source` zakáže existující zdroj v konfiguračních souborech NuGet.</span><span class="sxs-lookup"><span data-stu-id="4a0b7-109">The `dotnet nuget disable source` command disables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="4a0b7-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4a0b7-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="4a0b7-111">Název zdroje.</span><span class="sxs-lookup"><span data-stu-id="4a0b7-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="4a0b7-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="4a0b7-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="4a0b7-113">Konfigurační soubor NuGet.</span><span class="sxs-lookup"><span data-stu-id="4a0b7-113">The NuGet configuration file.</span></span> <span data-ttu-id="4a0b7-114">Pokud je zadán, budou použita pouze nastavení z tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="4a0b7-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="4a0b7-115">Pokud není zadán, bude použita hierarchie konfiguračních souborů z aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="4a0b7-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="4a0b7-116">Další informace naleznete [v tématu Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="4a0b7-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="4a0b7-117">Příklady</span><span class="sxs-lookup"><span data-stu-id="4a0b7-117">Examples</span></span>

- <span data-ttu-id="4a0b7-118">Zakázat zdroj s `mySource`názvem :</span><span class="sxs-lookup"><span data-stu-id="4a0b7-118">Disable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget disable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="4a0b7-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a0b7-119">See also</span></span>

- [<span data-ttu-id="4a0b7-120">Zdrojové oddíly balíčku v souborech NuGet.config</span><span class="sxs-lookup"><span data-stu-id="4a0b7-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="4a0b7-121">příkaz zdroje (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="4a0b7-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
