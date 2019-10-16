---
title: 'Služba: Počet volání s chybou'
ms.date: 03/30/2017
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
ms.openlocfilehash: d02139bcd6540fb973e0f1040c8877c04addc2f4
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321432"
---
# <a name="service-calls-faulted"></a><span data-ttu-id="29ef5-102">Služba: Počet volání s chybou</span><span class="sxs-lookup"><span data-stu-id="29ef5-102">Service: Calls Faulted</span></span>
<span data-ttu-id="29ef5-103">Název čítače: počet volání s chybou.</span><span class="sxs-lookup"><span data-stu-id="29ef5-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="29ef5-104">Popis</span><span class="sxs-lookup"><span data-stu-id="29ef5-104">Description</span></span>  
 <span data-ttu-id="29ef5-105">Počet volání této služby, které vrátily chyby.</span><span class="sxs-lookup"><span data-stu-id="29ef5-105">Number of calls to this service that have returned faults.</span></span> <span data-ttu-id="29ef5-106">V aplikacích Windows Communication Foundation (WCF) metody služeb sdělují informace o chybě zpracování pomocí zpráv o chybách protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="29ef5-106">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="29ef5-107">Chyby protokolu SOAP jsou typy zpráv, které jsou zahrnuty v metadatech pro operaci služby. proto je možné vytvořit kontrakt selhání, který mohou klienti použít, aby jejich spuštění bylo robustnější nebo interaktivní.</span><span class="sxs-lookup"><span data-stu-id="29ef5-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="29ef5-108">Vzhledem k tomu, že chyby protokolu SOAP jsou vyjádřeny klientům ve formátu XML, jsou vysoce interoperabilní.</span><span class="sxs-lookup"><span data-stu-id="29ef5-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ef5-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29ef5-109">See also</span></span>

- [<span data-ttu-id="29ef5-110">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="29ef5-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
