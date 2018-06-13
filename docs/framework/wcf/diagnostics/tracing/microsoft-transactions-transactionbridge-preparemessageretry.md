---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: affa647b30dbeb9237e4c20ebb441645eda94276
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474321"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="1ec67-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="1ec67-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="1ec67-103">Příprava opakování zpráva byla odeslána reagovat účastník.</span><span class="sxs-lookup"><span data-stu-id="1ec67-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1ec67-104">Popis</span><span class="sxs-lookup"><span data-stu-id="1ec67-104">Description</span></span>  
 <span data-ttu-id="1ec67-105">Sledovat v případě potřeby místní správce transakcí o doručení zprávy Příprava na podřízené účastník, protože nepřijala odpověď dané množství času.</span><span class="sxs-lookup"><span data-stu-id="1ec67-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="1ec67-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="1ec67-106">Troubleshooting</span></span>  
 <span data-ttu-id="1ec67-107">Zjistěte, jestli potenciální sítě nebo problémů produktu, které brání doručován včas odpověď.</span><span class="sxs-lookup"><span data-stu-id="1ec67-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="1ec67-108">Pokud řadu tyto zprávy se zobrazují, může to znamenat problémy s infrastrukturou nebo neobvykle dlouhou dobou odezvy.</span><span class="sxs-lookup"><span data-stu-id="1ec67-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="1ec67-109">Obě problémy může výrazně snížit propustnost transakce v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="1ec67-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ec67-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ec67-110">See Also</span></span>  
 [<span data-ttu-id="1ec67-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="1ec67-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="1ec67-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="1ec67-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="1ec67-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="1ec67-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
