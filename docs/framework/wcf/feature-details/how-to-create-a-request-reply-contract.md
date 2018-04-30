---
title: 'Postupy: Vytvoření kontraktu požadavku a odpovědi'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2a272eaa88a53814daea9d515550a37f7991ecb8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-request-reply-contract"></a><span data-ttu-id="0c8b5-102">Postupy: Vytvoření kontraktu požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="0c8b5-102">How to: Create a Request-Reply Contract</span></span>
<span data-ttu-id="0c8b5-103">Kontraktu požadavku a odpovědi určuje metodu, která vrátí odpověď.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-103">A request-reply contract specifies a method that returns a reply.</span></span> <span data-ttu-id="0c8b5-104">Odpovědi musí být odeslána a korelována žádost v souladu s podmínkami této smlouvy.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-104">The reply must be sent and correlated to the request under the terms of this contract.</span></span> <span data-ttu-id="0c8b5-105">I v případě, že metoda vrátí odpověď (`void` v jazyce C# nebo `Sub` v jazyce Visual Basic), infrastruktura vytvoří a odešle zprávu o prázdný volajícímu.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-105">Even if the method returns no reply (`void` in C#, or a `Sub` in Visual Basic), the infrastructure creates and sends an empty message to the caller.</span></span> <span data-ttu-id="0c8b5-106">Aby odesílání zprávy odpovědi prázdná, použijte jednosměrného kontraktu pro operaci.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-106">To prevent the sending of an empty reply message, use a one-way contract for the operation.</span></span>  
  
### <a name="to-create-a-request-reply-contract"></a><span data-ttu-id="0c8b5-107">K vytvoření kontraktu požadavku a odpovědi</span><span class="sxs-lookup"><span data-stu-id="0c8b5-107">To create a request-reply contract</span></span>  
  
1.  <span data-ttu-id="0c8b5-108">Vytvořte rozhraní v programovací jazyk podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-108">Create an interface in the programming language of your choice.</span></span>  
  
2.  <span data-ttu-id="0c8b5-109">Použít <xref:System.ServiceModel.ServiceContractAttribute> atribut rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
3.  <span data-ttu-id="0c8b5-110">Použít <xref:System.ServiceModel.OperationContractAttribute> atribut každá metoda, který lze vyvolat klientů.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-110">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to each method that clients can invoke.</span></span>  
  
4.  <span data-ttu-id="0c8b5-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-111">Optional.</span></span> <span data-ttu-id="0c8b5-112">Nastavte hodnotu <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost `true` zabránit odesílání zprávy prázdnou odpověď.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-112">Set the value of the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` to prevent the sending of an empty reply message.</span></span> <span data-ttu-id="0c8b5-113">Ve výchozím nastavení jsou všechny operace kontraktů požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-113">By default, all operations are request-reply contracts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c8b5-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c8b5-114">Example</span></span>  
 <span data-ttu-id="0c8b5-115">Následující příklad definuje kontrakt služby kalkulačky, která poskytuje `Add` a `Subtract` metody.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-115">The following sample defines a contract for a calculator service that provides `Add` and `Subtract` methods.</span></span> <span data-ttu-id="0c8b5-116">`Multiply` Metoda není součástí kontraktu protože není označena pomocí <xref:System.ServiceModel.OperationContractAttribute> třídy a proto není přístupná pro klienty.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-116">The `Multiply` method is not part of the contract because it is not marked by the <xref:System.ServiceModel.OperationContractAttribute> class and so it is not accessible to clients.</span></span>  
  
```
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
  
-   <span data-ttu-id="0c8b5-117">Další informace o tom, jak určit kontrakty operaci najdete v tématu <xref:System.ServiceModel.OperationContractAttribute> třídy a <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-117">For more information about how to specify operation contracts, see the <xref:System.ServiceModel.OperationContractAttribute> class and the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property.</span></span>  
  
-   <span data-ttu-id="0c8b5-118">Použití <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> atributy způsobí automatické generování definice kontraktu služby webové služby popis Language (WSDL) dokumentu po nasazení služby.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-118">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes causes the automatic generation of service contract definitions in a Web Services Description Language (WSDL) document once the service is deployed.</span></span> <span data-ttu-id="0c8b5-119">Stažení dokumentu připojením `?wsdl` na HTTP základní adresa pro službu.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-119">The document is downloaded by appending `?wsdl` to the HTTP base address for the service.</span></span> <span data-ttu-id="0c8b5-120">Třeba `http://microsoft/CalculatorService?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="0c8b5-120">For example, `http://microsoft/CalculatorService?wsdl`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8b5-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c8b5-121">See Also</span></span>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="0c8b5-122">Navrhování kontraktů služby</span><span class="sxs-lookup"><span data-stu-id="0c8b5-122">Designing Service Contracts</span></span>](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [<span data-ttu-id="0c8b5-123">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="0c8b5-123">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
