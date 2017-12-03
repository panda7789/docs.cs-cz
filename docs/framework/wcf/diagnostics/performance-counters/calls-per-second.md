---
title: "Počet volání za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0efb5a94-d83b-4793-b529-6fcbedb65c43
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: baef18df3e1dda8725859c9529ab61c0668c8ff3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="calls-per-second"></a><span data-ttu-id="6920b-102">Počet volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="6920b-102">Calls Per Second</span></span>
<span data-ttu-id="6920b-103">Název čítače: Počet volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="6920b-103">Counter Name: Calls Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="6920b-104">Popis</span><span class="sxs-lookup"><span data-stu-id="6920b-104">Description</span></span>  
 <span data-ttu-id="6920b-105">Počet volání s touto operací za sekundu.</span><span class="sxs-lookup"><span data-stu-id="6920b-105">Number of calls to this operation in a second.</span></span>  
  
 <span data-ttu-id="6920b-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="6920b-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="6920b-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="6920b-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
