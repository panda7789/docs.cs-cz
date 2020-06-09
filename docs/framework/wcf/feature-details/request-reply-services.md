---
title: Služby požadavku a odpovědi
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: df42f3fa8f5a15572987b0d4859856c7f838e632
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586231"
---
# <a name="request-reply-services"></a><span data-ttu-id="1c626-102">Služby požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="1c626-102">Request-Reply Services</span></span>
<span data-ttu-id="1c626-103">Služby požadavku a odpovědi jsou výchozím typem kontraktu operace v Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1c626-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="1c626-104">Klienti volají operace se službami a čekají na odpověď od služby.</span><span class="sxs-lookup"><span data-stu-id="1c626-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="1c626-105">Můžete provést volání do operace služby buď synchronně, kde klient blokuje odpověď, dokud neobdrží odpověď ze služby nebo času volání, nebo asynchronně, kde klient provede volání operace služby, pokračuje v práci a přijme odpověď ze služby v jiném vlákně.</span><span class="sxs-lookup"><span data-stu-id="1c626-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="1c626-106">Chcete-li vytvořit kontrakt služby požadavek-odpověď, definujte kontrakt služby a použijte <xref:System.ServiceModel.OperationContractAttribute> pro každou operaci třídu, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="1c626-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="1c626-107">Vlastnost není nutné nastavovat <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> , `false` protože se jedná o výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="1c626-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c626-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c626-108">See also</span></span>

- [<span data-ttu-id="1c626-109">Jednosměrné služby</span><span class="sxs-lookup"><span data-stu-id="1c626-109">One-Way Services</span></span>](one-way-services.md)
- [<span data-ttu-id="1c626-110">Duplexní služby</span><span class="sxs-lookup"><span data-stu-id="1c626-110">Duplex Services</span></span>](duplex-services.md)
