---
title: 'Postupy: Povolení Služby sdílení portů Net.TCP'
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 77d1d983da87b37c6267cc38a16db446782797f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130647"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="86a2b-102">Postupy: Povolení Služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="86a2b-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="86a2b-103">Windows Communication Foundation (WCF) používá službu Windows volá služba Sdílení portů Net.TCP k usnadnění sdílení portů TCP napříč více procesy.</span><span class="sxs-lookup"><span data-stu-id="86a2b-103">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="86a2b-104">Tato služba je nainstalován jako součást služby WCF, ale služba není povolená ve výchozím nastavení jako bezpečnostní opatření a proto musíte ručně povolit před prvním použitím.</span><span class="sxs-lookup"><span data-stu-id="86a2b-104">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="86a2b-105">Toto téma popisuje, jak nakonfigurovat službu Net TCP Port Sharing pomocí modulu snap-In konzoly Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="86a2b-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="86a2b-106">Po povolení služby Sdílení portů Net.TCP a spustit ručně, najdete v článku [jak: Konfigurace použití sdílení portů ve službě WCF](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) informace o tom, jak nakonfigurovat svoji službu pro tuto službu používat.</span><span class="sxs-lookup"><span data-stu-id="86a2b-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="86a2b-107">Ukázku, která používá net.tcp:// sdílení portů najdete v tématu [ukázka sdílení portů Net.TCP](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="86a2b-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="86a2b-108">Chcete-li povolit službu Net.TCP Port Sharing pomocí konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="86a2b-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1.  <span data-ttu-id="86a2b-109">Z nabídky Start otevřete konzolu pro správu služeb tak, že otevřete okno příkazového řádku a zadáte `services.msc` nebo otevřením spustit a zadáním `services.msc` do pole.</span><span class="sxs-lookup"><span data-stu-id="86a2b-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2.  <span data-ttu-id="86a2b-110">V **název** klikněte pravým tlačítkem na sloupec v seznamu služeb, **služba Sdílení portů Net.Tcp**a vyberte **vlastnosti** z nabídky.</span><span class="sxs-lookup"><span data-stu-id="86a2b-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3.  <span data-ttu-id="86a2b-111">Povolit ruční spuštění služby, v **vlastnosti** vyberte okno **Obecné** kartu a v **typ spouštění** vyberte ručně a klepněte na tlačítko **Použít**.</span><span class="sxs-lookup"><span data-stu-id="86a2b-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4.  <span data-ttu-id="86a2b-112">Chcete-li spustit službu, v oblasti stavu služby, klikněte na tlačítko **Start** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="86a2b-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="86a2b-113">Stav služby nyní zobrazeno "Začínáme".</span><span class="sxs-lookup"><span data-stu-id="86a2b-113">The service status should now display "Started".</span></span>  
  
5.  <span data-ttu-id="86a2b-114">Chcete-li vrátit do seznamu služeb, klikněte na tlačítko **OK**a ukončete konzolu MMC.</span><span class="sxs-lookup"><span data-stu-id="86a2b-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86a2b-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="86a2b-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86a2b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86a2b-116">See also</span></span>

- [<span data-ttu-id="86a2b-117">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="86a2b-117">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="86a2b-118">Konfigurace Služby sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="86a2b-118">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
