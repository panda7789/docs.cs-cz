---
title: 'Postupy: Vytvoření služby pomocí rozhraní kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: cd0ae76040f235b4573a90764566205a2d5d81e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536721"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="d9eae-102">Postupy: Vytvoření služby pomocí rozhraní kontraktu</span><span class="sxs-lookup"><span data-stu-id="d9eae-102">How to: Create a Service with a Contract Interface</span></span>
<span data-ttu-id="d9eae-103">Pomocí rozhraní je upřednostňovaný způsob vytvoření kontraktu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d9eae-103">The preferred way to create a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="d9eae-104">Tento kontrakt určuje kolekci a struktura zpráv, které jsou nutné pro přístup k operace nabídky služeb.</span><span class="sxs-lookup"><span data-stu-id="d9eae-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="d9eae-105">Toto rozhraní definuje vstupní a výstupní typy použitím <xref:System.ServiceModel.ServiceContractAttribute> třídy rozhraní a <xref:System.ServiceModel.OperationContractAttribute> třídy pro metody, které chcete zveřejnit.</span><span class="sxs-lookup"><span data-stu-id="d9eae-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 <span data-ttu-id="d9eae-106">Další informace o kontraktech služeb najdete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="d9eae-106">For more information about service contracts, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="d9eae-107">Vytvoření pomocí rozhraní kontraktu WCF</span><span class="sxs-lookup"><span data-stu-id="d9eae-107">Creating a WCF contract with an interface</span></span>  
  
1.  <span data-ttu-id="d9eae-108">Vytvoření nového rozhraní pomocí jazyka Visual Basic C#, nebo jakéhokoli jiného common language runtime jazyka.</span><span class="sxs-lookup"><span data-stu-id="d9eae-108">Create a new interface using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2.  <span data-ttu-id="d9eae-109">Použít <xref:System.ServiceModel.ServiceContractAttribute> třídy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d9eae-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3.  <span data-ttu-id="d9eae-110">Definujte metody v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d9eae-110">Define the methods in the interface.</span></span>  
  
4.  <span data-ttu-id="d9eae-111">Použít <xref:System.ServiceModel.OperationContractAttribute> třídy pro každou metodu, která musí být v rámci veřejného kontraktu WCF vystavené.</span><span class="sxs-lookup"><span data-stu-id="d9eae-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9eae-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9eae-112">Example</span></span>  
 <span data-ttu-id="d9eae-113">Následující příklad kódu ukazuje rozhraní, které definuje kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="d9eae-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="d9eae-114">Metody, které mají <xref:System.ServiceModel.OperationContractAttribute> Třída použitá použít model zprávy požadavku a odpovědi ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="d9eae-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="d9eae-115">Další informace o tomto vzoru zprávy naleznete v tématu [jak: Vytvoření kontraktu požadavku a odpovědi](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="d9eae-115">For more information about this message pattern, see [How to: Create a Request-Reply Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="d9eae-116">Můžete také vytvořit a použít další způsoby zpráva nastavením vlastností atributu.</span><span class="sxs-lookup"><span data-stu-id="d9eae-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="d9eae-117">Další příklady najdete v tématu [jak: Vytvoření jednosměrného kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) a [jak: Vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="d9eae-117">For more examples, see [How to: Create a One-Way Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9eae-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9eae-118">See also</span></span>
- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
