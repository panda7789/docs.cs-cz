---
title: 'Koncový bod: Počet volání s chybou za sekundu'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: 84dabf1215a02133874f3a0a55578c684a3308d9
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319981"
---
# <a name="endpoint-calls-faulted-per-second"></a><span data-ttu-id="47906-102">Koncový bod: Počet volání s chybou za sekundu</span><span class="sxs-lookup"><span data-stu-id="47906-102">Endpoint: Calls Faulted Per Second</span></span>
<span data-ttu-id="47906-103">Název čítače: počet volání s chybou za sekundu.</span><span class="sxs-lookup"><span data-stu-id="47906-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="47906-104">Popis</span><span class="sxs-lookup"><span data-stu-id="47906-104">Description</span></span>  
 <span data-ttu-id="47906-105">Počet volání, která vrátily chyby do tohoto koncového bodu za sekundu.</span><span class="sxs-lookup"><span data-stu-id="47906-105">Number of calls that have returned faults to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="47906-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="47906-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="47906-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="47906-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="47906-108">V aplikacích Windows Communication Foundation (WCF) metody služeb sdělují informace o chybě zpracování pomocí zpráv o chybách protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="47906-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="47906-109">Chyby protokolu SOAP jsou typy zpráv, které jsou zahrnuty v metadatech pro operaci služby. proto je možné vytvořit kontrakt selhání, který mohou klienti použít, aby jejich spuštění bylo robustnější nebo interaktivní.</span><span class="sxs-lookup"><span data-stu-id="47906-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="47906-110">Vzhledem k tomu, že chyby protokolu SOAP jsou vyjádřeny klientům ve formátu XML, jsou vysoce interoperabilní.</span><span class="sxs-lookup"><span data-stu-id="47906-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47906-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47906-111">See also</span></span>

- [<span data-ttu-id="47906-112">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="47906-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
