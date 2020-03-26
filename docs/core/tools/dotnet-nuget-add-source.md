---
title: dotnet nuget přidat zdrojový příkaz
description: Dotnet nuget přidat zdrojový příkaz přidá nový zdroj balíčku do konfiguračních souborů NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: c1e398699c7482a69b750cde718e6f9178b5c4bd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148566"
---
# <a name="dotnet-nuget-add-source"></a><span data-ttu-id="fab94-103">dotnet nuget přidat zdroj</span><span class="sxs-lookup"><span data-stu-id="fab94-103">dotnet nuget add source</span></span>

<span data-ttu-id="fab94-104">**Tento článek se týká:** ✔️ .NET Core 3.1.200 SDK a novější verze</span><span class="sxs-lookup"><span data-stu-id="fab94-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="fab94-105">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="fab94-105">Name</span></span>

<span data-ttu-id="fab94-106">`dotnet nuget add source`- Přidejte zdroj NuGet.</span><span class="sxs-lookup"><span data-stu-id="fab94-106">`dotnet nuget add source` - Add a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fab94-107">Synopse</span><span class="sxs-lookup"><span data-stu-id="fab94-107">Synopsis</span></span>

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget add source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="fab94-108">Popis</span><span class="sxs-lookup"><span data-stu-id="fab94-108">Description</span></span>

<span data-ttu-id="fab94-109">Příkaz `dotnet nuget add source` přidá nový zdroj balíčku do konfiguračních souborů NuGet.</span><span class="sxs-lookup"><span data-stu-id="fab94-109">The `dotnet nuget add source` command adds a new package source to your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="fab94-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fab94-110">Arguments</span></span>

- **`PACKAGE_SOURCE_PATH`**

  <span data-ttu-id="fab94-111">Cesta ke zdroji balíčku.</span><span class="sxs-lookup"><span data-stu-id="fab94-111">Path to the package source.</span></span>

## <a name="options"></a><span data-ttu-id="fab94-112">Možnosti</span><span class="sxs-lookup"><span data-stu-id="fab94-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="fab94-113">Konfigurační soubor NuGet.</span><span class="sxs-lookup"><span data-stu-id="fab94-113">The NuGet configuration file.</span></span> <span data-ttu-id="fab94-114">Pokud je zadán, budou použita pouze nastavení z tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="fab94-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="fab94-115">Pokud není zadán, bude použita hierarchie konfiguračních souborů z aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="fab94-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="fab94-116">Další informace naleznete [v tématu Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="fab94-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-n|--name`**

  <span data-ttu-id="fab94-117">Název zdroje.</span><span class="sxs-lookup"><span data-stu-id="fab94-117">Name of the source.</span></span>

- **`-p|--password`**

  <span data-ttu-id="fab94-118">Heslo, které se má použít při připojování k ověřenému zdroji.</span><span class="sxs-lookup"><span data-stu-id="fab94-118">Password to be used when connecting to an authenticated source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="fab94-119">Umožňuje ukládání pověření zdroje přenosných balíčků zakázáním šifrování hesel.</span><span class="sxs-lookup"><span data-stu-id="fab94-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username`**

  <span data-ttu-id="fab94-120">Uživatelské jméno, které má být použito při připojování k ověřenému zdroji.</span><span class="sxs-lookup"><span data-stu-id="fab94-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types`**

  <span data-ttu-id="fab94-121">Seznam platných typů ověřování pro tento zdroj oddělený čárkou.</span><span class="sxs-lookup"><span data-stu-id="fab94-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="fab94-122">Nastavte tuto `basic` možnost na, pokud server inzeruje NTLM nebo Negotiate a vaše přihlašovací údaje musí být odeslány pomocí základnímechanismus, například při použití PAT s místní Azure DevOps Server.</span><span class="sxs-lookup"><span data-stu-id="fab94-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="fab94-123">Mezi další `negotiate`platné `kerberos` `ntlm`hodnoty `digest`patří , , a , ale tyto hodnoty pravděpodobně nebudou užitečné.</span><span class="sxs-lookup"><span data-stu-id="fab94-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="fab94-124">Příklady</span><span class="sxs-lookup"><span data-stu-id="fab94-124">Examples</span></span>

- <span data-ttu-id="fab94-125">Přidat `nuget.org` jako zdroj:</span><span class="sxs-lookup"><span data-stu-id="fab94-125">Add `nuget.org` as a source:</span></span>

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- <span data-ttu-id="fab94-126">Přidat `c:\packages` jako místní zdroj:</span><span class="sxs-lookup"><span data-stu-id="fab94-126">Add `c:\packages` as a local source:</span></span>

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- <span data-ttu-id="fab94-127">Přidejte zdroj, který vyžaduje ověření:</span><span class="sxs-lookup"><span data-stu-id="fab94-127">Add a source that needs authentication:</span></span>

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- <span data-ttu-id="fab94-128">Přidejte zdroj, který potřebuje ověření (pak přejděte k instalaci zprostředkovatele pověření):</span><span class="sxs-lookup"><span data-stu-id="fab94-128">Add a source that needs authentication (then go install credential provider):</span></span>

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a><span data-ttu-id="fab94-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="fab94-129">See also</span></span>

- [<span data-ttu-id="fab94-130">Zdrojové oddíly balíčku v souborech NuGet.config</span><span class="sxs-lookup"><span data-stu-id="fab94-130">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="fab94-131">příkaz zdroje (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="fab94-131">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
