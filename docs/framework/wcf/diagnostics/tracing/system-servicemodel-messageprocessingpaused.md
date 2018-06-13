---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: 6fb1463b811d985f54b9a99e59d1280eaa040256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33482811"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="b0d64-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="b0d64-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="b0d64-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="b0d64-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="b0d64-104">Popis</span><span class="sxs-lookup"><span data-stu-id="b0d64-104">Description</span></span>  
 <span data-ttu-id="b0d64-105">Při zpracování zprávy byly přepnout vláken.</span><span class="sxs-lookup"><span data-stu-id="b0d64-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="b0d64-106">Pozastavit zpracování zprávy lze z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="b0d64-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="b0d64-107">Režim ConcurrencyMode je jednoduchá nebo vícenásobné a služba zpracovává další zprávu.</span><span class="sxs-lookup"><span data-stu-id="b0d64-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="b0d64-108">Transakce je povolená a služba zpracovává jinou transakcí.</span><span class="sxs-lookup"><span data-stu-id="b0d64-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="b0d64-109">Kontext synchronizace není aktuální.</span><span class="sxs-lookup"><span data-stu-id="b0d64-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0d64-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0d64-110">See Also</span></span>  
 [<span data-ttu-id="b0d64-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="b0d64-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="b0d64-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="b0d64-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="b0d64-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="b0d64-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
