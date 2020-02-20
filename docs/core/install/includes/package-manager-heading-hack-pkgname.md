---
ms.openlocfilehash: 51b3c1b3e3d61b23a0511ca807afef0269ac9ee4
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77466132"
---

Balíčky přidané do kanálů správce balíčků jsou pojmenovány ve formátu zneužitelných: `{product}-{type}-{version}`.

- \ **produktu**
Typ produktu .NET, který se má nainstalovat Platné možnosti jsou:

  - DotNet
  - aspnetcore

- **zadejte**\
Zvolí sadu SDK nebo modul runtime. Platné možnosti jsou:

  - SDK
  - modul runtime

- \ **verze**
Verze sady SDK nebo modulu runtime, která má být nainstalována. V tomto článku se vždycky dostanou pokyny pro nejnovější podporovanou verzi. Platné možnosti jsou všechny vydané verze, například:

  - 3.1
  - 3.0
  - 2.1

  Je možné, že sada SDK/modul runtime, kterou se pokoušíte stáhnout, není k dispozici pro distribuci systému Linux. Seznam podporovaných distribucí najdete v tématu [závislosti a požadavky .NET Core](../dependencies.md?pivots=os-linux).

### <a name="examples"></a>Příklady

- Instalace modulu runtime ASP.NET Core 3,1: `aspnetcore-runtime-3.1`
- Instalace modulu runtime .NET Core 2,1: `dotnet-runtime-2.1`
- Instalace sady .NET Core 3,0 SDK: `dotnet-sdk-3.0`

### <a name="package-missing"></a>Chybějící balíček

Pokud kombinace verze balíčku nefunguje, není k dispozici. Například sada SDK není ASP.NET Core, součásti sady SDK jsou součástí .NET Core SDK. Hodnota `aspnetcore-sdk-2.2` není správná a měla by být `dotnet-sdk-2.2`. Seznam distribucí pro Linux podporovaných rozhraním .NET Core najdete v tématu [závislosti a požadavky .NET Core](../dependencies.md?pivots=os-linux).
