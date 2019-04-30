---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: ac1dacef94d6446aa407e4a390b9561d033af1bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61927020"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="fa49e-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="fa49e-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="fa49e-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="fa49e-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="fa49e-104">Popis</span><span class="sxs-lookup"><span data-stu-id="fa49e-104">Description</span></span>  
 <span data-ttu-id="fa49e-105">Při zpracování zprávy byly přepnout vlákna.</span><span class="sxs-lookup"><span data-stu-id="fa49e-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="fa49e-106">Pozastavit zpracování zprávy lze z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="fa49e-106">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="fa49e-107">Režim ConcurrencyMode je jednoduché nebo vícenásobné a služba zpracovává jinou zprávu.</span><span class="sxs-lookup"><span data-stu-id="fa49e-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="fa49e-108">Transakce je povolená a služba zpracovává jinou transakcí.</span><span class="sxs-lookup"><span data-stu-id="fa49e-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="fa49e-109">Kontext synchronizace není aktuální.</span><span class="sxs-lookup"><span data-stu-id="fa49e-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa49e-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa49e-110">See also</span></span>

- [<span data-ttu-id="fa49e-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="fa49e-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="fa49e-112">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="fa49e-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="fa49e-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="fa49e-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
