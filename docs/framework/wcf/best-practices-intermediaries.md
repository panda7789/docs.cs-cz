---
title: "Doporučené postupy: Prostředníci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d41b337-8132-4ac2-bea2-6e9ae2f00f8d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7aecdcecedcee98828b398f9172985d2e09fb9be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-intermediaries"></a><span data-ttu-id="cf607-102">Doporučené postupy: Prostředníci</span><span class="sxs-lookup"><span data-stu-id="cf607-102">Best Practices: Intermediaries</span></span>
<span data-ttu-id="cf607-103">Musí dát pozor správně zpracování chyb při volání metody prostředníci a ujistěte se, že jsou služby straně kanály na zprostředkovatele uzavřít správně.</span><span class="sxs-lookup"><span data-stu-id="cf607-103">Care must be taken to handle faults correctly when calling intermediaries to make sure service side channels on the intermediary are closed properly.</span></span>  
  
 <span data-ttu-id="cf607-104">Vezměte v úvahu následující scénář.</span><span class="sxs-lookup"><span data-stu-id="cf607-104">Consider the following scenario.</span></span> <span data-ttu-id="cf607-105">Klient zavolá zprostředkovatele, který pak zavolá back endové službě.</span><span class="sxs-lookup"><span data-stu-id="cf607-105">A client makes a call to an intermediary which then calls a back-end service.</span></span>  <span data-ttu-id="cf607-106">Back endové službě definuje žádná chyba – kontrakt, takže jakékoli chyby vyvolaných z dané služby budou považovány za beztypové selhání.</span><span class="sxs-lookup"><span data-stu-id="cf607-106">The back-end service defines no fault contract, so any fault thrown from that service will be treated as an un-typed fault.</span></span>  <span data-ttu-id="cf607-107">Vrátí back endové služby <xref:System.ApplicationException> a WCF správně zruší kanál straně služby.</span><span class="sxs-lookup"><span data-stu-id="cf607-107">The back-end service throws an <xref:System.ApplicationException> and WCF correctly aborts the service-side channel.</span></span> <span data-ttu-id="cf607-108"><xref:System.ApplicationException> Potom zobrazí jako <xref:System.ServiceModel.FaultException> , je vyvolána zprostředkovatelem.</span><span class="sxs-lookup"><span data-stu-id="cf607-108">The <xref:System.ApplicationException> then surfaces as a <xref:System.ServiceModel.FaultException> that is thrown to the intermediary.</span></span> <span data-ttu-id="cf607-109">Zprostředkovatel znovu vyvolá <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="cf607-109">The intermediary re-throws the <xref:System.ApplicationException>.</span></span> <span data-ttu-id="cf607-110">WCF interpretuje jako beztypové chybu z zprostředkovatel a předává ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="cf607-110">WCF interprets this as an un-typed fault from the intermediary and forwards it on to the client.</span></span> <span data-ttu-id="cf607-111">Po přijetí chyby, zprostředkovatel i klienta poruch jejich kanály straně klienta.</span><span class="sxs-lookup"><span data-stu-id="cf607-111">Upon receiving the fault, both the intermediary and the client fault their client-side channels.</span></span> <span data-ttu-id="cf607-112">Zprostředkovatel na straně služby kanál ale zůstane otevřená, protože WCF neví, že je závažné chyby.</span><span class="sxs-lookup"><span data-stu-id="cf607-112">The intermediary’s service-side channel however remains open because WCF doesn’t know the fault is fatal.</span></span>  
  
 <span data-ttu-id="cf607-113">Osvědčeným postupem v tomto scénáři je zjistit, jestli je závažné selhání přicházející ze služby, a pokud zprostředkovatel tak by měl poruch jeho kanál straně služby, jak je znázorněno v následující fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="cf607-113">The best practice in this scenario is to detect if the fault coming from the service is fatal and if so the intermediary should fault its service-side channel as shown in the following code snippet.</span></span>  
  
```csharp  
catch (Exception e)  
{  
    bool faulted = service.State == CommunicationState.Faulted;  
    service.Abort();  
    if (faulted)  
    {  
        throw new ApplicationException(e.Message);  
    }  
    Else  
    {  
        throw;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf607-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf607-114">See Also</span></span>  
 [<span data-ttu-id="cf607-115">Zpracování chyb WCF</span><span class="sxs-lookup"><span data-stu-id="cf607-115">WCF Error Handling</span></span>](../../../docs/framework/wcf/wcf-error-handling.md)  
 [<span data-ttu-id="cf607-116">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="cf607-116">Specifying and Handling Faults in Contracts and Services</span></span>](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
