---
title: 'Postupy: Povolení služby sdílení portů Net.TCP'
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 8b305b98d620636328866bce848411f395053485
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593127"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="15f0b-102">Postupy: Povolení služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="15f0b-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="15f0b-103">Windows Communication Foundation (WCF) používá službu systému Windows s názvem služba sdílení portů Net. TCP, která usnadňuje sdílení portů TCP mezi více procesy.</span><span class="sxs-lookup"><span data-stu-id="15f0b-103">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="15f0b-104">Tato služba je nainstalovaná jako součást WCF, ale ve výchozím nastavení není služba standardně povolená, protože je bezpečnostní opatření, takže před prvním použitím je nutné ručně povolit.</span><span class="sxs-lookup"><span data-stu-id="15f0b-104">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="15f0b-105">Toto téma popisuje, jak nakonfigurovat službu sdílení portu NET TCP pomocí modulu snap-in konzoly Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="15f0b-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="15f0b-106">Jakmile povolíte službu sdílení portů Net. TCP a spustíte ji ručně, přečtěte si téma [Postupy: Konfigurace služby WCF pro použití sdílení portů](how-to-configure-a-wcf-service-to-use-port-sharing.md) , kde najdete informace o tom, jak službu nakonfigurovat tak, aby používala tuto službu.</span><span class="sxs-lookup"><span data-stu-id="15f0b-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="15f0b-107">Ukázku, která využívá sdílení NET. TCP://port, najdete v [ukázce sdílení portů Net. TCP](../samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="15f0b-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="15f0b-108">Povolení služby sdílení portů Net. TCP pomocí konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="15f0b-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1. <span data-ttu-id="15f0b-109">V nabídce Start otevřete konzolu pro správu služby buď otevřením okna příkazového řádku, zadáním `services.msc` nebo otevřením příkazu Spustit a zadáním `services.msc` do pole Otevřít.</span><span class="sxs-lookup"><span data-stu-id="15f0b-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2. <span data-ttu-id="15f0b-110">Ve sloupci **název** v seznamu služeb klikněte pravým tlačítkem na **službu sdílení portů Net. TCP**a v nabídce vyberte možnost **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="15f0b-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3. <span data-ttu-id="15f0b-111">Chcete-li povolit ruční spuštění služby, v okně **vlastnosti** vyberte kartu **Obecné** a v poli **Typ spuštění** vyberte možnost ručně a potom klikněte na tlačítko **použít**.</span><span class="sxs-lookup"><span data-stu-id="15f0b-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4. <span data-ttu-id="15f0b-112">Službu spustíte tak, že v oblasti stav služby kliknete na tlačítko **Spustit** .</span><span class="sxs-lookup"><span data-stu-id="15f0b-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="15f0b-113">Stav služby by nyní měl zobrazovat "spuštěno".</span><span class="sxs-lookup"><span data-stu-id="15f0b-113">The service status should now display "Started".</span></span>  
  
5. <span data-ttu-id="15f0b-114">Chcete-li se vrátit do seznamu služeb, klikněte na tlačítko **OK**a ukončete konzolu MMC.</span><span class="sxs-lookup"><span data-stu-id="15f0b-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15f0b-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="15f0b-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f0b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="15f0b-116">See also</span></span>

- [<span data-ttu-id="15f0b-117">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="15f0b-117">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="15f0b-118">Konfigurace služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="15f0b-118">Configuring the Net.TCP Port Sharing Service</span></span>](configuring-the-net-tcp-port-sharing-service.md)
