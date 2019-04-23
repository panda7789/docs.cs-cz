---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.date: 03/30/2017
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
ms.openlocfilehash: afe84db3d4df8914ff1ed001b064439d581ead89
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085387"
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="fad6b-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="fad6b-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="fad6b-103">Nastane, pokud službu nelze řádně uzavřít a byl přerušen.</span><span class="sxs-lookup"><span data-stu-id="fad6b-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fad6b-104">Popis</span><span class="sxs-lookup"><span data-stu-id="fad6b-104">Description</span></span>  
 <span data-ttu-id="fad6b-105">Tento kód chyby se zobrazí jenom v souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="fad6b-105">This error code only appears in the log file.</span></span> <span data-ttu-id="fad6b-106">To obvykle znamená programovací chyba, například při pokusu o uzavření službu po přerušení již byla volána.</span><span class="sxs-lookup"><span data-stu-id="fad6b-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="fad6b-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="fad6b-107">Troubleshooting</span></span>  
 <span data-ttu-id="fad6b-108">Zkontrolujte zdrojový kód aplikace.</span><span class="sxs-lookup"><span data-stu-id="fad6b-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fad6b-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fad6b-109">See also</span></span>

- [<span data-ttu-id="fad6b-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="fad6b-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="fad6b-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="fad6b-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="fad6b-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="fad6b-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
