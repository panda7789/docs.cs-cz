---
title: Spravované ladicí programy - .NET Core
description: Přehled ladicích programů Visual Studio a Visual Studio Code spravované.
ms.date: 08/05/2019
ms.openlocfilehash: 065b1b0fc32eb76b398cb3821c8592a1955c9359
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715557"
---
# <a name="net-core-managed-debuggers"></a>Ladicí programy spravované jádrem .NET Core

Ladicí programy umožňují pozastavu nebo spuštění programů krok za krokem. Po pozastavení lze zobrazit aktuální stav procesu. Krokování prostřednictvím klíčových oddílů, získáte pochopení kódu a proč vytváří výsledek, který dělá.

Společnost Microsoft poskytuje ladicí programy spravovaného kódu v **sadě Visual Studio** a Visual Studio **Code**.

## <a name="visual-studio-managed-debugger"></a>Ladicí program spravované houštinou visual studia

**Visual Studio** je integrované vývojové prostředí s nejkomplexnějšíladicí nepřístupnou. Visual Studio je vynikající volbou pro vývojáře pracující v systému Windows.

- [Kurz – ladění aplikace .NET Core v systému Windows pomocí sady Visual Studio](../tutorials/debugging-with-visual-studio.md)

Zatímco Visual Studio je aplikace pro Windows, lze ji stále použít k vzdálenéladění aplikací pro Linux a macOS.

- [Ladění aplikace .NET Core v Linuxu/OSX pomocí sady Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 Ladění ASP.NET aplikace Core vyžadují mírně odlišné pokyny.

- [Ladění aplikací ASP.NET Core ve Visual Studiu](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a>Ladicí program spravovaného kódu Visual Studio

**Visual Studio Code** je lehký editor kódu pro různé platformy. Používá stejnou implementaci ladicího programu .NET Core jako Visual Studio, ale se zjednodušeným uživatelským rozhraním.

- [Kurz – ladění aplikace .NET Core pomocí kódu sady Visual Studio](../tutorials/with-visual-studio-code.md#debug)
- [Ladění v kódu sady Visual Studio](https://code.visualstudio.com/docs/editor/debugging)
