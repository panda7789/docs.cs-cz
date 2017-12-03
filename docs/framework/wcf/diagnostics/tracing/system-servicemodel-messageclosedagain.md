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
ms.openlocfilehash: ec4a0acc70f1878756776d7ed8e8d8e5ee64035f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="4a25e-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="4a25e-102">System.ServiceModel.MessageClosedAgain</span></span>
<span data-ttu-id="4a25e-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="4a25e-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="4a25e-104">Popis</span><span class="sxs-lookup"><span data-stu-id="4a25e-104">Description</span></span>  
 <span data-ttu-id="4a25e-105">Zprávu se zavřel znovu.</span><span class="sxs-lookup"><span data-stu-id="4a25e-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="4a25e-106">Zprávu by měly být ukončeny pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="4a25e-106">A message should be closed only once.</span></span> <span data-ttu-id="4a25e-107">Pokud trasování je právě vygenerované v uživatelském kódu rozšíření, znamená to, že uživatelského kódu rozšíření ukončuje zprávu, která již byl uzavřen.</span><span class="sxs-lookup"><span data-stu-id="4a25e-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="4a25e-108">Pokud toto trasování je právě vygenerované prostřednictvím kód produktu, znamená to, že uživatelského kódu rozšíření může potenciálně být zavření zprávy příliš brzké.</span><span class="sxs-lookup"><span data-stu-id="4a25e-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a25e-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a25e-109">See Also</span></span>  
 [<span data-ttu-id="4a25e-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="4a25e-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="4a25e-111">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="4a25e-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="4a25e-112">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="4a25e-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
