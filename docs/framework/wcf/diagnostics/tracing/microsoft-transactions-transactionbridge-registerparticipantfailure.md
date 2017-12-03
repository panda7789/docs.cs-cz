---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 16b0261a53df29b1fc2049c25375c651735a524c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="3d22e-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="3d22e-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="3d22e-103">Služba protokolu WS-AT se nepodařilo zaregistrovat účastníka pro protokol ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3d22e-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3d22e-104">Popis</span><span class="sxs-lookup"><span data-stu-id="3d22e-104">Description</span></span>  
 <span data-ttu-id="3d22e-105">Trasovat, pokud služba MSDTC zjistí Neplatná žádost o registraci.</span><span class="sxs-lookup"><span data-stu-id="3d22e-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="3d22e-106">Příčinou může být více dokončení žádosti o registraci a interní chyby.</span><span class="sxs-lookup"><span data-stu-id="3d22e-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="3d22e-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="3d22e-107">Troubleshooting</span></span>  
 <span data-ttu-id="3d22e-108">Nepokoušejte se registrace pro dokončení více než jednou.</span><span class="sxs-lookup"><span data-stu-id="3d22e-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="3d22e-109">Také zkontrolujte stav řetězce v rámci zpráva trasování, která k určení, zda existuje libovolnou položku níž lze provést akci.</span><span class="sxs-lookup"><span data-stu-id="3d22e-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d22e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d22e-110">See Also</span></span>  
 [<span data-ttu-id="3d22e-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="3d22e-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="3d22e-112">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="3d22e-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="3d22e-113">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="3d22e-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
