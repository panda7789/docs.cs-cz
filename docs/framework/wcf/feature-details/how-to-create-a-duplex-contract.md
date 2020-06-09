---
title: 'Postupy: Vytvoření duplexního kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: e5b6c7eecce08a23490b6ab1991e4561d9462469
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598980"
---
# <a name="how-to-create-a-duplex-contract"></a><span data-ttu-id="eb931-102">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="eb931-102">How to: Create a Duplex Contract</span></span>
<span data-ttu-id="eb931-103">V tomto tématu se dozvíte o základních krocích pro vytváření metod, které používají oboustranný (obousměrný) kontrakt.</span><span class="sxs-lookup"><span data-stu-id="eb931-103">This topic shows the basic steps to create methods that use a duplex (two-way) contract.</span></span> <span data-ttu-id="eb931-104">Oboustranný kontrakt umožňuje klientům a serverům vzájemně komunikovat nezávisle na sobě, takže může iniciovat volání do druhé.</span><span class="sxs-lookup"><span data-stu-id="eb931-104">A duplex contract allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="eb931-105">Duplexní smlouva je jedním ze tří vzorů zpráv, které jsou k dispozici pro Windows Communication Foundation služby (WCF).</span><span class="sxs-lookup"><span data-stu-id="eb931-105">The duplex contract is one of three message patterns available to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="eb931-106">Další dva vzory zpráv jsou jednosměrné a vyžadují odpověď.</span><span class="sxs-lookup"><span data-stu-id="eb931-106">The other two message patterns are one-way and request-reply.</span></span> <span data-ttu-id="eb931-107">Duplexní kontrakt se skládá z 2 1 kontraktů mezi klientem a serverem a nevyžaduje, aby byla volání metod korelace.</span><span class="sxs-lookup"><span data-stu-id="eb931-107">A duplex contract consists of two one-way contracts between the client and the server and does not require that the method calls be correlated.</span></span> <span data-ttu-id="eb931-108">Tento druh smlouvy použijte v případě, že se vaše služba musí dotazovat klienta na Další informace nebo explicitně vyvolat události na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="eb931-108">Use this kind of contract when your service must query the client for more information or explicitly raise events on the client.</span></span> <span data-ttu-id="eb931-109">Další informace o vytváření klientských aplikací pro duplexní smlouvu najdete v tématu [Postup: přístup ke službám pomocí duplexního kontraktu](how-to-access-services-with-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="eb931-109">For more information about creating a client application for a duplex contract, see [How to: Access Services with a Duplex Contract](how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="eb931-110">Pracovní ukázku najdete v ukázce [duplexní](../samples/duplex.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="eb931-110">For a working sample, see the [Duplex](../samples/duplex.md) sample.</span></span>  
  
### <a name="to-create-a-duplex-contract"></a><span data-ttu-id="eb931-111">Postup vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="eb931-111">To create a duplex contract</span></span>  
  
1. <span data-ttu-id="eb931-112">Vytvořte rozhraní, které vytvoří na straně serveru oboustranně duplexní smlouvu.</span><span class="sxs-lookup"><span data-stu-id="eb931-112">Create the interface that makes up the server side of the duplex contract.</span></span>  
  
2. <span data-ttu-id="eb931-113">Použijte <xref:System.ServiceModel.ServiceContractAttribute> třídu na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eb931-113">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. <span data-ttu-id="eb931-114">Deklaruje signatury metody v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eb931-114">Declare the method signatures in the interface.</span></span>  
  
4. <span data-ttu-id="eb931-115">Použijte <xref:System.ServiceModel.OperationContractAttribute> třídu pro každý podpis metody, který musí být součástí veřejné smlouvy.</span><span class="sxs-lookup"><span data-stu-id="eb931-115">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
5. <span data-ttu-id="eb931-116">Vytvořte rozhraní zpětného volání, které definuje sadu operací, které může služba vyvolat na klientovi.</span><span class="sxs-lookup"><span data-stu-id="eb931-116">Create the callback interface that defines the set of operations that the service can invoke on the client.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. <span data-ttu-id="eb931-117">Deklarujete signatury metod v rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="eb931-117">Declare the method signatures in the callback interface.</span></span>  
  
7. <span data-ttu-id="eb931-118">Použijte <xref:System.ServiceModel.OperationContractAttribute> třídu pro každý podpis metody, který musí být součástí veřejné smlouvy.</span><span class="sxs-lookup"><span data-stu-id="eb931-118">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
8. <span data-ttu-id="eb931-119">Propojte dvě rozhraní s meziduplexní smlouvou nastavením <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> vlastnosti v primárním rozhraní na typ rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="eb931-119">Link the two interfaces into a duplex contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property in the primary interface to the type of the callback interface.</span></span>  
  
### <a name="to-call-methods-on-the-client"></a><span data-ttu-id="eb931-120">Volání metod na klienta</span><span class="sxs-lookup"><span data-stu-id="eb931-120">To call methods on the client</span></span>  
  
1. <span data-ttu-id="eb931-121">V implementaci primární smlouvy v rámci služby deklarujte proměnnou pro rozhraní zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="eb931-121">In the service's implementation of the primary contract, declare a variable for the callback interface.</span></span>  
  
2. <span data-ttu-id="eb931-122">Nastavte proměnnou na odkaz na objekt vrácený <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> metodou <xref:System.ServiceModel.OperationContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="eb931-122">Set the variable to the object reference returned by the <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> method of the <xref:System.ServiceModel.OperationContext> class.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. <span data-ttu-id="eb931-123">Volejte metody definované rozhraním zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="eb931-123">Call the methods defined by the callback interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb931-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb931-124">Example</span></span>  
 <span data-ttu-id="eb931-125">Následující příklad kódu ukazuje duplexní komunikaci.</span><span class="sxs-lookup"><span data-stu-id="eb931-125">The following code example demonstrates duplex communication.</span></span> <span data-ttu-id="eb931-126">Kontrakt služby obsahuje operace služby pro přesun dopředu a zpět.</span><span class="sxs-lookup"><span data-stu-id="eb931-126">The service’s contract contains service operations for moving forward and backward.</span></span> <span data-ttu-id="eb931-127">Smlouva klienta obsahuje operaci služby pro vytváření sestav své pozice.</span><span class="sxs-lookup"><span data-stu-id="eb931-127">The client’s contract contains a service operation for reporting its position.</span></span>  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
- <span data-ttu-id="eb931-128">Použití <xref:System.ServiceModel.ServiceContractAttribute> atributů a <xref:System.ServiceModel.OperationContractAttribute> umožňuje automatické generování definic servisních smluv v jazyce WSDL (Web Services Description Language).</span><span class="sxs-lookup"><span data-stu-id="eb931-128">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes allows the automatic generation of service contract definitions in the Web Services Description Language (WSDL).</span></span>  
  
- <span data-ttu-id="eb931-129">K načtení dokumentu WSDL a (volitelného) kódu a konfiguraci pro klienta použijte nástroj pro dodané [metadata (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="eb931-129">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to retrieve the WSDL document and (optional) code and configuration for a client.</span></span>  
  
- <span data-ttu-id="eb931-130">Koncové body, které zveřejňují duplexní služby, musí být zabezpečené.</span><span class="sxs-lookup"><span data-stu-id="eb931-130">Endpoints exposing duplex services must be secured.</span></span> <span data-ttu-id="eb931-131">Když služba obdrží duplexní zprávu, při zjištění, kam se má odpověď odeslat, vyhledá na pozici v této příchozí zprávě ReplyTo.</span><span class="sxs-lookup"><span data-stu-id="eb931-131">When a service receives a duplex message, it looks at the ReplyTo in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="eb931-132">Pokud kanál není zabezpečený, může nedůvěryhodný klient odeslat škodlivou zprávu s parametrem ReplyTo cílového počítače, což vede k odepření služby cílového počítače.</span><span class="sxs-lookup"><span data-stu-id="eb931-132">If the channel is not secured, then an untrusted client could send a malicious message with a target machine's ReplyTo, leading to a denial of service of the target machine.</span></span> <span data-ttu-id="eb931-133">S běžnými zprávami pro odpověď na požadavek se nejedná o problém, protože parametr ReplyTo je ignorován a odpověď je odeslána na kanál, na kterém byla odeslána původní zpráva.</span><span class="sxs-lookup"><span data-stu-id="eb931-133">With regular request-reply messages, this is not an issue, because the ReplyTo is ignored and the response is sent on the channel the original message came in on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb931-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb931-134">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="eb931-135">Postupy: Přístup ke službám pomocí duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="eb931-135">How to: Access Services with a Duplex Contract</span></span>](how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="eb931-136">Duplex</span><span class="sxs-lookup"><span data-stu-id="eb931-136">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="eb931-137">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="eb931-137">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
- [<span data-ttu-id="eb931-138">Postupy: Definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="eb931-138">How to: Define a Service Contract</span></span>](../how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="eb931-139">Relace</span><span class="sxs-lookup"><span data-stu-id="eb931-139">Session</span></span>](../samples/session.md)
