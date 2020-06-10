---
ms.openlocfilehash: 7723892a33bf7dd8e475b2f696db5d9ab287e182
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602990"
---

Balíčky přidané do kanálů správce balíčků jsou pojmenovány ve formátu zneužitelných: `{product}-{type}-{version}` .

- **produktu**\
Typ produktu .NET, který se má nainstalovat Platné možnosti jsou:

  - dotnet
  - aspnetcore

- **textový**\
Zvolí sadu SDK nebo modul runtime. Platné možnosti jsou:

  - SDK
  - modul runtime

- **znění**\
Verze sady SDK nebo modulu runtime, která má být nainstalována. V tomto článku se vždycky dostanou pokyny pro nejnovější podporovanou verzi. Platné možnosti jsou všechny vydané verze, například:

  - 3.1
  - 3.0
  - 2.1

  Je možné, že sada SDK/modul runtime, kterou se pokoušíte stáhnout, není k dispozici pro distribuci systému Linux. Seznam podporovaných distribucí najdete v tématu [závislosti a požadavky .NET Core](../linux.md).

### <a name="examples"></a>Příklady

- Instalace modulu runtime ASP.NET Core 3,1:`aspnetcore-runtime-3.1`
- Nainstalujte modul runtime .NET Core 2,1:`dotnet-runtime-2.1`
- Nainstalujte sadu .NET Core 3,1 SDK:`dotnet-sdk-3.1`

### <a name="package-missing"></a>Chybějící balíček

Pokud kombinace verze balíčku nefunguje, není k dispozici. Například sada SDK není ASP.NET Core, součásti sady SDK jsou součástí .NET Core SDK. Hodnota `aspnetcore-sdk-2.2` je nesprávná a měla by být `dotnet-sdk-2.2` . Seznam distribucí pro Linux podporovaných rozhraním .NET Core najdete v tématu [závislosti a požadavky .NET Core](../linux.md).
