---
title: "Služby požadavku a odpovědi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a38a90d4e9ec249f91e8bfda88c646c006890d8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="request-reply-services"></a><span data-ttu-id="1074a-102">Služby požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="1074a-102">Request-Reply Services</span></span>
<span data-ttu-id="1074a-103">Služby požadavku a odpovědi jsou výchozí typ operace kontrakt [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1074a-103">Request-reply services are the default type of operation contract in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="1074a-104">Klienti volat operace služby a čekat na odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="1074a-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="1074a-105">Můžete provádět volání operace služby buď synchronně, kde klient blokuje až ji přijme odpověď ze služby nebo časy volání nebo asynchronně, pokračuje v práci tam, kde klient podá volání operace služby a přijímá odpověď ze služby na jiné vlákno.</span><span class="sxs-lookup"><span data-stu-id="1074a-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="1074a-106">K vytvoření kontraktu služby požadavku a odpovědi, zadejte své smlouvy a použít <xref:System.ServiceModel.OperationContractAttribute> třídy na každou operaci, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="1074a-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="1074a-107">Není nutné nastavit <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost `false` vzhledem k tomu, že toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="1074a-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1074a-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="1074a-108">See Also</span></span>  
 [<span data-ttu-id="1074a-109">Jednosměrné služby</span><span class="sxs-lookup"><span data-stu-id="1074a-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)  
 [<span data-ttu-id="1074a-110">Duplexní služby</span><span class="sxs-lookup"><span data-stu-id="1074a-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
