---
ms.openlocfilehash: 7d398df060c031ae891218b82a2712d74f4c33b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602983"
---

<span data-ttu-id="cecb5-101">Pokud se zobrazí chybová zpráva podobná té, že se **nepovedlo najít balíček {Netcore-Package}**, spusťte následující příkazy.</span><span class="sxs-lookup"><span data-stu-id="cecb5-101">If you receive an error message similar to **Unable to locate package {netcore-package}**, run the following commands.</span></span>

<span data-ttu-id="cecb5-102">Následující sada příkazů obsahuje dva zástupné symboly.</span><span class="sxs-lookup"><span data-stu-id="cecb5-102">There are two placeholders in the following set of commands.</span></span>

- `{dotnet-package}`\
<span data-ttu-id="cecb5-103">To představuje balíček .NET Core, který instalujete, například `aspnetcore-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="cecb5-103">This represents the .NET Core package you're installing, such as `aspnetcore-runtime-3.1`.</span></span> <span data-ttu-id="cecb5-104">Tento příkaz se používá v `sudo apt-get install` níže uvedeném příkazu.</span><span class="sxs-lookup"><span data-stu-id="cecb5-104">This is used in the `sudo apt-get install` command below.</span></span>

- `{os-version}`\
<span data-ttu-id="cecb5-105">To představuje verzi systému Linux, na které se nacházíte.</span><span class="sxs-lookup"><span data-stu-id="cecb5-105">This represents the Linux version you are on.</span></span> <span data-ttu-id="cecb5-106">Tento příkaz se používá v `wget` níže uvedeném příkazu.</span><span class="sxs-lookup"><span data-stu-id="cecb5-106">This is used in the `wget` command below.</span></span>

<span data-ttu-id="cecb5-107">Zkuste seznam balíčků vymazáním:</span><span class="sxs-lookup"><span data-stu-id="cecb5-107">Try purging the package list:</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {dotnet-package}
```

<span data-ttu-id="cecb5-108">Pokud to nefunguje, můžete spustit ruční instalaci s následujícími příkazy:</span><span class="sxs-lookup"><span data-stu-id="cecb5-108">If that doesn't work, you can run a manual install with the following commands:</span></span>
