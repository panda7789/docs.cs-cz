---
ms.openlocfilehash: 4340ed7444681b4601dea50c93926b0ee0c07eec
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134114"
---

Balíčky přidané do informačních kanálů správce balíčků jsou `{product}-{type}-{version}`pojmenovány v hackovatelném formátu: .

- **Produktu**\
Typ produktu .NET k instalaci. Platné možnosti jsou:

  - dotnet
  - aspnetcore

- **Typ**\
Vybere sadu SDK nebo runtime. Platné možnosti jsou:

  - SDK
  - modul runtime

- **Verze**\
Verze sady SDK nebo runtime k instalaci. Tento článek bude vždy dávat pokyny pro nejnovější podporovanou verzi. Platné možnosti jsou všechny vydané verze, například:

  - 3.1
  - 3.0
  - 2.1

  Je možné, že sada SDK/runtime, kterou se pokoušíte stáhnout, není k dispozici pro distribuci Linuxu. Seznam podporovaných distribucí naleznete [v tématu .NET Core závislosti a požadavky](../dependencies.md?pivots=os-linux).

### <a name="examples"></a>Příklady

- Nainstalujte ASP.NET core 3.1 runtime:`aspnetcore-runtime-3.1`
- Nainstalujte runtime .NET Core 2.1:`dotnet-runtime-2.1`
- Nainstalujte sdk .NET Core 3.1:`dotnet-sdk-3.1`

### <a name="package-missing"></a>Balíček chybí.

Pokud kombinace verze balíčku nefunguje, není k dispozici. Například neexistuje ASP.NET core sdk, součásti Sady SDK jsou součástí sady .NET Core SDK. Hodnota `aspnetcore-sdk-2.2` je nesprávná `dotnet-sdk-2.2`a měla by být . Seznam linuxových distribucí podporovaných rozhraním .NET Core naleznete v [tématu .NET Core závislostí a požadavků](../dependencies.md?pivots=os-linux).
