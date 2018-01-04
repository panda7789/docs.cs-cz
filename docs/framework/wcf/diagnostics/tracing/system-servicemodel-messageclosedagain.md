---
title: System.ServiceModel.MessageClosedAgain
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57500bf3c66c0aec47150bb21cc8871738d4b72d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="01ecb-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="01ecb-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="01ecb-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="01ecb-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="01ecb-104">Popis</span><span class="sxs-lookup"><span data-stu-id="01ecb-104">Description</span></span>  
 <span data-ttu-id="01ecb-105">Zprávu se zavřel znovu.</span><span class="sxs-lookup"><span data-stu-id="01ecb-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="01ecb-106">Zprávu by měly být ukončeny pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="01ecb-106">A message should be closed only once.</span></span> <span data-ttu-id="01ecb-107">Pokud trasování je právě vygenerované v uživatelském kódu rozšíření, znamená to, že uživatelského kódu rozšíření ukončuje zprávu, která již byl uzavřen.</span><span class="sxs-lookup"><span data-stu-id="01ecb-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="01ecb-108">Pokud toto trasování je právě vygenerované prostřednictvím kód produktu, znamená to, že uživatelského kódu rozšíření může potenciálně být zavření zprávy příliš brzké.</span><span class="sxs-lookup"><span data-stu-id="01ecb-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ecb-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="01ecb-109">See Also</span></span>  
 [<span data-ttu-id="01ecb-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="01ecb-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="01ecb-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="01ecb-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="01ecb-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="01ecb-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
