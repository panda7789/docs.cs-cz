---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be874cc0b3fb15f80bb5cd6b97174b515703385c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="f8d7c-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="f8d7c-102">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>
<span data-ttu-id="f8d7c-103">Opakování potvrzení zpráva byla odeslána reagovat účastník.</span><span class="sxs-lookup"><span data-stu-id="f8d7c-103">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f8d7c-104">Popis</span><span class="sxs-lookup"><span data-stu-id="f8d7c-104">Description</span></span>  
 <span data-ttu-id="f8d7c-105">Sledovat v případě potřeby místní správce transakcí o doručení zprávy potvrzení k podřízené účastník, protože nepřijala odpověď dané množství času.</span><span class="sxs-lookup"><span data-stu-id="f8d7c-105">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f8d7c-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="f8d7c-106">Troubleshooting</span></span>  
 <span data-ttu-id="f8d7c-107">Zjistěte, jestli potenciální sítě nebo problémů produktu, které brání doručován včas odpověď.</span><span class="sxs-lookup"><span data-stu-id="f8d7c-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="f8d7c-108">Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy.</span><span class="sxs-lookup"><span data-stu-id="f8d7c-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="f8d7c-109">Obě tyto chyby se výrazně zjednodušit propustnost transakce v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="f8d7c-109">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8d7c-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8d7c-110">See Also</span></span>  
 [<span data-ttu-id="f8d7c-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="f8d7c-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f8d7c-112">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="f8d7c-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f8d7c-113">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="f8d7c-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
