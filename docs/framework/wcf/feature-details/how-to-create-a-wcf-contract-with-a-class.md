---
title: 'Postupy: Vytvoření kontraktu Windows Communication Foundation s třídou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 296f500532040aaebf0f6d7d37a7a9aae99a3451
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491808"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="850e5-102">Postupy: Vytvoření kontraktu Windows Communication Foundation s třídou</span><span class="sxs-lookup"><span data-stu-id="850e5-102">How to: Create a Windows Communication Foundation Contract with a Class</span></span>
<span data-ttu-id="850e5-103">Pomocí rozhraní je upřednostňovaný způsob vytvoření kontraktu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="850e5-103">The preferred way of creating a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="850e5-104">Další informace najdete v tématu [postupy: definování kontraktu služby](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="850e5-104">For more information, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span> <span data-ttu-id="850e5-105">Alternativní, popsané tady, je vytvoření třídy a následně použít <xref:System.ServiceModel.ServiceContractAttribute> atribut třídy přímo a <xref:System.ServiceModel.OperationContractAttribute> atribut každá z metod ve třídě, které jsou součástí smlouvy.</span><span class="sxs-lookup"><span data-stu-id="850e5-105">An alternative, outlined here, is to create a class and then apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the class directly and the <xref:System.ServiceModel.OperationContractAttribute> attribute to each of the methods in the class that are part of the contract.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="850e5-106">`[ServiceContract]` a `[ServiceContractAttribute]` stejnou věc udělat.</span><span class="sxs-lookup"><span data-stu-id="850e5-106">`[ServiceContract]` and `[ServiceContractAttribute]` do the same thing.</span></span> <span data-ttu-id="850e5-107">Samé ho true pro `[OperationContract]` a `[OperationContractAttribute]`.</span><span class="sxs-lookup"><span data-stu-id="850e5-107">The same thing it true for `[OperationContract]` and `[OperationContractAttribute]`.</span></span> <span data-ttu-id="850e5-108">V každém případě je sdružená vlastnost pro tento první.</span><span class="sxs-lookup"><span data-stu-id="850e5-108">In each case the former is shorthand for the latter.</span></span>  
  
 <span data-ttu-id="850e5-109">Další informace o kontraktů služby najdete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="850e5-109">For more information about service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a><span data-ttu-id="850e5-110">Vytvoření kontraktu Windows Communication Foundation s třídou</span><span class="sxs-lookup"><span data-stu-id="850e5-110">Creating a Windows Communication Foundation contract with a class</span></span>  
  
1.  <span data-ttu-id="850e5-111">Vytvořte novou třídu pomocí jazyka Visual Basic, C# nebo jakéhokoli jiného common language runtime jazyka.</span><span class="sxs-lookup"><span data-stu-id="850e5-111">Create a new class using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="850e5-112">Použít <xref:System.ServiceModel.ServiceContractAttribute> třída pro třídu.</span><span class="sxs-lookup"><span data-stu-id="850e5-112">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the class.</span></span>  
  
3.  <span data-ttu-id="850e5-113">Vytvoření metody ve třídě.</span><span class="sxs-lookup"><span data-stu-id="850e5-113">Create methods in the class.</span></span>  
  
4.  <span data-ttu-id="850e5-114">Použít <xref:System.ServiceModel.OperationContractAttribute> třída pro každou metodu, který musí být zveřejněný v rámci veřejného kontraktu WCF.</span><span class="sxs-lookup"><span data-stu-id="850e5-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="850e5-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="850e5-115">Example</span></span>  
 <span data-ttu-id="850e5-116">Následující příklad kódu ukazuje třídu, která definuje kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="850e5-116">The following code example shows a class that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 <span data-ttu-id="850e5-117">Metody, které mají <xref:System.ServiceModel.OperationContractAttribute> třída použije ve výchozím nastavení používá vzor zprávu požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="850e5-117">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="850e5-118">Další informace o tomto vzoru zpráva najdete v tématu [postupy: vytvoření kontraktu požadavku a odpovědi](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="850e5-118">For more information about this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="850e5-119">Můžete také vytvořit a použít dalších zpráv vzorech nastavením vlastnosti atributu.</span><span class="sxs-lookup"><span data-stu-id="850e5-119">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="850e5-120">Další příklady najdete v tématu [postupy: vytvoření kontraktu One-Way](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) a [postupy: vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="850e5-120">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="850e5-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="850e5-121">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
