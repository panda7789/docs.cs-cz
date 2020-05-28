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
# <a name="install-extra-mlnet-dependencies"></a>Nainstalovat nadbytečné závislosti ML.NET

Ve většině případů je instalace ML.NET na všech operačních systémech jednoduchá a odkazuje na příslušný balíček NuGet.

```dotnetcli
dotnet add package Microsoft.ML
```

V některých případech existují i další požadavky na instalaci, zejména v případě, že jsou požadovány nativní součásti. Tento dokument popisuje požadavky na instalaci pro tyto případy. Oddíly jsou rozdělené podle konkrétního `Microsoft.ML.*` balíčku NuGet, který má další závislost.

## <a name="microsoftmltimeseries-microsoftmlautoml"></a>Microsoft. ML. časové řady, Microsoft. ML. AutoML

Oba tyto balíčky mají závislost na `Microsoft.ML.MKL.Redist` , která má závislost na `libiomp` .

### <a name="windows"></a>Windows

Nevyžadují se žádné další kroky instalace. Knihovna se nainstaluje, když se do projektu přidá balíček NuGet.

### <a name="linux"></a>Linux

1. Instalace klíče GPG pro úložiště

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

2. Přidání úložiště APT pro MKL

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. Balíčky aktualizací

    ```bash
    sudo apt-get update
    ```

4. Nainstalovat MKL

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    Příklad:

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    Určení umístění`libiomp.so`

    ```bash
    find /opt -name "libiomp5.so"
    ```

    Příklad:

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. Přidat toto umístění do cesty ke knihovně načtení:

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a>Mac

1. Nainstalujte knihovnu s`Homebrew`

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
