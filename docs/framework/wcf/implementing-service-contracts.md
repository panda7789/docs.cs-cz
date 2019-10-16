---
title: Implementace kontraktů služeb
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: ac27329278edc2b9ca693aa15bcc5bb58edffe05
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320164"
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="52531-102">Implementace kontraktů služeb</span><span class="sxs-lookup"><span data-stu-id="52531-102">Implementing Service Contracts</span></span>
<span data-ttu-id="52531-103">Služba je třída, která zpřístupňuje funkce dostupné klientům v jednom nebo více koncových bodech.</span><span class="sxs-lookup"><span data-stu-id="52531-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="52531-104">Chcete-li vytvořit službu, napište třídu, která implementuje kontrakt Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="52531-104">To create a service, write a class that implements a Windows Communication Foundation (WCF) contract.</span></span> <span data-ttu-id="52531-105">To můžete provést jedním ze dvou způsobů.</span><span class="sxs-lookup"><span data-stu-id="52531-105">You can do this in one of two ways.</span></span> <span data-ttu-id="52531-106">Kontrakt můžete definovat samostatně jako rozhraní a pak vytvořit třídu, která implementuje toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="52531-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="52531-107">Alternativně můžete vytvořit třídu a kontrakt přímo tak, že umístíte atribut <xref:System.ServiceModel.ServiceContractAttribute> do samotné třídy a atribut <xref:System.ServiceModel.OperationContractAttribute> pro metody, které jsou k dispozici pro klienty služby.</span><span class="sxs-lookup"><span data-stu-id="52531-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="52531-108">Vytvoření třídy služby</span><span class="sxs-lookup"><span data-stu-id="52531-108">Creating a service class</span></span>  
 <span data-ttu-id="52531-109">Následuje příklad služby, která implementuje kontrakt `IMath`, který byl definován samostatně.</span><span class="sxs-lookup"><span data-stu-id="52531-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
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
  
 <span data-ttu-id="52531-110">Případně může služba vystavit kontrakt přímo.</span><span class="sxs-lookup"><span data-stu-id="52531-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="52531-111">Následuje příklad třídy služby, která definuje a implementuje kontrakt `MathService`.</span><span class="sxs-lookup"><span data-stu-id="52531-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
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
  
 <span data-ttu-id="52531-112">Všimněte si, že předchozí služby zveřejňují různé kontrakty, protože názvy kontraktů se liší.</span><span class="sxs-lookup"><span data-stu-id="52531-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="52531-113">V prvním případě se kontrakt s názvem "`IMath`" v druhém případě nazývá kontrakt "`MathService`".</span><span class="sxs-lookup"><span data-stu-id="52531-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="52531-114">Na úrovních implementace služby a operace můžete nastavit pár věcí, jako je například souběžnost a vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="52531-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> <span data-ttu-id="52531-115">Další informace najdete v tématu [navrhování a implementace služeb](designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="52531-115">For more information, see [Designing and Implementing Services](designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="52531-116">Po implementaci kontraktu služby musíte pro službu vytvořit jeden nebo více koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="52531-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> <span data-ttu-id="52531-117">Další informace najdete v tématu [Přehled vytváření koncových bodů](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="52531-117">For more information, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="52531-118">Další informace o tom, jak spustit službu, najdete v tématu [hostingové služby](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="52531-118">For more information about how to run a service, see [Hosting Services](hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52531-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52531-119">See also</span></span>

- [<span data-ttu-id="52531-120">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="52531-120">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)
- [<span data-ttu-id="52531-121">Postupy: Vytvoření služby s třídou kontraktu</span><span class="sxs-lookup"><span data-stu-id="52531-121">How to: Create a Service with a Contract Class</span></span>](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [<span data-ttu-id="52531-122">Postupy: Vytvoření služby pomocí rozhraní kontraktu</span><span class="sxs-lookup"><span data-stu-id="52531-122">How to: Create a Service with a Contract Interface</span></span>](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [<span data-ttu-id="52531-123">Určování chování služby za běhu</span><span class="sxs-lookup"><span data-stu-id="52531-123">Specifying Service Run-Time Behavior</span></span>](specifying-service-run-time-behavior.md)
