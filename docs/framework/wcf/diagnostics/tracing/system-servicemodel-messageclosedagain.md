---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: 3a73834888ae4a8945bd71492d787e23868fa5e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33480740"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="75935-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="75935-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="75935-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="75935-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="75935-104">Popis</span><span class="sxs-lookup"><span data-stu-id="75935-104">Description</span></span>  
 <span data-ttu-id="75935-105">Zprávu se zavřel znovu.</span><span class="sxs-lookup"><span data-stu-id="75935-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="75935-106">Zprávu by měly být ukončeny pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="75935-106">A message should be closed only once.</span></span> <span data-ttu-id="75935-107">Pokud trasování je právě vygenerované v uživatelském kódu rozšíření, znamená to, že uživatelského kódu rozšíření ukončuje zprávu, která již byl uzavřen.</span><span class="sxs-lookup"><span data-stu-id="75935-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="75935-108">Pokud toto trasování je právě vygenerované prostřednictvím kód produktu, znamená to, že uživatelského kódu rozšíření může potenciálně být zavření zprávy příliš brzké.</span><span class="sxs-lookup"><span data-stu-id="75935-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75935-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="75935-109">See Also</span></span>  
 [<span data-ttu-id="75935-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="75935-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="75935-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="75935-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="75935-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="75935-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
