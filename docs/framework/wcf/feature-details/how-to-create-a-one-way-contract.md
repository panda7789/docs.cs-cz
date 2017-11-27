---
title: "Postupy: Vytvoření jednosměrného kontraktu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fb899bdc8d1452046b71fdce5d0782e1d1338d2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-one-way-contract"></a><span data-ttu-id="c2408-102">Postupy: Vytvoření jednosměrného kontraktu</span><span class="sxs-lookup"><span data-stu-id="c2408-102">How to: Create a One-Way Contract</span></span>
<span data-ttu-id="c2408-103">Toto téma ukazuje základní kroky pro vytvoření metody, které používají jednosměrného kontraktu.</span><span class="sxs-lookup"><span data-stu-id="c2408-103">This topic shows the basic steps to create methods that use a one-way contract.</span></span> <span data-ttu-id="c2408-104">Tyto metody vyvolání operací na [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby z klienta, ale Nečekejte na odpověď.</span><span class="sxs-lookup"><span data-stu-id="c2408-104">Such methods invoke operations on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service from a client but do not expect a reply.</span></span> <span data-ttu-id="c2408-105">Tento typ smlouvy můžete použít například k publikování oznámení pro mnoho odběratele.</span><span class="sxs-lookup"><span data-stu-id="c2408-105">This type of contract can be used, for example, to publish notifications to many subscribers.</span></span> <span data-ttu-id="c2408-106">Jednosměrné kontrakty můžete také použít při vytváření duplexního kontraktu (obousměrné), která umožňuje klientům a serverům ke komunikaci mezi sebou nezávisle tak, aby buď můžete spustit volání na druhý.</span><span class="sxs-lookup"><span data-stu-id="c2408-106">You can also use one-way contracts when creating a duplex (two-way) contract, which allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="c2408-107">Můžete to umožní na konkrétní server jednosměrný volání klientovi, který klient může považovat za události.</span><span class="sxs-lookup"><span data-stu-id="c2408-107">This can allow, in particular, the server to make one-way calls to the client that the client can treat as events.</span></span> <span data-ttu-id="c2408-108">Podrobné informace o zadávání jednosměrné metody najdete v tématu <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost a <xref:System.ServiceModel.OperationContractAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="c2408-108">For detailed information about specifying one-way methods, see the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property and the <xref:System.ServiceModel.OperationContractAttribute> class.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="c2408-109">Vytvoření aplikace klienta pro duplexního kontraktu, najdete v části [postupy: přístup ke službě pomocí jednosměrných kontraktů a kontraktů požadavek-odpověď](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="c2408-109"> creating a client application for a duplex contract, see [How to: Access Services with One-Way and Request-Reply Contracts](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md).</span></span> <span data-ttu-id="c2408-110">Ukázku práce, najdete [jednosměrný](../../../../docs/framework/wcf/samples/one-way.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="c2408-110">For a working sample, see the [One-Way](../../../../docs/framework/wcf/samples/one-way.md) sample.</span></span>  
  
### <a name="to-create-a-one-way-contract"></a><span data-ttu-id="c2408-111">K vytvoření jednosměrného kontraktu</span><span class="sxs-lookup"><span data-stu-id="c2408-111">To create a one-way contract</span></span>  
  
1.  <span data-ttu-id="c2408-112">Vytvoření kontrakt služby s použitím <xref:System.ServiceModel.ServiceContractAttribute> třídy rozhraní, které definuje metody, služba je k implementaci.</span><span class="sxs-lookup"><span data-stu-id="c2408-112">Create the service contract by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface that defines the methods the service is to implement.</span></span>  
  
2.  <span data-ttu-id="c2408-113">Označuje, které metody v rozhraní klienta můžete vyvolat použití <xref:System.ServiceModel.OperationContractAttribute> třída k nim.</span><span class="sxs-lookup"><span data-stu-id="c2408-113">Indicate which methods in the interface a client can invoked by applying the <xref:System.ServiceModel.OperationContractAttribute> class to them.</span></span>  
  
3.  <span data-ttu-id="c2408-114">Určit operace, které musí mít žádný výstup (žádnou návratovou hodnotu a žádné na víc systémů nebo parametry ref) jako jednosměrný nastavením <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="c2408-114">Designate operations that must have no output (no return value and no out or ref parameters) as one-way by setting the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`.</span></span> <span data-ttu-id="c2408-115">Všimněte si, že operace, která provádění <xref:System.ServiceModel.OperationContractAttribute> třída splnit kontraktu požadavku a odpovědi ve výchozím nastavení, protože <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost je `false` ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c2408-115">Note that the operations that carry the <xref:System.ServiceModel.OperationContractAttribute> class satisfy a request-reply contract by default because the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property is `false` by default.</span></span> <span data-ttu-id="c2408-116">Proto je nutné explicitně zadat hodnotu atributu vlastnost, která má být `true` Pokud chcete pro metodu jednosměrného kontraktu.</span><span class="sxs-lookup"><span data-stu-id="c2408-116">So you must explicitly specify the value of the attribute property to be `true` if you want a one-way contract for the method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2408-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2408-117">Example</span></span>  
 <span data-ttu-id="c2408-118">Následující příklad kódu definuje kontrakt služby, který obsahuje několik metod, jednosměrná.</span><span class="sxs-lookup"><span data-stu-id="c2408-118">The following code example defines a contract for a service that includes several one-way methods.</span></span> <span data-ttu-id="c2408-119">Všechny metody mít jednosměrné kontrakty s výjimkou `Equals`, který použije se výchozí hodnota požadavku a odpovědi a vrátí výsledek.</span><span class="sxs-lookup"><span data-stu-id="c2408-119">All of the methods have one-way contracts except `Equals`, which defaults to request-reply and returns a result.</span></span>  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c2408-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2408-120">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="c2408-121">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="c2408-121">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="c2408-122">Postupy: definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="c2408-122">How to: Define a Service Contract</span></span>](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [<span data-ttu-id="c2408-123">Relace</span><span class="sxs-lookup"><span data-stu-id="c2408-123">Session</span></span>](../../../../docs/framework/wcf/samples/session.md)  
 [<span data-ttu-id="c2408-124">Postupy: vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="c2408-124">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
