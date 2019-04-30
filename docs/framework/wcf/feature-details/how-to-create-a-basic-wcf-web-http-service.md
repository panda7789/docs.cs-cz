---
title: 'Postupy: Vytvoření základní webové služby HTTP WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: 1b76d21cb4f416aae76e7597ad16cfd45e5b7cad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779194"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a><span data-ttu-id="3cf79-102">Postupy: Vytvoření základní webové služby HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="3cf79-102">How to: Create a Basic WCF Web HTTP Service</span></span>

<span data-ttu-id="3cf79-103">Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje webový koncový bod.</span><span class="sxs-lookup"><span data-stu-id="3cf79-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a Web endpoint.</span></span> <span data-ttu-id="3cf79-104">Koncové body webové odesílat data XML nebo JSON, neexistuje žádný obálku protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="3cf79-104">Web endpoints send data by XML or JSON, there is no SOAP envelope.</span></span> <span data-ttu-id="3cf79-105">Toto téma ukazuje, jak vystavit takové koncový bod.</span><span class="sxs-lookup"><span data-stu-id="3cf79-105">This topic demonstrates how to expose such an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="3cf79-106">Jediný způsob, jak zabezpečit webový koncový bod je zveřejnit přes HTTPS pomocí zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="3cf79-106">The only way to secure a Web endpoint is to expose it through HTTPS, using transport security.</span></span> <span data-ttu-id="3cf79-107">Při použití zabezpečení na základě zpráv, informace o zabezpečení obvykle umístěny v záhlaví SOAP a protože zprávy odeslané do koncových bodů protokolu SOAP obsahovat žádné obálku protokolu SOAP, není nikde umístit informace o zabezpečení a musíte spoléhat na zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="3cf79-107">When using message-based security, security information is usually placed in SOAP headers and because the messages sent to non-SOAP endpoints contain no SOAP envelope, there is nowhere to place the security information and you must rely on transport security.</span></span>

## <a name="to-create-a-web-endpoint"></a><span data-ttu-id="3cf79-108">Chcete-li vytvořit webový koncový bod</span><span class="sxs-lookup"><span data-stu-id="3cf79-108">To create a Web endpoint</span></span>

1. <span data-ttu-id="3cf79-109">Definování kontraktu služby pomocí rozhraní označené <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> a <xref:System.ServiceModel.Web.WebGetAttribute> atributy.</span><span class="sxs-lookup"><span data-stu-id="3cf79-109">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes.</span></span>

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="3cf79-110">Ve výchozím nastavení <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje příspěvek volání operace.</span><span class="sxs-lookup"><span data-stu-id="3cf79-110">By default, <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="3cf79-111">Můžete však určit metodu HTTP (například HEAD, PUT nebo DELETE) pro mapování na operaci zadáním "metoda =" parametr.</span><span class="sxs-lookup"><span data-stu-id="3cf79-111">You can, however, specify the HTTP method (for example, HEAD, PUT, or DELETE) to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="3cf79-112"><xref:System.ServiceModel.Web.WebGetAttribute> nemá "metoda =" parametr a jen mapy GET volání operace služby.</span><span class="sxs-lookup"><span data-stu-id="3cf79-112"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="3cf79-113">Implementace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="3cf79-113">Implement the service contract.</span></span>

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="3cf79-114">K hostování služby</span><span class="sxs-lookup"><span data-stu-id="3cf79-114">To host the service</span></span>

1. <span data-ttu-id="3cf79-115">Vytvoření <xref:System.ServiceModel.Web.WebServiceHost> objektu.</span><span class="sxs-lookup"><span data-stu-id="3cf79-115">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. <span data-ttu-id="3cf79-116">Přidat <xref:System.ServiceModel.Description.ServiceEndpoint> s <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="3cf79-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > <span data-ttu-id="3cf79-117">Pokud nemůžete přidat koncový bod, <xref:System.ServiceModel.Web.WebServiceHost> automaticky vytvoří výchozí koncový bod.</span><span class="sxs-lookup"><span data-stu-id="3cf79-117">If you do not add an endpoint, <xref:System.ServiceModel.Web.WebServiceHost> automatically creates a default endpoint.</span></span> <span data-ttu-id="3cf79-118"><xref:System.ServiceModel.Web.WebServiceHost> také přidá <xref:System.ServiceModel.Description.WebHttpBehavior> a zakáže stránky s nápovědou HTTP a funkci GET webové služby WSDL (Description Language), takže koncový bod metadat nebude v konfliktu s výchozí koncový bod HTTP.</span><span class="sxs-lookup"><span data-stu-id="3cf79-118"><xref:System.ServiceModel.Web.WebServiceHost> also adds <xref:System.ServiceModel.Description.WebHttpBehavior> and disables the HTTP Help page and the Web Services Description Language (WSDL) GET functionality so the metadata endpoint does not interfere with the default HTTP endpoint.</span></span>
    >
    >  <span data-ttu-id="3cf79-119">Přidat koncový bod-protokolu SOAP s adresou URL "" způsobí neočekávané chování při pokusu o volání operace v koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="3cf79-119">Adding a non-SOAP endpoint with a URL of "" causes unexpected behavior when an attempt is made to call an operation on the endpoint.</span></span> <span data-ttu-id="3cf79-120">Důvodem je listen URI koncového bodu je stejný jako identifikátor URI na stránce nápovědy (stránka, která se zobrazí, když přejdete na základní adresa služby WCF).</span><span class="sxs-lookup"><span data-stu-id="3cf79-120">The reason for this is the listen URI of the endpoint is the same as the URI for the help page (the page that is displayed when you browse to the base address of a WCF service).</span></span>

     <span data-ttu-id="3cf79-121">Můžete provést jednu z následujících akcí k tomu nedocházelo:</span><span class="sxs-lookup"><span data-stu-id="3cf79-121">You can do one of the following actions to prevent this from happening:</span></span>

    - <span data-ttu-id="3cf79-122">Vždycky zadejte neprázdný identifikátor URI pro koncový bod-protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="3cf79-122">Always specify a non-blank URI for a non-SOAP endpoint.</span></span>

    - <span data-ttu-id="3cf79-123">Vypněte stránky s nápovědou.</span><span class="sxs-lookup"><span data-stu-id="3cf79-123">Turn off the help page.</span></span> <span data-ttu-id="3cf79-124">To lze provést následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="3cf79-124">This can be done with the following code:</span></span>

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. <span data-ttu-id="3cf79-125">Otevření hostitele služby a počkejte, až uživatel stiskne klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="3cf79-125">Open the service host and wait until the user presses ENTER.</span></span>

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     <span data-ttu-id="3cf79-126">Tento příklad ukazuje, jak hostování stylu webové služby pomocí konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="3cf79-126">This sample demonstrates how to host a Web-Style service with a console application.</span></span> <span data-ttu-id="3cf79-127">Také můžete hostovat služby, v rámci služby IIS.</span><span class="sxs-lookup"><span data-stu-id="3cf79-127">You can also host such a service within IIS.</span></span> <span data-ttu-id="3cf79-128">Chcete-li to provést, zadejte <xref:System.ServiceModel.Activation.WebServiceHostFactory> třídy v souboru SVC, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="3cf79-128">To do this, specify the <xref:System.ServiceModel.Activation.WebServiceHostFactory> class in a .svc file as the following code demonstrates.</span></span>

    ```
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="3cf79-129">K volání operací služby namapované k získání přístupu v aplikaci Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="3cf79-129">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="3cf79-130">Otevřete aplikaci Internet Explorer a zadejte "`http://localhost:8000/EchoWithGet?s=Hello, world!`" a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="3cf79-130">Open Internet Explorer and type "`http://localhost:8000/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="3cf79-131">Adresa URL obsahuje základní adresa služby (`http://localhost:8000/`), relativní adresu koncového bodu (""), operace služby k volání ("EchoWithGet") a otazník následovaný seznamem pojmenovaných parametrů oddělených ampersandem (&).</span><span class="sxs-lookup"><span data-stu-id="3cf79-131">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-in-code"></a><span data-ttu-id="3cf79-132">K volání operací služby v kódu</span><span class="sxs-lookup"><span data-stu-id="3cf79-132">To call service operations in code</span></span>

1. <span data-ttu-id="3cf79-133">Vytvoření instance <xref:System.ServiceModel.ChannelFactory%601> v rámci `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="3cf79-133">Create an instance of <xref:System.ServiceModel.ChannelFactory%601> within a `using` block.</span></span>

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. <span data-ttu-id="3cf79-134">Přidat <xref:System.ServiceModel.Description.WebHttpBehavior> ke koncovému bodu <xref:System.ServiceModel.ChannelFactory%601> volání.</span><span class="sxs-lookup"><span data-stu-id="3cf79-134">Add <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint the <xref:System.ServiceModel.ChannelFactory%601> calls.</span></span>

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. <span data-ttu-id="3cf79-135">Vytvoření kanálu a volání služby.</span><span class="sxs-lookup"><span data-stu-id="3cf79-135">Create the channel and call the service.</span></span>

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. <span data-ttu-id="3cf79-136">Zavřít <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="3cf79-136">Close the <xref:System.ServiceModel.Web.WebServiceHost>.</span></span>

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a><span data-ttu-id="3cf79-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="3cf79-137">Example</span></span>

<span data-ttu-id="3cf79-138">Následuje úplný výpis v tomto příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="3cf79-138">The following is the full code listing for this example.</span></span>

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a><span data-ttu-id="3cf79-139">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="3cf79-139">Compiling the code</span></span>

<span data-ttu-id="3cf79-140">Při kompilaci Service.cs reference System.ServiceModel.dll a System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="3cf79-140">When compiling Service.cs reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="3cf79-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3cf79-141">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="3cf79-142">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="3cf79-142">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)