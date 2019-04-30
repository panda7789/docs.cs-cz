---
title: 'Koncový bod: Počet volání s chybou za sekundu'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: f425d95868a9ba5bc3c2f2291db2bc414b1918e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797303"
---
# <a name="endpoint-calls-faulted-per-second"></a><span data-ttu-id="e0acd-102">Koncový bod: Počet volání s chybou za sekundu</span><span class="sxs-lookup"><span data-stu-id="e0acd-102">Endpoint: Calls Faulted Per Second</span></span>
<span data-ttu-id="e0acd-103">Název čítače: Počet volání s chybou za sekundu.</span><span class="sxs-lookup"><span data-stu-id="e0acd-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e0acd-104">Popis</span><span class="sxs-lookup"><span data-stu-id="e0acd-104">Description</span></span>  
 <span data-ttu-id="e0acd-105">Počet volání, které se mají vrátit chyby k tomuto koncovému bodu za sekundu.</span><span class="sxs-lookup"><span data-stu-id="e0acd-105">Number of calls that have returned faults to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="e0acd-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="e0acd-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e0acd-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="e0acd-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="e0acd-108">V aplikacích Windows Communication Foundation (WCF) komunikují metod služby informace o chybě zpracování pomocí chybové zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e0acd-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="e0acd-109">Typy zpráv, které jsou zahrnuty v metadatech pro operaci služby a proto vytvořit selhání kontrakt, který můžou klienti použít k jejich spuštění zkontrolujte robustní nebo interaktivní jsou chyby SOAP.</span><span class="sxs-lookup"><span data-stu-id="e0acd-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="e0acd-110">Protože chyb SOAP jsou vyjádřeny klientům v podobě XML, jsou vysoce interoperabilní.</span><span class="sxs-lookup"><span data-stu-id="e0acd-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0acd-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0acd-111">See also</span></span>

- [<span data-ttu-id="e0acd-112">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="e0acd-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
