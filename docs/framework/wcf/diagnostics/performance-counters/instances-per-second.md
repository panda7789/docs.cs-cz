---
title: Počet instancí za sekundu
ms.date: 03/30/2017
ms.assetid: 74579397-1058-4278-80cf-2d00854a480f
ms.openlocfilehash: c955d2cd0d87c89f412892e7088285f2db27ff42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471865"
---
# <a name="instances-per-second"></a><span data-ttu-id="46d7c-102">Počet instancí za sekundu</span><span class="sxs-lookup"><span data-stu-id="46d7c-102">Instances Per Second</span></span>
<span data-ttu-id="46d7c-103">Název čítače: Instance vytvořené za sekundu.</span><span class="sxs-lookup"><span data-stu-id="46d7c-103">Counter Name: Instances Created Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="46d7c-104">Popis</span><span class="sxs-lookup"><span data-stu-id="46d7c-104">Description</span></span>  
 <span data-ttu-id="46d7c-105">Celkový počet instancí služby vytvořené za sekundu.</span><span class="sxs-lookup"><span data-stu-id="46d7c-105">Total number of service instances created in a second.</span></span>  
  
 <span data-ttu-id="46d7c-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="46d7c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="46d7c-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="46d7c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
