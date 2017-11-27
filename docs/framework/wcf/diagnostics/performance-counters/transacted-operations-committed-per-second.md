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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0408bbc4bbe6e49bcd830a1de8563c02002f1b7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="0f075-102">Počet potvrzených zpracovaných operací za sekundu</span><span class="sxs-lookup"><span data-stu-id="0f075-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="0f075-103">Název čítače: Potvrzených zpracovaných operací za sekundu.</span><span class="sxs-lookup"><span data-stu-id="0f075-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0f075-104">Popis</span><span class="sxs-lookup"><span data-stu-id="0f075-104">Description</span></span>  
 <span data-ttu-id="0f075-105">Počet transakcí operací, které byl potvrzen v rámci této služby za sekundu.</span><span class="sxs-lookup"><span data-stu-id="0f075-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="0f075-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="0f075-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="0f075-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="0f075-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
