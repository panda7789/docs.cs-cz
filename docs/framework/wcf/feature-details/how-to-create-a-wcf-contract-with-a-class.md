---
title: 'Postupy: Vytvoření kontraktu Windows Communication Foundation s třídou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 0be2400ef3da5f0bbc218032ecd69af23f82cabd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597134"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="dda8a-102">Postupy: Vytvoření kontraktu Windows Communication Foundation s třídou</span><span class="sxs-lookup"><span data-stu-id="dda8a-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="dda8a-103">Upřednostňovaným způsobem vytvoření kontraktu Windows Communication Foundation (WCF) je použití rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dda8a-103">The preferred way of creating a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="dda8a-104">Další informace najdete v tématu [Postup: Definování kontraktu služby](../how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="dda8a-104">For more information, see [How to: Define a Service Contract](../how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="dda8a-105">Alternativa, která je zde uvedená, je vytvořit třídu a potom použít <xref:System.ServiceModel.ServiceContractAttribute> atribut přímo pro třídu a <xref:System.ServiceModel.OperationContractAttribute> atribut pro každou metodu ve třídě, která je součástí kontraktu.</span><span class="sxs-lookup"><span data-stu-id="dda8a-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="dda8a-106">`[ServiceContract]`a `[ServiceContractAttribute]` udělejte stejné věci.</span><span class="sxs-lookup"><span data-stu-id="dda8a-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="dda8a-107">Totéž platí pro `[OperationContract]` a `[OperationContractAttribute]` .</span><span class="sxs-lookup"><span data-stu-id="dda8a-107">The same thing is true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="dda8a-108">V každém případě je původní zkratka pro druhý.</span><span class="sxs-lookup"><span data-stu-id="dda8a-108">In each case, the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="dda8a-109">Další informace o kontraktech služeb najdete v tématu [Navrhování kontraktů služeb](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="dda8a-109">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="dda8a-110">Vytvoření kontraktu Windows Communication Foundation s třídou</span><span class="sxs-lookup"><span data-stu-id="dda8a-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1. <span data-ttu-id="dda8a-111">Vytvořte novou třídu pomocí Visual Basic, jazyka C# nebo jakéhokoli jiného jazyka Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="dda8a-111">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="dda8a-112">Použijte <xref:System.ServiceModel.ServiceContractAttribute> třídu pro třídu.</span><span class="sxs-lookup"><span data-stu-id="dda8a-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3. <span data-ttu-id="dda8a-113">Vytvořte metody ve třídě.</span><span class="sxs-lookup"><span data-stu-id="dda8a-113">Create methods in the class.</span></span>  
  
4. <span data-ttu-id="dda8a-114">Použijte <xref:System.ServiceModel.OperationContractAttribute> třídu pro každou metodu, která musí být vystavena jako součást veřejné smlouvy WCF.</span><span class="sxs-lookup"><span data-stu-id="dda8a-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dda8a-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="dda8a-115">Example</span></span>  
 <span data-ttu-id="dda8a-116">Následující příklad kódu ukazuje třídu, která definuje kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="dda8a-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="dda8a-117">Metody, které mají <xref:System.ServiceModel.OperationContractAttribute> použitou třídu, používají ve výchozím nastavení vzor zprávy požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="dda8a-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="dda8a-118">Další informace o tomto vzoru zprávy najdete v tématu [Postupy: Vytvoření kontraktu požadavku a odpovědi](how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="dda8a-118">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="dda8a-119">Můžete také vytvořit a použít jiné vzorce zprávy nastavením vlastností atributu.</span><span class="sxs-lookup"><span data-stu-id="dda8a-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="dda8a-120">Další příklady naleznete v tématu [Postupy: vytvoření jednosměrného kontraktu](how-to-create-a-one-way-contract.md) a [Postup: Vytvoření duplexního kontraktu](how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="dda8a-120">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda8a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="dda8a-121">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
