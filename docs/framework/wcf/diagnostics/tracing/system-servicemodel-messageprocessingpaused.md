---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: 85bec8255e0d20d6e76ea354e5b8c42b83d7d8e6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598148"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="987a0-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="987a0-102">System.ServiceModel.MessageProcessingPaused</span></span>
<span data-ttu-id="987a0-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="987a0-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="987a0-104">Popis</span><span class="sxs-lookup"><span data-stu-id="987a0-104">Description</span></span>  
 <span data-ttu-id="987a0-105">Při zpracování zprávy došlo k přepnutí vláken.</span><span class="sxs-lookup"><span data-stu-id="987a0-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="987a0-106">Zpracování zpráv může být pozastaveno z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="987a0-106">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="987a0-107">Režim ConcurrencyMode je jeden nebo znovu vstupující a služba zpracovává jinou zprávu.</span><span class="sxs-lookup"><span data-stu-id="987a0-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="987a0-108">Transakce je povolena a služba zpracovává jinou transakci.</span><span class="sxs-lookup"><span data-stu-id="987a0-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="987a0-109">Kontext synchronizace není aktuální.</span><span class="sxs-lookup"><span data-stu-id="987a0-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="987a0-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="987a0-110">See also</span></span>

- [<span data-ttu-id="987a0-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="987a0-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="987a0-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="987a0-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="987a0-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="987a0-113">Administration and Diagnostics</span></span>](../index.md)
