---
title: 'Postupy: Vytvoření kontraktu požadavku a odpovědi'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 793f7214f8319e87c3e344990577841fc029bc55
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185034"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="0e0f0-102">Postupy: Vytvoření kontraktu požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="0e0f0-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="0e0f0-103">Smlouva požadavek odpověď určuje metodu, která vrací odpověď.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="0e0f0-104">Odpověď musí být zaslána a korelována s žádostí podle podmínek této smlouvy.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="0e0f0-105">I v případě, že`void` metoda vrátí žádnou odpověď (v jazyce C#, nebo `Sub` v jazyce Visual Basic), infrastruktura vytvoří a odešle prázdnou zprávu volajícímu.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="0e0f0-106">Chcete-li zabránit odeslání prázdné zprávy s odpovědí, použijte pro operaci jednosměrnou smlouvu.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="0e0f0-107">Vytvoření smlouvy požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="0e0f0-107">To create a request-reply contract</span></span>  
  
1. <span data-ttu-id="0e0f0-108">Vytvořte rozhraní v programovacím jazyce dle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-108">Create an interface in the programming language of your choice.</span></span>  
  
2. <span data-ttu-id="0e0f0-109">Použijte <xref:System.ServiceModel.ServiceContractAttribute> atribut rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3. <span data-ttu-id="0e0f0-110">Použijte <xref:System.ServiceModel.OperationContractAttribute> atribut pro každou metodu, kterou mohou klienti vyvolat.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4. <span data-ttu-id="0e0f0-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-111">Optional.</span></span> <span data-ttu-id="0e0f0-112">Nastavte hodnotu <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnosti, chcete-li `true` zabránit odeslání prázdné zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="0e0f0-113">Ve výchozím nastavení jsou všechny operace smlouvy požadavku odpověď.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e0f0-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e0f0-114">Example</span></span>  
 <span data-ttu-id="0e0f0-115">Následující ukázka definuje smlouvu pro službu kalkulačky, která poskytuje `Add` a `Subtract` metody.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="0e0f0-116">Metoda `Multiply` není součástí smlouvy, protože není označena <xref:System.ServiceModel.OperationContractAttribute> třídou, a proto není přístupná klientům.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
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
  
- <span data-ttu-id="0e0f0-117">Další informace o tom, jak určit <xref:System.ServiceModel.OperationContractAttribute> smlouvy <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> operace, naleznete třídy a vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
- <span data-ttu-id="0e0f0-118">Použití <xref:System.ServiceModel.ServiceContractAttribute> atributů a <xref:System.ServiceModel.OperationContractAttribute> způsobí automatické generování definic servisnísmlouvy v dokumentu jazyka WSDL (Web Services Description Language) po nasazení služby.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="0e0f0-119">Dokument se stáhne připojením `?wsdl` k základní adrese HTTP pro službu.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="0e0f0-120">Například `http://microsoft/CalculatorService?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="0e0f0-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e0f0-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e0f0-121">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="0e0f0-122">Navrhování kontraktů služby</span><span class="sxs-lookup"><span data-stu-id="0e0f0-122">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)
- [<span data-ttu-id="0e0f0-123">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="0e0f0-123">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
