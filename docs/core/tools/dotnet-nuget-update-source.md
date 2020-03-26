---
title: Dotnet nuget zdroj aktualizace příkaz
description: Dotnet nuget update source command updates a existing source in your NuGet configuration files.
ms.date: 03/20/2020
ms.openlocfilehash: 38335e07f91850756c7671413e1193c2578e7e7e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148545"
---
# <a name="dotnet-nuget-update-source"></a><span data-ttu-id="b64e4-103">Zdroj aktualizace dotnet nuget</span><span class="sxs-lookup"><span data-stu-id="b64e4-103">dotnet nuget update source</span></span>

<span data-ttu-id="b64e4-104">**Tento článek se týká:** ✔️ .NET Core 3.1.200 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="b64e4-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b64e4-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="b64e4-105">Name</span></span>

<span data-ttu-id="b64e4-106">`dotnet nuget update source`- Aktualizace nuget zdroj.</span><span class="sxs-lookup"><span data-stu-id="b64e4-106">`dotnet nuget update source` - Update a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b64e4-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="b64e4-107">Synopsis</span></span>

```dotnetcli
dotnet nuget update source <NAME> [--source] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget update source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="b64e4-108">Popis</span><span class="sxs-lookup"><span data-stu-id="b64e4-108">Description</span></span>

<span data-ttu-id="b64e4-109">Příkaz `dotnet nuget update source` aktualizuje existující zdroj v konfiguračních souborech NuGet.</span><span class="sxs-lookup"><span data-stu-id="b64e4-109">The `dotnet nuget update source` command updates an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="b64e4-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b64e4-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="b64e4-111">Název zdroje.</span><span class="sxs-lookup"><span data-stu-id="b64e4-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="b64e4-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="b64e4-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="b64e4-113">Konfigurační soubor NuGet.</span><span class="sxs-lookup"><span data-stu-id="b64e4-113">The NuGet configuration file.</span></span> <span data-ttu-id="b64e4-114">Pokud je zadán, budou použita pouze nastavení z tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="b64e4-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="b64e4-115">Pokud není zadán, bude použita hierarchie konfiguračních souborů z aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="b64e4-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="b64e4-116">Další informace naleznete [v tématu Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="b64e4-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-p|--password`**

  <span data-ttu-id="b64e4-117">Heslo, které se má použít při připojování k ověřenému zdroji.</span><span class="sxs-lookup"><span data-stu-id="b64e4-117">Password to be used when connecting to an authenticated source.</span></span>

- **`-s|--source`**

  <span data-ttu-id="b64e4-118">Cesta ke zdroji balíčku.</span><span class="sxs-lookup"><span data-stu-id="b64e4-118">Path to the package source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="b64e4-119">Umožňuje ukládání pověření zdroje přenosných balíčků zakázáním šifrování hesel.</span><span class="sxs-lookup"><span data-stu-id="b64e4-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username`**

  <span data-ttu-id="b64e4-120">Uživatelské jméno, které má být použito při připojování k ověřenému zdroji.</span><span class="sxs-lookup"><span data-stu-id="b64e4-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types`**

  <span data-ttu-id="b64e4-121">Seznam platných typů ověřování pro tento zdroj oddělený čárkou.</span><span class="sxs-lookup"><span data-stu-id="b64e4-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="b64e4-122">Nastavte tuto `basic` možnost na, pokud server inzeruje NTLM nebo Negotiate a vaše přihlašovací údaje musí být odeslány pomocí základnímechanismus, například při použití PAT s místní Azure DevOps Server.</span><span class="sxs-lookup"><span data-stu-id="b64e4-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="b64e4-123">Mezi další `negotiate`platné `kerberos` `ntlm`hodnoty `digest`patří , , a , ale tyto hodnoty pravděpodobně nebudou užitečné.</span><span class="sxs-lookup"><span data-stu-id="b64e4-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="b64e4-124">Příklady</span><span class="sxs-lookup"><span data-stu-id="b64e4-124">Examples</span></span>

- <span data-ttu-id="b64e4-125">Aktualizace zdroje s `mySource`názvem :</span><span class="sxs-lookup"><span data-stu-id="b64e4-125">Update a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a><span data-ttu-id="b64e4-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="b64e4-126">See also</span></span>

- [<span data-ttu-id="b64e4-127">Zdrojové oddíly balíčku v souborech NuGet.config</span><span class="sxs-lookup"><span data-stu-id="b64e4-127">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="b64e4-128">příkaz zdroje (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="b64e4-128">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
