---
title: Instalace .NET Framework 3,5 ve Windows 10, 8,1, 8
description: Přečtěte si, jak nainstalovat .NET Framework 3,5 ve Windows 10, Windows 8.1 a Windows 8.
ms.date: 07/16/2018
ms.openlocfilehash: 208016e22eed324a3996552284072c6ad29637a5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716382"
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Instalace rozhraní .NET Framework 3.5 v systému Windows 10, Windows 8.1 a Windows 8

Pro spuštění aplikace ve Windows 10, Windows 8.1 a Windows 8 možná budete potřebovat .NET Framework 3,5. Tyto pokyny můžete použít také pro dřívější verze systému Windows.

## <a name="install-the-net-framework-35-on-demand"></a>Instalace .NET Framework 3,5 na vyžádání

Pokud se pokusíte spustit aplikaci, která vyžaduje .NET Framework 3,5, může se zobrazit následující konfigurační dialog. Výběrem možnosti **nainstalovat tuto funkci** povolíte .NET Framework 3,5. Tato možnost vyžaduje připojení k Internetu.

![Snímek obrazovky s dialogovým oknem instalace .NET Framework](./media/dotnet-35-windows-10/dotnet-framework-installation-dialog.png)

### <a name="why-am-i-getting-this-pop-up"></a>Proč se tento překryv zobrazuje?

.NET Framework vytvoří společnost Microsoft a poskytuje prostředí pro spouštění aplikací. K dispozici jsou různé verze. Řada společností vyvíjí své aplikace pro spouštění pomocí .NET Framework a tyto aplikace cílí na konkrétní verzi. Pokud se zobrazí toto automaticky otevírané okno, pokoušíte se spustit aplikaci, která vyžaduje verzi .NET Framework 3,5, ale tato verze není v systému nainstalovaná.

## <a name="enable-the-net-framework-35-in-control-panel"></a>Povolení .NET Framework 3,5 v Ovládacích panelech

.NET Framework 3,5 můžete povolit prostřednictvím ovládacího panelu systému Windows. Tato možnost vyžaduje připojení k Internetu.

1. Stiskněte klávesu Windows ![snímek obrazovky s logem Windows Key.](./media/dotnet-35-windows-10/windows-keyboard-logo.png) na klávesnici zadejte "funkce systému Windows" a stiskněte klávesu ENTER. Zobrazí se dialogové okno **zapnout nebo vypnout funkce systému Windows** .

2. Zaškrtněte políčko **.NET Framework 3,5 (zahrnuje rozhraní .net 2,0 a 3,0)** , vyberte **OK**a po zobrazení výzvy restartujte počítač.

   ![Snímek obrazovky s instalací rozhraní .NET pomocí ovládacích panelů](./media/dotnet-35-windows-10/dotnet-control-panel.png)

   Nemusíte vybírat podřízené položky pro aktivaci pomocí **protokolu HTTP služby Windows Communication Foundation (WCF)** a **Windows Communication Foundation (WCF) bez protokolu HTTP** , pokud nejste vývojář nebo správce serveru, který tuto funkci vyžaduje.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>Řešení potíží s instalací .NET Framework 3,5

Během instalace můžete narazit na chybu chyby 0x800F0906, 0x800f0907, 0x800F081F nebo 0x800F0922. v takovém případě se v takovém případě zobrazí [Chyba instalace .NET Framework 3,5: chyby 0x800F0906, 0x800f0907 nebo 0x800F081F](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) , kde zjistíte, jak tyto problémy vyřešit.

Pokud stále nemůžete problém s instalací vyřešit nebo nemáte připojení k Internetu, můžete ho zkusit nainstalovat pomocí instalačního média Windows. Další informace najdete v tématu [nasazení .NET Framework 3,5 pomocí nástroje pro údržbu a správu bitových kopií (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism). Pokud nemáte instalační médium, přečtěte si téma [Vytvoření instalačního média pro Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).

> [!WARNING]
> Pokud nespoléháte na web Windows Update jako zdroj pro instalaci .NET Framework 3,5, je nutné zajistit výhradně použití zdrojů ze stejné odpovídající verze operačního systému Windows. Použití zdrojové cesty, která neodpovídá stejné verzi Windows, nezabrání v instalaci neshodné verze .NET Framework 3,5. Dojde ale k tomu, že systém bude v nepodporovaném a neprovozního stavu.
