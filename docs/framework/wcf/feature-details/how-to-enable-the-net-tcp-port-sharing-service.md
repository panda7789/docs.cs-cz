---
title: "Postupy: povolení služby Sdílení portů Net.TCP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e9934d198b8f3e30a4dc350c968263851ebeab1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="fdf9f-102">Postupy: povolení služby Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="fdf9f-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="fdf9f-103">používá službu systému Windows s názvem služba Net.TCP Port Sharing usnadňuje sdílení portů TCP více procesy.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-103"> uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="fdf9f-104">Tato služba nainstaluje jako součást [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ale služba není povolena ve výchozím nastavení jako bezpečnostní opatření a, musí se zapnout ručně před prvním použití.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-104">This service is installed as part of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="fdf9f-105">Toto téma popisuje, jak nakonfigurovat službu Net TCP Port Sharing pomocí modulu snap-In konzoly Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="fdf9f-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="fdf9f-106">Po povolení služby Sdílení portů Net.TCP a jej spustit ručně, najdete v části [postupy: konfigurace použít sdílení portů ve službě WCF](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) informace o tom, jak nakonfigurovat služby k používání této služby.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="fdf9f-107">Příklad, který používá net.tcp:// sdílení portů, najdete v článku [ukázka sdílení portů Net.TCP](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="fdf9f-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="fdf9f-108">Chcete-li povolit službu Net.TCP Port Sharing pomocí konzoly MMC</span><span class="sxs-lookup"><span data-stu-id="fdf9f-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1.  <span data-ttu-id="fdf9f-109">Z nabídky Start, otevřete konzolu pro správu služby tak, že otevřete okno příkazového řádku a zadáte `services.msc` nebo otevřením spustit a zadáním `services.msc` do pole Otevřít.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2.  <span data-ttu-id="fdf9f-110">V **název** sloupec seznamu služeb, klikněte pravým tlačítkem myši **služba Net.Tcp Port Sharing**a vyberte **vlastnosti** z nabídky.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3.  <span data-ttu-id="fdf9f-111">Povolit ruční spuštění služby, v **vlastnosti** vyberte okno **Obecné** kartě a v **typ spuštění** pole vyberte ručně a pak klikněte na **Použít**.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4.  <span data-ttu-id="fdf9f-112">Chcete-li spustit službu, v oblasti stav služby, klikněte na tlačítko **spustit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="fdf9f-113">Stav služby by nyní měla zobrazovat "Začínáme".</span><span class="sxs-lookup"><span data-stu-id="fdf9f-113">The service status should now display "Started".</span></span>  
  
5.  <span data-ttu-id="fdf9f-114">Chcete-li se vrátit do seznamu služeb, klikněte na tlačítko **OK**a zavřete konzolu MMC.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdf9f-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="fdf9f-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdf9f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdf9f-116">See Also</span></span>  
 [<span data-ttu-id="fdf9f-117">Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="fdf9f-117">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [<span data-ttu-id="fdf9f-118">Konfigurace služby Sdílení portů Net.TCP</span><span class="sxs-lookup"><span data-stu-id="fdf9f-118">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
