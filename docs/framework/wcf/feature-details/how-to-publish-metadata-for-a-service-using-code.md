---
title: 'Postupy: Publikování metadat služby promocí kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: 5f60bcdb02f61d39711115b07ba989229e39c28c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929131"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a><span data-ttu-id="c5b89-102">Postupy: Publikování metadat služby promocí kódu</span><span class="sxs-lookup"><span data-stu-id="c5b89-102">How to: Publish Metadata for a Service Using Code</span></span>
<span data-ttu-id="c5b89-103">Jedná se o jedno ze dvou témat s postupy, které popisují publikování metadat pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c5b89-103">This is one of two how-to topics that discuss publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="c5b89-104">Existují dva způsoby, jak zadat, jak má služba publikovat metadata, pomocí konfiguračního souboru a pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="c5b89-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="c5b89-105">V tomto tématu se dozvíte, jak publikovat metadata pro službu pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="c5b89-105">This topic shows how to publish metadata for a service using a code.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c5b89-106">V tomto tématu se dozvíte, jak publikovat metadata nezabezpečeným způsobem.</span><span class="sxs-lookup"><span data-stu-id="c5b89-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="c5b89-107">Každý klient může získat metadata ze služby.</span><span class="sxs-lookup"><span data-stu-id="c5b89-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="c5b89-108">Pokud vyžadujete, aby služba publikovala metadata zabezpečeným způsobem.</span><span class="sxs-lookup"><span data-stu-id="c5b89-108">If you require your service to publish metadata in a secure manner.</span></span> <span data-ttu-id="c5b89-109">viz [Vlastní zabezpečený koncový bod metadat](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="c5b89-109">see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="c5b89-110">Další informace o publikování metadat v konfiguračním souboru najdete v tématu [How to: Publikování metadat pro službu pomocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="c5b89-110">For more information about publishing metadata in a configuration file, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span> <span data-ttu-id="c5b89-111">Publikování metadat umožňuje klientům načíst metadata pomocí žádosti o WS-Transfer Get nebo požadavku HTTP/GET pomocí `?wsdl` řetězce dotazu.</span><span class="sxs-lookup"><span data-stu-id="c5b89-111">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="c5b89-112">Abyste měli jistotu, že kód pracuje, musíte vytvořit základní službu WCF.</span><span class="sxs-lookup"><span data-stu-id="c5b89-112">To be sure that the code is working you must create a basic WCF service.</span></span> <span data-ttu-id="c5b89-113">Základní Samoobslužná služba je k dispozici v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="c5b89-113">A basic self-hosted service is provided in the following code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a><span data-ttu-id="c5b89-114">Publikování metadat v kódu</span><span class="sxs-lookup"><span data-stu-id="c5b89-114">To publish metadata in code</span></span>  
  
1. <span data-ttu-id="c5b89-115">V rámci metody Main aplikace konzoly vytvořte instanci <xref:System.ServiceModel.ServiceHost> objektu předáním typu služby a základní adresy.</span><span class="sxs-lookup"><span data-stu-id="c5b89-115">Within the main method of a console application, instantiate a <xref:System.ServiceModel.ServiceHost> object by passing in the service type and the base address.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. <span data-ttu-id="c5b89-116">Vytvořte blok try hned pod kódem pro krok 1, zachytí všechny výjimky, které se vyvolaly, když je služba spuštěná.</span><span class="sxs-lookup"><span data-stu-id="c5b89-116">Create a try block immediately below the code for step 1, this catches any exceptions that get thrown while the service is running.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. <span data-ttu-id="c5b89-117">Zkontrolujte, zda hostitel služby již obsahuje <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, a v případě potřeby vytvořte novou <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instanci.</span><span class="sxs-lookup"><span data-stu-id="c5b89-117">Check to see whether the service host already contains a <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, if not, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. <span data-ttu-id="c5b89-118"><xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> Nastavte vlastnost na`true.`</span><span class="sxs-lookup"><span data-stu-id="c5b89-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true.`</span></span>  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. <span data-ttu-id="c5b89-119"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> Obsahuje<xref:System.ServiceModel.Description.MetadataExporter> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c5b89-119">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contains a <xref:System.ServiceModel.Description.MetadataExporter> property.</span></span> <span data-ttu-id="c5b89-120"><xref:System.ServiceModel.Description.MetadataExporter> Obsahuje<xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c5b89-120">The <xref:System.ServiceModel.Description.MetadataExporter> contains a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property.</span></span> <span data-ttu-id="c5b89-121">Nastavte hodnotu <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnosti na <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span><span class="sxs-lookup"><span data-stu-id="c5b89-121">Set the value of the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span></span> <span data-ttu-id="c5b89-122">Vlastnost lze také nastavit na <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>hodnotu. <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A></span><span class="sxs-lookup"><span data-stu-id="c5b89-122">The <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property can also be set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span></span> <span data-ttu-id="c5b89-123">Když je nastaveno <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> na Exportér metadat, vygeneruje informace o zásadách s metadaty, která odpovídá protokolu WS-Policy 1,5.</span><span class="sxs-lookup"><span data-stu-id="c5b89-123">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> the metadata exporter generates policy information with the metadata that" conforms to WS-Policy 1.5.</span></span> <span data-ttu-id="c5b89-124">Když se nastaví <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> na Exportér metadat, vygeneruje informace o zásadách, které odpovídají WS-Policy 1,2.</span><span class="sxs-lookup"><span data-stu-id="c5b89-124">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> the metadata exporter generates policy information that conforms to WS-Policy 1.2.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. <span data-ttu-id="c5b89-125"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> Přidejte instanci do kolekce chování hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="c5b89-125">Add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance to the service host's behaviors collection.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. <span data-ttu-id="c5b89-126">Přidejte koncový bod výměny metadat do hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="c5b89-126">Add the metadata exchange endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. <span data-ttu-id="c5b89-127">Přidejte koncový bod aplikace do hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="c5b89-127">Add an application endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    > <span data-ttu-id="c5b89-128">Pokud do služby nepřidáte žádné koncové body, modul runtime přidá pro vás výchozí koncové body.</span><span class="sxs-lookup"><span data-stu-id="c5b89-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="c5b89-129">V tomto příkladu, protože je služba <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nastavená na `true`, služba má povolená metadata publikování.</span><span class="sxs-lookup"><span data-stu-id="c5b89-129">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, the service has publishing metadata enabled.</span></span> <span data-ttu-id="c5b89-130">Další informace o výchozích koncových bodech najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c5b89-130">For more information about default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="c5b89-131">Otevřete hostitele služby a počkejte na příchozí volání.</span><span class="sxs-lookup"><span data-stu-id="c5b89-131">Open the service host and wait for incoming calls.</span></span> <span data-ttu-id="c5b89-132">Když uživatel stiskne klávesu ENTER, uzavřete hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="c5b89-132">When the user presses ENTER, close the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. <span data-ttu-id="c5b89-133">Vytvořte a spusťte konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c5b89-133">Build and run the console application.</span></span>  
  
11. <span data-ttu-id="c5b89-134">Pomocí Internet Exploreru přejděte na základní adresu služby (http://localhost:8001/MetadataSample v této ukázce) a ověřte, jestli je zapnuté publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="c5b89-134">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="c5b89-135">Měla by se zobrazit webová stránka, která uvádí "jednoduchá služba" na začátku a hned pod "jste vytvořili službu."</span><span class="sxs-lookup"><span data-stu-id="c5b89-135">You should see a Web page displayed that says "Simple Service" at the top and immediately below "You have created a service."</span></span> <span data-ttu-id="c5b89-136">V takovém případě se zobrazí zpráva v horní části výsledné stránky: "Publikování metadat pro tuto službu je momentálně zakázané."</span><span class="sxs-lookup"><span data-stu-id="c5b89-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5b89-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5b89-137">Example</span></span>  
 <span data-ttu-id="c5b89-138">Následující příklad kódu ukazuje implementaci základní služby WCF, která publikuje metadata pro službu v kódu.</span><span class="sxs-lookup"><span data-stu-id="c5b89-138">The following code example shows the implementation of a basic WCF service that publishes metadata for the service in code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="c5b89-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5b89-139">See also</span></span>

- [<span data-ttu-id="c5b89-140">Postupy: Hostování služby WCF ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="c5b89-140">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="c5b89-141">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="c5b89-141">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="c5b89-142">Přehled architektury metadat</span><span class="sxs-lookup"><span data-stu-id="c5b89-142">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="c5b89-143">Používání metadat</span><span class="sxs-lookup"><span data-stu-id="c5b89-143">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="c5b89-144">Postupy: Publikování metadat pro službu pomocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c5b89-144">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
