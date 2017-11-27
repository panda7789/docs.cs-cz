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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e3cbe9443f32ec9752198646e96cc1012d7343c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="07f2c-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="07f2c-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="07f2c-103">Služba protokolu WS-AT se nepodařilo zaregistrovat účastníka pro protokol ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="07f2c-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="07f2c-104">Popis</span><span class="sxs-lookup"><span data-stu-id="07f2c-104">Description</span></span>  
 <span data-ttu-id="07f2c-105">Trasovat, pokud služba MSDTC zjistí Neplatná žádost o registraci.</span><span class="sxs-lookup"><span data-stu-id="07f2c-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="07f2c-106">Příčinou může být více dokončení žádosti o registraci a interní chyby.</span><span class="sxs-lookup"><span data-stu-id="07f2c-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="07f2c-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="07f2c-107">Troubleshooting</span></span>  
 <span data-ttu-id="07f2c-108">Nepokoušejte se registrace pro dokončení více než jednou.</span><span class="sxs-lookup"><span data-stu-id="07f2c-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="07f2c-109">Také zkontrolujte stav řetězce v rámci zpráva trasování, která k určení, zda existuje libovolnou položku níž lze provést akci.</span><span class="sxs-lookup"><span data-stu-id="07f2c-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f2c-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="07f2c-110">See Also</span></span>  
 [<span data-ttu-id="07f2c-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="07f2c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="07f2c-112">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="07f2c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="07f2c-113">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="07f2c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
