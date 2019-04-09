---
title: Implementace kontraktů služeb
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: 766e0c4d30a4fa0eed9ce154ca932f5371a43211
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196317"
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="f972f-102">Implementace kontraktů služeb</span><span class="sxs-lookup"><span data-stu-id="f972f-102">Implementing Service Contracts</span></span>
<span data-ttu-id="f972f-103">Služba je třída, která zpřístupňuje funkce, které jsou k dispozici pro klienty na jeden nebo více koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="f972f-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="f972f-104">Pokud chcete vytvořit službu, zápis třídu, která implementuje kontraktu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f972f-104">To create a service, write a class that implements a Windows Communication Foundation (WCF) contract.</span></span> <span data-ttu-id="f972f-105">Provedete to jedním ze dvou způsobů.</span><span class="sxs-lookup"><span data-stu-id="f972f-105">You can do this in one of two ways.</span></span> <span data-ttu-id="f972f-106">Můžete definovat kontrakt samostatně jako rozhraní a pak vytvořit třídu, která implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f972f-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="f972f-107">Alternativně můžete vytvořit třídu a kontrakt přímo tak, že <xref:System.ServiceModel.ServiceContractAttribute> atributu na vlastní třídy a <xref:System.ServiceModel.OperationContractAttribute> atributů pro metody, které jsou k dispozici pro klienty službu.</span><span class="sxs-lookup"><span data-stu-id="f972f-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="f972f-108">Vytvoření třídy služby</span><span class="sxs-lookup"><span data-stu-id="f972f-108">Creating a service class</span></span>  
 <span data-ttu-id="f972f-109">Následuje příklad služby, který implementuje `IMath` kontrakt, který byl definován samostatně.</span><span class="sxs-lookup"><span data-stu-id="f972f-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]   
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="f972f-110">Služby, případně můžete zveřejnění kontraktu přímo.</span><span class="sxs-lookup"><span data-stu-id="f972f-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="f972f-111">Následující je příkladem služby třídu, která definuje a implementuje `MathService` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f972f-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="f972f-112">Všimněte si, že předchozí služby vystavují různé kontrakty, protože se liší názvy kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f972f-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="f972f-113">V prvním případě je zveřejněné kontraktu s názvem "`IMath`"zatímco ve druhém případě je s názvem kontraktu"`MathService`".</span><span class="sxs-lookup"><span data-stu-id="f972f-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="f972f-114">Pár věcí můžete nastavit na služby a operace implementace úrovně, jako je například souběžnosti a vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="f972f-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> <span data-ttu-id="f972f-115">Další informace najdete v tématu [návrh a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="f972f-115">For more information, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="f972f-116">Po implementaci kontraktu služby, je potřeba vytvořit jeden nebo víc koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="f972f-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> <span data-ttu-id="f972f-117">Další informace najdete v tématu [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f972f-117">For more information, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="f972f-118">Další informace o tom, jak spustit službu, naleznete v tématu [hostování služeb](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="f972f-118">For more information about how to run a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f972f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f972f-119">See also</span></span>

- [<span data-ttu-id="f972f-120">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="f972f-120">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)
- [<span data-ttu-id="f972f-121">Postupy: Vytvoření služby s třídou kontraktu</span><span class="sxs-lookup"><span data-stu-id="f972f-121">How to: Create a Service with a Contract Class</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [<span data-ttu-id="f972f-122">Postupy: Vytvoření služby pomocí rozhraní kontraktu</span><span class="sxs-lookup"><span data-stu-id="f972f-122">How to: Create a Service with a Contract Interface</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [<span data-ttu-id="f972f-123">Určování chování služby za běhu</span><span class="sxs-lookup"><span data-stu-id="f972f-123">Specifying Service Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
