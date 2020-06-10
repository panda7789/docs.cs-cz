---
title: 'Postupy: Vytvoření kontraktu požadavku a odpovědi'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 8a09c265c77edc584b591477e64314f1e76e332b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593435"
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="6273d-102">Postupy: Vytvoření kontraktu požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="6273d-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="6273d-103">Kontrakt požadavek-odpověď určuje metodu, která vrací odpověď.</span><span class="sxs-lookup"><span data-stu-id="6273d-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="6273d-104">Odpověď musí být zaslána a koreluje s požadavkem v rámci podmínek této smlouvy.</span><span class="sxs-lookup"><span data-stu-id="6273d-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="6273d-105">I v případě, že metoda nevrátí žádnou odpověď ( `void` v jazyce C# nebo `Sub` v Visual Basic), infrastruktura vytvoří a pošle prázdnou zprávu volajícímu.</span><span class="sxs-lookup"><span data-stu-id="6273d-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="6273d-106">Chcete-li zabránit odeslání prázdné zprávy s odpovědí, použijte pro tuto operaci jednosměrný kontrakt.</span><span class="sxs-lookup"><span data-stu-id="6273d-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="6273d-107">Vytvoření kontraktu požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="6273d-107">To create a request-reply contract</span></span>  
  
1. <span data-ttu-id="6273d-108">Vytvořte rozhraní v programovacím jazyce podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="6273d-108">Create an interface in the programming language of your choice.</span></span>  
  
2. <span data-ttu-id="6273d-109">Použijte <xref:System.ServiceModel.ServiceContractAttribute> atribut pro rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6273d-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3. <span data-ttu-id="6273d-110">Použijte <xref:System.ServiceModel.OperationContractAttribute> atribut na každou metodu, kterou mohou klienti vyvolat.</span><span class="sxs-lookup"><span data-stu-id="6273d-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4. <span data-ttu-id="6273d-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="6273d-111">Optional.</span></span> <span data-ttu-id="6273d-112">Nastavte hodnotu <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnosti na, chcete `true` -li zabránit odeslání prázdné zprávy s odpovědí.</span><span class="sxs-lookup"><span data-stu-id="6273d-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="6273d-113">Ve výchozím nastavení jsou všechny operace kontraktů požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="6273d-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6273d-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="6273d-114">Example</span></span>  
 <span data-ttu-id="6273d-115">Následující příklad definuje kontrakt pro službu kalkulačky, která poskytuje `Add` metody a `Subtract` .</span><span class="sxs-lookup"><span data-stu-id="6273d-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="6273d-116">`Multiply`Metoda není součástí kontraktu, protože není označena <xref:System.ServiceModel.OperationContractAttribute> třídou, takže není přístupná pro klienty.</span><span class="sxs-lookup"><span data-stu-id="6273d-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
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
  
- <span data-ttu-id="6273d-117">Další informace o tom, jak zadat kontrakty operací, naleznete v tématu <xref:System.ServiceModel.OperationContractAttribute> Třída a <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6273d-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
- <span data-ttu-id="6273d-118">Použití <xref:System.ServiceModel.ServiceContractAttribute> atributů a <xref:System.ServiceModel.OperationContractAttribute> způsobuje automatickou generaci definic kontraktů služby v dokumentu WSDL (Web Services Description Language) po nasazení služby.</span><span class="sxs-lookup"><span data-stu-id="6273d-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="6273d-119">Dokument se stáhne připojením `?wsdl` k základní adrese http služby.</span><span class="sxs-lookup"><span data-stu-id="6273d-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="6273d-120">Například `http://microsoft/CalculatorService?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="6273d-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6273d-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="6273d-121">See also</span></span>

- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="6273d-122">Navrhování kontraktů služby</span><span class="sxs-lookup"><span data-stu-id="6273d-122">Designing Service Contracts</span></span>](../designing-service-contracts.md)
- [<span data-ttu-id="6273d-123">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="6273d-123">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
