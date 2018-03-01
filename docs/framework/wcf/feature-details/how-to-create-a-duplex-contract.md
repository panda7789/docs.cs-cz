---
title: "Postupy: Vytvoření duplexního kontraktu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 003b07326612f3b51390d691c7bba0ef1c1b85dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-duplex-contract"></a><span data-ttu-id="60d80-102">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="60d80-102">How to: Create a Duplex Contract</span></span>
<span data-ttu-id="60d80-103">Toto téma ukazuje základní kroky pro vytvoření metody, které používají duplexního kontraktu (obousměrné).</span><span class="sxs-lookup"><span data-stu-id="60d80-103">This topic shows the basic steps to create methods that use a duplex (two-way) contract.</span></span> <span data-ttu-id="60d80-104">Duplexní kontrakt umožňuje klienty a servery pro komunikaci mezi sebou nezávisle tak, aby buď můžete spustit volání na druhý.</span><span class="sxs-lookup"><span data-stu-id="60d80-104">A duplex contract allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="60d80-105">Duplexní kontrakt je jedním ze tří vzorů zprávy k dispozici pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="60d80-105">The duplex contract is one of three message patterns available to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services.</span></span> <span data-ttu-id="60d80-106">Další dva zprávy vzory jsou jednosměrná a požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="60d80-106">The other two message patterns are one-way and request-reply.</span></span> <span data-ttu-id="60d80-107">Duplexního kontraktu se skládá ze dvou jednosměrné kontrakty mezi klientem a serverem a nevyžaduje korelaci volání metody.</span><span class="sxs-lookup"><span data-stu-id="60d80-107">A duplex contract consists of two one-way contracts between the client and the server and does not require that the method calls be correlated.</span></span> <span data-ttu-id="60d80-108">Tento druh kontrakt použijte, pokud vaše služba musí dotazovat klienta pro další informace nebo explicitně vyvolávání událostí na klientovi.</span><span class="sxs-lookup"><span data-stu-id="60d80-108">Use this kind of contract when your service must query the client for more information or explicitly raise events on the client.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="60d80-109">Vytvoření aplikace klienta pro duplexního kontraktu, najdete v části [postupy: přístup k službám pomocí duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="60d80-109"> creating a client application for a duplex contract, see [How to: Access Services with a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="60d80-110">Ukázku práce, najdete [duplexní](../../../../docs/framework/wcf/samples/duplex.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="60d80-110">For a working sample, see the [Duplex](../../../../docs/framework/wcf/samples/duplex.md) sample.</span></span>  
  
### <a name="to-create-a-duplex-contract"></a><span data-ttu-id="60d80-111">K vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="60d80-111">To create a duplex contract</span></span>  
  
1.  <span data-ttu-id="60d80-112">Vytvořte rozhraní, které tvoří duplexního kontraktu na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="60d80-112">Create the interface that makes up the server side of the duplex contract.</span></span>  
  
2.  <span data-ttu-id="60d80-113">Použít <xref:System.ServiceModel.ServiceContractAttribute> třídy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="60d80-113">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3.  <span data-ttu-id="60d80-114">Podpisy metoda v rozhraní deklarujte.</span><span class="sxs-lookup"><span data-stu-id="60d80-114">Declare the method signatures in the interface.</span></span>  
  
4.  <span data-ttu-id="60d80-115">Použít <xref:System.ServiceModel.OperationContractAttribute> třída pro každý podpis metody, které musí být součástí veřejného kontraktu.</span><span class="sxs-lookup"><span data-stu-id="60d80-115">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
5.  <span data-ttu-id="60d80-116">Vytvořte rozhraní zpětného volání, která definuje sadu operací, které můžete vyvolat službu na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="60d80-116">Create the callback interface that defines the set of operations that the service can invoke on the client.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6.  <span data-ttu-id="60d80-117">Deklarujte podpisy metoda v rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="60d80-117">Declare the method signatures in the callback interface.</span></span>  
  
7.  <span data-ttu-id="60d80-118">Použít <xref:System.ServiceModel.OperationContractAttribute> třída pro každý podpis metody, které musí být součástí veřejného kontraktu.</span><span class="sxs-lookup"><span data-stu-id="60d80-118">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
8.  <span data-ttu-id="60d80-119">Propojení dvě rozhraní do duplexního kontraktu nastavením <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> vlastnost v primární rozhraní pro typ rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="60d80-119">Link the two interfaces into a duplex contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property in the primary interface to the type of the callback interface.</span></span>  
  
### <a name="to-call-methods-on-the-client"></a><span data-ttu-id="60d80-120">Volání metody na straně klienta</span><span class="sxs-lookup"><span data-stu-id="60d80-120">To call methods on the client</span></span>  
  
1.  <span data-ttu-id="60d80-121">V implementaci služby primární kontraktu deklarujte proměnnou pro rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="60d80-121">In the service's implementation of the primary contract, declare a variable for the callback interface.</span></span>  
  
2.  <span data-ttu-id="60d80-122">Nastavte proměnnou na odkaz na objekt vrácený <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> metodu <xref:System.ServiceModel.OperationContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="60d80-122">Set the variable to the object reference returned by the <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> method of the <xref:System.ServiceModel.OperationContext> class.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3.  <span data-ttu-id="60d80-123">Volání metody definované rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="60d80-123">Call the methods defined by the callback interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60d80-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="60d80-124">Example</span></span>  
 <span data-ttu-id="60d80-125">Následující příklad kódu ukazuje duplexní komunikace.</span><span class="sxs-lookup"><span data-stu-id="60d80-125">The following code example demonstrates duplex communication.</span></span> <span data-ttu-id="60d80-126">Kontrakt služby obsahuje operací služby pro přesun vpřed a zpět.</span><span class="sxs-lookup"><span data-stu-id="60d80-126">The service’s contract contains service operations for moving forward and backward.</span></span> <span data-ttu-id="60d80-127">Kontrakt klienta obsahuje operace služby pro vytváření sestav jeho umístění.</span><span class="sxs-lookup"><span data-stu-id="60d80-127">The client’s contract contains a service operation for reporting its position.</span></span>  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
-   <span data-ttu-id="60d80-128">Použití <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> atributy umožňuje automatické generování definice kontraktu služby ve webové služby popis Language (WSDL).</span><span class="sxs-lookup"><span data-stu-id="60d80-128">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes allows the automatic generation of service contract definitions in the Web Services Description Language (WSDL).</span></span>  
  
-   <span data-ttu-id="60d80-129">Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k načtení dokumentu WSDL a kódu (volitelné) a konfigurace pro klienta.</span><span class="sxs-lookup"><span data-stu-id="60d80-129">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to retrieve the WSDL document and (optional) code and configuration for a client.</span></span>  
  
-   <span data-ttu-id="60d80-130">Koncové body vystavení duplexní služby musí být zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="60d80-130">Endpoints exposing duplex services must be secured.</span></span> <span data-ttu-id="60d80-131">Když služba přijme zprávu o duplexní, vypadá to na ReplyTo v této příchozí zprávy k určení místa k odeslání odpovědi.</span><span class="sxs-lookup"><span data-stu-id="60d80-131">When a service receives a duplex message, it looks at the ReplyTo in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="60d80-132">Pokud není zabezpečený kanál, může nedůvěryhodného klienta odeslat škodlivý zprávu s ReplyTo cílový počítač vedoucí k odmítnutí služby cílového počítače.</span><span class="sxs-lookup"><span data-stu-id="60d80-132">If the channel is not secured, then an untrusted client could send a malicious message with a target machine's ReplyTo, leading to a denial of service of the target machine.</span></span> <span data-ttu-id="60d80-133">S regulární požadavku a odpovědi zprávy to není problém, protože ReplyTo je ignorován a odpovědi se odesílají na kanál, který původní zpráva byla přijata v na.</span><span class="sxs-lookup"><span data-stu-id="60d80-133">With regular request-reply messages, this is not an issue, because the ReplyTo is ignored and the response is sent on the channel the original message came in on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60d80-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="60d80-134">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="60d80-135">Postupy: Přístup ke službám pomocí duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="60d80-135">How to: Access Services with a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [<span data-ttu-id="60d80-136">Duplex</span><span class="sxs-lookup"><span data-stu-id="60d80-136">Duplex</span></span>](../../../../docs/framework/wcf/samples/duplex.md)  
 [<span data-ttu-id="60d80-137">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="60d80-137">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="60d80-138">Postupy: Definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="60d80-138">How to: Define a Service Contract</span></span>](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [<span data-ttu-id="60d80-139">Relace</span><span class="sxs-lookup"><span data-stu-id="60d80-139">Session</span></span>](../../../../docs/framework/wcf/samples/session.md)
