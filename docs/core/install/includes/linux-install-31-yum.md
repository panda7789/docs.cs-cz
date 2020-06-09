---
ms.openlocfilehash: 1dad65a9242750e30f1e43dac7d2951f1dbd7b7f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603123"
---

### <a name="install-the-sdk"></a>Instalace sady SDK

.NET Core SDK umožňuje vyvíjet aplikace pomocí .NET Core. Pokud nainstalujete .NET Core SDK, nemusíte instalovat odpovídající modul runtime. Chcete-li nainstalovat .NET Core SDK, spusťte následující příkazy:

```bash
sudo yum install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a>Instalace modulu runtime

Modul runtime .NET Core umožňuje spouštět aplikace, které byly vytvořeny pomocí .NET Core, které neobsahovaly modul runtime. Níže uvedené příkazy nainstalují modul runtime ASP.NET Core, což je nejvíce kompatibilní modul runtime pro .NET Core. V terminálu spusťte následující příkazy.

```bash
sudo yum install aspnetcore-runtime-3.1
```

Jako alternativu k modulu runtime ASP.NET Core můžete nainstalovat modul runtime .NET Core, který neobsahuje podporu ASP.NET Core: Nahraďte `aspnetcore-runtime-2.1` v příkazu výše `dotnet-runtime-3.1` .

```bash
sudo yum install dotnet-runtime-3.1
```
