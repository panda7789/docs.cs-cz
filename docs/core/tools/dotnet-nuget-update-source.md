---
title: Dotnet nuget zdroj aktualizace příkaz
description: Dotnet nuget update source command updates a existing source in your NuGet configuration files.
ms.date: 03/20/2020
ms.openlocfilehash: 42b1aec95cdd57e53f966400f6692a3d0150c16c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463481"
---
# <a name="dotnet-nuget-update-source"></a><span data-ttu-id="26007-103">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="26007-103">dotnet nuget update source</span></span>

<span data-ttu-id="26007-104">**Tento článek se týká:** ✔️ .NET Core 3.1.200 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="26007-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="26007-105">Název</span><span class="sxs-lookup"><span data-stu-id="26007-105">Name</span></span>

<span data-ttu-id="26007-106">`dotnet nuget update source`- Aktualizace nuget zdroj.</span><span class="sxs-lookup"><span data-stu-id="26007-106">`dotnet nuget update source` - Update a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="26007-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="26007-107">Synopsis</span></span>

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a><span data-ttu-id="26007-108">Popis</span><span class="sxs-lookup"><span data-stu-id="26007-108">Description</span></span>

<span data-ttu-id="26007-109">Příkaz `dotnet nuget update source` aktualizuje existující zdroj v konfiguračních souborech NuGet.</span><span class="sxs-lookup"><span data-stu-id="26007-109">The `dotnet nuget update source` command updates an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="26007-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="26007-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="26007-111">Název zdroje.</span><span class="sxs-lookup"><span data-stu-id="26007-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="26007-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="26007-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="26007-113">Konfigurační soubor NuGet.</span><span class="sxs-lookup"><span data-stu-id="26007-113">The NuGet configuration file.</span></span> <span data-ttu-id="26007-114">Pokud je zadán, budou použita pouze nastavení z tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="26007-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="26007-115">Pokud není zadán, bude použita hierarchie konfiguračních souborů z aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="26007-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="26007-116">Další informace naleznete [v tématu Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="26007-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="26007-117">Heslo, které se má použít při připojování k ověřenému zdroji.</span><span class="sxs-lookup"><span data-stu-id="26007-117">Password to be used when connecting to an authenticated source.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="26007-118">Cesta ke zdroji balíčku.</span><span class="sxs-lookup"><span data-stu-id="26007-118">Path to the package source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="26007-119">Umožňuje ukládání pověření zdroje přenosných balíčků zakázáním šifrování hesel.</span><span class="sxs-lookup"><span data-stu-id="26007-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="26007-120">Uživatelské jméno, které má být použito při připojování k ověřenému zdroji.</span><span class="sxs-lookup"><span data-stu-id="26007-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="26007-121">Seznam platných typů ověřování pro tento zdroj oddělený čárkou.</span><span class="sxs-lookup"><span data-stu-id="26007-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="26007-122">Nastavte tuto `basic` možnost na, pokud server inzeruje NTLM nebo Negotiate a vaše přihlašovací údaje musí být odeslány pomocí základnímechanismus, například při použití PAT s místní Azure DevOps Server.</span><span class="sxs-lookup"><span data-stu-id="26007-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="26007-123">Mezi další `negotiate`platné `kerberos` `ntlm`hodnoty `digest`patří , , a , ale tyto hodnoty pravděpodobně nebudou užitečné.</span><span class="sxs-lookup"><span data-stu-id="26007-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="26007-124">Příklady</span><span class="sxs-lookup"><span data-stu-id="26007-124">Examples</span></span>

- <span data-ttu-id="26007-125">Aktualizace zdroje s `mySource`názvem :</span><span class="sxs-lookup"><span data-stu-id="26007-125">Update a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a><span data-ttu-id="26007-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="26007-126">See also</span></span>

- [<span data-ttu-id="26007-127">Zdrojové oddíly balíčku v souborech NuGet.config</span><span class="sxs-lookup"><span data-stu-id="26007-127">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="26007-128">příkaz zdroje (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="26007-128">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
