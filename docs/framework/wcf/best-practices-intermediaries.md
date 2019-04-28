---
title: 'Doporučené postupy: Prostředníci'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: 0bd553486bfb89a0ec14c42a1bb7d2ed9c4c540d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608902"
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="d8715-102">Doporučené postupy: Prostředníci</span><span class="sxs-lookup"><span data-stu-id="d8715-102">Best Practices: Intermediaries</span></span>
<span data-ttu-id="d8715-103">Chcete-li správně zpracovávaly chyby při volání metody zprostředkovatele, abyste měli jistotu, že jsou správně uzavřeny kanály na straně služby na zprostředkovatele musí věnovat pozornost.</span><span class="sxs-lookup"><span data-stu-id="d8715-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="d8715-104">Vezměte v úvahu následující scénář.</span><span class="sxs-lookup"><span data-stu-id="d8715-104">Consider the following scenario.</span></span> <span data-ttu-id="d8715-105">Klient provede volání zprostředkovatele, který pak volá back-end služby.</span><span class="sxs-lookup"><span data-stu-id="d8715-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="d8715-106">Back-end služba definuje žádná chyba – kontrakt, tak jakékoli chyby vyvolané z dané služby, bude zacházeno jako netypové selhání.</span><span class="sxs-lookup"><span data-stu-id="d8715-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="d8715-107">Vyvolá back-end službu <xref:System.ApplicationException> a WCF správně zruší kanál straně služby.</span><span class="sxs-lookup"><span data-stu-id="d8715-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="d8715-108"><xref:System.ApplicationException> Potom zobrazí jako <xref:System.ServiceModel.FaultException> , která je vyvolána zprostředkovatelem.</span><span class="sxs-lookup"><span data-stu-id="d8715-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="d8715-109">Zprostředkovatel znovu vyvolá <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="d8715-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="d8715-110">WCF interpretuje jako netypové selhání od zprostředkovatele a předá jej ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="d8715-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="d8715-111">Při přijetí chyby zprostředkovatele a klient selhání jejich kanály na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="d8715-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="d8715-112">Zprostředkovatel na straně služby kanálu ale zůstane otevřený, protože WCF neví, že je závažné chyby.</span><span class="sxs-lookup"><span data-stu-id="d8715-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="d8715-113">Osvědčeným postupem v tomto scénáři je zjistit, jestli je závažné chyby pocházející ze služby, a pokud zprostředkovatel tak by měl selhání svůj kanál ze strany služby, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="d8715-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8715-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8715-114">See also</span></span>

- [<span data-ttu-id="d8715-115">Zpracování chyb WCF</span><span class="sxs-lookup"><span data-stu-id="d8715-115">WCF Error Handling</span></span>](../../../docs/framework/wcf/wcf-error-handling.md)
- [<span data-ttu-id="d8715-116">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="d8715-116">Specifying and Handling Faults in Contracts and Services</span></span>](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
