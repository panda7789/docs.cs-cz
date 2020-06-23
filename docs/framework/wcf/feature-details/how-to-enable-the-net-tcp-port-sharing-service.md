---
title: 'Postupy: Povolení služby sdílení portů Net.TCP'
description: Naučte se konfigurovat službu sdílení portů net TCP pomocí konzoly MMC k povolení NET. TCP, která je ve výchozím nastavení zakázaná.
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 0292559e3befde7f0b00b36aa10a2d9615daf049
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246997"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="b1316-103">Postupy: Povolení služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="b1316-103">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="b1316-104">Windows Communication Foundation (WCF) používá službu systému Windows s názvem služba sdílení portů Net. TCP, která usnadňuje sdílení portů TCP mezi více procesy.</span><span class="sxs-lookup"><span data-stu-id="b1316-104">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="b1316-105">Tato služba je nainstalovaná jako součást WCF, ale ve výchozím nastavení není služba standardně povolená, protože je bezpečnostní opatření, takže před prvním použitím je nutné ručně povolit.</span><span class="sxs-lookup"><span data-stu-id="b1316-105">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="b1316-106">Toto téma popisuje, jak nakonfigurovat službu sdílení portu NET TCP pomocí modulu snap-in konzoly Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="b1316-106">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="b1316-107">Jakmile povolíte službu sdílení portů Net. TCP a spustíte ji ručně, přečtěte si téma [Postupy: Konfigurace služby WCF pro použití sdílení portů](how-to-configure-a-wcf-service-to-use-port-sharing.md) , kde najdete informace o tom, jak službu nakonfigurovat tak, aby používala tuto službu.</span><span class="sxs-lookup"><span data-stu-id="b1316-107">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="b1316-108">Ukázku, která využívá sdílení NET. TCP://port, najdete v [ukázce sdílení portů Net. TCP](../samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b1316-108">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="b1316-109">Povolení služby sdílení portů Net. TCP pomocí konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="b1316-109">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1. <span data-ttu-id="b1316-110">V nabídce Start otevřete konzolu pro správu služby buď otevřením okna příkazového řádku, zadáním `services.msc` nebo otevřením příkazu Spustit a zadáním `services.msc` do pole Otevřít.</span><span class="sxs-lookup"><span data-stu-id="b1316-110">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2. <span data-ttu-id="b1316-111">Ve sloupci **název** v seznamu služeb klikněte pravým tlačítkem na **službu sdílení portů Net. TCP**a v nabídce vyberte možnost **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="b1316-111">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3. <span data-ttu-id="b1316-112">Chcete-li povolit ruční spuštění služby, v okně **vlastnosti** vyberte kartu **Obecné** a v poli **Typ spuštění** vyberte možnost ručně a potom klikněte na tlačítko **použít**.</span><span class="sxs-lookup"><span data-stu-id="b1316-112">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4. <span data-ttu-id="b1316-113">Službu spustíte tak, že v oblasti stav služby kliknete na tlačítko **Spustit** .</span><span class="sxs-lookup"><span data-stu-id="b1316-113">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="b1316-114">Stav služby by nyní měl zobrazovat "spuštěno".</span><span class="sxs-lookup"><span data-stu-id="b1316-114">The service status should now display "Started".</span></span>  
  
5. <span data-ttu-id="b1316-115">Chcete-li se vrátit do seznamu služeb, klikněte na tlačítko **OK**a ukončete konzolu MMC.</span><span class="sxs-lookup"><span data-stu-id="b1316-115">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1316-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1316-116">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1316-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1316-117">See also</span></span>

- [<span data-ttu-id="b1316-118">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="b1316-118">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="b1316-119">Konfigurace služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="b1316-119">Configuring the Net.TCP Port Sharing Service</span></span>](configuring-the-net-tcp-port-sharing-service.md)
