---
title: 'Postupy: Publikování metadat služby promocí kódu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: 870142724321629d6dbeccd4118b814283901776
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039127"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a><span data-ttu-id="c28a7-102">Postupy: Publikování metadat služby promocí kódu</span><span class="sxs-lookup"><span data-stu-id="c28a7-102">How to: Publish Metadata for a Service Using Code</span></span>
<span data-ttu-id="c28a7-103">Toto je jedna z dva postupy: témata, které popisují publikování metadat služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c28a7-103">This is one of two how-to topics that discuss publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="c28a7-104">Existují dva způsoby, jak určit, jak by měla služba publikování metadat, je používán konfigurační soubor a pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="c28a7-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="c28a7-105">Toto téma ukazuje, jak publikování metadat služby promocí kódu.</span><span class="sxs-lookup"><span data-stu-id="c28a7-105">This topic shows how to publish metadata for a service using a code.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c28a7-106">Toto téma ukazuje, jak měla být zveřejněna metadata nezabezpečené způsobem.</span><span class="sxs-lookup"><span data-stu-id="c28a7-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="c28a7-107">Jakýkoli klient může načíst metadata ze služby.</span><span class="sxs-lookup"><span data-stu-id="c28a7-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="c28a7-108">Pokud budete potřebovat vaše služba měla být zveřejněna metadata bezpečným způsobem.</span><span class="sxs-lookup"><span data-stu-id="c28a7-108">If you require your service to publish metadata in a secure manner.</span></span> <span data-ttu-id="c28a7-109">Zobrazit [koncový bod metadat zabezpečení vlastní](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="c28a7-109">see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="c28a7-110">Další informace o publikování metadat v konfiguračním souboru, naleznete v tématu [jak: Publikování metadat služby promocí konfiguračního souboru](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="c28a7-110">For more information about publishing metadata in a configuration file, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span> <span data-ttu-id="c28a7-111">Publikování metadat umožňuje klientům pro načtení metadat pomocí žádost o přenos WS získat nebo pomocí požadavku HTTP/GET `?wsdl` řetězec dotazu.</span><span class="sxs-lookup"><span data-stu-id="c28a7-111">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="c28a7-112">Ujistěte se, že kód funguje je nutné vytvořit základní služby WCF.</span><span class="sxs-lookup"><span data-stu-id="c28a7-112">To be sure that the code is working you must create a basic WCF service.</span></span> <span data-ttu-id="c28a7-113">Základní služba v místním prostředí je k dispozici v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="c28a7-113">A basic self-hosted service is provided in the following code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a><span data-ttu-id="c28a7-114">Publikování metadat v kódu</span><span class="sxs-lookup"><span data-stu-id="c28a7-114">To publish metadata in code</span></span>  
  
1. <span data-ttu-id="c28a7-115">V rámci metody main konzolové aplikace vytvořit instanci <xref:System.ServiceModel.ServiceHost> objekt předáním typ služby a základní adresa.</span><span class="sxs-lookup"><span data-stu-id="c28a7-115">Within the main method of a console application, instantiate a <xref:System.ServiceModel.ServiceHost> object by passing in the service type and the base address.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. <span data-ttu-id="c28a7-116">Vytvořit blok try bezprostředně pod kód v kroku 1, to zachytává všechny výjimky, které získat vyvolána, když je služba spuštěna.</span><span class="sxs-lookup"><span data-stu-id="c28a7-116">Create a try block immediately below the code for step 1, this catches any exceptions that get thrown while the service is running.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. <span data-ttu-id="c28a7-117">Zkontrolujte, zda již obsahuje tohoto hostitele služby <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, pokud ne, vytvořte nový <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span><span class="sxs-lookup"><span data-stu-id="c28a7-117">Check to see whether the service host already contains a <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, if not, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. <span data-ttu-id="c28a7-118">Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost `true.`</span><span class="sxs-lookup"><span data-stu-id="c28a7-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true.`</span></span>  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. <span data-ttu-id="c28a7-119"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> Obsahuje <xref:System.ServiceModel.Description.MetadataExporter> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c28a7-119">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contains a <xref:System.ServiceModel.Description.MetadataExporter> property.</span></span> <span data-ttu-id="c28a7-120"><xref:System.ServiceModel.Description.MetadataExporter> Obsahuje <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c28a7-120">The <xref:System.ServiceModel.Description.MetadataExporter> contains a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property.</span></span> <span data-ttu-id="c28a7-121">Nastavte hodnotu <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span><span class="sxs-lookup"><span data-stu-id="c28a7-121">Set the value of the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span></span> <span data-ttu-id="c28a7-122"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Vlastnost může být také nastavena na <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span><span class="sxs-lookup"><span data-stu-id="c28a7-122">The <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property can also be set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span></span> <span data-ttu-id="c28a7-123">Pokud je nastavena na <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> Exportér metadat generuje informace o zásadách s metadaty, která "odpovídá 1.5 WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="c28a7-123">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> the metadata exporter generates policy information with the metadata that" conforms to WS-Policy 1.5.</span></span> <span data-ttu-id="c28a7-124">Pokud je nastavena na <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> Exportér metadat generuje informace o zásadách, která odpovídá 1.2 WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="c28a7-124">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> the metadata exporter generates policy information that conforms to WS-Policy 1.2.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. <span data-ttu-id="c28a7-125">Přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance hostitele služby kolekce chování.</span><span class="sxs-lookup"><span data-stu-id="c28a7-125">Add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance to the service host's behaviors collection.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. <span data-ttu-id="c28a7-126">Přidáte koncový bod výměny metadat k hostiteli služby.</span><span class="sxs-lookup"><span data-stu-id="c28a7-126">Add the metadata exchange endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. <span data-ttu-id="c28a7-127">Přidání koncového bodu aplikace k hostiteli služby.</span><span class="sxs-lookup"><span data-stu-id="c28a7-127">Add an application endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  <span data-ttu-id="c28a7-128">Pokud nemůžete přidat žádné koncové body pro službu, modulu runtime přidá výchozí koncové body za vás.</span><span class="sxs-lookup"><span data-stu-id="c28a7-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="c28a7-129">V tomto příkladu vzhledem k tomu, že služba má <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nastavena na `true`, že služba má povoleno publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="c28a7-129">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, the service has publishing metadata enabled.</span></span> <span data-ttu-id="c28a7-130">Další informace o výchozí koncové body, naleznete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c28a7-130">For more information about default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="c28a7-131">Otevření hostitele služby a čekání na příchozí volání.</span><span class="sxs-lookup"><span data-stu-id="c28a7-131">Open the service host and wait for incoming calls.</span></span> <span data-ttu-id="c28a7-132">Když uživatel stiskne klávesu ENTER, zavřete hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="c28a7-132">When the user presses ENTER, close the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. <span data-ttu-id="c28a7-133">Vytvořte a spusťte konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c28a7-133">Build and run the console application.</span></span>  
  
11. <span data-ttu-id="c28a7-134">Pomocí aplikace Internet Explorer a přejděte do základní adresa služby (http://localhost:8001/MetadataSample v této ukázce) a ověřte, zda je povoleno publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="c28a7-134">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="c28a7-135">Zobrazí se webové stránky zobrazí s textem "Jednoduché služby" v horní části a bezprostředně pod "Službu jste vytvořili."</span><span class="sxs-lookup"><span data-stu-id="c28a7-135">You should see a Web page displayed that says "Simple Service" at the top and immediately below "You have created a service."</span></span> <span data-ttu-id="c28a7-136">Pokud ne, zobrazí se zpráva v horní části výslednou stránku: "Publikování metadat pro tuto službu je aktuálně zakázaný."</span><span class="sxs-lookup"><span data-stu-id="c28a7-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
## <a name="example"></a><span data-ttu-id="c28a7-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="c28a7-137">Example</span></span>  
 <span data-ttu-id="c28a7-138">Následující příklad kódu ukazuje implementaci základní služby WCF, který publikuje metadata pro služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="c28a7-138">The following code example shows the implementation of a basic WCF service that publishes metadata for the service in code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="c28a7-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c28a7-139">See also</span></span>

- [<span data-ttu-id="c28a7-140">Postupy: Hostování služby WCF ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="c28a7-140">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="c28a7-141">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="c28a7-141">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="c28a7-142">Přehled architektury metadat</span><span class="sxs-lookup"><span data-stu-id="c28a7-142">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="c28a7-143">Používání metadat</span><span class="sxs-lookup"><span data-stu-id="c28a7-143">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="c28a7-144">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c28a7-144">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
