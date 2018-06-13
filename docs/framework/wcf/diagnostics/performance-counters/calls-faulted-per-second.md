---
title: Počet volání s chybou za sekundu
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: af84a379a36324131861aaa7e8577b5a44273917
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471338"
---
# <a name="calls-faulted-per-second"></a><span data-ttu-id="eccf4-102">Počet volání s chybou za sekundu</span><span class="sxs-lookup"><span data-stu-id="eccf4-102">Calls Faulted Per Second</span></span>
<span data-ttu-id="eccf4-103">Název čítače: Počet volání s chybou za sekundu</span><span class="sxs-lookup"><span data-stu-id="eccf4-103">Counter Name: Calls Faulted Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="eccf4-104">Popis</span><span class="sxs-lookup"><span data-stu-id="eccf4-104">Description</span></span>  
 <span data-ttu-id="eccf4-105">Počet volání, která vrátila chyby s touto operací za sekundu.</span><span class="sxs-lookup"><span data-stu-id="eccf4-105">Number of calls that returned faults to this operation in a second.</span></span>  
  
 <span data-ttu-id="eccf4-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="eccf4-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="eccf4-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="eccf4-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="eccf4-108">V aplikacích Windows Communication Foundation (WCF) metody služeb komunikaci pomocí protokolu SOAP zprávy selhání informace o chybě zpracování.</span><span class="sxs-lookup"><span data-stu-id="eccf4-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="eccf4-109">Chyb SOAP jsou typy zpráv, které jsou součástí metadat pro operace služby a proto vytvoření kontraktu selhání, který můžou klienti používat, aby jejich spuštění více robustní nebo interaktivní.</span><span class="sxs-lookup"><span data-stu-id="eccf4-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="eccf4-110">Vzhledem k tomu, že chyb SOAP jsou vyjádřeny klientům ve formátu XML, jsou vysoce umožňuje vzájemnou spolupráci.</span><span class="sxs-lookup"><span data-stu-id="eccf4-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eccf4-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="eccf4-111">See Also</span></span>  
 [<span data-ttu-id="eccf4-112">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="eccf4-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
