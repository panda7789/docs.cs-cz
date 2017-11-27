---
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b497231326c640b93b96500df39732104e0f0c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="cf73e-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="cf73e-102">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>
<span data-ttu-id="cf73e-103">Služba Protokol WS-AT přijala zprávu připravit nebo odpovědět z nestálého účastníka.</span><span class="sxs-lookup"><span data-stu-id="cf73e-103">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="cf73e-104">Chyba byla vrácena účastníka s deklaruje, že výstup transakce je nejistá.</span><span class="sxs-lookup"><span data-stu-id="cf73e-104">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cf73e-105">Popis</span><span class="sxs-lookup"><span data-stu-id="cf73e-105">Description</span></span>  
 <span data-ttu-id="cf73e-106">Sledovat, když místní správce transakcí přijme zprávu o připravit nebo odpovědět z Volatile zařazení, který již má zapomenete.</span><span class="sxs-lookup"><span data-stu-id="cf73e-106">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="cf73e-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="cf73e-107">Troubleshooting</span></span>  
 <span data-ttu-id="cf73e-108">Zkoumání příčin opožděné zprávy přicházející z Volatile účastník.</span><span class="sxs-lookup"><span data-stu-id="cf73e-108">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf73e-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf73e-109">See Also</span></span>  
 [<span data-ttu-id="cf73e-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="cf73e-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="cf73e-111">Řešení potíží s vaší aplikace pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="cf73e-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="cf73e-112">Správa a Diagnostika</span><span class="sxs-lookup"><span data-stu-id="cf73e-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
