---
ms.openlocfilehash: 7a55641b3673dc4d8d9b328f0de99b7247ca51d4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450882"
---

Balíčky přidané do kanálů správce balíčků jsou pojmenovány ve formátu zneužitelných: `{product}-{type}-{version}`.

- \ **produktu**
Typ produktu .NET, který se má nainstalovat Platné možnosti jsou:

  - DotNet
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
- Instalace modulu runtime ASP.NET Core 3,0: `aspnetcore-runtime-3.0`
- Instalace modulu runtime .NET Core 2,1: `dotnet-runtime-2.1`

### <a name="troubleshoot"></a>Řešení problémů

Pokud kombinace balíčku nefunguje, není k dispozici. Například sada SDK není ASP.NET Core, součásti sady SDK jsou součástí .NET Core SDK. Hodnota `aspnetcore-sdk-2.2` není správná a měla by být `dotnet-sdk-2.2`
