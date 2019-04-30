---
title: 'Postupy: Povolení Služby sdílení portů Net.TCP'
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 20db0ef427a5e791bd6b8dcef90bf7911ae0d4a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772954"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="2d50a-102">Postupy: Povolení Služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="2d50a-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="2d50a-103">Windows Communication Foundation (WCF) používá službu Windows volá služba Sdílení portů Net.TCP k usnadnění sdílení portů TCP napříč více procesy.</span><span class="sxs-lookup"><span data-stu-id="2d50a-103">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="2d50a-104">Tato služba je nainstalován jako součást služby WCF, ale služba není povolená ve výchozím nastavení jako bezpečnostní opatření a proto musíte ručně povolit před prvním použitím.</span><span class="sxs-lookup"><span data-stu-id="2d50a-104">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="2d50a-105">Toto téma popisuje, jak nakonfigurovat službu Net TCP Port Sharing pomocí modulu snap-In konzoly Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="2d50a-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="2d50a-106">Po povolení služby Sdílení portů Net.TCP a spustit ručně, najdete v článku [jak: Konfigurace použití sdílení portů ve službě WCF](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) informace o tom, jak nakonfigurovat svoji službu pro tuto službu používat.</span><span class="sxs-lookup"><span data-stu-id="2d50a-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="2d50a-107">Ukázku, která používá net.tcp:// sdílení portů najdete v tématu [ukázka sdílení portů Net.TCP](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2d50a-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="2d50a-108">Chcete-li povolit službu Net.TCP Port Sharing pomocí konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="2d50a-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1. <span data-ttu-id="2d50a-109">Z nabídky Start otevřete konzolu pro správu služeb tak, že otevřete okno příkazového řádku a zadáte `services.msc` nebo otevřením spustit a zadáním `services.msc` do pole.</span><span class="sxs-lookup"><span data-stu-id="2d50a-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2. <span data-ttu-id="2d50a-110">V **název** klikněte pravým tlačítkem na sloupec v seznamu služeb, **služba Sdílení portů Net.Tcp**a vyberte **vlastnosti** z nabídky.</span><span class="sxs-lookup"><span data-stu-id="2d50a-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3. <span data-ttu-id="2d50a-111">Povolit ruční spuštění služby, v **vlastnosti** vyberte okno **Obecné** kartu a v **typ spouštění** vyberte ručně a klepněte na tlačítko **Použít**.</span><span class="sxs-lookup"><span data-stu-id="2d50a-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4. <span data-ttu-id="2d50a-112">Chcete-li spustit službu, v oblasti stavu služby, klikněte na tlačítko **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2d50a-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="2d50a-113">Stav služby nyní zobrazeno "Začínáme".</span><span class="sxs-lookup"><span data-stu-id="2d50a-113">The service status should now display "Started".</span></span>  
  
5. <span data-ttu-id="2d50a-114">Chcete-li vrátit do seznamu služeb, klikněte na tlačítko **OK**a ukončete konzolu MMC.</span><span class="sxs-lookup"><span data-stu-id="2d50a-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d50a-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d50a-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d50a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d50a-116">See also</span></span>

- [<span data-ttu-id="2d50a-117">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="2d50a-117">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="2d50a-118">Konfigurace služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="2d50a-118">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
