---
title: Nainstalujte rozhraní .NET Framework 3.5 ve Windows 10, Windows 8.1 a Windows 8
description: Zjistěte, jak nainstalovat rozhraní .NET Framework 3.5 na Windows 10, Windows 8.1 a Windows 8.
author: rlander
ms.author: mairaw
ms.date: 03/30/2018
ms.topic: article
ms.prod: .net-framework
ms.workload:
- dotnet
ms.openlocfilehash: 09c4f81da76bb6608c3e579c442cf686ffab1688
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Nainstalujte rozhraní .NET Framework 3.5 ve Windows 10, Windows 8.1 a Windows 8

Může být nutné rozhraní .NET Framework 3.5 ke spuštění aplikace na Windows 10, Windows 8.1 a Windows 8. Také můžete použít tyto pokyny pro starší verze systému Windows.

## <a name="install-the-net-framework-35-on-demand"></a>Na požádání nainstalovat rozhraní .NET Framework 3.5

Pokud se pokusíte spustit aplikaci, která vyžaduje rozhraní .NET Framework 3.5, může se zobrazit následující dialogové okno konfigurace. Zvolte **nainstalujte tuto funkci** povolení rozhraní .NET Framework 3.5. Tato možnost vyžaduje připojení k Internetu.

![Dialogové okno instalace rozhraní .NET framework](./media/dotnet-framework-installation-dialog.jpg)

### <a name="why-am-i-getting-this-pop-up"></a>Proč se zobrazuje toto automaticky otevírané okno?

Rozhraní .NET Framework se vytvoří společností Microsoft a poskytuje prostředí pro spouštění aplikací. Nejsou k dispozici různé verze. Mnoho společností vyvíjet jejich aplikace a používajících rozhraní .NET Framework a tyto aplikace cílit na konkrétní verzi. Pokud se zobrazí toto automaticky otevírané okno, se pokoušíte spustit aplikaci, která vyžaduje rozhraní .NET Framework verze 3.5, ale tuto verzi není nainstalován ve vašem systému.

## <a name="enable-the-net-framework-35-in-control-panel"></a>Povolení rozhraní .NET Framework 3.5 v Ovládacích panelech

Můžete povolit rozhraní .NET Framework 3.5 prostřednictvím ovládacího panelu Windows. Tato možnost vyžaduje připojení k Internetu.

1. Stiskněte klávesu Windows Windows ![s logem Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) na klávesnici, zadejte "Funkce systému Windows" a stiskněte klávesu Enter. **Windows zapnout nebo vypnout funkce** zobrazí se dialogové okno.

2. Vyberte **rozhraní .NET Framework 3.5 (zahrnuje rozhraní .NET 2.0 a 3.0)** zaškrtněte políčko **OK**a pokud se zobrazí výzva, restartujte počítač.

   ![Instalace rozhraní .NET pomocí ovládacího panelu](./media/dotnet-control-panel.png)

   Není třeba vybírat podřízené položky pro **aktivace Windows Communication Foundation (WCF) protokolem HTTP** a **Aktivace jiným protokolem než HTTP Windows Communication Foundation (WCF)** Pokud jste vývojář nebo Správce serveru, který tato funkce vyžaduje.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>Řešení potíží instalace rozhraní .NET Framework 3.5

Během instalace, se můžete setkat chyba 0x800f0906 0x800f0907, 0x800f081f nebo 0x800F0922, v takovém případě odkazovat na [chyby instalace rozhraní .NET Framework 3.5: 0x800f0906, 0x800f0907 nebo 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) chcete zjistit, jak chcete-li tyto problémy.

Pokud stále nelze vyřešit problém instalace nebo nemáte připojení k Internetu, můžete zkusit instalaci pomocí instalačního média systému Windows. Další informace najdete v tématu [nasazení rozhraní .NET Framework 3.5 pomocí Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism). Pokud nemáte k dispozici na instalačním médiu, přečtěte si téma [vytvořit instalační médium pro Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).
