---
title: 'Postupy: Vytvoření základní webové služby HTTP WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: e9646235f9423f2a4df9cfe09a5e83a91dcdcace
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895187"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a><span data-ttu-id="d3676-102">Postupy: Vytvoření základní webové služby HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="d3676-102">How to: Create a Basic WCF Web HTTP Service</span></span>

<span data-ttu-id="d3676-103">Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje webový koncový bod.</span><span class="sxs-lookup"><span data-stu-id="d3676-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a Web endpoint.</span></span> <span data-ttu-id="d3676-104">Webové koncové body odesílají data pomocí kódu XML nebo JSON, ale není k dispozici žádná obálka SOAP.</span><span class="sxs-lookup"><span data-stu-id="d3676-104">Web endpoints send data by XML or JSON, there is no SOAP envelope.</span></span> <span data-ttu-id="d3676-105">Toto téma ukazuje, jak vystavit takový koncový bod.</span><span class="sxs-lookup"><span data-stu-id="d3676-105">This topic demonstrates how to expose such an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="d3676-106">Jediným způsobem, jak zajistit zabezpečení webového koncového bodu, je jeho zpřístupnění prostřednictvím protokolu HTTPS pomocí zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="d3676-106">The only way to secure a Web endpoint is to expose it through HTTPS, using transport security.</span></span> <span data-ttu-id="d3676-107">Při použití zabezpečení založeného na zprávách jsou informace o zabezpečení obvykle umístěny v hlavičkách SOAP a protože zprávy odeslané koncovým bodům bez protokolu SOAP neobsahují žádnou obálku SOAP, je nikde umístit informace o zabezpečení a musíte spoléhat na zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="d3676-107">When using message-based security, security information is usually placed in SOAP headers and because the messages sent to non-SOAP endpoints contain no SOAP envelope, there is nowhere to place the security information and you must rely on transport security.</span></span>

## <a name="to-create-a-web-endpoint"></a><span data-ttu-id="d3676-108">Vytvoření webového koncového bodu</span><span class="sxs-lookup"><span data-stu-id="d3676-108">To create a Web endpoint</span></span>

1. <span data-ttu-id="d3676-109">Definujte kontrakt služby pomocí rozhraní označeného <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> <xref:System.ServiceModel.Web.WebGetAttribute> atributem a.</span><span class="sxs-lookup"><span data-stu-id="d3676-109">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes.</span></span>

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="d3676-110">Ve výchozím nastavení <xref:System.ServiceModel.Web.WebInvokeAttribute> mapuje post volání operace.</span><span class="sxs-lookup"><span data-stu-id="d3676-110">By default, <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="d3676-111">Můžete však zadat metodu HTTP (například HEAD, PUT nebo DELETE) k mapování na operaci zadáním parametru "Method =".</span><span class="sxs-lookup"><span data-stu-id="d3676-111">You can, however, specify the HTTP method (for example, HEAD, PUT, or DELETE) to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="d3676-112"><xref:System.ServiceModel.Web.WebGetAttribute>nemá parametr "Method =" a pouze mapuje volání GET na operaci služby.</span><span class="sxs-lookup"><span data-stu-id="d3676-112"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="d3676-113">Implementujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="d3676-113">Implement the service contract.</span></span>

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="d3676-114">Hostování služby</span><span class="sxs-lookup"><span data-stu-id="d3676-114">To host the service</span></span>

1. <span data-ttu-id="d3676-115"><xref:System.ServiceModel.Web.WebServiceHost> Vytvořte objekt.</span><span class="sxs-lookup"><span data-stu-id="d3676-115">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. <span data-ttu-id="d3676-116"><xref:System.ServiceModel.Description.ServiceEndpoint> Přidejte<xref:System.ServiceModel.Description.WebHttpBehavior>s.</span><span class="sxs-lookup"><span data-stu-id="d3676-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > <span data-ttu-id="d3676-117">Pokud koncový bod nepřidáte, <xref:System.ServiceModel.Web.WebServiceHost> automaticky vytvoří výchozí koncový bod.</span><span class="sxs-lookup"><span data-stu-id="d3676-117">If you do not add an endpoint, <xref:System.ServiceModel.Web.WebServiceHost> automatically creates a default endpoint.</span></span> <span data-ttu-id="d3676-118"><xref:System.ServiceModel.Web.WebServiceHost>také přidá <xref:System.ServiceModel.Description.WebHttpBehavior> a zakáže stránku Nápověda http a funkci get jazyka WSDL (Web Services Description Language), takže koncový bod metadat nekoliduje s výchozím koncovým bodem http.</span><span class="sxs-lookup"><span data-stu-id="d3676-118"><xref:System.ServiceModel.Web.WebServiceHost> also adds <xref:System.ServiceModel.Description.WebHttpBehavior> and disables the HTTP Help page and the Web Services Description Language (WSDL) GET functionality so the metadata endpoint does not interfere with the default HTTP endpoint.</span></span>
    >
    >  <span data-ttu-id="d3676-119">Přidání koncového bodu bez protokolu SOAP s adresou URL "" způsobí neočekávané chování při pokusu o volání operace na koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="d3676-119">Adding a non-SOAP endpoint with a URL of "" causes unexpected behavior when an attempt is made to call an operation on the endpoint.</span></span> <span data-ttu-id="d3676-120">Důvodem je, že identifikátor URI příposlechu koncového bodu je stejný jako identifikátor URI stránky s nápovědu (stránka, která se zobrazí při procházení k základní adrese služby WCF).</span><span class="sxs-lookup"><span data-stu-id="d3676-120">The reason for this is the listen URI of the endpoint is the same as the URI for the help page (the page that is displayed when you browse to the base address of a WCF service).</span></span>

     <span data-ttu-id="d3676-121">K tomu, abyste zabránili tomu, můžete provést jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="d3676-121">You can do one of the following actions to prevent this from happening:</span></span>

    - <span data-ttu-id="d3676-122">Vždy zadejte neprázdný identifikátor URI pro koncový bod, který není typu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d3676-122">Always specify a non-blank URI for a non-SOAP endpoint.</span></span>

    - <span data-ttu-id="d3676-123">Vypněte stránku s usnadněním.</span><span class="sxs-lookup"><span data-stu-id="d3676-123">Turn off the help page.</span></span> <span data-ttu-id="d3676-124">To lze provést pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="d3676-124">This can be done with the following code:</span></span>

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. <span data-ttu-id="d3676-125">Otevřete hostitele služby a počkejte, dokud uživatel nestiskne klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="d3676-125">Open the service host and wait until the user presses ENTER.</span></span>

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     <span data-ttu-id="d3676-126">Tato ukázka předvádí, jak hostovat službu webového stylu pomocí konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="d3676-126">This sample demonstrates how to host a Web-Style service with a console application.</span></span> <span data-ttu-id="d3676-127">Takovou službu můžete hostovat i v rámci služby IIS.</span><span class="sxs-lookup"><span data-stu-id="d3676-127">You can also host such a service within IIS.</span></span> <span data-ttu-id="d3676-128">Provedete to tak, <xref:System.ServiceModel.Activation.WebServiceHostFactory> že zadáte třídu v souboru. svc, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="d3676-128">To do this, specify the <xref:System.ServiceModel.Activation.WebServiceHostFactory> class in a .svc file as the following code demonstrates.</span></span>

    ```text
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="d3676-129">Volání operací služby mapovaných na získání v aplikaci Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="d3676-129">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="d3676-130">Spusťte Internet Explorer a zadejte "`http://localhost:8000/EchoWithGet?s=Hello, world!`" a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="d3676-130">Open Internet Explorer and type "`http://localhost:8000/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="d3676-131">Adresa URL obsahuje základní adresu služby (`http://localhost:8000/`), relativní adresu koncového bodu (""), volanou operaci služby ("EchoWithGet") a otazník následovaný seznamem pojmenovaných parametrů oddělených ampersandem (&).</span><span class="sxs-lookup"><span data-stu-id="d3676-131">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-in-code"></a><span data-ttu-id="d3676-132">Volání operací služby v kódu</span><span class="sxs-lookup"><span data-stu-id="d3676-132">To call service operations in code</span></span>

1. <span data-ttu-id="d3676-133">Vytvoří instanci <xref:System.ServiceModel.ChannelFactory%601> `using` v rámci bloku.</span><span class="sxs-lookup"><span data-stu-id="d3676-133">Create an instance of <xref:System.ServiceModel.ChannelFactory%601> within a `using` block.</span></span>

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. <span data-ttu-id="d3676-134">Přidejte <xref:System.ServiceModel.Description.WebHttpBehavior> do<xref:System.ServiceModel.ChannelFactory%601> koncového bodu volání.</span><span class="sxs-lookup"><span data-stu-id="d3676-134">Add <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint the <xref:System.ServiceModel.ChannelFactory%601> calls.</span></span>

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. <span data-ttu-id="d3676-135">Vytvořte kanál a zavolejte službu.</span><span class="sxs-lookup"><span data-stu-id="d3676-135">Create the channel and call the service.</span></span>

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. <span data-ttu-id="d3676-136"><xref:System.ServiceModel.Web.WebServiceHost>Zavřete.</span><span class="sxs-lookup"><span data-stu-id="d3676-136">Close the <xref:System.ServiceModel.Web.WebServiceHost>.</span></span>

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a><span data-ttu-id="d3676-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3676-137">Example</span></span>

<span data-ttu-id="d3676-138">Následuje úplný výpis kódu pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="d3676-138">The following is the full code listing for this example.</span></span>

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a><span data-ttu-id="d3676-139">Kompilování kódu</span><span class="sxs-lookup"><span data-stu-id="d3676-139">Compiling the code</span></span>

<span data-ttu-id="d3676-140">Při kompilaci Service.cs reference System. ServiceModel. dll a System. ServiceModel. Web. dll.</span><span class="sxs-lookup"><span data-stu-id="d3676-140">When compiling Service.cs reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3676-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3676-141">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="d3676-142">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="d3676-142">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
