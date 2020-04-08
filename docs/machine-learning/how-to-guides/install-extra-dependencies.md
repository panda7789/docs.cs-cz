---
title: Instalace dalších ML.NET závislostí
description: Zjistěte, jak nainstalovat všechny nativní knihovny, na kterých jsou ML.NET balíčky závislé, ale neinstalují se s balíčky NuGet.
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: 0b870542706c065295d48205b7780e568e267ab6
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888300"
---
# <a name="install-extra-mlnet-dependencies"></a><span data-ttu-id="18cf6-103">Instalace dalších ML.NET závislostí</span><span class="sxs-lookup"><span data-stu-id="18cf6-103">Install extra ML.NET dependencies</span></span>

<span data-ttu-id="18cf6-104">Ve většině případů ve všech operačních systémech je instalace ML.NET stejně jednoduchá jako odkazování na příslušný balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="18cf6-104">In most cases, on all operating systems, installing ML.NET is as simple as referencing the appropriate NuGet package.</span></span>

```bash
dotnet add package Microsoft.ML
```

<span data-ttu-id="18cf6-105">V některých případech však existují další požadavky na instalaci, zejména pokud jsou požadovány nativní součásti.</span><span class="sxs-lookup"><span data-stu-id="18cf6-105">In some cases though, there are additional installation requirements, particularly when native components are required.</span></span> <span data-ttu-id="18cf6-106">Tento dokument popisuje požadavky na instalaci pro tyto případy.</span><span class="sxs-lookup"><span data-stu-id="18cf6-106">This document describes the installation requirements for those cases.</span></span> <span data-ttu-id="18cf6-107">Oddíly jsou rozděleny `Microsoft.ML.*` podle konkrétní nuget balíček, který má další závislost.</span><span class="sxs-lookup"><span data-stu-id="18cf6-107">The sections are broken down by the specific `Microsoft.ML.*` NuGet package that has the additional dependency.</span></span>

## <a name="microsoftmltimeseries-microsoftmlautoml"></a><span data-ttu-id="18cf6-108">Časové řady Microsoft.ML., Microsoft.ML.AutoML</span><span class="sxs-lookup"><span data-stu-id="18cf6-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span></span>

<span data-ttu-id="18cf6-109">Oba tyto balíčky mají `Microsoft.ML.MKL.Redist`závislost na , který `libiomp`má závislost na .</span><span class="sxs-lookup"><span data-stu-id="18cf6-109">Both of these packages have a dependency on `Microsoft.ML.MKL.Redist`, which has a dependency on `libiomp`.</span></span>

### <a name="windows"></a><span data-ttu-id="18cf6-110">Windows</span><span class="sxs-lookup"><span data-stu-id="18cf6-110">Windows</span></span>

<span data-ttu-id="18cf6-111">Nejsou vyžadovány žádné další kroky instalace.</span><span class="sxs-lookup"><span data-stu-id="18cf6-111">No extra installation steps required.</span></span> <span data-ttu-id="18cf6-112">Knihovna je nainstalována při přidání balíčku NuGet do projektu.</span><span class="sxs-lookup"><span data-stu-id="18cf6-112">The library is installed when the NuGet package is added to the project.</span></span>

### <a name="linux"></a><span data-ttu-id="18cf6-113">Linux</span><span class="sxs-lookup"><span data-stu-id="18cf6-113">Linux</span></span>

1. <span data-ttu-id="18cf6-114">Instalace klíče GPG pro úložiště</span><span class="sxs-lookup"><span data-stu-id="18cf6-114">Install the GPG key for the repository</span></span>

    ```bash
    sudo bash
    # <type your user password when prompted.  this will put you in a root shell>
    # cd to /tmp where this shell has write permission
    cd /tmp
    # now get the key:
    wget https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now install that key
    apt-key add GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now remove the public key file exit the root shell
    rm GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    exit
    ```

2. <span data-ttu-id="18cf6-115">Přidání úložiště APT pro MKL</span><span class="sxs-lookup"><span data-stu-id="18cf6-115">Add the APT Repository for MKL</span></span>

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. <span data-ttu-id="18cf6-116">Aktualizovat balíčky</span><span class="sxs-lookup"><span data-stu-id="18cf6-116">Update packages</span></span>

    ```bash
    sudo apt-get update
    ```

4. <span data-ttu-id="18cf6-117">Instalace MKL</span><span class="sxs-lookup"><span data-stu-id="18cf6-117">Install MKL</span></span>

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    <span data-ttu-id="18cf6-118">Příklad:</span><span class="sxs-lookup"><span data-stu-id="18cf6-118">For example:</span></span>

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    <span data-ttu-id="18cf6-119">Určete umístění`libiomp.so`</span><span class="sxs-lookup"><span data-stu-id="18cf6-119">Determine the location of `libiomp.so`</span></span>

    ```bash
    find /opt -name "libiomp5.so"
    ```

    <span data-ttu-id="18cf6-120">Příklad:</span><span class="sxs-lookup"><span data-stu-id="18cf6-120">For example:</span></span>

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. <span data-ttu-id="18cf6-121">Přidejte toto umístění do cesty knihovny vytížení:</span><span class="sxs-lookup"><span data-stu-id="18cf6-121">Add this location to the load library path:</span></span>

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_li
    ```

### <a name="mac"></a><span data-ttu-id="18cf6-122">Mac</span><span class="sxs-lookup"><span data-stu-id="18cf6-122">Mac</span></span>

1. <span data-ttu-id="18cf6-123">Nainstalujte knihovnu pomocí`Homebrew`</span><span class="sxs-lookup"><span data-stu-id="18cf6-123">Install the library with `Homebrew`</span></span>

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
