---
title: "Počet instancí za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74579397-1058-4278-80cf-2d00854a480f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 38aef88b343ff658702ae1a6e1d4afd0c7e4531a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="instances-per-second"></a><span data-ttu-id="cd257-102">Počet instancí za sekundu</span><span class="sxs-lookup"><span data-stu-id="cd257-102">Instances Per Second</span></span>
<span data-ttu-id="cd257-103">Název čítače: Instance vytvořené za sekundu.</span><span class="sxs-lookup"><span data-stu-id="cd257-103">Counter Name: Instances Created Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cd257-104">Popis</span><span class="sxs-lookup"><span data-stu-id="cd257-104">Description</span></span>  
 <span data-ttu-id="cd257-105">Celkový počet instancí služby vytvořené za sekundu.</span><span class="sxs-lookup"><span data-stu-id="cd257-105">Total number of service instances created in a second.</span></span>  
  
 <span data-ttu-id="cd257-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="cd257-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="cd257-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="cd257-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
