---
title: Instalace .NET Framework ve Windows 10
description: Naučte se, jak nainstalovat .NET Framework ve Windows 10 nebo Windows serveru 2016.
author: rlander
ms.author: mairaw
ms.date: 04/18/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 33805230e0aa6c75443773d60e73f9463ee1fde5
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106548"
---
# <a name="install-the-net-framework-on-windows-10-and-windows-server-2016-and-later"></a>Instalace .NET Framework ve Windows 10 a Windows serveru 2016 a novějších verzích

.NET Framework se vyžaduje ke spouštění mnoha aplikací v systému Windows. Pokyny v tomto článku vám pomůžou nainstalovat .NET Framework verze, které potřebujete. [.NET Framework 4,8](https://github.com/Microsoft/dotnet/tree/master/releases/net48) je nejnovější dostupná verze.

Po pokusu o spuštění aplikace a zobrazení dialogu na počítači, který bude vypadat přibližně takto:

![Tuto aplikaci nebylo možné spustit.](./media/this-application-could-not-be-started.png)

## <a name="net-framework-48"></a>.NET Framework 4,8

.NET Framework 4,8 je součástí:

- [Windows 10 Květen 2019 Update](https://support.microsoft.com/help/4028685/windows-10-get-the-update)

> [!div class="button"]
> [Stáhnout .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)

[.NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48) lze použít ke spouštění aplikací vytvořených pro .NET Framework 4,0 až 4.7.2.

[.NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48) můžete nainstalovat na:

- Windows 10 říjen 2018 Update (verze 1809)
- Aktualizace Windows 10 z dubna 2018 (verze 1803)
- Aktualizace Creators v systému Windows 10 (verze 1709)
- Windows 10 Creators Update (verze 1703)
- Windows 10 – aktualizace pro výročí (verze 1607)
- Windows Server. 2019
- Windows Server verze 1809
- Windows Server verze 1803
- Windows Server 2016

.NET Framework 4,8 není podporován na:

- Windows 10 1507
- Windows 10 1511

Pokud používáte Windows 10 1507 nebo 1511 a chcete nainstalovat .NET Framework 4,8, musíte nejdřív upgradovat na novější verzi Windows 10.

## <a name="net-framework-462"></a>.NET Framework 4.6.2

[.NET Framework 4.6.2](https://www.microsoft.com/download/details.aspx?id=53345) je nejnovější podporovaná verze .NET Framework ve Windows 10 1507 a 1511.

.NET Framework 4.6.2 podporuje aplikace sestavené pro .NET Framework 4,0 až 4.6.2.

## <a name="net-framework-35"></a>.NET Framework 3.5

Postupujte podle pokynů a nainstalujte [.NET Framework 3,5 ve Windows 10](dotnet-35-windows-10.md).

.NET Framework 3,5 podporuje aplikace sestavené pro .NET Framework 1,0 až 3,5.

## <a name="additional-information"></a>Další informace

Verze .NET Framework 4. x jsou místní aktualizace na starší verze. To znamená následující:

- V počítači můžete mít nainstalovanou jenom jednu verzi .NET Framework 4. x.

- Starší verzi .NET Framework nejde nainstalovat na váš počítač, pokud už je nainstalovaná novější verze.

- 4. x verze .NET Framework lze použít ke spouštění aplikací vytvořených pro .NET Framework 4,0 prostřednictvím této verze. Například .NET Framework 4,7 lze použít ke spouštění aplikací vytvořených pro .NET Framework 4,0 až 4,7. Nejnovější verzi (.NET Framework 4,8) lze použít ke spouštění aplikací vytvořených ve všech verzích .NET Framework počínaje verzí 4,0.

Seznam všech verzí .NET Framework dostupných ke stažení najdete na stránce [soubory ke stažení pro rozhraní .NET](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral) .

## <a name="help"></a>Help

Pokud se vám nedaří nainstalovat správnou verzi .NET Framework, můžete [požádat o pomoc Microsoft](mailto:dotnet-install-help@service.microsoft.com?subject=Install-Help).

## <a name="see-also"></a>Viz také:

- [Soubory ke stažení pro .NET](https://www.microsoft.com/net/download?utm_source=ms-docs&utm_medium=referral)
- [Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
- [Instalace .NET Framework pro vývojáře](guide-for-developers.md)
