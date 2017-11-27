---
title: System.ServiceModel.MessageProcessingPaused
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1176af676673e19eb2d8cd54cc4d2d254c7ba324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="da9a6-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="da9a6-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="da9a6-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="da9a6-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="da9a6-104">Popis</span><span class="sxs-lookup"><span data-stu-id="da9a6-104">Description</span></span>  
 <span data-ttu-id="da9a6-105">Při zpracování zprávy byly přepnout vláken.</span><span class="sxs-lookup"><span data-stu-id="da9a6-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="da9a6-106">Pozastavit zpracování zprávy lze z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="da9a6-106">Message processing can be paused by the following reasons:</span></span>  
  
-   <span data-ttu-id="da9a6-107">Režim ConcurrencyMode je jednoduchá nebo vícenásobné a služba zpracovává další zprávu.</span><span class="sxs-lookup"><span data-stu-id="da9a6-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
-   <span data-ttu-id="da9a6-108">Transakce je povolená a služba zpracovává jinou transakcí.</span><span class="sxs-lookup"><span data-stu-id="da9a6-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
-   <span data-ttu-id="da9a6-109">Kontext synchronizace není aktuální.</span><span class="sxs-lookup"><span data-stu-id="da9a6-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da9a6-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="da9a6-110">See Also</span></span>  
 [<span data-ttu-id="da9a6-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="da9a6-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="da9a6-112">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="da9a6-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="da9a6-113">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="da9a6-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
