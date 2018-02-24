---
title: "Nainstalujte rozhraní .NET Framework 3.5 ve Windows 10, Windows 8.1 a Windows 8"
description: "Zjistěte, jak nainstalovat rozhraní .NET Framework 3.5 na Windows 10, Windows 8.1 a Windows 8."
author: rlander
ms.author: mairaw
ms.date: 11/27/2017
ms.topic: article
ms.prod: .net-framework
ms.workload:
- dotnet
ms.openlocfilehash: e81008eca3019860789db548d40998a7a7565d31
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a><span data-ttu-id="55a5c-103">Nainstalujte rozhraní .NET Framework 3.5 ve Windows 10, Windows 8.1 a Windows 8</span><span class="sxs-lookup"><span data-stu-id="55a5c-103">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>

<span data-ttu-id="55a5c-104">Může být nutné rozhraní .NET Framework 3.5 ke spuštění aplikace na Windows 10, Windows 8.1 a Windows 8.</span><span class="sxs-lookup"><span data-stu-id="55a5c-104">You may need the .NET Framework 3.5 to run an app on Windows 10, Windows 8.1, and Windows 8.</span></span> <span data-ttu-id="55a5c-105">Také můžete použít tyto pokyny pro starší verze systému Windows.</span><span class="sxs-lookup"><span data-stu-id="55a5c-105">You can also use these instructions for earlier Windows versions.</span></span>

## <a name="install-the-net-framework-35-on-demand"></a><span data-ttu-id="55a5c-106">Na požádání nainstalovat rozhraní .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="55a5c-106">Install the .NET Framework 3.5 on Demand</span></span>

<span data-ttu-id="55a5c-107">Pokud se pokusíte spustit aplikaci, která vyžaduje rozhraní .NET Framework 3.5, může se zobrazit následující dialogové okno konfigurace.</span><span class="sxs-lookup"><span data-stu-id="55a5c-107">You may see the following configuration dialog if you try to run an app that requires the .NET Framework 3.5.</span></span> <span data-ttu-id="55a5c-108">Zvolte **nainstalujte tuto funkci** povolení rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="55a5c-108">Choose **Install this feature** to enable the .NET Framework 3.5.</span></span> <span data-ttu-id="55a5c-109">Tato možnost vyžaduje připojení k Internetu.</span><span class="sxs-lookup"><span data-stu-id="55a5c-109">This option requires an Internet connection.</span></span>

![Dialogové okno instalace rozhraní .NET framework](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a><span data-ttu-id="55a5c-111">Povolení rozhraní .NET Framework 3.5 v Ovládacích panelech</span><span class="sxs-lookup"><span data-stu-id="55a5c-111">Enable the .NET Framework 3.5 in Control Panel</span></span>

<span data-ttu-id="55a5c-112">Můžete povolit rozhraní .NET Framework 3.5 prostřednictvím ovládacího panelu Windows.</span><span class="sxs-lookup"><span data-stu-id="55a5c-112">You can enable the .NET Framework 3.5 through the Windows Control Panel.</span></span> <span data-ttu-id="55a5c-113">Tato možnost vyžaduje připojení k Internetu.</span><span class="sxs-lookup"><span data-stu-id="55a5c-113">This option requires an Internet connection.</span></span>

1. <span data-ttu-id="55a5c-114">Stiskněte klávesu Windows Windows ![s logem Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) na klávesnici, zadejte "Funkce systému Windows" a stiskněte klávesu Enter.</span><span class="sxs-lookup"><span data-stu-id="55a5c-114">Press the Windows key Windows ![Windows logo](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) on your keyboard, type "Windows Features", and press Enter.</span></span> <span data-ttu-id="55a5c-115">**Windows zapnout nebo vypnout funkce** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="55a5c-115">The **Turn Windows features on or off** dialog box appears.</span></span>

2. <span data-ttu-id="55a5c-116">Vyberte **rozhraní .NET Framework 3.5 (zahrnuje rozhraní .NET 2.0 a 3.0)** zaškrtněte políčko **OK**a pokud se zobrazí výzva, restartujte počítač.</span><span class="sxs-lookup"><span data-stu-id="55a5c-116">Select the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box, select **OK**, and reboot your computer if prompted.</span></span>

   ![Instalace rozhraní .NET pomocí ovládacího panelu](./media/dotnet-control-panel.png)

   <span data-ttu-id="55a5c-118">Není třeba vybírat podřízené položky pro **aktivace Windows Communication Foundation (WCF) protokolem HTTP** a **Aktivace jiným protokolem než HTTP Windows Communication Foundation (WCF)** Pokud jste vývojář nebo Správce serveru, který tato funkce vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="55a5c-118">You don't need to select the child items for **Windows Communication Foundation (WCF) HTTP Activation** and **Windows Communication Foundation (WCF) Non-HTTP Activation** unless you're a developer or server administrator who requires this functionality.</span></span>

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a><span data-ttu-id="55a5c-119">Řešení potíží instalace rozhraní .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="55a5c-119">Troubleshoot the installation of the .NET Framework 3.5</span></span>

<span data-ttu-id="55a5c-120">Během instalace, se můžete setkat chyba 0x800f0906 0x800f0907, 0x800f081f nebo 0x800F0922, v takovém případě odkazovat na [chyby instalace rozhraní .NET Framework 3.5: 0x800f0906, 0x800f0907 nebo 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) chcete zjistit, jak chcete-li tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="55a5c-120">During installation, you may encounter error 0x800f0906, 0x800f0907, 0x800f081f, or 0x800F0922, in which case refer to [.NET Framework 3.5 installation error: 0x800f0906, 0x800f0907, or 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) to see how to resolve these issues.</span></span>

<span data-ttu-id="55a5c-121">Pokud některou z metod popsaných v předchozím článku nezdaří, nebo pokud nemáte připojení k Internetu, je třeba použít instalačním médiu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="55a5c-121">If any of the methods discussed in the previous article fail or if you don't have an Internet connection, it's necessary to use your Windows installation media.</span></span> <span data-ttu-id="55a5c-122">Další informace najdete v tématu [nasazení rozhraní .NET Framework 3.5 pomocí Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism).</span><span class="sxs-lookup"><span data-stu-id="55a5c-122">For more information, see [Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism).</span></span> <span data-ttu-id="55a5c-123">Pokud nemáte k dispozici na instalačním médiu, přečtěte si téma [vytvořit instalační médium pro Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span><span class="sxs-lookup"><span data-stu-id="55a5c-123">If you don't have the installation media, see [Create installation media for Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).</span></span>
