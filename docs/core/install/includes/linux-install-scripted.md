---
ms.openlocfilehash: fb78e1439a680a8dbb9fc0eb8afdeee3efef7ead
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768391"
---

[Příkaz dotnet – instalační skripty](../../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci **sady SDK** a **modulu runtime**bez správy. Skript si můžete stáhnout z <https://dot.net/v1/dotnet-install.sh> .

Ve výchozím nastavení se jedná o instalaci nejnovější verze [LTS (SDK pro dlouhodobé podpory)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1. Chcete-li nainstalovat aktuální vydání, které nemusí být verzí (LTS), použijte `-c Current` parametr.

```bash
./dotnet-install.sh -c Current
```

Pokud chcete místo sady SDK nainstalovat modul runtime .NET Core, použijte `--runtime` parametr.

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

Konkrétní verzi můžete nainstalovat změnou `-c` parametru tak, aby označovala konkrétní verzi. Následující příkaz nainstaluje .NET Core SDK 3,1.

```bash
./dotnet-install.sh -c 3.1
```

Další informace naleznete v tématu [dotnet-Install Scripts reference](../../tools/dotnet-install-script.md).
