---
title: Nainstalovat distribuce .NET Core a Linux
description: Přečtěte si, jaké distribuce systému Linux podporují instalaci .NET Core v systému Linux.
author: thraka
ms.author: adegeo
ms.date: 06/01/2020
ms.openlocfilehash: fec3cf9e99c2db5d7312280f676bc2a3344f1ae1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602892"
---
# <a name="install-net-core-on-linux"></a>Nainstalovat .NET Core v systému Linux

Rozhraní .NET Core je k dispozici v různých distribucích systému Linux. Většina platforem a distribucí pro Linux má každý rok hlavní verzi a většina nabízí správce balíčků, který se používá k instalaci .NET Core. Tento článek popisuje, co je aktuálně podporováno a který správce balíčků používá.

Zbytek tohoto článku je rozpis každé hlavní distribuce systému Linux, kterou podporuje .NET Core. Všechna vydání .NET Core zůstanou podporovaná, dokud verze [.NET Core nedosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo dokud nebude distribuce systému Linux na konci životního cyklu.

Pro zajištění nejlepší kompatibility vyberte verzi LTS (Long-termed Release).

## <a name="unsupported-releases"></a>Nepodporované verze

Následující verze rozhraní .NET Core již nejsou ❌ podporovány. Soubory ke stažení pro tyto soubory zůstanou publikované:

- 3.0
- 2,2
- 2.0

Tyto nepodporované verze nejsou podrobně popsané v následujících částech a při pokusu o jejich instalaci se můžou lišit vaše kilometry.

## <a name="centos"></a>CentOS

CentOS 7 používá Yumu jako správce balíčků a CentOS 8 používá DNF.

Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core na CentOS 7 a CentOS 8. Tato verze zůstane podporovaná, dokud [nedosáhne žádné verze rozhraní .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo pokud není podporovaná verze CentOS.

| CentOS                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (jenom ruční instalace) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-centos.md#centos-8-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [7](linux-centos.md#centos-7-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |

Další informace najdete v tématu [instalace .NET Core na CentOS](linux-centos.md).

## <a name="debian"></a>Debian

Debian používá APT (pokročilý nástroj Package) jako správce balíčků.

Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze Debian, na kterých jsou podporované. Tato verze zůstane podporovaná, dokud žádná verze [.NET Core nedosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo když verze [Debian dosáhne konce životnosti](https://wiki.debian.org/DebianReleases).

- ✔️ označuje, že je stále podporovaná verze Debian nebo .NET Core.
- ❌Indikuje, že verze Debian nebo .NET Core není v této verzi Debian podporována.
- Pokud se ✔️á jak verze Debian, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.

| Debian                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (jenom ruční instalace) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [10](linux-debian.md#debian-10-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [9](linux-debian.md#debian-9-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ❌[8](linux-debian.md#debian-8-)       | ✔️ 2,1        | ❌3,1        | ❌5,0 Preview |

## <a name="fedora"></a>Fedora

Fedora jako správce balíčků používá DNF.

Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze Fedora, na kterých jsou podporované. Tato verze zůstane podporovaná, dokud žádná verze [.NET Core nedosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo když verze [Fedora dosáhne konce životnosti](https://fedoraproject.org/wiki/End_of_life).

- ✔️ označuje, že je stále podporovaná verze Fedora nebo .NET Core.
- ❌Indikuje, že verze Fedora nebo .NET Core není v této verzi Fedora podporována.
- Pokud se ✔️á jak verze Fedora, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.

| Fedora                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (jenom ruční instalace) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [32](linux-fedora.md#fedora-32-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [31](linux-fedora.md#fedora-31-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ❌[30](linux-fedora.md#fedora-30-) | ✔️ 2,1        | ✔️ 3,1        | ❌5,0 Preview |
| ❌[29](linux-fedora.md#fedora-29-) | ✔️ 2,1        | ✔️ 3,1        | ❌5,0 Preview |
| ❌[28](linux-fedora.md#fedora-28-) | ✔️ 2,1        | ❌3,1        | ❌5,0 Preview |
| ❌[27](linux-fedora.md#fedora-27-) | ✔️ 2,1        | ❌3,1        | ❌5,0 Preview |

Další informace najdete v tématu [instalace .NET Core na Fedora](linux-fedora.md).

## <a name="opensuse"></a>openSUSE

openSUSE používá zypperu jako správce balíčků.

Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core na openSUSE 15. Tato verze zůstane podporovaná, dokud [nedosáhne žádné verze rozhraní .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo pokud není podporovaná verze openSUSE.

- ✔️ označuje, že je stále podporovaná verze openSUSE nebo .NET Core.
- ❌Indikuje, že verze openSUSE nebo .NET Core není v této verzi openSUSE podporována.
- Pokud se ✔️á jak verze openSUSE, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.

| openSUSE                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (jenom ruční instalace) |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-opensuse.md#opensuse-15-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |

## <a name="red-hat"></a>Red Hat

Red Hat Enterprise Linux (RHEL) používá jako správce balíčků Yumu (RHEL 7) a DNF (RHEL 8).

Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core na RHEL 7 a RHEL 8. Tato verze zůstane podporovaná, dokud [nedosáhne žádné verze rozhraní .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo pokud není podporovaná verze RHEL.

- ✔️ označuje, že je stále podporovaná verze RHEL nebo .NET Core.
- ❌Indikuje, že verze RHEL nebo .NET Core není v této verzi RHEL podporována.
- Pokud se ✔️á jak verze RHEL, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.

| RHEL                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (jenom ruční instalace) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-rhel.md#rhel-8-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [7](linux-rhel.md#rhel-7-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |

## <a name="sles"></a>SLES

SLES používá zypperu jako správce balíčků.

Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core na SLES 12 SP2 a SLES 15. Tato verze zůstane podporovaná, dokud [nedosáhne žádné verze rozhraní .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo pokud není podporovaná verze SLES.

- ✔️ označuje, že je stále podporovaná verze SLES nebo .NET Core.
- ❌Indikuje, že verze SLES nebo .NET Core není v této verzi SLES podporována.
- Pokud se ✔️á jak verze SLES, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.

| SLES                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (jenom ruční instalace) |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-sles.md#sles-15-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [12 SP2](linux-sles.md#sles-12-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |

## <a name="ubuntu"></a>Ubuntu

Ubuntu používá APT (pokročilý nástroj Package) jako správce balíčků.

Následující tabulka představuje stav podpory Ubuntu a .NET Core.

- ✔️ označuje, že je stále podporovaná verze Ubuntu nebo .NET Core.
- ❌Indikuje, že verze Ubuntu nebo .NET Core není v této verzi Ubuntu podporována.
- Pokud se ✔️á jak verze Ubuntu, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.

| Ubuntu                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (jenom ruční instalace) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [20,04 (LTS)](linux-ubuntu.md#2004-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [19,10](linux-ubuntu.md#1910-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ❌[19,04](linux-ubuntu.md#1904-)       | ✔️ 2,1        | ✔️ 3,1        | ❌5,0 Preview |
| ❌[18,10](linux-ubuntu.md#1810-)       | ✔️ 2,1        | ❌3,1        | ❌5,0 Preview |
| ✔️ [18,04 (LTS)](linux-ubuntu.md#1804-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ❌[17,10](linux-ubuntu.md#1710-)       | ✔️ 2,1        | ❌3,1        | ❌5,0 Preview |
| ❌[17,04](linux-ubuntu.md#1704-)       | ✔️ 2,1        | ❌3,1        | ❌5,0 Preview |
| ❌[16,10](linux-ubuntu.md#1610-)       | ❌2,1        | ❌3,1        | ❌5,0 Preview |
| ✔️ [16,04 (LTS)](linux-ubuntu.md#1604-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |

Další informace najdete v tématu [instalace .NET Core na Ubuntu](linux-ubuntu.md).
