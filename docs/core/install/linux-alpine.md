---
title: Nainstalovat .NET Core na alpské – .NET Core
description: Ukazuje různé způsoby, jak nainstalovat .NET Core SDK a modul runtime .NET Core v alpské.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: bbaf4ee9020dcd33c894b5376bf04ad65db8d378
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84771501"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a>Nainstalovat .NET Core SDK nebo modul runtime .NET Core v alpské

Tento článek popisuje, jak nainstalovat .NET Core na alpské. V případě, že se v alpské verzi nedostává podpora, .NET Core už tuto verzi nepodporuje. Tyto pokyny vám ale můžou usnadnit práci s .NET Core na těchto verzích, i když není podporovaná.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

Pro Alpine nejsou k dispozici žádní instalační programy. Musíte buď použít [instalační skript](#scripted-install) , nebo postupovat podle pokynů k [ruční instalaci](#manual-install) .

## <a name="supported-distributions"></a>Podporované distribuce

Následující tabulka uvádí seznam aktuálně podporovaných vydání .NET Core a verze alpské, na kterých jsou podporované. Tyto verze zůstanou podporované, dokud verze [.NET Core nedosáhne konce podpory](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nebo když verze [alpské dosáhne konce životnosti](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).

- ✔️ označuje, že verze Alpine nebo .NET Core je stále podporovaná.
- ❌Indikuje, že verze Alpine nebo .NET Core není v této alpské verzi podporovaná.
- Pokud se ✔️á jak verze Alpine, tak i verze .NET Core, je podporovaná kombinace operačních systémů a .NET.

| Alpine                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview |
|--------------------------|---------------|---------------|----------------|
| ✔️ 3,12  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ 3,11  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ 3,10  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ 3,9   | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ❌3,8   | ✔️ 2,1        | ❌3,1        | ❌5,0 Preview |

Následující verze rozhraní .NET Core již nejsou podporovány. Soubory ke stažení pro tyto soubory zůstanou publikované:

- 3.0
- 2,2
- 2.0

## <a name="dependencies"></a>Závislosti

.NET Core v systému Alpine Linux vyžaduje nainstalované následující závislosti:

- ICU – knihovny
- krb5 – knihovny
- libintl
- libssl 1.1 (Alpine v 3.9 nebo vyšší)
- libssl 1.0 (Alpine v 3.8)
- libstdc + +
- lttng – tým UST
- numactl (volitelné)
- ZLIB

## <a name="scripted-install"></a>Skriptovaná instalace

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Ruční instalace

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Další kroky

- [Kurz: Vytvoření konzolové aplikace s .NET Core SDK pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md)
