---
ms.openlocfilehash: fb78e1439a680a8dbb9fc0eb8afdeee3efef7ead
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768391"
---

<span data-ttu-id="5fef4-101">[Příkaz dotnet – instalační skripty](../../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci **sady SDK** a **modulu runtime**bez správy.</span><span class="sxs-lookup"><span data-stu-id="5fef4-101">The [dotnet-install scripts](../../tools/dotnet-install-script.md) are used for automation and non-admin installs of the **SDK** and **Runtime**.</span></span> <span data-ttu-id="5fef4-102">Skript si můžete stáhnout z <https://dot.net/v1/dotnet-install.sh> .</span><span class="sxs-lookup"><span data-stu-id="5fef4-102">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="5fef4-103">Ve výchozím nastavení se jedná o instalaci nejnovější verze [LTS (SDK pro dlouhodobé podpory)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="5fef4-103">The script defaults to installing the latest SDK [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="5fef4-104">Chcete-li nainstalovat aktuální vydání, které nemusí být verzí (LTS), použijte `-c Current` parametr.</span><span class="sxs-lookup"><span data-stu-id="5fef4-104">To install the current release, which may not be an (LTS) version, use the `-c Current` parameter.</span></span>

```bash
./dotnet-install.sh -c Current
```

<span data-ttu-id="5fef4-105">Pokud chcete místo sady SDK nainstalovat modul runtime .NET Core, použijte `--runtime` parametr.</span><span class="sxs-lookup"><span data-stu-id="5fef4-105">To install .NET Core Runtime instead of the SDK, use the `--runtime` parameter.</span></span>

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

<span data-ttu-id="5fef4-106">Konkrétní verzi můžete nainstalovat změnou `-c` parametru tak, aby označovala konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="5fef4-106">You can install a specific version by altering the `-c` parameter to indicate the specific version.</span></span> <span data-ttu-id="5fef4-107">Následující příkaz nainstaluje .NET Core SDK 3,1.</span><span class="sxs-lookup"><span data-stu-id="5fef4-107">The following command installs .NET Core SDK 3.1.</span></span>

```bash
./dotnet-install.sh -c 3.1
```

<span data-ttu-id="5fef4-108">Další informace naleznete v tématu [dotnet-Install Scripts reference](../../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="5fef4-108">For more information, see [dotnet-install scripts reference](../../tools/dotnet-install-script.md).</span></span>
