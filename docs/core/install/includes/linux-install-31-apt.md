---
ms.openlocfilehash: b6f2af7af77398d5e902aae995590b5dde4cf76a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602906"
---

### <a name="install-the-sdk"></a>Instalace sady SDK

.NET Core SDK umožňuje vyvíjet aplikace pomocí .NET Core. Pokud nainstalujete .NET Core SDK, nemusíte instalovat odpovídající modul runtime. Chcete-li nainstalovat .NET Core SDK, spusťte následující příkazy:

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-3.1
```

> [!IMPORTANT]
> Pokud se zobrazí chybová zpráva podobná té, že se **nepovedlo najít balíček dotnet-SDK-3,1**, přečtěte si část [věnované řešení potíží s apt](#apt-troubleshooting) .

### <a name="install-the-runtime"></a>Instalace modulu runtime

Modul runtime .NET Core umožňuje spouštět aplikace, které byly vytvořeny pomocí .NET Core, které neobsahovaly modul runtime. Níže uvedené příkazy nainstalují modul runtime ASP.NET Core, což je nejvíce kompatibilní modul runtime pro .NET Core. V terminálu spusťte následující příkazy.

```bash
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> Pokud se zobrazí chybová zpráva podobná té, že **nejde najít Package aspnetcore-runtime-3,1**, přečtěte si část [věnované odstraňování potíží s apt](#apt-troubleshooting) .

Jako alternativu k modulu runtime ASP.NET Core můžete nainstalovat modul runtime .NET Core, který neobsahuje podporu ASP.NET Core: Nahraďte `aspnetcore-runtime-3.1` v příkazu výše `dotnet-runtime-3.1` .

```bash
sudo apt-get install -y dotnet-runtime-3.1
```
