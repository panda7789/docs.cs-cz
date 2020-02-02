---
ms.openlocfilehash: ef3e4f9f8145677732b9d2e66d416be277697f55
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920638"
---

Balíčky přidané do kanálů správce balíčků jsou pojmenovány ve formátu zneužitelných: `{product}-{type}-{version}`.

- \ **produktu**
Typ produktu .NET, který se má nainstalovat Platné možnosti jsou:

  - dotnet
  - aspnetcore

- **zadejte**\
Zvolí sadu SDK nebo modul runtime. Platné možnosti jsou:

  - sdk
  - modul runtime

- \ **verze**
Verze sady SDK nebo modulu runtime, která má být nainstalována. V tomto článku se vždycky dostanou pokyny pro nejnovější podporovanou verzi. Platné možnosti jsou všechny vydané verze, například:

  - 3,0
  - 2.2
  - 2.1

### <a name="examples"></a>Příklady

- Instalace sady .NET Core 2,2 SDK: `dotnet-sdk-2.2`
- Instalace modulu runtime ASP.NET Core 3,1: `aspnetcore-runtime-3.1`
- Instalace modulu runtime .NET Core 2,1: `dotnet-runtime-2.1`

### <a name="package-missing"></a>Chybějící balíček

Pokud kombinace verze balíčku nefunguje, není k dispozici. Například sada SDK není ASP.NET Core, součásti sady SDK jsou součástí .NET Core SDK. Hodnota `aspnetcore-sdk-2.2` není správná a měla by být `dotnet-sdk-2.2`.
