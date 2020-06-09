---
ms.openlocfilehash: 9ba55c45dc8087c2f7766e5cad32dae97784ffd0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603025"
---

### <a name="install-the-sdk"></a>Instalace sady SDK

.NET Core SDK umožňuje vyvíjet aplikace pomocí .NET Core. Pokud nainstalujete .NET Core SDK, nemusíte instalovat odpovídající modul runtime. Chcete-li nainstalovat .NET Core SDK, spusťte následující příkazy:

```bash
sudo dnf install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a>Instalace modulu runtime

Modul runtime .NET Core umožňuje spouštět aplikace, které byly vytvořeny pomocí .NET Core, které neobsahovaly modul runtime. Níže uvedené příkazy nainstalují modul runtime ASP.NET Core, což je nejvíce kompatibilní modul runtime pro .NET Core. V terminálu spusťte následující příkazy.

```bash
sudo dnf install aspnetcore-runtime-3.1
```

Jako alternativu k modulu runtime ASP.NET Core můžete nainstalovat modul runtime .NET Core, který neobsahuje podporu ASP.NET Core: Nahraďte `aspnetcore-runtime-3.1` v příkazu výše `dotnet-runtime-3.1` .

```bash
sudo dnf install dotnet-runtime-3.1
```
