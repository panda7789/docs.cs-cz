---
title: Nainstalovat nadbytečné závislosti ML.NET
description: Naučte se instalovat všechny nativní knihovny, na kterých jsou ML.NET balíčky závislé, ale neinstalují se s balíčky NuGet.
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: c744b42b4b95681de7b0cbeaef338cc890708fd8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008427"
---
# <a name="install-extra-mlnet-dependencies"></a><span data-ttu-id="3712e-103">Nainstalovat nadbytečné závislosti ML.NET</span><span class="sxs-lookup"><span data-stu-id="3712e-103">Install extra ML.NET dependencies</span></span>

<span data-ttu-id="3712e-104">Ve většině případů je instalace ML.NET na všech operačních systémech jednoduchá a odkazuje na příslušný balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="3712e-104">In most cases, on all operating systems, installing ML.NET is as simple as referencing the appropriate NuGet package.</span></span>

```dotnetcli
dotnet add package Microsoft.ML
```

<span data-ttu-id="3712e-105">V některých případech existují i další požadavky na instalaci, zejména v případě, že jsou požadovány nativní součásti.</span><span class="sxs-lookup"><span data-stu-id="3712e-105">In some cases though, there are additional installation requirements, particularly when native components are required.</span></span> <span data-ttu-id="3712e-106">Tento dokument popisuje požadavky na instalaci pro tyto případy.</span><span class="sxs-lookup"><span data-stu-id="3712e-106">This document describes the installation requirements for those cases.</span></span> <span data-ttu-id="3712e-107">Oddíly jsou rozdělené podle konkrétního `Microsoft.ML.*` balíčku NuGet, který má další závislost.</span><span class="sxs-lookup"><span data-stu-id="3712e-107">The sections are broken down by the specific `Microsoft.ML.*` NuGet package that has the additional dependency.</span></span>

## <a name="microsoftmltimeseries-microsoftmlautoml"></a><span data-ttu-id="3712e-108">Microsoft. ML. časové řady, Microsoft. ML. AutoML</span><span class="sxs-lookup"><span data-stu-id="3712e-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span></span>

<span data-ttu-id="3712e-109">Oba tyto balíčky mají závislost na `Microsoft.ML.MKL.Redist` , která má závislost na `libiomp` .</span><span class="sxs-lookup"><span data-stu-id="3712e-109">Both of these packages have a dependency on `Microsoft.ML.MKL.Redist`, which has a dependency on `libiomp`.</span></span>

### <a name="windows"></a><span data-ttu-id="3712e-110">Windows</span><span class="sxs-lookup"><span data-stu-id="3712e-110">Windows</span></span>

<span data-ttu-id="3712e-111">Nevyžadují se žádné další kroky instalace.</span><span class="sxs-lookup"><span data-stu-id="3712e-111">No extra installation steps required.</span></span> <span data-ttu-id="3712e-112">Knihovna se nainstaluje, když se do projektu přidá balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="3712e-112">The library is installed when the NuGet package is added to the project.</span></span>

### <a name="linux"></a><span data-ttu-id="3712e-113">Linux</span><span class="sxs-lookup"><span data-stu-id="3712e-113">Linux</span></span>

1. <span data-ttu-id="3712e-114">Instalace klíče GPG pro úložiště</span><span class="sxs-lookup"><span data-stu-id="3712e-114">Install the GPG key for the repository</span></span>

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

2. <span data-ttu-id="3712e-115">Přidání úložiště APT pro MKL</span><span class="sxs-lookup"><span data-stu-id="3712e-115">Add the APT Repository for MKL</span></span>

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. <span data-ttu-id="3712e-116">Balíčky aktualizací</span><span class="sxs-lookup"><span data-stu-id="3712e-116">Update packages</span></span>

    ```bash
    sudo apt-get update
    ```

4. <span data-ttu-id="3712e-117">Nainstalovat MKL</span><span class="sxs-lookup"><span data-stu-id="3712e-117">Install MKL</span></span>

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    <span data-ttu-id="3712e-118">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3712e-118">For example:</span></span>

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    <span data-ttu-id="3712e-119">Určení umístění`libiomp.so`</span><span class="sxs-lookup"><span data-stu-id="3712e-119">Determine the location of `libiomp.so`</span></span>

    ```bash
    find /opt -name "libiomp5.so"
    ```

    <span data-ttu-id="3712e-120">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3712e-120">For example:</span></span>

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. <span data-ttu-id="3712e-121">Přidat toto umístění do cesty ke knihovně načtení:</span><span class="sxs-lookup"><span data-stu-id="3712e-121">Add this location to the load library path:</span></span>

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a><span data-ttu-id="3712e-122">Mac</span><span class="sxs-lookup"><span data-stu-id="3712e-122">Mac</span></span>

1. <span data-ttu-id="3712e-123">Nainstalujte knihovnu s`Homebrew`</span><span class="sxs-lookup"><span data-stu-id="3712e-123">Install the library with `Homebrew`</span></span>

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
