---
ms.openlocfilehash: 0d29407896145bc3b2ed8284c839ae8f2f0521b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602948"
---

[Dotnet – instalační skripty](../../tools/dotnet-install-script.md) se používají pro automatizaci a pro instalaci **sady SDK**bez správy. Skript si můžete stáhnout z <https://dot.net/v1/dotnet-install.sh> .

Skript ve výchozím nastavení instaluje nejnovější verzi [LTS (Long Term support)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , což je .net Core 3,1. Chcete-li nainstalovat aktuální vydání, které nemusí být verzí (LTS), použijte `-c Current` parametr.

```bash
./dotnet-install.sh -c Current
```

Pokud chcete místo sady SDK nainstalovat modul runtime .NET Core, použijte `--runtime` parametr.

```bash
./dotnet-install.sh -c Current --runtime
```

Konkrétní verzi můžete nainstalovat změnou `-c` parametru tak, aby označovala konkrétní verzi. Následující příkaz nainstaluje .NET Core SDK 3,1.

```bash
./dotnet-install.sh -c 3.1
```

Další informace naleznete v tématu [dotnet-Install Scripts reference](../../tools/dotnet-install-script.md).
