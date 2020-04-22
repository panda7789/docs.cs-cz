---
title: Instalace dalších ML.NET závislostí
description: Zjistěte, jak nainstalovat všechny nativní knihovny, na kterých jsou ML.NET balíčky závislé, ale neinstalují se s balíčky NuGet.
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: c427439d0950bfea38f1d6d11af84216e0f1965f
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021854"
---
# <a name="install-extra-mlnet-dependencies"></a>Instalace dalších ML.NET závislostí

Ve většině případů ve všech operačních systémech je instalace ML.NET stejně jednoduchá jako odkazování na příslušný balíček NuGet.

```bash
dotnet add package Microsoft.ML
```

V některých případech však existují další požadavky na instalaci, zejména pokud jsou požadovány nativní součásti. Tento dokument popisuje požadavky na instalaci pro tyto případy. Oddíly jsou rozděleny `Microsoft.ML.*` podle konkrétní nuget balíček, který má další závislost.

## <a name="microsoftmltimeseries-microsoftmlautoml"></a>Časové řady Microsoft.ML., Microsoft.ML.AutoML

Oba tyto balíčky mají `Microsoft.ML.MKL.Redist`závislost na , který `libiomp`má závislost na .

### <a name="windows"></a>Windows

Nejsou vyžadovány žádné další kroky instalace. Knihovna je nainstalována při přidání balíčku NuGet do projektu.

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

3. Aktualizovat balíčky

    ```bash
    sudo apt-get update
    ```

4. Instalace MKL

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    Příklad:

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    Určete umístění`libiomp.so`

    ```bash
    find /opt -name "libiomp5.so"
    ```

    Příklad:

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. Přidejte toto umístění do cesty knihovny vytížení:

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a>Mac

1. Nainstalujte knihovnu pomocí`Homebrew`

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
