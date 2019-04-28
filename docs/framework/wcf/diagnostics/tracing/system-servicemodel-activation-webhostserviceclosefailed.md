---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.date: 03/30/2017
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
ms.openlocfilehash: afe84db3d4df8914ff1ed001b064439d581ead89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61752760"
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="89eb5-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="89eb5-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="89eb5-103">Nastane, pokud službu nelze řádně uzavřít a byl přerušen.</span><span class="sxs-lookup"><span data-stu-id="89eb5-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="89eb5-104">Popis</span><span class="sxs-lookup"><span data-stu-id="89eb5-104">Description</span></span>  
 <span data-ttu-id="89eb5-105">Tento kód chyby se zobrazí jenom v souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="89eb5-105">This error code only appears in the log file.</span></span> <span data-ttu-id="89eb5-106">To obvykle znamená programovací chyba, například při pokusu o uzavření službu po přerušení již byla volána.</span><span class="sxs-lookup"><span data-stu-id="89eb5-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="89eb5-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="89eb5-107">Troubleshooting</span></span>  
 <span data-ttu-id="89eb5-108">Zkontrolujte zdrojový kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="89eb5-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89eb5-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89eb5-109">See also</span></span>

- [<span data-ttu-id="89eb5-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="89eb5-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="89eb5-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="89eb5-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="89eb5-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="89eb5-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
