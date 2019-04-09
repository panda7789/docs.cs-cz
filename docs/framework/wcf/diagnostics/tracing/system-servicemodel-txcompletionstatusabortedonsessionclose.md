---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 7b1f6a2f4a344b566c76d0095942b84a8a4e76f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166501"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="8261f-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="8261f-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="8261f-103">Zadaný transakce byla přerušena, protože při zavření relace, a atribut TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute byl nastaven na hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="8261f-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8261f-104">Popis</span><span class="sxs-lookup"><span data-stu-id="8261f-104">Description</span></span>  
 <span data-ttu-id="8261f-105">Sledovat aktuální aktivní relace byla ukončena a transakce nebyla dokončena a TransactionAutoCompleteOnSessionClose nastavená na `false`.</span><span class="sxs-lookup"><span data-stu-id="8261f-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="8261f-106">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="8261f-106">Troubleshooting</span></span>  
 <span data-ttu-id="8261f-107">Trasování označuje potenciální chyby aplikace, které by mělo být vypátráno.</span><span class="sxs-lookup"><span data-stu-id="8261f-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8261f-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8261f-108">See also</span></span>

- [<span data-ttu-id="8261f-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="8261f-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="8261f-110">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="8261f-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="8261f-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="8261f-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
