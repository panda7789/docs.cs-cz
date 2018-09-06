---
title: 'Služba: Počet volání s chybou za sekundu'
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: b4a8a1eeec13195e4f8fe088da14dff7c06ecdb3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785112"
---
# <a name="service-calls-faulted-per-second"></a><span data-ttu-id="9b200-102">Služba: Počet volání s chybou za sekundu</span><span class="sxs-lookup"><span data-stu-id="9b200-102">Service: Calls Faulted Per Second</span></span>
<span data-ttu-id="9b200-103">Název čítače: Počet volání s chybou za sekundu.</span><span class="sxs-lookup"><span data-stu-id="9b200-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9b200-104">Popis</span><span class="sxs-lookup"><span data-stu-id="9b200-104">Description</span></span>  
 <span data-ttu-id="9b200-105">Počet volání, které se mají vrátit chyby k této službě za sekundu.</span><span class="sxs-lookup"><span data-stu-id="9b200-105">Number of calls that have returned faults to this service in a second.</span></span>  
  
 <span data-ttu-id="9b200-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="9b200-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9b200-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="9b200-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="9b200-108">V aplikacích Windows Communication Foundation (WCF) komunikují metod služby informace o chybě zpracování pomocí chybové zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="9b200-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="9b200-109">Typy zpráv, které jsou zahrnuty v metadatech pro operaci služby a proto vytvořit selhání kontrakt, který můžou klienti použít k jejich spuštění zkontrolujte robustní nebo interaktivní jsou chyby SOAP.</span><span class="sxs-lookup"><span data-stu-id="9b200-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="9b200-110">Protože chyb SOAP jsou vyjádřeny klientům v podobě XML, jsou vysoce interoperabilní.</span><span class="sxs-lookup"><span data-stu-id="9b200-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b200-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b200-111">See Also</span></span>  
 [<span data-ttu-id="9b200-112">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="9b200-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
