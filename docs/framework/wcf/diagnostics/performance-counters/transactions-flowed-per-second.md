---
title: "Počet plynoucích transakcí za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 776b9e9f019aadb5fa96a6b6a7bb4a4a07eb16ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="bfafa-102">Počet plynoucích transakcí za sekundu</span><span class="sxs-lookup"><span data-stu-id="bfafa-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="bfafa-103">Název čítače: Počet plynoucích transakcí za sekundu</span><span class="sxs-lookup"><span data-stu-id="bfafa-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="bfafa-104">Popis</span><span class="sxs-lookup"><span data-stu-id="bfafa-104">Description</span></span>  
 <span data-ttu-id="bfafa-105">Počet transakcí plynoucích s touto operací za sekundu.</span><span class="sxs-lookup"><span data-stu-id="bfafa-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="bfafa-106">Tento čítač se zvýší, když je součástí zprávy, která je odeslána operaci ID transakce.</span><span class="sxs-lookup"><span data-stu-id="bfafa-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="bfafa-107">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="bfafa-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="bfafa-108">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="bfafa-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
