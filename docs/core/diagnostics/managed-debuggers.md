---
title: Spravované ladicí programy – .NET Core
description: Přehled sady Visual Studio a Visual Studio Code spravovaných ladicích programů.
ms.date: 08/05/2019
ms.openlocfilehash: 065b1b0fc32eb76b398cb3821c8592a1955c9359
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715557"
---
# <a name="net-core-managed-debuggers"></a>Spravované ladicí programy .NET Core

Ladicí programy umožňují pozastaví nebo spustit programy krok za krokem. Při pozastavení lze aktuální stav procesu zobrazit. Díky krokování v klíčových částech získáte vysvětlení kódu a proč vytvoří výsledek, který dělá.

Společnost Microsoft poskytuje ladicí programy pro spravovaný kód v **aplikaci Visual Studio** a **Visual Studio Code**.

## <a name="visual-studio-managed-debugger"></a>Spravovaný ladicí program sady Visual Studio

**Visual Studio** je integrované vývojové prostředí s nejkomplexním ladicím programem, který je k dispozici. Visual Studio je vynikající volbou pro vývojáře, kteří pracují na Windows.

- [Kurz – ladění aplikace .NET Core ve Windows se sadou Visual Studio](../tutorials/debugging-with-visual-studio.md)

I když je Visual Studio aplikace pro Windows, může se pořád použít k vzdálené ladění aplikací pro Linux a macOS.

- [Ladění aplikace .NET Core v systému Linux/OSX pomocí sady Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 Ladění ASP.NET Core aplikací vyžaduje trochu jiné pokyny.

- [Ladění aplikací ASP.NET Core v aplikaci Visual Studio](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a>Visual Studio Code spravovaný ladicí program

**Visual Studio Code** je zjednodušený Editor kódu pro různé platformy. Používá stejnou implementaci ladicího programu .NET Core jako Visual Studio, ale má zjednodušené uživatelské rozhraní.

- [Kurz – ladění aplikace .NET Core pomocí Visual Studio Code](../tutorials/with-visual-studio-code.md#debug)
- [Ladění v Visual Studio Code](https://code.visualstudio.com/docs/editor/debugging)
