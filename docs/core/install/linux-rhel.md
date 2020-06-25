---
title: Instalace .NET Core na RHEL – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v RHEL.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 4a406fe1834c16bab9a5548b69206b51270b33fa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324716"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-rhel"></a>Instalace .NET Core SDK nebo modulu runtime .NET Core v RHEL

Rozhraní .NET Core je podporováno v RHEL. Tento článek popisuje, jak nainstalovat .NET Core na RHEL.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>Zaregistrujte si předplatné Red Hat

Pokud chcete nainstalovat .NET Core ze Red Hat na RHEL, musíte se nejdřív zaregistrovat pomocí Správce předplatných Red Hat. Pokud jste to ještě neudělali v systému nebo pokud si nejste jistí, přečtěte si část [dokumentace k produktu Red Hat pro .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="supported-distributions"></a>Podporované distribuce

Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core na RHEL 7 a RHEL 8. Tato verze zůstane podporovaná, dokud [nedosáhne žádné verze rozhraní .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo pokud není podporovaná verze RHEL.

- ✔️ označuje, že je stále podporovaná verze RHEL nebo .NET Core.
- ❌Indikuje, že verze RHEL nebo .NET Core není v této verzi RHEL podporována.
- Pokud se ✔️á jak verze RHEL, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.

| RHEL                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (jenom ruční instalace) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](#rhel-8-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [7](#rhel-7-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |

Následující verze rozhraní .NET Core již nejsou podporovány. Soubory ke stažení pro tyto soubory zůstanou publikované:

- 3.0
- 2,2
- 2.0

## <a name="how-to-install-other-versions"></a>Jak nainstalovat další verze

Projděte si [dokumentaci k Red Hat pro .NET Core](https://access.redhat.com/documentation/net_core/) podle kroků vyžadovaných k instalaci jiných verzí rozhraní .NET Core.

## <a name="rhel-8-"></a>RHEL 8 ✔️

Rozhraní .NET Core je zahrnuté v úložištích AppStream pro RHEL 8.

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="rhel-7-"></a>RHEL 7 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

Následující příkaz nainstaluje `scl-utils` balíček:

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a>Instalace sady SDK

.NET Core SDK umožňuje vyvíjet aplikace pomocí .NET Core. Pokud nainstalujete .NET Core SDK, nemusíte instalovat odpovídající modul runtime. Chcete-li nainstalovat .NET Core SDK, spusťte následující příkazy:

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

Red Hat nedoporučuje trvalé povolení `rh-dotnet31` , protože může ovlivnit jiné programy. Například `rh-dotnet31` obsahuje verzi nástroje `libcurl` , která se liší od základní verze RHEL. To může vést k problémům v programech, které neočekávají jinou verzi `libcurl` . Pokud chcete povolit možnost `rh-dotnet` trvale, přidejte do souboru _~/.bashrc_ následující řádek.

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a>Instalace modulu runtime

Modul runtime .NET Core umožňuje spouštět aplikace, které byly vytvořeny pomocí .NET Core, které neobsahovaly modul runtime. Níže uvedené příkazy nainstalují modul runtime ASP.NET Core, což je nejvíce kompatibilní modul runtime pro .NET Core. V terminálu spusťte následující příkazy.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

Red Hat nedoporučuje trvalé povolení `rh-dotnet31-aspnetcore-runtime-3.1` , protože může ovlivnit jiné programy. Například `rh-dotnet31-aspnetcore-runtime-3.1` obsahuje verzi nástroje `libcurl` , která se liší od základní verze RHEL. To může vést k problémům v programech, které neočekávají jinou verzi `libcurl` . Pokud chcete povolit možnost `rh-dotnet31-aspnetcore-runtime-3.1` trvale, přidejte do souboru _~/.bashrc_ následující řádek.

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

Jako alternativu k modulu runtime ASP.NET Core můžete nainstalovat modul runtime .NET Core, který neobsahuje podporu ASP.NET Core: Nahraďte `rh-dotnet31-aspnetcore-runtime-3.1` v příkazech uvedených výše `rh-dotnet31-dotnet-runtime-3.1` .

## <a name="snap"></a>Moduly snap

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>Závislosti

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a>Skriptovaná instalace

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Ruční instalace

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Další kroky

- [Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md)
