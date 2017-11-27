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
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="1adc2-104">Nainstalujte rozhraní .NET Framework 3.5 ve Windows 10, Windows 8.1 a Windows 8</span><span class="sxs-lookup"><span data-stu-id="1adc2-104">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="1adc2-105">Může být nutné rozhraní .NET Framework 3.5 ke spuštění aplikace na Windows 10, Windows 8.1 a Windows 8.</span><span class="sxs-lookup"><span data-stu-id="1adc2-105">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="1adc2-106">Také můžete použít tyto pokyny pro starší verze systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1adc2-106">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="1adc2-107">Na požádání nainstalovat rozhraní .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="1adc2-107">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="1adc2-108">Pokud se pokusíte spustit aplikaci, která vyžaduje rozhraní .NET Framework 3.5, může se zobrazit následující dialogové okno konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1adc2-108">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="1adc2-109">Zvolte **nainstalujte tuto funkci** povolení rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="1adc2-109">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="1adc2-110">Tato možnost vyžaduje připojení k Internetu.</span><span class="sxs-lookup"><span data-stu-id="1adc2-110">This option requires an Internet connection.</span></span>

![Dialogové okno instalace rozhraní .NET framework](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="1adc2-112">Povolení rozhraní .NET Framework 3.5 v Ovládacích panelech</span><span class="sxs-lookup"><span data-stu-id="1adc2-112">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="1adc2-113">Můžete povolit rozhraní .NET Framework 3.5 prostřednictvím ovládacího panelu Windows.</span><span class="sxs-lookup"><span data-stu-id="1adc2-113">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="1adc2-114">Tato možnost vyžaduje připojení k Internetu.</span><span class="sxs-lookup"><span data-stu-id="1adc2-114">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="1adc2-115">Stiskněte klávesu Windows Windows ![s logem Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) na klávesnici, zadejte "Funkce systému Windows" a stiskněte klávesu Enter.</span><span class="sxs-lookup"><span data-stu-id="1adc2-115">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="1adc2-116">**Windows zapnout nebo vypnout funkce** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="1adc2-116">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="1adc2-117">Vyberte **rozhraní .NET Framework 3.5 (zahrnuje rozhraní .NET 2.0 a 3.0)** zaškrtněte políčko **OK**a pokud se zobrazí výzva, restartujte počítač.</span><span class="sxs-lookup"><span data-stu-id="1adc2-117">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![Instalace rozhraní .NET pomocí ovládacího panelu](./media/dotnet-control-panel.png)

   <span data-ttu-id="1adc2-119">Není třeba vybírat podřízené položky pro **aktivace Windows Communication Foundation (WCF) protokolem HTTP** a **Aktivace jiným protokolem než HTTP Windows Communication Foundation (WCF)** Pokud jste vývojář nebo Správce serveru, který tato funkce vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="1adc2-119">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>
