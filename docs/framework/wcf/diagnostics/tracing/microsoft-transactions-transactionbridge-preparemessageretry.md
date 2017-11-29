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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b8199398e4e0bfe8ad42f6c8ba8adb11e883236e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="a0395-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="a0395-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="a0395-103">Příprava opakování zpráva byla odeslána reagovat účastník.</span><span class="sxs-lookup"><span data-stu-id="a0395-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a0395-104">Popis</span><span class="sxs-lookup"><span data-stu-id="a0395-104">Description</span></span>  
 <span data-ttu-id="a0395-105">Sledovat v případě potřeby místní správce transakcí o doručení zprávy Příprava na podřízené účastník, protože nepřijala odpověď dané množství času.</span><span class="sxs-lookup"><span data-stu-id="a0395-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="a0395-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="a0395-106">Troubleshooting</span></span>  
 <span data-ttu-id="a0395-107">Zjistěte, jestli potenciální sítě nebo problémů produktu, které brání doručován včas odpověď.</span><span class="sxs-lookup"><span data-stu-id="a0395-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="a0395-108">Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy.</span><span class="sxs-lookup"><span data-stu-id="a0395-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="a0395-109">Obě problémy může výrazně snížit propustnost transakce v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="a0395-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0395-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0395-110">See Also</span></span>  
 [<span data-ttu-id="a0395-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="a0395-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="a0395-112">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="a0395-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="a0395-113">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="a0395-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
