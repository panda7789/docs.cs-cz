---
title: 'Postupy: Vytvoření kontraktu požadavku a odpovědi'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: f5af7f3a0954e9becf1b9098f372878b537fec9c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645813"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="e0e9d-102">Postupy: Vytvoření kontraktu požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="e0e9d-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="e0e9d-103">Určuje kontraktů požadavek odpověď, která vrací odpověď.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="e0e9d-104">Odpovědi musí být odeslána a korelována žádost podle podmínek této smlouvy.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="e0e9d-105">I v případě, že metoda vrátí odpověď (`void` v jazyce C#, nebo `Sub` v jazyce Visual Basic), infrastruktura vytvoří a odešle zprávu o prázdný volajícímu.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="e0e9d-106">Pokud chcete zabránit odeslání odpovědi prázdný, použijte jednosměrného kontraktu pro operaci.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="e0e9d-107">Vytvoření kontraktu požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="e0e9d-107">To create a request-reply contract</span></span>  
  
1. <span data-ttu-id="e0e9d-108">Vytvoření rozhraní v programovacím jazyce podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-108">Create an interface in the programming language of your choice.</span></span>  
  
2. <span data-ttu-id="e0e9d-109">Použít <xref:System.ServiceModel.ServiceContractAttribute> atribut rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3. <span data-ttu-id="e0e9d-110">Použít <xref:System.ServiceModel.OperationContractAttribute> atribut pro jednotlivé metody, který může vyvolat klientů.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4. <span data-ttu-id="e0e9d-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-111">Optional.</span></span> <span data-ttu-id="e0e9d-112">Nastavte hodnotu <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost `true` zabránit odeslání zprávy prázdnou odpověď.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="e0e9d-113">Ve výchozím nastavení jsou všechny operace kontraktů požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0e9d-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0e9d-114">Example</span></span>  
 <span data-ttu-id="e0e9d-115">Následující příklad definuje kontrakt pro službu kalkulačky, která poskytuje `Add` a `Subtract` metody.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="e0e9d-116">`Multiply` Metoda není součástí kontraktu proto není označeno atributem <xref:System.ServiceModel.OperationContractAttribute> třídy a proto není přístupný pro klienty.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
```csharp
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);
    
    [OperationContract]
    int Subtract(int a, int b);
    
    int Multiply(int a, int b)
}
```
  
- <span data-ttu-id="e0e9d-117">Další informace o tom, jak určit operace kontrakty, najdete v článku <xref:System.ServiceModel.OperationContractAttribute> třídy a <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
- <span data-ttu-id="e0e9d-118">Použití <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> atributy způsobí, že se automatické generování definice kontraktu služby ve webové služby WSDL (Description Language) dokumentu po nasazení služby.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="e0e9d-119">Dokument se stáhne přidáním `?wsdl` na HTTP základní adresa pro službu.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="e0e9d-120">Třeba `http://microsoft/CalculatorService?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="e0e9d-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0e9d-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0e9d-121">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="e0e9d-122">Navrhování kontraktů služby</span><span class="sxs-lookup"><span data-stu-id="e0e9d-122">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
- [<span data-ttu-id="e0e9d-123">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="e0e9d-123">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
