---
title: 'Postupy: Zveřejnění kontraktu klientům SOAP a webovým klientům'
description: Naučte se, jak zpřístupnit koncový bod serveru WFC pro klienty SOAP i non-SOAP. Ve výchozím nastavení jsou koncové body k dispozici pouze klientům SOAP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: b1bdb7af51e0e2795c36865058fbeb34a716e3e2
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246971"
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a><span data-ttu-id="5c8f5-104">Postupy: Zveřejnění kontraktu klientům SOAP a webovým klientům</span><span class="sxs-lookup"><span data-stu-id="5c8f5-104">How to: Expose a Contract to SOAP and Web Clients</span></span>

<span data-ttu-id="5c8f5-105">Ve výchozím nastavení služba Windows Communication Foundation (WCF) zpřístupňuje koncové body pouze klientům SOAP.</span><span class="sxs-lookup"><span data-stu-id="5c8f5-105">By default, Windows Communication Foundation (WCF) makes endpoints available only to SOAP clients.</span></span> <span data-ttu-id="5c8f5-106">V tématu [Postupy: Vytvoření základní webové služby HTTP WCF](how-to-create-a-basic-wcf-web-http-service.md)je koncový bod zpřístupněn klientům bez protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="5c8f5-106">In [How to: Create a Basic WCF Web HTTP Service](how-to-create-a-basic-wcf-web-http-service.md), an endpoint is made available to non-SOAP clients.</span></span> <span data-ttu-id="5c8f5-107">Může nastat situace, kdy budete chtít, aby stejný kontrakt byl dostupný jak jako koncový bod, tak jako koncový bod SOAP.</span><span class="sxs-lookup"><span data-stu-id="5c8f5-107">There may be times when you want to make the same contract available both ways, as a Web endpoint and as a SOAP endpoint.</span></span> <span data-ttu-id="5c8f5-108">Toto téma ukazuje příklad toho, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="5c8f5-108">This topic shows an example of how to do this.</span></span>

## <a name="to-define-the-service-contract"></a><span data-ttu-id="5c8f5-109">Definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="5c8f5-109">To define the service contract</span></span>

1. <span data-ttu-id="5c8f5-110">Definujte kontrakt služby pomocí rozhraní označeného <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> <xref:System.ServiceModel.Web.WebGetAttribute> atributem a, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="5c8f5-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes, as shown in the following code:</span></span>

    [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
    [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="5c8f5-111">Ve výchozím nastavení <xref:System.ServiceModel.Web.WebInvokeAttribute> namapuje volání post na operaci.</span><span class="sxs-lookup"><span data-stu-id="5c8f5-111">By default <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="5c8f5-112">Můžete však zadat metodu pro mapování na operaci zadáním parametru "Method =".</span><span class="sxs-lookup"><span data-stu-id="5c8f5-112">You can, however, specify the method to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="5c8f5-113"><xref:System.ServiceModel.Web.WebGetAttribute>nemá parametr "Method =" a pouze mapuje volání GET na operaci služby.</span><span class="sxs-lookup"><span data-stu-id="5c8f5-113"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="5c8f5-114">Implementujte kontrakt služby, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="5c8f5-114">Implement the service contract, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="5c8f5-115">Hostování služby</span><span class="sxs-lookup"><span data-stu-id="5c8f5-115">To host the service</span></span>

1. <span data-ttu-id="5c8f5-116">Vytvořte <xref:System.ServiceModel.ServiceHost> objekt, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="5c8f5-116">Create a <xref:System.ServiceModel.ServiceHost> object, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]

2. <span data-ttu-id="5c8f5-117">Přidejte objekt <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> pro koncový bod SOAP, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="5c8f5-117">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> for the SOAP endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]

3. <span data-ttu-id="5c8f5-118">Přidejte objekt <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> pro koncový bod bez SOAP a přidejte <xref:System.ServiceModel.Description.WebHttpBehavior> ho do koncového bodu, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="5c8f5-118">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> for the non-SOAP endpoint and add the <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]

4. <span data-ttu-id="5c8f5-119">Zavolejte `Open()` na <xref:System.ServiceModel.ServiceHost> instanci pro otevření hostitele služby, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="5c8f5-119">Call `Open()` on a <xref:System.ServiceModel.ServiceHost> instance to open the service host, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="5c8f5-120">Volání operací služby mapovaných na získání v aplikaci Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="5c8f5-120">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="5c8f5-121">Spusťte Internet Explorer a zadejte " `http://localhost:8000/Web/EchoWithGet?s=Hello, world!` " a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="5c8f5-121">Open Internet Explorer and type "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="5c8f5-122">Adresa URL obsahuje základní adresu služby ( `http://localhost:8000/` ), relativní adresu koncového bodu (""), volanou operaci služby ("EchoWithGet") a otazník následovaný seznamem pojmenovaných parametrů oddělených ampersandem (&).</span><span class="sxs-lookup"><span data-stu-id="5c8f5-122">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a><span data-ttu-id="5c8f5-123">Volání operací služby na koncovém bodu webu v kódu</span><span class="sxs-lookup"><span data-stu-id="5c8f5-123">To call service operations on the Web endpoint in code</span></span>

1. <span data-ttu-id="5c8f5-124">Vytvořte instanci <xref:System.ServiceModel.Web.WebChannelFactory%601> v rámci `using` bloku, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5c8f5-124">Create an instance of <xref:System.ServiceModel.Web.WebChannelFactory%601> within a `using` block, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]

> [!NOTE]
> <span data-ttu-id="5c8f5-125">`Close()`se automaticky volá na kanálu na konci `using` bloku.</span><span class="sxs-lookup"><span data-stu-id="5c8f5-125">`Close()` is automatically called on the channel at the end of the `using` block.</span></span>

1. <span data-ttu-id="5c8f5-126">Vytvořte kanál a zavolejte službu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5c8f5-126">Create the channel and call the service, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]

## <a name="to-call-service-operations-on-the-soap-endpoint"></a><span data-ttu-id="5c8f5-127">Volání operací služby na koncovém bodu SOAP</span><span class="sxs-lookup"><span data-stu-id="5c8f5-127">To call service operations on the SOAP endpoint</span></span>

1. <span data-ttu-id="5c8f5-128">Vytvořte instanci <xref:System.ServiceModel.ChannelFactory> v rámci `using` bloku, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5c8f5-128">Create an instance of <xref:System.ServiceModel.ChannelFactory> within a `using` block, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
    [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]

2. <span data-ttu-id="5c8f5-129">Vytvořte kanál a zavolejte službu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5c8f5-129">Create the channel and call the service, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
    [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]

## <a name="to-close-the-service-host"></a><span data-ttu-id="5c8f5-130">Zavření hostitele služby</span><span class="sxs-lookup"><span data-stu-id="5c8f5-130">To close the service host</span></span>

1. <span data-ttu-id="5c8f5-131">Ukončete hostitele služby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5c8f5-131">Close the service host, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
    [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]

## <a name="example"></a><span data-ttu-id="5c8f5-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c8f5-132">Example</span></span>

<span data-ttu-id="5c8f5-133">V následujícím seznamu je uveden úplný výpis kódu pro toto téma:</span><span class="sxs-lookup"><span data-stu-id="5c8f5-133">The following is the full code listing for this topic:</span></span>

[!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
[!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]

## <a name="compiling-the-code"></a><span data-ttu-id="5c8f5-134">Zkompilování kódu</span><span class="sxs-lookup"><span data-stu-id="5c8f5-134">Compiling the code</span></span>

 <span data-ttu-id="5c8f5-135">Při kompilaci Service.cs, referenční System.ServiceModel.dll a System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="5c8f5-135">When compiling Service.cs, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c8f5-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c8f5-136">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.ChannelFactory>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="5c8f5-137">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="5c8f5-137">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
