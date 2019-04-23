---
title: Služby požadavku a odpovědi
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 1ff11b1cae4ec8f6fe886a55cb0add27831048d0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177811"
---
# <a name="request-reply-services"></a><span data-ttu-id="50b62-102">Služby požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="50b62-102">Request-Reply Services</span></span>
<span data-ttu-id="50b62-103">Služby požadavku a odpovědi jsou výchozí typ operace kontraktu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="50b62-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="50b62-104">Klienti volání operací služby a čekat na odpověď ze služby.</span><span class="sxs-lookup"><span data-stu-id="50b62-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="50b62-105">Můžete provádět volání operace služby buď synchronně, kde blokuje, dokud klient obdrží odpověď ze služby nebo časy volání, nebo asynchronně, pokračuje v práci tam, kde klient provede volání operace služby a přijímá odpověď od služby v jiném vlákně.</span><span class="sxs-lookup"><span data-stu-id="50b62-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="50b62-106">Vytvoření kontraktu požadavku a odpovědi služby, definujte servisní smlouvě a použít <xref:System.ServiceModel.OperationContractAttribute> třídy pro každou operaci, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="50b62-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="50b62-107">Není nutné nastavit <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost `false` vzhledem k tomu, že toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="50b62-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50b62-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50b62-108">See also</span></span>

- [<span data-ttu-id="50b62-109">Jednosměrné služby</span><span class="sxs-lookup"><span data-stu-id="50b62-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [<span data-ttu-id="50b62-110">Duplexní služby</span><span class="sxs-lookup"><span data-stu-id="50b62-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
