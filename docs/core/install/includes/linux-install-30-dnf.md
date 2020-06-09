---
ms.openlocfilehash: f9ea0ee6402187365cec5cdced1617ee2ae66bed
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603067"
---

### <a name="install-the-sdk"></a>Instalace sady SDK

.NET Core SDK umožňuje vyvíjet aplikace pomocí .NET Core. Pokud nainstalujete .NET Core SDK, nemusíte instalovat odpovídající modul runtime. Chcete-li nainstalovat .NET Core SDK, spusťte následující příkazy:

```bash
sudo dnf install dotnet-sdk-3.0
```

### <a name="install-the-runtime"></a>Instalace modulu runtime

Modul runtime .NET Core umožňuje spouštět aplikace, které byly vytvořeny pomocí .NET Core, které neobsahovaly modul runtime. Níže uvedené příkazy nainstalují modul runtime ASP.NET Core, což je nejvíce kompatibilní modul runtime pro .NET Core. V terminálu spusťte následující příkazy.

```bash
sudo dnf install aspnetcore-runtime-3.0
```

Jako alternativu k modulu runtime ASP.NET Core můžete nainstalovat modul runtime .NET Core, který neobsahuje podporu ASP.NET Core: Nahraďte `aspnetcore-runtime-3.0` v příkazu výše `dotnet-runtime-3.0` .

```bash
sudo dnf install dotnet-runtime-3.0
```
