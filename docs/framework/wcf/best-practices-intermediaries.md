---
title: 'Doporučené postupy: Prostředníci'
ms.date: 03/30/2017
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
ms.openlocfilehash: a7c037b5942a404b1ff790638979a8e430394151
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320789"
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="f1dad-102">Doporučené postupy: Prostředníci</span><span class="sxs-lookup"><span data-stu-id="f1dad-102">Best Practices: Intermediaries</span></span>
<span data-ttu-id="f1dad-103">Při volání zprostředkovatelů, aby bylo zajištěno, že kanály na straně služby na straně zprostředkovatele jsou správně uzavřeny, je nutné vzít v potaz správné zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="f1dad-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="f1dad-104">Vezměte v úvahu následující scénář.</span><span class="sxs-lookup"><span data-stu-id="f1dad-104">Consider the following scenario.</span></span> <span data-ttu-id="f1dad-105">Klient provede volání do zprostředkovatele, který pak zavolá back-end službu.</span><span class="sxs-lookup"><span data-stu-id="f1dad-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="f1dad-106">Back-endové služba nedefinuje žádnou kontrakt selhání, takže jakákoli chyba vyvolaná z této služby bude považována za chybu bez typu.</span><span class="sxs-lookup"><span data-stu-id="f1dad-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="f1dad-107">Back-endové služba vyvolá <xref:System.ApplicationException> a WCF správně přerušuje kanál na straně služby.</span><span class="sxs-lookup"><span data-stu-id="f1dad-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="f1dad-108">@No__t-0 pak povrchy jako <xref:System.ServiceModel.FaultException>, které se vyvolaly zprostředkovateli.</span><span class="sxs-lookup"><span data-stu-id="f1dad-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="f1dad-109">Zprostředkovatel znovu vyvolá <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="f1dad-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="f1dad-110">Služba WCF interpretuje tuto chybu jako netypovou chybu ze zprostředkovatele a předá ji klientovi.</span><span class="sxs-lookup"><span data-stu-id="f1dad-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="f1dad-111">Po obdržení chyby je to jak zprostředkovatel, tak Chyba klienta na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="f1dad-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="f1dad-112">Kanál na straně služby zprostředkujícího poskytovatele zůstane otevřený, protože služba WCF neví, že chyba je závažná.</span><span class="sxs-lookup"><span data-stu-id="f1dad-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="f1dad-113">Osvědčeným postupem v tomto scénáři je zjistit, zda chyba přicházející ze služby je závažná, a pokud by zprostředkovatel neměl chybu kanálu na straně služby, jak je znázorněno v následujícím fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="f1dad-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f1dad-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1dad-114">See also</span></span>

- [<span data-ttu-id="f1dad-115">Zpracování chyb WCF</span><span class="sxs-lookup"><span data-stu-id="f1dad-115">WCF Error Handling</span></span>](wcf-error-handling.md)
- [<span data-ttu-id="f1dad-116">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="f1dad-116">Specifying and Handling Faults in Contracts and Services</span></span>](specifying-and-handling-faults-in-contracts-and-services.md)
