---
title: 'Postupy: Vytvoření služby pomocí rozhraní kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: c7d4bce174790b97db6b95aa5d15af455f261f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597160"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="ae44c-102">Postupy: Vytvoření služby pomocí rozhraní kontraktu</span><span class="sxs-lookup"><span data-stu-id="ae44c-102">How to: Create a Service with a Contract Interface</span></span>
<span data-ttu-id="ae44c-103">Upřednostňovaný způsob, jak vytvořit kontrakt Windows Communication Foundation (WCF), je pomocí rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ae44c-103">The preferred way to create a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="ae44c-104">Tato smlouva určuje kolekci a strukturu zpráv potřebných pro přístup k operacím, které služba nabízí.</span><span class="sxs-lookup"><span data-stu-id="ae44c-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="ae44c-105">Toto rozhraní definuje vstupní a výstupní typy tím, že použije <xref:System.ServiceModel.ServiceContractAttribute> třídu na rozhraní a <xref:System.ServiceModel.OperationContractAttribute> třídu na metody, které chcete zveřejnit.</span><span class="sxs-lookup"><span data-stu-id="ae44c-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 <span data-ttu-id="ae44c-106">Další informace o kontraktech služeb najdete v tématu [Navrhování kontraktů služeb](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="ae44c-106">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="ae44c-107">Vytvoření kontraktu WCF s rozhraním</span><span class="sxs-lookup"><span data-stu-id="ae44c-107">Creating a WCF contract with an interface</span></span>  
  
1. <span data-ttu-id="ae44c-108">Vytvořte nové rozhraní pomocí Visual Basic, C# nebo jakéhokoli jiného jazyka modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="ae44c-108">Create a new interface using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="ae44c-109">Použijte <xref:System.ServiceModel.ServiceContractAttribute> třídu na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ae44c-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3. <span data-ttu-id="ae44c-110">Definujte metody v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ae44c-110">Define the methods in the interface.</span></span>  
  
4. <span data-ttu-id="ae44c-111">Použijte <xref:System.ServiceModel.OperationContractAttribute> třídu pro každou metodu, která musí být vystavena jako součást veřejné smlouvy WCF.</span><span class="sxs-lookup"><span data-stu-id="ae44c-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae44c-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae44c-112">Example</span></span>  
 <span data-ttu-id="ae44c-113">Následující příklad kódu ukazuje rozhraní, které definuje kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="ae44c-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="ae44c-114">Metody, které mají <xref:System.ServiceModel.OperationContractAttribute> použitou třídu, používají ve výchozím nastavení vzor zprávy požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="ae44c-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="ae44c-115">Další informace o tomto vzoru zprávy najdete v tématu [Postupy: Vytvoření kontraktu požadavku a odpovědi](how-to-create-a-request-reply-contract.md).</span><span class="sxs-lookup"><span data-stu-id="ae44c-115">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="ae44c-116">Můžete také vytvořit a použít jiné vzorce zprávy nastavením vlastností atributu.</span><span class="sxs-lookup"><span data-stu-id="ae44c-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="ae44c-117">Další příklady naleznete v tématu [Postupy: vytvoření jednosměrného kontraktu](how-to-create-a-one-way-contract.md) a [Postup: Vytvoření duplexního kontraktu](how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="ae44c-117">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae44c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae44c-118">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
