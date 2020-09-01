---
ms.openlocfilehash: 9d4c031eda291b0a8832c824789efdffe4084926
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132938"
---

<span data-ttu-id="4ff1e-101">Pokud se zobrazí chybová zpráva podobná té, že se **nepovedlo najít balíček {Netcore-Package}** nebo **některé balíčky nešlo nainstalovat**, spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="4ff1e-101">If you receive an error message similar to **Unable to locate package {netcore-package}** or **Some packages could not be installed**, run the following commands.</span></span>

<span data-ttu-id="4ff1e-102">Následující sada příkazů obsahuje dva zástupné symboly.</span><span class="sxs-lookup"><span data-stu-id="4ff1e-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="4ff1e-103">To představuje balíček .NET Core, který instalujete, například `aspnetcore-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="4ff1e-103">This represents the .NET Core package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="4ff1e-104">Tento příkaz se používá v `sudo apt-get install` níže uvedeném příkazu.</span><span class="sxs-lookup"><span data-stu-id="4ff1e-104">This is used in the `sudo apt-get install` command below.</span></span>

- `{os-version}`\
<span data-ttu-id="4ff1e-105">To představuje verzi systému Linux, na které se nacházíte.</span><span class="sxs-lookup"><span data-stu-id="4ff1e-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="4ff1e-106">Tento příkaz se používá v `wget` níže uvedeném příkazu.</span><span class="sxs-lookup"><span data-stu-id="4ff1e-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="4ff1e-107">Nejdřív zkuste seznam balíčků vypsat:</span><span class="sxs-lookup"><span data-stu-id="4ff1e-107">First, try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
```

<span data-ttu-id="4ff1e-108">Pak zkuste znovu nainstalovat .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4ff1e-108">Then, try to install .NET Core again.</span></span> <span data-ttu-id="4ff1e-109">Pokud to nefunguje, můžete spustit ruční instalaci s následujícími příkazy:</span><span class="sxs-lookup"><span data-stu-id="4ff1e-109">If that doesn't work, you can run a manual install with the following commands:</span></span>
