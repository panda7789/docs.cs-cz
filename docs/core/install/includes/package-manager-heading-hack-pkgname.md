---
ms.openlocfilehash: 47e8e15a64236d8ade2febb1add81fa4e5c030d9
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116139"
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

### <a name="troubleshoot"></a>Řešení problémů

Pokud kombinace balíčku nefunguje, není k dispozici. Například sada SDK není ASP.NET Core, součásti sady SDK jsou součástí .NET Core SDK. Hodnota `aspnetcore-sdk-2.2` není správná a měla by být `dotnet-sdk-2.2`
