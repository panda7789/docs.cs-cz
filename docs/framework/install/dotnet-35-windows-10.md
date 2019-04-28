---
title: Instalace rozhraní .NET Framework 3.5 v systému Windows 10, Windows 8.1 a Windows 8
description: Informace o instalaci rozhraní .NET Framework 3.5 v systému Windows 10, Windows 8.1 a Windows 8.
author: rlander
ms.author: mairaw
ms.date: 07/16/2018
ms.openlocfilehash: 7b3b7ca5709008260ea284602a3ed8d2b288c410
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644183"
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Instalace rozhraní .NET Framework 3.5 v systému Windows 10, Windows 8.1 a Windows 8

Možná bude nutné rozhraní .NET Framework 3.5 ke spuštění aplikace na Windows 10, Windows 8.1 a Windows 8. Můžete také použít tyto pokyny pro starší verze Windows.

## <a name="install-the-net-framework-35-on-demand"></a>Instalace rozhraní .NET Framework 3.5 na vyžádání

Pokud se pokusíte spustit aplikaci, která vyžaduje rozhraní .NET Framework 3.5, může se zobrazit následující dialogové okno konfigurace. Zvolte **nainstalujte tuto funkci** povolit rozhraní .NET Framework 3.5. Tato možnost vyžaduje připojení k Internetu.

![Dialogové okno instalace rozhraní .NET framework](./media/dotnet-framework-installation-dialog.jpg)

### <a name="why-am-i-getting-this-pop-up"></a>Proč se zobrazuje toto automaticky otevírané?

Rozhraní .NET Framework je vytvořené microsoftem a poskytuje prostředí pro spouštění aplikací. K dispozici jsou různé verze. Mnoho společností vývoj aplikací pro spuštění pomocí rozhraní .NET Framework a tyto aplikace cílí na konkrétní verzi. Pokud se zobrazí toto automaticky otevírané okno, se snažíte spustit aplikaci, která vyžaduje rozhraní .NET Framework verze 3.5, ale není ve vašem systému nainstalována verze.

## <a name="enable-the-net-framework-35-in-control-panel"></a>Povolení rozhraní .NET Framework 3.5 v Ovládacích panelech

Můžete povolit rozhraní .NET Framework 3.5 prostřednictvím Ovládacích panelech Windows. Tato možnost vyžaduje připojení k Internetu.

1. Stiskněte klávesu Windows Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) na klávesnici, zadejte "Windows funkce" a stiskněte klávesu Enter. **Windows zapnout nebo vypnout funkce** zobrazí se dialogové okno.

2. Vyberte **rozhraní .NET Framework 3.5 (zahrnuje .NET 2.0 a 3.0)** zaškrtněte políčko **OK**a pokud se zobrazí výzva, restartujte počítač.

   ![Instalace .NET pomocí ovládacího panelu](./media/dotnet-control-panel.png)

   Nemusíte vybrat podřízené položky pro **aktivace Windows Communication Foundation (WCF) protokolem HTTP** a **Aktivace jiným protokolem než HTTP Windows Communication Foundation (WCF)** Pokud jste vývojář, nebo Správce serveru, který vyžaduje tuto funkci.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>Řešení potíží s instalací rozhraní .NET Framework 3.5

Během instalace, můžete narazit chyby 0x800f0906, 0x800f0907, 0x800f081f nebo 0x800F0922, v takovém případě si [Chyba instalace rozhraní .NET Framework 3.5: 0x800f0906, 0x800f0907 nebo 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) informace o tom, jak tyto problémy vyřešit.

Pokud stále nelze vyřešit váš problém s instalací nebo nemáte připojení k Internetu, můžete zkusit instalaci pomocí instalačního média Windows. Další informace najdete v tématu [nasazení rozhraní .NET Framework 3.5 pomocí Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism). Pokud nemáte k dispozici instalačním médiu, přečtěte si téma [vytvořit instalační médium pro Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).

> [!WARNING]
> Pokud nejsou spoléhat na webu Windows Update jako zdroj pro instalaci rozhraní .NET Framework 3.5, je nutné zajistit výhradně pomocí zdroje ze stejné odpovídající verzi operačního systému Windows. Pomocí cestu ke zdroji, který neodpovídá na stejnou verzi Windows nebudou zabránit instalaci neodpovídající verzi rozhraní .NET Framework 3.5. To však způsobí systém, aby byl ve stavu nepodporované a činnosti.
