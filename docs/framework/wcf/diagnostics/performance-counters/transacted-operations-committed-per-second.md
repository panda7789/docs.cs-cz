---
title: "Počet potvrzených zpracovaných operací za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96a17d99329248dff4a29f3c68649c67622c45d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="edadf-102">Počet potvrzených zpracovaných operací za sekundu</span><span class="sxs-lookup"><span data-stu-id="edadf-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="edadf-103">Název čítače: Potvrzených zpracovaných operací za sekundu.</span><span class="sxs-lookup"><span data-stu-id="edadf-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="edadf-104">Popis</span><span class="sxs-lookup"><span data-stu-id="edadf-104">Description</span></span>  
 <span data-ttu-id="edadf-105">Počet transakcí operací, které byl potvrzen v rámci této služby za sekundu.</span><span class="sxs-lookup"><span data-stu-id="edadf-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="edadf-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="edadf-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="edadf-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="edadf-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
