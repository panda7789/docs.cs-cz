---
ms.openlocfilehash: e7d35045892c62f759aad5067962ac5c15a9fb8b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602927"
---

.NET Core SDK i modul runtime .NET Core lze po stažení ručně nainstalovat. Pokud nainstalujete .NET Core SDK, nemusíte instalovat odpovídající modul runtime. Nejprve Stáhněte binární verzi pro sadu SDK nebo modul runtime z jednoho z následujících lokalit:

- [soubory ke stažení ✔️ .net 5,0 Preview](https://dotnet.microsoft.com/download/dotnet/5.0)
- [soubory ke stažení ✔️ .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ❌[Soubory ke stažení pro .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- ❌[Soubory ke stažení pro .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [soubory ke stažení ✔️ .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

Dále Extrahujte stažený soubor a pomocí `export` příkazu nastavte proměnné používané .NET Core a pak zajistěte, aby byl .NET Core v cestě.

Chcete-li extrahovat modul runtime a zpřístupnit příkazy .NET Core CLI v terminálu, nejprve Stáhněte binární verzi .NET Core. Pak otevřete terminál a spusťte následující příkazy z adresáře, kam byl soubor uložen.

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Předchozí `export` příkazy zpřístupní pouze příkazy .NET Core CLI pro relaci terminálu, ve které byla spuštěna.
>
> Úpravou profilu prostředí můžete tyto příkazy trvale přidat. K dispozici je řada různých prostředí pro Linux a každá má jiný profil. Například:
>
> - **Prostředí bash**: *~/. bash_profile*, *~/.bashrc*
> - **Korn shell**: *~/.KSHRC* nebo *. Profile*
> - **Prostředí Z**: *~/.zshrc* nebo *. zprofile*
>
> Upravte příslušný zdrojový soubor pro prostředí a přidejte `:$HOME/dotnet` na konec existujícího `PATH` příkazu. Pokud `PATH` není žádný příkaz zahrnutý, přidejte nový řádek s `export PATH=$PATH:$HOME/dotnet` .
>
> Přidejte také `export DOTNET_ROOT=$HOME/dotnet` na konec souboru.

Tento přístup umožňuje nainstalovat různé verze do samostatných umístění a zvolit, která z nich se má použít pro kterou aplikaci.
