---
title: "Postupy: Vytvoření základní webové služby HTTP WCF"
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
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8352c7761447322d1ddf8381be145e38d6b7df8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a><span data-ttu-id="48997-102">Postupy: Vytvoření základní webové služby HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="48997-102">How to: Create a Basic WCF Web HTTP Service</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="48997-103">Umožňuje vytvořit službu, která zveřejňuje koncový bod webové.</span><span class="sxs-lookup"><span data-stu-id="48997-103"> allows you to create a service that exposes a Web endpoint.</span></span> <span data-ttu-id="48997-104">Koncových bodů webové odesílat data XML nebo JSON, že neexistují žádné obálku protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="48997-104">Web endpoints send data by XML or JSON, there is no SOAP envelope.</span></span> <span data-ttu-id="48997-105">Toto téma ukazuje, jak vystavit takové koncový bod.</span><span class="sxs-lookup"><span data-stu-id="48997-105">This topic demonstrates how to expose such an endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48997-106">Jediný způsob, jak zabezpečit koncový bod webové je zveřejnění prostřednictvím protokolu HTTPS, pomocí zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="48997-106">The only way to secure a Web endpoint is to expose it through HTTPS, using transport security.</span></span> <span data-ttu-id="48997-107">Při použití zabezpečení na základě zpráv, informace o zabezpečení je obvykle umístěny v hlavičkách protokolu SOAP a protože zprávy odeslané do koncových bodů protokolu SOAP obsahovat žádné obálku protokolu SOAP, není nikde umístit informace o zabezpečení a musíte spoléhat na zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="48997-107">When using message-based security, security information is usually placed in SOAP headers and because the messages sent to non-SOAP endpoints contain no SOAP envelope, there is nowhere to place the security information and you must rely on transport security.</span></span>  
  
### <a name="to-create-a-web-endpoint"></a><span data-ttu-id="48997-108">Chcete-li vytvořit koncový bod webové</span><span class="sxs-lookup"><span data-stu-id="48997-108">To create a Web endpoint</span></span>  
  
1.  <span data-ttu-id="48997-109">Definování kontraktu služby pomocí rozhraní označené jako <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> a <xref:System.ServiceModel.Web.WebGetAttribute> atributy.</span><span class="sxs-lookup"><span data-stu-id="48997-109">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes.</span></span>  
  
     [!code-csharp[htBasicService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="48997-110">Ve výchozím nastavení <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje POST volání operace.</span><span class="sxs-lookup"><span data-stu-id="48997-110">By default, <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="48997-111">Můžete však zadat metodu protokolu HTTP (například HEAD, PUT nebo odstraňte) pro mapování na operaci zadáním "metoda =" parametr.</span><span class="sxs-lookup"><span data-stu-id="48997-111">You can, however, specify the HTTP method (for example, HEAD, PUT, or DELETE) to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="48997-112"><xref:System.ServiceModel.Web.WebGetAttribute>nemá "metoda =" parametr a pouze mapy GET volání operace služby.</span><span class="sxs-lookup"><span data-stu-id="48997-112"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>  
  
2.  <span data-ttu-id="48997-113">Implementujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="48997-113">Implement the service contract.</span></span>  
  
     [!code-csharp[htBasicService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="48997-114">K hostování služby</span><span class="sxs-lookup"><span data-stu-id="48997-114">To host the service</span></span>  
  
1.  <span data-ttu-id="48997-115">Vytvoření <xref:System.ServiceModel.Web.WebServiceHost> objektu.</span><span class="sxs-lookup"><span data-stu-id="48997-115">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htBasicService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]  
  
2.  <span data-ttu-id="48997-116">Přidat <xref:System.ServiceModel.Description.ServiceEndpoint> s <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="48997-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
     [!code-csharp[htBasicService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]  
  
    > [!NOTE]
    >  <span data-ttu-id="48997-117">Pokud je nemůžete přidat koncový bod, <xref:System.ServiceModel.Web.WebServiceHost> automaticky vytvoří výchozí koncový bod.</span><span class="sxs-lookup"><span data-stu-id="48997-117">If you do not add an endpoint, <xref:System.ServiceModel.Web.WebServiceHost> automatically creates a default endpoint.</span></span> <span data-ttu-id="48997-118"><xref:System.ServiceModel.Web.WebServiceHost>také přidá <xref:System.ServiceModel.Description.WebHttpBehavior> a zakáže stránku nápovědy HTTP a funkci GET webové služby popis Language (WSDL), takže koncový bod metadat nebudou v konfliktu s výchozí koncový bod HTTP.</span><span class="sxs-lookup"><span data-stu-id="48997-118"><xref:System.ServiceModel.Web.WebServiceHost> also adds <xref:System.ServiceModel.Description.WebHttpBehavior> and disables the HTTP Help page and the Web Services Description Language (WSDL) GET functionality so the metadata endpoint does not interfere with the default HTTP endpoint.</span></span>  
    >   
    >  <span data-ttu-id="48997-119">Přidání koncový bod-protokolu SOAP s adresou URL služby "" způsobí neočekávanému chování, když je proveden pokus o volání operace v koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="48997-119">Adding a non-SOAP endpoint with a URL of "" causes unexpected behavior when an attempt is made to call an operation on the endpoint.</span></span> <span data-ttu-id="48997-120">Důvodem je, naslouchání identifikátoru URI koncového bodu je stejný jako identifikátor URI pro stránku nápovědy (stránka, ke které se zobrazí, když přejdete na adresu základní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby).</span><span class="sxs-lookup"><span data-stu-id="48997-120">The reason for this is the listen URI of the endpoint is the same as the URI for the help page (the page that is displayed when you browse to the base address of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service).</span></span>  
  
     <span data-ttu-id="48997-121">Můžete provést jednu z následujících akcí k tomu nedocházelo:</span><span class="sxs-lookup"><span data-stu-id="48997-121">You can do one of the following actions to prevent this from happening:</span></span>  
  
    -   <span data-ttu-id="48997-122">Vždycky zadejte prázdný identifikátor URI pro koncový bod-protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="48997-122">Always specify a non-blank URI for a non-SOAP endpoint.</span></span>  
  
    -   <span data-ttu-id="48997-123">Vypněte na stránce nápovědy.</span><span class="sxs-lookup"><span data-stu-id="48997-123">Turn off the help page.</span></span> <span data-ttu-id="48997-124">To lze provést následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="48997-124">This can be done with the following code.</span></span>  
  
     [!code-csharp[htBasicService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]  
  
3.  <span data-ttu-id="48997-125">Otevření hostitele služby a počkejte, dokud uživatel stiskne klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="48997-125">Open the service host and wait until the user presses ENTER.</span></span>  
  
     [!code-csharp[htBasicService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]  
  
     <span data-ttu-id="48997-126">Tento příklad ukazuje, jak hostování stylu webové služby pomocí konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="48997-126">This sample demonstrates how to host a Web-Style service with a console application.</span></span> <span data-ttu-id="48997-127">Můžete taky hostitele služby v rámci služby IIS.</span><span class="sxs-lookup"><span data-stu-id="48997-127">You can also host such a service within IIS.</span></span> <span data-ttu-id="48997-128">Chcete-li to provést, zadejte <xref:System.ServiceModel.Activation.WebServiceHostFactory> třídy v souboru .svc, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="48997-128">To do this, specify the <xref:System.ServiceModel.Activation.WebServiceHostFactory> class in a .svc file as the following code demonstrates.</span></span>  
  
    ```  
          <%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Samples.Service"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory%>  
    ```  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="48997-129">K volání operací služby namapované na GET v Internet Exploreru</span><span class="sxs-lookup"><span data-stu-id="48997-129">To call service operations mapped to GET in Internet Explorer</span></span>  
  
1.  <span data-ttu-id="48997-130">Otevřete Internet Explorer a zadejte "`http://localhost:8000/EchoWithGet?s=Hello, world!`" a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="48997-130">Open Internet Explorer and type "`http://localhost:8000/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="48997-131">Adresa URL obsahuje základní adresa služby ("http://localhost: 8000 /"), relativní adresa koncového bodu (""), operace služby k volání ("EchoWithGet") a otazník následuje seznam pojmenované parametry oddělených ampersandem (&).</span><span class="sxs-lookup"><span data-stu-id="48997-131">The URL contains the base address of the service ("http://localhost:8000/"), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>  
  
### <a name="to-call-service-operations-in-code"></a><span data-ttu-id="48997-132">K volání operací služby v kódu</span><span class="sxs-lookup"><span data-stu-id="48997-132">To call service operations in code</span></span>  
  
1.  <span data-ttu-id="48997-133">Vytvoření instance <!--zz <xref:System.ServiceModel.Web.WebChannelFactory>--> `System.ServiceModel.Web.WebChannelFactory` v rámci `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="48997-133">Create an instance of <!--zz <xref:System.ServiceModel.Web.WebChannelFactory>--> `System.ServiceModel.Web.WebChannelFactory` within a `using` block.</span></span>  
  
     [!code-csharp[htBasicService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]  
  
2.  <span data-ttu-id="48997-134">Přidat <xref:System.ServiceModel.Description.WebHttpBehavior> ke koncovému bodu <xref:System.ServiceModel.ChannelFactory> volání.</span><span class="sxs-lookup"><span data-stu-id="48997-134">Add <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint the <xref:System.ServiceModel.ChannelFactory> calls.</span></span>  
  
     [!code-csharp[htBasicService#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]  
  
3.  <span data-ttu-id="48997-135">Vytvoření kanálu a volání služby.</span><span class="sxs-lookup"><span data-stu-id="48997-135">Create the channel and call the service.</span></span>  
  
     [!code-csharp[htBasicService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]  
  
4.  <span data-ttu-id="48997-136">Zavřít <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="48997-136">Close the <xref:System.ServiceModel.Web.WebServiceHost>.</span></span>  
  
     [!code-csharp[htBasicService#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="48997-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="48997-137">Example</span></span>  
 <span data-ttu-id="48997-138">Zde je úplný výpis pro tento příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="48997-138">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htBasicService#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
 [!code-vb[htBasicService#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="48997-139">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="48997-139">Compiling the Code</span></span>  
 <span data-ttu-id="48997-140">Při kompilování Service.cs odkaz System.ServiceModel.dll a System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="48997-140">When compiling Service.cs reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48997-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="48997-141">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="48997-142">Model programování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="48997-142">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
