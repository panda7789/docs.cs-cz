---
title: Implementace kontraktů služeb
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: aefe146a8941d98d7d9138e4ece83c330c967034
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184006"
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="db099-102">Implementace kontraktů služeb</span><span class="sxs-lookup"><span data-stu-id="db099-102">Implementing Service Contracts</span></span>
<span data-ttu-id="db099-103">Služba je třída, která zveřejňuje funkce, které jsou k dispozici klientům v jednom nebo více koncových bodech.</span><span class="sxs-lookup"><span data-stu-id="db099-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="db099-104">Chcete-li vytvořit službu, napište třídu, která implementuje smlouvu WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="db099-104">To create a service, write a class that implements a Windows Communication Foundation (WCF) contract.</span></span> <span data-ttu-id="db099-105">Můžete to provést dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="db099-105">You can do this in one of two ways.</span></span> <span data-ttu-id="db099-106">Můžete definovat smlouvu samostatně jako rozhraní a potom vytvořit třídu, která implementuje toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="db099-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="db099-107">Případně můžete vytvořit třídu a smlouvu <xref:System.ServiceModel.ServiceContractAttribute> přímo umístěním atributu <xref:System.ServiceModel.OperationContractAttribute> na samotnou třídu a atribut na metody, které jsou k dispozici klientům služby.</span><span class="sxs-lookup"><span data-stu-id="db099-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="db099-108">Vytvoření třídy služeb</span><span class="sxs-lookup"><span data-stu-id="db099-108">Creating a service class</span></span>  
 <span data-ttu-id="db099-109">Následuje příklad služby, která implementuje smlouvu, `IMath` která byla definována samostatně.</span><span class="sxs-lookup"><span data-stu-id="db099-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
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
  
 <span data-ttu-id="db099-110">Alternativně služba může vystavit smlouvy přímo.</span><span class="sxs-lookup"><span data-stu-id="db099-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="db099-111">Následuje příklad třídy služeb, která definuje a `MathService` implementuje smlouvu.</span><span class="sxs-lookup"><span data-stu-id="db099-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
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
  
 <span data-ttu-id="db099-112">Všimněte si, že předchozí služby vystavit různé smlouvy, protože názvy smluv se liší.</span><span class="sxs-lookup"><span data-stu-id="db099-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="db099-113">V prvním případě je exponovaná`IMath`smlouva pojmenována " ",`MathService`zatímco v druhém případě je smlouva pojmenována " ".</span><span class="sxs-lookup"><span data-stu-id="db099-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="db099-114">Můžete nastavit několik věcí na úrovni implementace služby a operace, jako je například souběžnost a instance.</span><span class="sxs-lookup"><span data-stu-id="db099-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> <span data-ttu-id="db099-115">Další informace naleznete v [tématu Návrh a implementace služeb](designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="db099-115">For more information, see [Designing and Implementing Services](designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="db099-116">Po implementaci smlouvy o poskytování služeb je nutné vytvořit jeden nebo více koncových bodů pro službu.</span><span class="sxs-lookup"><span data-stu-id="db099-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> <span data-ttu-id="db099-117">Další informace naleznete v [tématu Přehled vytváření koncových bodů](endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="db099-117">For more information, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="db099-118">Další informace o spuštění služby naleznete v [tématu Hosting Services](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="db099-118">For more information about how to run a service, see [Hosting Services](hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db099-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="db099-119">See also</span></span>

- [<span data-ttu-id="db099-120">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="db099-120">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)
- [<span data-ttu-id="db099-121">Postupy: Vytvoření služby s třídou kontraktu</span><span class="sxs-lookup"><span data-stu-id="db099-121">How to: Create a Service with a Contract Class</span></span>](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [<span data-ttu-id="db099-122">Postupy: Vytvoření služby pomocí rozhraní kontraktu</span><span class="sxs-lookup"><span data-stu-id="db099-122">How to: Create a Service with a Contract Interface</span></span>](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [<span data-ttu-id="db099-123">Určování chování služby za běhu</span><span class="sxs-lookup"><span data-stu-id="db099-123">Specifying Service Run-Time Behavior</span></span>](specifying-service-run-time-behavior.md)
