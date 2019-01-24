---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.date: 03/30/2017
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
ms.openlocfilehash: 0ed3a9a1c16247f94c739a43d84d51e4750b3c2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597655"
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="c95bf-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="c95bf-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="c95bf-103">Nastane, pokud službu nelze řádně uzavřít a byl přerušen.</span><span class="sxs-lookup"><span data-stu-id="c95bf-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c95bf-104">Popis</span><span class="sxs-lookup"><span data-stu-id="c95bf-104">Description</span></span>  
 <span data-ttu-id="c95bf-105">Tento kód chyby se zobrazí jenom v souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="c95bf-105">This error code only appears in the log file.</span></span> <span data-ttu-id="c95bf-106">To obvykle znamená programovací chyba, například při pokusu o uzavření službu po přerušení již byla volána.</span><span class="sxs-lookup"><span data-stu-id="c95bf-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="c95bf-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="c95bf-107">Troubleshooting</span></span>  
 <span data-ttu-id="c95bf-108">Zkontrolujte zdrojový kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="c95bf-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c95bf-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c95bf-109">See also</span></span>
- [<span data-ttu-id="c95bf-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="c95bf-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="c95bf-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="c95bf-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c95bf-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="c95bf-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
