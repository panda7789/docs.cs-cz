---
title: Instalace rozhraní .NET Framework 3.5 ve Windows 10, 8.1, 8
description: Přečtěte si, jak nainstalovat rozhraní .NET Framework 3.5 ve Windows 10, Windows 8.1 a Windows 8.
ms.date: 07/16/2018
ms.openlocfilehash: cfe21c0821b8f3223301dcc802533e1aaf024a79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965942"
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Instalace rozhraní .NET Framework 3.5 v systému Windows 10, Windows 8.1 a Windows 8

Ke spuštění aplikace ve Windows 10, Windows 8.1 a Windows 8 8 bude možná potřeba rozhraní .NET Framework 3.5. Tyto pokyny můžete použít také pro starší verze systému Windows.

## <a name="download-the-offline-installer"></a>Stažení offline instalačního programu

Offline instalační program rozhraní .NET Framework 3.5 SP1 je k dispozici na [stránce pro stažení rozhraní .NET Framework 3.5 SP1](https://dotnet.microsoft.com/download/dotnet-framework/net35-sp1) a je k dispozici pro verze windows před Windows 10.

## <a name="install-the-net-framework-35-on-demand"></a>Instalace rozhraní .NET Framework 3.5 na vyžádání

Pokud se pokusíte spustit aplikaci, která vyžaduje rozhraní .NET Framework 3.5, může se zobrazit následující dialogové okno konfigurace. Chcete-li povolit rozhraní .NET Framework 3.5, zvolte **Nainstalovat tuto funkci.** Tato možnost vyžaduje připojení k Internetu.

![Snímek obrazovky s instalačním dialogem rozhraní .NET Framework](./media/dotnet-35-windows-10/dotnet-framework-installation-dialog.png)

### <a name="why-am-i-getting-this-pop-up"></a>Proč dostávám tohle vyskakovací okno?

Rozhraní .NET Framework je vytvořeno společností Microsoft a poskytuje prostředí pro spouštění aplikací. K dispozici jsou různé verze. Mnoho společností vyvíjí své aplikace ke spuštění pomocí rozhraní .NET Framework a tyto aplikace cílí na konkrétní verzi. Pokud se zobrazí toto automaticky otevírané okno, pokoušíte se spustit aplikaci, která vyžaduje rozhraní .NET Framework verze 3.5, ale tato verze není v systému nainstalována.

## <a name="enable-the-net-framework-35-in-control-panel"></a>Povolení ovládacího panelu Rozhraní .NET Framework 3.5

Rozhraní .NET Framework 3.5 můžete povolit pomocí Ovládacích panelů systému Windows. Tato možnost vyžaduje připojení k Internetu.

1. Stiskněte klávesu ![Windows Snímek obrazovky loga klávesy Windows.](./media/dotnet-35-windows-10/windows-keyboard-logo.png) na klávesnici, zadejte "Funkce Windows" a stiskněte Enter. Zobrazí se dialogové okno **Zapnout nebo vypnout funkce systému Windows.**

2. Zaškrtněte políčko **.NET Framework 3.5 (včetně .NET 2.0 a 3.0),** zaškrtněte **políčko OK**a restartujte počítač, pokud se zobrazí výzva.

   ![Snímek obrazovky zobrazující instalaci rozhraní .NET s ovládacím panelem](./media/dotnet-35-windows-10/dotnet-control-panel.png)

   Není nutné vybírat podřízené položky pro **aktivaci http (WCF) Windows Communication Foundation** **(WCF) bez http aktivace,** pokud nejste vývojář nebo správce serveru, který tuto funkci vyžaduje.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>Řešení potíží s instalací rozhraní .NET Framework 3.5

Během instalace se může zobrazit chyba 0x800f0906, 0x800f0907, 0x800f081f nebo 0x800F0922, v takovém případě se podívejte na [chybu instalace rozhraní .NET Framework 3.5: 0x800f0906, 0x800f0907 nebo 0x800f081f,](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) abyste zjistili, jak tyto problémy vyřešit.

Pokud stále nemůžete vyřešit problém s instalací nebo nemáte připojení k Internetu, můžete jej zkusit nainstalovat pomocí instalačního média systému Windows. Další informace naleznete [v tématu Deploy .NET Framework 3.5 pomocí deployment image servicing and Management (DISM).](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism) Pokud nemáte instalační médium, přečtěte si informace [o vytvoření instalačního média pro Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).

> [!WARNING]
> Pokud nespoléháte na službu Windows Update jako na zdroj pro instalaci rozhraní .NET Framework 3.5, musíte zajistit přísné použití zdrojů ze stejné odpovídající verze operačního systému Windows. Použití zdrojové cesty, která neodpovídá stejné verzi systému Windows, nezabrání instalaci neodpovídající verze rozhraní .NET Framework 3.5. To však způsobí, že systém bude v nepodporovaném a neopravitelném stavu.
