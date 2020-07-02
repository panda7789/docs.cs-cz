---
ms.openlocfilehash: ea2883912907843e4b6d65db5ba186af43f27aaa
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85806131"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="251a6-101">Jako alternativu ke správcům balíčků si můžete stáhnout a ručně nainstalovat sadu SDK a modul runtime.</span><span class="sxs-lookup"><span data-stu-id="251a6-101">As an alternative to the package managers, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="251a6-102">Ruční instalace se obvykle provádí jako součást testování průběžné integrace nebo při nepodporované distribuci systému Linux.</span><span class="sxs-lookup"><span data-stu-id="251a6-102">Manual install is usually performed as part of continuous integration testing or on an unsupported Linux distribution.</span></span> <span data-ttu-id="251a6-103">Pro vývojáře nebo uživatele je obecně lepší používat Správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="251a6-103">For a developer or user, it's generally better to use a package manager.</span></span>

<span data-ttu-id="251a6-104">Pokud nainstalujete .NET Core SDK, nemusíte instalovat odpovídající modul runtime.</span><span class="sxs-lookup"><span data-stu-id="251a6-104">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="251a6-105">Nejprve stáhněte **binární** verzi pro sadu SDK nebo modul runtime z jednoho z následujících lokalit:</span><span class="sxs-lookup"><span data-stu-id="251a6-105">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="251a6-106">[soubory ke stažení ✔️ .net 5,0 Preview](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="251a6-106">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="251a6-107">[soubory ke stažení ✔️ .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="251a6-107">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="251a6-108">[soubory ke stažení ✔️ .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="251a6-108">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="251a6-109">Všechny soubory ke stažení pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="251a6-109">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="251a6-110">Dále Extrahujte stažený soubor a pomocí `export` příkazu nastavte proměnné používané .NET Core a pak zajistěte, aby byl .NET Core v cestě.</span><span class="sxs-lookup"><span data-stu-id="251a6-110">Next, extract the downloaded file and use the `export` command to set variables used by .NET Core and then ensure .NET Core is in PATH.</span></span>

<span data-ttu-id="251a6-111">Chcete-li extrahovat modul runtime a zpřístupnit příkazy .NET Core CLI v terminálu, nejprve Stáhněte binární verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="251a6-111">To extract the runtime and make the .NET Core CLI commands available at the terminal, first download a .NET Core binary release.</span></span> <span data-ttu-id="251a6-112">Pak otevřete terminál a spusťte následující příkazy z adresáře, kam byl soubor uložen.</span><span class="sxs-lookup"><span data-stu-id="251a6-112">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="251a6-113">Název souboru archivu se může lišit v závislosti na tom, co jste stáhli.</span><span class="sxs-lookup"><span data-stu-id="251a6-113">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="251a6-114">**K extrakci modulu runtime použijte následující příkaz**:</span><span class="sxs-lookup"><span data-stu-id="251a6-114">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="251a6-115">**K extrakci sady SDK použijte následující příkaz**:</span><span class="sxs-lookup"><span data-stu-id="251a6-115">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="251a6-116">Předchozí `export` příkazy zpřístupní pouze příkazy .NET Core CLI pro relaci terminálu, ve které byla spuštěna.</span><span class="sxs-lookup"><span data-stu-id="251a6-116">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="251a6-117">Úpravou profilu prostředí můžete tyto příkazy trvale přidat.</span><span class="sxs-lookup"><span data-stu-id="251a6-117">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="251a6-118">K dispozici je řada různých prostředí pro Linux a každá má jiný profil.</span><span class="sxs-lookup"><span data-stu-id="251a6-118">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="251a6-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="251a6-119">For example:</span></span>
>
> - <span data-ttu-id="251a6-120">**Prostředí bash**: *~/. bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="251a6-120">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="251a6-121">**Korn shell**: *~/.KSHRC* nebo *. Profile*</span><span class="sxs-lookup"><span data-stu-id="251a6-121">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="251a6-122">**Prostředí Z**: *~/.zshrc* nebo *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="251a6-122">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="251a6-123">Upravte příslušný zdrojový soubor pro prostředí a přidejte `:$HOME/dotnet` na konec existujícího `PATH` příkazu.</span><span class="sxs-lookup"><span data-stu-id="251a6-123">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="251a6-124">Pokud `PATH` není žádný příkaz zahrnutý, přidejte nový řádek s `export PATH=$PATH:$HOME/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="251a6-124">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="251a6-125">Přidejte také `export DOTNET_ROOT=$HOME/dotnet` na konec souboru.</span><span class="sxs-lookup"><span data-stu-id="251a6-125">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="251a6-126">Tento přístup umožňuje nainstalovat různé verze do samostatných umístění a zvolit, která z nich se má použít pro kterou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="251a6-126">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>
