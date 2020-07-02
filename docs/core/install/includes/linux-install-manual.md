---
ms.openlocfilehash: ea2883912907843e4b6d65db5ba186af43f27aaa
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85806131"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

Jako alternativu ke správcům balíčků si můžete stáhnout a ručně nainstalovat sadu SDK a modul runtime. Ruční instalace se obvykle provádí jako součást testování průběžné integrace nebo při nepodporované distribuci systému Linux. Pro vývojáře nebo uživatele je obecně lepší používat Správce balíčků.

Pokud nainstalujete .NET Core SDK, nemusíte instalovat odpovídající modul runtime. Nejprve stáhněte **binární** verzi pro sadu SDK nebo modul runtime z jednoho z následujících lokalit:

- [soubory ke stažení ✔️ .net 5,0 Preview](https://dotnet.microsoft.com/download/dotnet/5.0)
- [soubory ke stažení ✔️ .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [soubory ke stažení ✔️ .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [Všechny soubory ke stažení pro .NET Core](https://dotnet.microsoft.com/download/dotnet-core)

Dále Extrahujte stažený soubor a pomocí `export` příkazu nastavte proměnné používané .NET Core a pak zajistěte, aby byl .NET Core v cestě.

Chcete-li extrahovat modul runtime a zpřístupnit příkazy .NET Core CLI v terminálu, nejprve Stáhněte binární verzi .NET Core. Pak otevřete terminál a spusťte následující příkazy z adresáře, kam byl soubor uložen. Název souboru archivu se může lišit v závislosti na tom, co jste stáhli.

**K extrakci modulu runtime použijte následující příkaz**:

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**K extrakci sady SDK použijte následující příkaz**:

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Předchozí `export` příkazy zpřístupní pouze příkazy .NET Core CLI pro relaci terminálu, ve které byla spuštěna.
>
> Úpravou profilu prostředí můžete tyto příkazy trvale přidat. K dispozici je řada různých prostředí pro Linux a každá má jiný profil. Příklad:
>
> - **Prostředí bash**: *~/. bash_profile*, *~/.bashrc*
> - **Korn shell**: *~/.KSHRC* nebo *. Profile*
> - **Prostředí Z**: *~/.zshrc* nebo *. zprofile*
>
> Upravte příslušný zdrojový soubor pro prostředí a přidejte `:$HOME/dotnet` na konec existujícího `PATH` příkazu. Pokud `PATH` není žádný příkaz zahrnutý, přidejte nový řádek s `export PATH=$PATH:$HOME/dotnet` .
>
> Přidejte také `export DOTNET_ROOT=$HOME/dotnet` na konec souboru.

Tento přístup umožňuje nainstalovat různé verze do samostatných umístění a zvolit, která z nich se má použít pro kterou aplikaci.
