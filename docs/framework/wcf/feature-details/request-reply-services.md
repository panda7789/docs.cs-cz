---
title: Služby požadavku a odpovědi
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: f58da6f1cdaad1b976659ee2e9febe12cc07726f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991145"
---
# <a name="request-reply-services"></a><span data-ttu-id="dd572-102">Služby požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="dd572-102">Request-Reply Services</span></span>
<span data-ttu-id="dd572-103">Služby požadavku a odpovědi jsou výchozím typem kontraktu operace v Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="dd572-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="dd572-104">Klienti volají operace se službami a čekají na odpověď od služby.</span><span class="sxs-lookup"><span data-stu-id="dd572-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="dd572-105">Můžete provést volání do operace služby buď synchronně, kde klient blokuje odpověď, dokud neobdrží odpověď ze služby nebo času volání, nebo asynchronně, kde klient provádí volání operace služby, pokračuje v práci a přijímá odpověď ze služby v jiném vlákně.</span><span class="sxs-lookup"><span data-stu-id="dd572-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="dd572-106">Chcete-li vytvořit kontrakt služby požadavek-odpověď, definujte kontrakt služby a použijte <xref:System.ServiceModel.OperationContractAttribute> pro každou operaci třídu, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="dd572-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="dd572-107"><xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> Vlastnost není nutné nastavovat, `false` protože se jedná o výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="dd572-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd572-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd572-108">See also</span></span>

- [<span data-ttu-id="dd572-109">Jednosměrné služby</span><span class="sxs-lookup"><span data-stu-id="dd572-109">One-Way Services</span></span>](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [<span data-ttu-id="dd572-110">Duplexní služby</span><span class="sxs-lookup"><span data-stu-id="dd572-110">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
