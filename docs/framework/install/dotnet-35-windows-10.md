---
title: "Nainstalujte rozhraní .NET Framework 3.5 ve Windows 10, Windows 8.1 a Windows 8"
description: "Zjistěte, jak nainstalovat rozhraní .NET Framework 3.5 na Windows 10, Windows 8.1 a Windows 8."
author: rlander
ms.author: mairaw
keywords: "Rozhraní .NET framework, instalace"
ms.date: 05/26/2017
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 67cda1d5-c6g4-4eb5-93e6-4f478de07ff7
ms.openlocfilehash: 85a3cada074714c24015d90c26d94551f4f411f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Nainstalujte rozhraní .NET Framework 3.5 ve Windows 10, Windows 8.1 a Windows 8

Může být nutné rozhraní .NET Framework 3.5 ke spuštění aplikace na Windows 10, Windows 8.1 a Windows 8. Také můžete použít tyto pokyny pro starší verze systému Windows.

## <a name="install-the-net-framework-35-on-demand"></a>Na požádání nainstalovat rozhraní .NET Framework 3.5

Pokud se pokusíte spustit aplikaci, která vyžaduje rozhraní .NET Framework 3.5, může se zobrazit následující dialogové okno konfigurace. Zvolte **nainstalujte tuto funkci** povolení rozhraní .NET Framework 3.5. Tato možnost vyžaduje připojení k Internetu.

![Dialogové okno instalace rozhraní .NET framework](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a>Povolení rozhraní .NET Framework 3.5 v Ovládacích panelech

Můžete povolit rozhraní .NET Framework 3.5 prostřednictvím ovládacího panelu Windows. Tato možnost vyžaduje připojení k Internetu.

1. Stiskněte klávesu Windows Windows ![s logem Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) na klávesnici, zadejte "Funkce systému Windows" a stiskněte klávesu Enter. **Windows zapnout nebo vypnout funkce** zobrazí se dialogové okno.

2. Vyberte **rozhraní .NET Framework 3.5 (zahrnuje rozhraní .NET 2.0 a 3.0)** zaškrtněte políčko **OK**a pokud se zobrazí výzva, restartujte počítač.

   ![Instalace rozhraní .NET pomocí ovládacího panelu](./media/dotnet-control-panel.png)

   Není třeba vybírat podřízené položky pro **aktivace Windows Communication Foundation (WCF) protokolem HTTP** a **Aktivace jiným protokolem než HTTP Windows Communication Foundation (WCF)** Pokud jste vývojář nebo Správce serveru, který tato funkce vyžaduje.
