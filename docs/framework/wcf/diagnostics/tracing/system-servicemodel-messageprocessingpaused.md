---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: ac1dacef94d6446aa407e4a390b9561d033af1bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087466"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="3048f-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="3048f-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="3048f-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="3048f-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="3048f-104">Popis</span><span class="sxs-lookup"><span data-stu-id="3048f-104">Description</span></span>  
 <span data-ttu-id="3048f-105">Při zpracování zprávy byly přepnout vlákna.</span><span class="sxs-lookup"><span data-stu-id="3048f-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="3048f-106">Pozastavit zpracování zprávy lze z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="3048f-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="3048f-107">Režim ConcurrencyMode je jednoduché nebo vícenásobné a služba zpracovává jinou zprávu.</span><span class="sxs-lookup"><span data-stu-id="3048f-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="3048f-108">Transakce je povolená a služba zpracovává jinou transakcí.</span><span class="sxs-lookup"><span data-stu-id="3048f-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="3048f-109">Kontext synchronizace není aktuální.</span><span class="sxs-lookup"><span data-stu-id="3048f-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3048f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3048f-110">See also</span></span>

- [<span data-ttu-id="3048f-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="3048f-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="3048f-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="3048f-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="3048f-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="3048f-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
