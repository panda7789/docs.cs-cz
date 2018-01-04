---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3d3483165fe7a4895c6540f2c8023c09d6c00d2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="8dd25-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="8dd25-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="8dd25-103">Příprava opakování zpráva byla odeslána reagovat účastník.</span><span class="sxs-lookup"><span data-stu-id="8dd25-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8dd25-104">Popis</span><span class="sxs-lookup"><span data-stu-id="8dd25-104">Description</span></span>  
 <span data-ttu-id="8dd25-105">Sledovat v případě potřeby místní správce transakcí o doručení zprávy Příprava na podřízené účastník, protože nepřijala odpověď dané množství času.</span><span class="sxs-lookup"><span data-stu-id="8dd25-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8dd25-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="8dd25-106">Troubleshooting</span></span>  
 <span data-ttu-id="8dd25-107">Zjistěte, jestli potenciální sítě nebo problémů produktu, které brání doručován včas odpověď.</span><span class="sxs-lookup"><span data-stu-id="8dd25-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="8dd25-108">Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy.</span><span class="sxs-lookup"><span data-stu-id="8dd25-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="8dd25-109">Obě problémy může výrazně snížit propustnost transakce v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="8dd25-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dd25-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="8dd25-110">See Also</span></span>  
 [<span data-ttu-id="8dd25-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="8dd25-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="8dd25-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="8dd25-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="8dd25-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="8dd25-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
