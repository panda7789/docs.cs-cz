---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: f41fd08138591a90b6173b5e4806e5ac73ff07da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662761"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="8dd60-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="8dd60-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="8dd60-103">Zadaný transakce byla přerušena, protože při zavření relace, a atribut TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute byl nastaven na hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="8dd60-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8dd60-104">Popis</span><span class="sxs-lookup"><span data-stu-id="8dd60-104">Description</span></span>  
 <span data-ttu-id="8dd60-105">Sledovat aktuální aktivní relace byla ukončena a transakce nebyla dokončena a TransactionAutoCompleteOnSessionClose nastavená na `false`.</span><span class="sxs-lookup"><span data-stu-id="8dd60-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8dd60-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="8dd60-106">Troubleshooting</span></span>  
 <span data-ttu-id="8dd60-107">Trasování označuje potenciální chyby aplikace, které by mělo být vypátráno.</span><span class="sxs-lookup"><span data-stu-id="8dd60-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dd60-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8dd60-108">See also</span></span>
- [<span data-ttu-id="8dd60-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="8dd60-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="8dd60-110">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="8dd60-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8dd60-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="8dd60-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
