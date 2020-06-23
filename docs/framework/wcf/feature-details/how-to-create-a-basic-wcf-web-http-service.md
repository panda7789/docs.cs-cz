---
title: 'Postupy: Vytvoření základní webové služby HTTP WCF'
description: Naučte se vytvořit službu, která zveřejňuje webový koncový bod ve službě WCF. Webové koncové body odesílají data pomocí XML nebo JSON. Není k dispozici žádná obálka SOAP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: 7481367f27d973ba809dff5ca1c4a4f168fbbb98
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247101"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a><span data-ttu-id="61fc9-105">Postupy: Vytvoření základní webové služby HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="61fc9-105">How to: Create a Basic WCF Web HTTP Service</span></span>

<span data-ttu-id="61fc9-106">Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje webový koncový bod.</span><span class="sxs-lookup"><span data-stu-id="61fc9-106">Windows Communication Foundation (WCF) allows you to create a service that exposes a Web endpoint.</span></span> <span data-ttu-id="61fc9-107">Webové koncové body odesílají data pomocí kódu XML nebo JSON, ale není k dispozici žádná obálka SOAP.</span><span class="sxs-lookup"><span data-stu-id="61fc9-107">Web endpoints send data by XML or JSON, there is no SOAP envelope.</span></span> <span data-ttu-id="61fc9-108">Toto téma ukazuje, jak vystavit takový koncový bod.</span><span class="sxs-lookup"><span data-stu-id="61fc9-108">This topic demonstrates how to expose such an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="61fc9-109">Jediným způsobem, jak zajistit zabezpečení webového koncového bodu, je jeho zpřístupnění prostřednictvím protokolu HTTPS pomocí zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="61fc9-109">The only way to secure a Web endpoint is to expose it through HTTPS, using transport security.</span></span> <span data-ttu-id="61fc9-110">Při použití zabezpečení založeného na zprávách jsou informace o zabezpečení obvykle umístěny v hlavičkách SOAP a protože zprávy odeslané koncovým bodům bez protokolu SOAP neobsahují žádnou obálku SOAP, je nikde umístit informace o zabezpečení a musíte spoléhat na zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="61fc9-110">When using message-based security, security information is usually placed in SOAP headers and because the messages sent to non-SOAP endpoints contain no SOAP envelope, there is nowhere to place the security information and you must rely on transport security.</span></span>

## <a name="to-create-a-web-endpoint"></a><span data-ttu-id="61fc9-111">Vytvoření webového koncového bodu</span><span class="sxs-lookup"><span data-stu-id="61fc9-111">To create a Web endpoint</span></span>

1. <span data-ttu-id="61fc9-112">Definujte kontrakt služby pomocí rozhraní označeného <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> <xref:System.ServiceModel.Web.WebGetAttribute> atributem a.</span><span class="sxs-lookup"><span data-stu-id="61fc9-112">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes.</span></span>

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="61fc9-113">Ve výchozím nastavení <xref:System.ServiceModel.Web.WebInvokeAttribute> MAPUJE post volání operace.</span><span class="sxs-lookup"><span data-stu-id="61fc9-113">By default, <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="61fc9-114">Můžete však zadat metodu HTTP (například HEAD, PUT nebo DELETE) k mapování na operaci zadáním parametru "Method =".</span><span class="sxs-lookup"><span data-stu-id="61fc9-114">You can, however, specify the HTTP method (for example, HEAD, PUT, or DELETE) to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="61fc9-115"><xref:System.ServiceModel.Web.WebGetAttribute>nemá parametr "Method =" a pouze mapuje volání GET na operaci služby.</span><span class="sxs-lookup"><span data-stu-id="61fc9-115"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="61fc9-116">Implementujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="61fc9-116">Implement the service contract.</span></span>

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="61fc9-117">Hostování služby</span><span class="sxs-lookup"><span data-stu-id="61fc9-117">To host the service</span></span>

1. <span data-ttu-id="61fc9-118">Vytvořte <xref:System.ServiceModel.Web.WebServiceHost> objekt.</span><span class="sxs-lookup"><span data-stu-id="61fc9-118">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. <span data-ttu-id="61fc9-119">Přidejte <xref:System.ServiceModel.Description.ServiceEndpoint> s <xref:System.ServiceModel.Description.WebHttpBehavior> .</span><span class="sxs-lookup"><span data-stu-id="61fc9-119">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > <span data-ttu-id="61fc9-120">Pokud koncový bod nepřidáte, <xref:System.ServiceModel.Web.WebServiceHost> automaticky vytvoří výchozí koncový bod.</span><span class="sxs-lookup"><span data-stu-id="61fc9-120">If you do not add an endpoint, <xref:System.ServiceModel.Web.WebServiceHost> automatically creates a default endpoint.</span></span> <span data-ttu-id="61fc9-121"><xref:System.ServiceModel.Web.WebServiceHost>také přidá <xref:System.ServiceModel.Description.WebHttpBehavior> a zakáže stránku Nápověda http a funkci get jazyka WSDL (Web Services Description Language), takže koncový bod metadat nekoliduje s výchozím koncovým bodem http.</span><span class="sxs-lookup"><span data-stu-id="61fc9-121"><xref:System.ServiceModel.Web.WebServiceHost> also adds <xref:System.ServiceModel.Description.WebHttpBehavior> and disables the HTTP Help page and the Web Services Description Language (WSDL) GET functionality so the metadata endpoint does not interfere with the default HTTP endpoint.</span></span>
    >
    >  <span data-ttu-id="61fc9-122">Přidání koncového bodu bez protokolu SOAP s adresou URL "" způsobí neočekávané chování při pokusu o volání operace na koncovém bodu.</span><span class="sxs-lookup"><span data-stu-id="61fc9-122">Adding a non-SOAP endpoint with a URL of "" causes unexpected behavior when an attempt is made to call an operation on the endpoint.</span></span> <span data-ttu-id="61fc9-123">Důvodem je, že identifikátor URI příposlechu koncového bodu je stejný jako identifikátor URI stránky s nápovědu (stránka, která se zobrazí při procházení k základní adrese služby WCF).</span><span class="sxs-lookup"><span data-stu-id="61fc9-123">The reason for this is the listen URI of the endpoint is the same as the URI for the help page (the page that is displayed when you browse to the base address of a WCF service).</span></span>

     <span data-ttu-id="61fc9-124">K tomu, abyste zabránili tomu, můžete provést jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="61fc9-124">You can do one of the following actions to prevent this from happening:</span></span>

    - <span data-ttu-id="61fc9-125">Vždy zadejte neprázdný identifikátor URI pro koncový bod, který není typu SOAP.</span><span class="sxs-lookup"><span data-stu-id="61fc9-125">Always specify a non-blank URI for a non-SOAP endpoint.</span></span>

    - <span data-ttu-id="61fc9-126">Vypněte stránku s usnadněním.</span><span class="sxs-lookup"><span data-stu-id="61fc9-126">Turn off the help page.</span></span> <span data-ttu-id="61fc9-127">To lze provést pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="61fc9-127">This can be done with the following code:</span></span>

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. <span data-ttu-id="61fc9-128">Otevřete hostitele služby a počkejte, dokud uživatel nestiskne klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="61fc9-128">Open the service host and wait until the user presses ENTER.</span></span>

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     <span data-ttu-id="61fc9-129">Tato ukázka předvádí, jak hostovat službu webového stylu pomocí konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="61fc9-129">This sample demonstrates how to host a Web-Style service with a console application.</span></span> <span data-ttu-id="61fc9-130">Takovou službu můžete hostovat i v rámci služby IIS.</span><span class="sxs-lookup"><span data-stu-id="61fc9-130">You can also host such a service within IIS.</span></span> <span data-ttu-id="61fc9-131">Provedete to tak, že zadáte <xref:System.ServiceModel.Activation.WebServiceHostFactory> třídu v souboru. svc, jak ukazuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="61fc9-131">To do this, specify the <xref:System.ServiceModel.Activation.WebServiceHostFactory> class in a .svc file as the following code demonstrates.</span></span>

    ```text
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="61fc9-132">Volání operací služby mapovaných na získání v aplikaci Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="61fc9-132">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="61fc9-133">Spusťte Internet Explorer a zadejte " `http://localhost:8000/EchoWithGet?s=Hello, world!` " a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="61fc9-133">Open Internet Explorer and type "`http://localhost:8000/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="61fc9-134">Adresa URL obsahuje základní adresu služby ( `http://localhost:8000/` ), relativní adresu koncového bodu (""), volanou operaci služby ("EchoWithGet") a otazník následovaný seznamem pojmenovaných parametrů oddělených ampersandem (&).</span><span class="sxs-lookup"><span data-stu-id="61fc9-134">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-in-code"></a><span data-ttu-id="61fc9-135">Volání operací služby v kódu</span><span class="sxs-lookup"><span data-stu-id="61fc9-135">To call service operations in code</span></span>

1. <span data-ttu-id="61fc9-136">Vytvoří instanci <xref:System.ServiceModel.ChannelFactory%601> v rámci `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="61fc9-136">Create an instance of <xref:System.ServiceModel.ChannelFactory%601> within a `using` block.</span></span>

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. <span data-ttu-id="61fc9-137">Přidejte <xref:System.ServiceModel.Description.WebHttpBehavior> do koncového bodu <xref:System.ServiceModel.ChannelFactory%601> volání.</span><span class="sxs-lookup"><span data-stu-id="61fc9-137">Add <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint the <xref:System.ServiceModel.ChannelFactory%601> calls.</span></span>

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. <span data-ttu-id="61fc9-138">Vytvořte kanál a zavolejte službu.</span><span class="sxs-lookup"><span data-stu-id="61fc9-138">Create the channel and call the service.</span></span>

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. <span data-ttu-id="61fc9-139">Zavřete <xref:System.ServiceModel.Web.WebServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="61fc9-139">Close the <xref:System.ServiceModel.Web.WebServiceHost>.</span></span>

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a><span data-ttu-id="61fc9-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="61fc9-140">Example</span></span>

<span data-ttu-id="61fc9-141">Následuje úplný výpis kódu pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="61fc9-141">The following is the full code listing for this example.</span></span>

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a><span data-ttu-id="61fc9-142">Zkompilování kódu</span><span class="sxs-lookup"><span data-stu-id="61fc9-142">Compiling the code</span></span>

<span data-ttu-id="61fc9-143">Při kompilování Service.cs referenčních System.ServiceModel.dll a System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="61fc9-143">When compiling Service.cs reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="61fc9-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="61fc9-144">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="61fc9-145">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="61fc9-145">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
