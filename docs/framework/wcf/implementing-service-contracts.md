---
title: "Implementace kontraktů služeb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b4085e23120ad654121f33111eda68276259096
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="4043e-102">Implementace kontraktů služeb</span><span class="sxs-lookup"><span data-stu-id="4043e-102">Implementing Service Contracts</span></span>
<span data-ttu-id="4043e-103">Služba je třída, která poskytuje funkce, které jsou k dispozici pro klienty na jeden nebo více koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="4043e-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="4043e-104">Pokud chcete vytvořit službu, zápis třídu, která implementuje [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] kontrakt.</span><span class="sxs-lookup"><span data-stu-id="4043e-104">To create a service, write a class that implements a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] contract.</span></span> <span data-ttu-id="4043e-105">Provedete to jedním ze dvou způsobů.</span><span class="sxs-lookup"><span data-stu-id="4043e-105">You can do this in one of two ways.</span></span> <span data-ttu-id="4043e-106">Můžete definovat kontrakt samostatně jako rozhraní a pak vytvořte třídu, která implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4043e-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="4043e-107">Alternativně můžete vytvořit třídu a kontrakt přímo tím, že <xref:System.ServiceModel.ServiceContractAttribute> atributu na vlastní třídy a <xref:System.ServiceModel.OperationContractAttribute> atribut pro metody, které jsou k dispozici pro klienty služby.</span><span class="sxs-lookup"><span data-stu-id="4043e-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="4043e-108">Vytvoření třídy služby</span><span class="sxs-lookup"><span data-stu-id="4043e-108">Creating a service class</span></span>  
 <span data-ttu-id="4043e-109">Následuje příklad služby, který implementuje `IMath` kontraktu, která byla definována samostatně.</span><span class="sxs-lookup"><span data-stu-id="4043e-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
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
  
 <span data-ttu-id="4043e-110">Službu můžete taky můžou zpřístupnit kontraktu přímo.</span><span class="sxs-lookup"><span data-stu-id="4043e-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="4043e-111">Následuje příklad třídy služby, která definuje a implementuje `MathService` kontrakt.</span><span class="sxs-lookup"><span data-stu-id="4043e-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
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
  
 <span data-ttu-id="4043e-112">Všimněte si, že předchozí služby vystavit různých kontrakty vzhledem k tomu, že názvy kontraktu se liší.</span><span class="sxs-lookup"><span data-stu-id="4043e-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="4043e-113">V prvním případě zveřejněné kontrakt název "`IMath`"při v druhém případě je název kontraktu"`MathService`".</span><span class="sxs-lookup"><span data-stu-id="4043e-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="4043e-114">Pár věcí můžete nastavit na služby a operace implementace úrovně, jako je například souběžnosti a vytváření instancí.</span><span class="sxs-lookup"><span data-stu-id="4043e-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="4043e-115">[Navrhování a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="4043e-115"> [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="4043e-116">Po implementaci kontraktu služby, je nutné vytvořit jeden nebo více koncových bodů pro službu.</span><span class="sxs-lookup"><span data-stu-id="4043e-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="4043e-117">[Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4043e-117"> [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="4043e-118">spuštění služby najdete v tématu [hostování služeb](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="4043e-118"> how to run a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4043e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="4043e-119">See Also</span></span>  
 [<span data-ttu-id="4043e-120">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="4043e-120">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="4043e-121">Postupy: Vytvoření služby s třídou kontraktu</span><span class="sxs-lookup"><span data-stu-id="4043e-121">How to: Create a Service with a Contract Class</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)  
 [<span data-ttu-id="4043e-122">Postupy: Vytvoření služby pomocí rozhraní kontraktu</span><span class="sxs-lookup"><span data-stu-id="4043e-122">How to: Create a Service with a Contract Interface</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)  
 [<span data-ttu-id="4043e-123">Určování chování služby za běhu</span><span class="sxs-lookup"><span data-stu-id="4043e-123">Specifying Service Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
