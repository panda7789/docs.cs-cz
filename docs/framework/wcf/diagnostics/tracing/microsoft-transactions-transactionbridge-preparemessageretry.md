---
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: 0c53c1617f3aa3c5f16ba16e8ec548e46ce22137
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594332"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="30c70-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="30c70-102">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>
<span data-ttu-id="30c70-103">Připravená zpráva byla znovu poslána účastníkovi, který nereaguje.</span><span class="sxs-lookup"><span data-stu-id="30c70-103">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="30c70-104">Popis</span><span class="sxs-lookup"><span data-stu-id="30c70-104">Description</span></span>  
 <span data-ttu-id="30c70-105">Sledováno, pokud správce místní transakce potřebuje znovu odeslat přípravu zprávy podřízenému účastníkovi, protože v daném čase nedostal odpověď.</span><span class="sxs-lookup"><span data-stu-id="30c70-105">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="30c70-106">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="30c70-106">Troubleshooting</span></span>  
 <span data-ttu-id="30c70-107">Prozkoumejte potenciální problémy se sítí nebo produktem, které brání doručení odpovědi včas.</span><span class="sxs-lookup"><span data-stu-id="30c70-107">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="30c70-108">Pokud se zobrazí mnoho z těchto zpráv, může to znamenat problémy s infrastrukturou nebo nezvykle dlouhou dobu odezvy.</span><span class="sxs-lookup"><span data-stu-id="30c70-108">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="30c70-109">Oba problémy můžou významně snížit propustnost transakcí v rámci systému.</span><span class="sxs-lookup"><span data-stu-id="30c70-109">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c70-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="30c70-110">See also</span></span>

- [<span data-ttu-id="30c70-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="30c70-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="30c70-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="30c70-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="30c70-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="30c70-113">Administration and Diagnostics</span></span>](../index.md)
