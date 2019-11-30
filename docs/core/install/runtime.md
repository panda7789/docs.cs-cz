---
title: Instalace modulu runtime .NET Core v systémech Windows, Linux a macOS – .NET Core
description: Přečtěte si, jak nainstalovat .NET Core v systému Windows, Linux a macOS. Objevte závislosti potřebné ke spouštění aplikací .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: fbe9b9e12dc53d9ab6570299e03f2b0a8868fb53
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567270"
---
# <a name="install-the-net-core-runtime"></a>Instalace modulu runtime .NET Core

V tomto článku se dozvíte, jak stáhnout a nainstalovat modul runtime .NET Core. Modul runtime .NET Core se používá ke spouštění aplikací vytvořených pomocí .NET Core.

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a>Instalace pomocí instalačního programu

Windows i macOS mají samostatné instalační programy, které je možné použít k instalaci modulu runtime .NET Core 3,0.

- Procesory Windows [x64 (64-bit)](https://dotnet.microsoft.com/download/dotnet-core/3.0) | procesory [x86 (32 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- macOS [procesory x64 (64 bitů)](https://dotnet.microsoft.com/download/dotnet-core/3.0)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Instalace pomocí Správce balíčků

Modul runtime .NET Core můžete nainstalovat pomocí mnoha běžných správců balíčků pro Linux. Další informace najdete v tématu [Správce balíčků pro Linux – instalace .NET Core](linux-package-manager-rhel7.md).

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Instalace pomocí automatizace PowerShellu

[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci bez správy modulu runtime. Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).

Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 2,1. Chcete-li nainstalovat aktuální vydání rozhraní .NET Core (3,0), spusťte skript s následujícím přepínačem:

```powershell
dotnet-install.ps1 -Channel 3.0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Instalace pomocí služby bash Automation

[Dotnet – instalační skripty](../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci bez správy modulu runtime. Skript si můžete stáhnout z [referenční stránky dotnet-install Script](../tools/dotnet-install-script.md).

Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 2,1. Chcete-li nainstalovat aktuální vydání rozhraní .NET Core (3,0), spusťte skript s následujícím přepínačem:

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a>Všechny soubory ke stažení pro .NET Core

.NET Core můžete stáhnout a nainstalovat přímo s jedním z následujících odkazů:

- [Soubory ke stažení pro .NET Core 3,1 Preview](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Soubory ke stažení pro .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [Soubory ke stažení pro .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [Soubory ke stažení pro .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Kontejnery poskytují jednoduchý způsob izolace vaší aplikace ze zbytku hostitelského systému. Kontejnery na stejném počítači sdílejí jenom jádro a používají prostředky, které jsou dané aplikaci k.

.NET Core může běžet v kontejneru Docker. Oficiální image Docker pro .NET Core jsou publikované ve službě Microsoft Container Registry (MCR) a jsou zjistitelné v [úložišti Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/). Každé úložiště obsahuje obrázky pro různé kombinace rozhraní .NET (SDK nebo modulu runtime) a operačního systému, které můžete použít.

Společnost Microsoft poskytuje obrázky, které jsou upraveny pro konkrétní scénáře. Například [úložiště ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) poskytuje obrázky, které jsou vytvořené pro spouštění ASP.NET Core aplikací v produkčním prostředí.

Další informace o použití .NET Core v kontejneru Docker najdete v tématu [Úvod do .NET a Docker](../docker/introduction.md) a [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Další kroky

- [Jak zjistit, zda je rozhraní .NET Core již nainstalováno](how-to-detect-installed-versions.md).
