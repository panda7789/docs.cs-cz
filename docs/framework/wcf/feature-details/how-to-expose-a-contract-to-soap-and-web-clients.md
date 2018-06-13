---
title: 'Postupy: vystavení kontraktu protokolu SOAP a webovými klienty'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: a9a730fe94d1df8c887a2eaf20c1e338bd056ed5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494147"
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a><span data-ttu-id="44b4a-102">Postupy: vystavení kontraktu protokolu SOAP a webovými klienty</span><span class="sxs-lookup"><span data-stu-id="44b4a-102">How to: Expose a Contract to SOAP and Web Clients</span></span>
<span data-ttu-id="44b4a-103">Ve výchozím nastavení Windows Communication Foundation (WCF) zpřístupňuje koncové body k dispozici pouze klientům protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="44b4a-103">By default, Windows Communication Foundation (WCF) makes endpoints available only to SOAP clients.</span></span> <span data-ttu-id="44b4a-104">V [postupy: vytvoření základní služby WCF Web HTTP](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), koncový bod je k dispozici pro klienty protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="44b4a-104">In [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), an endpoint is made available to non-SOAP clients.</span></span> <span data-ttu-id="44b4a-105">Může nastat situace, kdy chcete zpřístupnit stejné smlouvy obou směrech, a to jako koncový bod webové a jako koncový bod protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="44b4a-105">There may be times when you want to make the same contract available both ways, as a Web endpoint and as a SOAP endpoint.</span></span> <span data-ttu-id="44b4a-106">Toto téma ukazuje příklad toho, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="44b4a-106">This topic shows an example of how to do this.</span></span>  
  
### <a name="to-define-the-service-contract"></a><span data-ttu-id="44b4a-107">K definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="44b4a-107">To define the service contract</span></span>  
  
1.  <span data-ttu-id="44b4a-108">Definování kontraktu služby pomocí rozhraní označené jako <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> a <xref:System.ServiceModel.Web.WebGetAttribute> atributy, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="44b4a-108">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
     [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="44b4a-109">Ve výchozím nastavení <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje POST volání operace.</span><span class="sxs-lookup"><span data-stu-id="44b4a-109">By default <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="44b4a-110">Můžete však zadat metodu pro mapování na operaci zadáním "metoda =" parametr.</span><span class="sxs-lookup"><span data-stu-id="44b4a-110">You can, however, specify the method to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="44b4a-111"><xref:System.ServiceModel.Web.WebGetAttribute> nemá "metoda =" parametr a pouze mapy GET volání operace služby.</span><span class="sxs-lookup"><span data-stu-id="44b4a-111"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>  
  
2.  <span data-ttu-id="44b4a-112">Implementujte kontrakt služby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="44b4a-112">Implement the service contract, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="44b4a-113">K hostování služby</span><span class="sxs-lookup"><span data-stu-id="44b4a-113">To host the service</span></span>  
  
1.  <span data-ttu-id="44b4a-114">Vytvoření <xref:System.ServiceModel.ServiceHost> objektu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="44b4a-114">Create a <xref:System.ServiceModel.ServiceHost> object, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]  
  
2.  <span data-ttu-id="44b4a-115">Přidat <xref:System.ServiceModel.Description.ServiceEndpoint> s <xref:System.ServiceModel.BasicHttpBinding> SOAP koncového bodu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="44b4a-115">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> for the SOAP endpoint, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]  
  
3.  <span data-ttu-id="44b4a-116">Přidat <xref:System.ServiceModel.Description.ServiceEndpoint> s <xref:System.ServiceModel.WebHttpBinding> pro koncový bod protokolu SOAP a přidejte <xref:System.ServiceModel.Description.WebHttpBehavior> ke koncovému bodu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="44b4a-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> for the non-SOAP endpoint and add the <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]  
  
4.  <span data-ttu-id="44b4a-117">Volání `Open()` na <xref:System.ServiceModel.ServiceHost> instance pro otevření hostitele služby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="44b4a-117">Call `Open()` on a <xref:System.ServiceModel.ServiceHost> instance to open the service host, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="44b4a-118">K volání operací služby namapované na GET v Internet Exploreru</span><span class="sxs-lookup"><span data-stu-id="44b4a-118">To call service operations mapped to GET in Internet Explorer</span></span>  
  
1.  <span data-ttu-id="44b4a-119">Otevřete Internet Explorer a zadejte "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="44b4a-119">Open Internet Explorer and type "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="44b4a-120">Adresa URL obsahuje základní adresa služby ("http://localhost:8000/"), relativní adresa koncového bodu (""), operace služby k volání ("EchoWithGet") a otazník následuje seznam pojmenované parametry oddělených ampersandem (&).</span><span class="sxs-lookup"><span data-stu-id="44b4a-120">The URL contains the base address of the service ("http://localhost:8000/"), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>  
  
### <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a><span data-ttu-id="44b4a-121">K volání operací služby na koncový bod webové v kódu</span><span class="sxs-lookup"><span data-stu-id="44b4a-121">To call service operations on the Web endpoint in code</span></span>  
  
1.  <span data-ttu-id="44b4a-122">Vytvoření instance <xref:System.ServiceModel.Web.WebChannelFactory%601> v rámci `using` blokovat, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="44b4a-122">Create an instance of <xref:System.ServiceModel.Web.WebChannelFactory%601> within a `using` block, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]  
  
> [!NOTE]
>  <span data-ttu-id="44b4a-123">`Close()` je automaticky volána na konci kanálu `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="44b4a-123">`Close()` is automatically called on the channel at the end of the `using` block.</span></span>  
  
1.  <span data-ttu-id="44b4a-124">Vytvoření kanálu a volání služby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="44b4a-124">Create the channel and call the service, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]  
  
### <a name="to-call-service-operations-on-the-soap-endpoint"></a><span data-ttu-id="44b4a-125">K volání operací služby na koncový bod protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="44b4a-125">To call service operations on the SOAP endpoint</span></span>  
  
1.  <span data-ttu-id="44b4a-126">Vytvoření instance <xref:System.ServiceModel.ChannelFactory> v rámci `using` blokovat, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="44b4a-126">Create an instance of <xref:System.ServiceModel.ChannelFactory> within a `using` block, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
     [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]  
  
2.  <span data-ttu-id="44b4a-127">Vytvoření kanálu a volání služby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="44b4a-127">Create the channel and call the service, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
     [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]  
  
### <a name="to-close-the-service-host"></a><span data-ttu-id="44b4a-128">Zavřete hostitele služby</span><span class="sxs-lookup"><span data-stu-id="44b4a-128">To close the service host</span></span>  
  
1.  <span data-ttu-id="44b4a-129">Zavřete hostitele služby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="44b4a-129">Close the service host, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
     [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="44b4a-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="44b4a-130">Example</span></span>  
 <span data-ttu-id="44b4a-131">Zde je kód úplný výpis pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="44b4a-131">The following is the full code listing for this topic.</span></span>  
  
 [!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
 [!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="44b4a-132">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="44b4a-132">Compiling the Code</span></span>  
 <span data-ttu-id="44b4a-133">Při kompilování Service.cs, odkaz System.ServiceModel.dll a System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="44b4a-133">When compiling Service.cs, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b4a-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="44b4a-134">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.ChannelFactory>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="44b4a-135">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="44b4a-135">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
