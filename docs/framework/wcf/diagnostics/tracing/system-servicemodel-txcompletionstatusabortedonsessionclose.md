---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: c398fc52d5924c033500b95924f9287b43cc9e9d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576600"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="e21e0-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="e21e0-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="e21e0-103">Zadaná transakce byla přerušena, protože nebyla dokončena při zavření relace a TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute byla nastavena na hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="e21e0-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e21e0-104">Popis</span><span class="sxs-lookup"><span data-stu-id="e21e0-104">Description</span></span>  
 <span data-ttu-id="e21e0-105">Sledováno, pokud byla aktuální aktivní relace zavřena a transakce nebyla dokončena a TransactionAutoCompleteOnSessionClose je nastavena na hodnotu `false` .</span><span class="sxs-lookup"><span data-stu-id="e21e0-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e21e0-106">Řešení potíží</span><span class="sxs-lookup"><span data-stu-id="e21e0-106">Troubleshooting</span></span>  
 <span data-ttu-id="e21e0-107">Toto trasování indikuje potenciální chybu aplikace, která by se měla prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="e21e0-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e21e0-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="e21e0-108">See also</span></span>

- [<span data-ttu-id="e21e0-109">Trasování</span><span class="sxs-lookup"><span data-stu-id="e21e0-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="e21e0-110">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="e21e0-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e21e0-111">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="e21e0-111">Administration and Diagnostics</span></span>](../index.md)
