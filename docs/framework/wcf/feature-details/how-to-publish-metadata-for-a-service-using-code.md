---
title: 'Postupy: Publikování metadat služby promocí kódu'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c3d2fd1222539ec8017846069e7eda9a2c503f22
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a><span data-ttu-id="96554-102">Postupy: Publikování metadat služby promocí kódu</span><span class="sxs-lookup"><span data-stu-id="96554-102">How to: Publish Metadata for a Service Using Code</span></span>
<span data-ttu-id="96554-103">Toto je jedna z dva postupy, které popisují publikování metadat pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="96554-103">This is one of two how-to topics that discuss publishing metadata for a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="96554-104">Existují dva způsoby, jak určit, jak by měla služba publikování metadat, použití konfiguračního souboru a pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="96554-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="96554-105">Toto téma ukazuje, jak publikování metadat služby promocí kódu.</span><span class="sxs-lookup"><span data-stu-id="96554-105">This topic shows how to publish metadata for a service using a code.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="96554-106">Toto téma ukazuje, jak publikování metadat nezabezpečená způsobem.</span><span class="sxs-lookup"><span data-stu-id="96554-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="96554-107">Jakýkoli klient může načíst metadata ze služby.</span><span class="sxs-lookup"><span data-stu-id="96554-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="96554-108">Pokud budete potřebovat k službě pro publikování metadat zabezpečeným způsobem.</span><span class="sxs-lookup"><span data-stu-id="96554-108">If you require your service to publish metadata in a secure manner.</span></span> <span data-ttu-id="96554-109">v tématu [koncový bod metadat zabezpečení vlastní](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="96554-109">see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="96554-110">Další informace o publikování metadat v konfiguračním souboru najdete v tématu [postupy: publikování metadat služby promocí konfigurační soubor](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="96554-110">For more information about publishing metadata in a configuration file, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span> <span data-ttu-id="96554-111">Publikování metadat umožňuje klientům pro načtení metadat pomocí žádost o přenos WS získat nebo žádosti o protokolu HTTP nebo získat pomocí `?wsdl` řetězec dotazu.</span><span class="sxs-lookup"><span data-stu-id="96554-111">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="96554-112">Ujistěte se, zda kód pracuje budete musíte vytvořit základní služby WCF.</span><span class="sxs-lookup"><span data-stu-id="96554-112">To be sure that the code is working you must create a basic WCF service.</span></span> <span data-ttu-id="96554-113">Základní služba s vlastním hostováním jsou uvedené v následující kód.</span><span class="sxs-lookup"><span data-stu-id="96554-113">A basic self-hosted service is provided in the following code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a><span data-ttu-id="96554-114">K publikování metadat v kódu</span><span class="sxs-lookup"><span data-stu-id="96554-114">To publish metadata in code</span></span>  
  
1.  <span data-ttu-id="96554-115">V rámci hlavní metoda aplikace konzoly, vytváření instancí <xref:System.ServiceModel.ServiceHost> objekt předáním typ služby a základní adresu.</span><span class="sxs-lookup"><span data-stu-id="96554-115">Within the main method of a console application, instantiate a <xref:System.ServiceModel.ServiceHost> object by passing in the service type and the base address.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2.  <span data-ttu-id="96554-116">Vytvoření bloku try bezprostředně pod kód pro krok 1, to zachytí všechny výjimky, které získat vyvolány, když je služba spuštěná.</span><span class="sxs-lookup"><span data-stu-id="96554-116">Create a try block immediately below the code for step 1, this catches any exceptions that get thrown while the service is running.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3.  <span data-ttu-id="96554-117">Zkontrolujte, zda hostitel služby již obsahuje <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, pokud ne, vytvořte novou <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span><span class="sxs-lookup"><span data-stu-id="96554-117">Check to see whether the service host already contains a <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, if not, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4.  <span data-ttu-id="96554-118">Nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnosti `true.`</span><span class="sxs-lookup"><span data-stu-id="96554-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true.`</span></span>  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5.  <span data-ttu-id="96554-119"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> Obsahuje <xref:System.ServiceModel.Description.MetadataExporter> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="96554-119">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contains a <xref:System.ServiceModel.Description.MetadataExporter> property.</span></span> <span data-ttu-id="96554-120"><xref:System.ServiceModel.Description.MetadataExporter> Obsahuje <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="96554-120">The <xref:System.ServiceModel.Description.MetadataExporter> contains a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property.</span></span> <span data-ttu-id="96554-121">Nastavte hodnotu <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> vlastnost <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span><span class="sxs-lookup"><span data-stu-id="96554-121">Set the value of the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span></span> <span data-ttu-id="96554-122"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> Vlastnost může být také nastavena na <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span><span class="sxs-lookup"><span data-stu-id="96554-122">The <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property can also be set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span></span> <span data-ttu-id="96554-123">Pokud nastavíte hodnotu <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> exportu metadat generuje informace o zásadách s metadaty, "odpovídá WS-Policy 1.5.</span><span class="sxs-lookup"><span data-stu-id="96554-123">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> the metadata exporter generates policy information with the metadata that" conforms to WS-Policy 1.5.</span></span> <span data-ttu-id="96554-124">Pokud nastavíte hodnotu <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> exportu metadat generuje informace o zásadách, který vyhovuje WS-Policy 1.2.</span><span class="sxs-lookup"><span data-stu-id="96554-124">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> the metadata exporter generates policy information that conforms to WS-Policy 1.2.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6.  <span data-ttu-id="96554-125">Přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance hostitele služby chování kolekce.</span><span class="sxs-lookup"><span data-stu-id="96554-125">Add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance to the service host's behaviors collection.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7.  <span data-ttu-id="96554-126">Přidejte do hostitele služby exchange koncovým bodem metadat.</span><span class="sxs-lookup"><span data-stu-id="96554-126">Add the metadata exchange endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8.  <span data-ttu-id="96554-127">Přidání koncového bodu aplikace do hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="96554-127">Add an application endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    >  <span data-ttu-id="96554-128">Pokud jste ke službě nepřidávejte žádné koncové body, modul runtime přidá výchozí koncové body pro vás.</span><span class="sxs-lookup"><span data-stu-id="96554-128">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="96554-129">V tomto příkladu protože služba má <xref:System.ServiceModel.Description.ServiceMetadataBehavior> nastavena na `true`, služba má povoleno publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="96554-129">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, the service has publishing metadata enabled.</span></span> <span data-ttu-id="96554-130">Další informace o výchozí koncové body najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="96554-130">For more information about default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="96554-131">Otevření hostitele služby a počkejte příchozí volání.</span><span class="sxs-lookup"><span data-stu-id="96554-131">Open the service host and wait for incoming calls.</span></span> <span data-ttu-id="96554-132">Když uživatel stiskne klávesu ENTER, zavřete hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="96554-132">When the user presses ENTER, close the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. <span data-ttu-id="96554-133">Sestavte a spusťte konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="96554-133">Build and run the console application.</span></span>  
  
11. <span data-ttu-id="96554-134">Použijte Internet Explorer a přejděte do základní adresa služby (http://localhost:8001/MetadataSample v této ukázce) a ověřte, jestli je zapnutá publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="96554-134">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="96554-135">Zobrazí webová stránka zobrazí, která říká "Jednoduché služba" v horní části a bezprostředně pod "Službu jste vytvořili."</span><span class="sxs-lookup"><span data-stu-id="96554-135">You should see a Web page displayed that says "Simple Service" at the top and immediately below "You have created a service."</span></span> <span data-ttu-id="96554-136">Pokud není, zobrazí se zpráva v horní části výsledné stránky: "publikování metadat pro tato služba je aktuálně zakázaná."</span><span class="sxs-lookup"><span data-stu-id="96554-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
## <a name="example"></a><span data-ttu-id="96554-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="96554-137">Example</span></span>  
 <span data-ttu-id="96554-138">Následující příklad kódu ukazuje implementaci základního [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba, která publikuje metadata pro služby v kódu.</span><span class="sxs-lookup"><span data-stu-id="96554-138">The following code example shows the implementation of a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that publishes metadata for the service in code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="96554-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="96554-139">See Also</span></span>  
 [<span data-ttu-id="96554-140">Postupy: Hostování služby WCF ve spravované aplikaci</span><span class="sxs-lookup"><span data-stu-id="96554-140">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [<span data-ttu-id="96554-141">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="96554-141">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="96554-142">Přehled architektury metadat</span><span class="sxs-lookup"><span data-stu-id="96554-142">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [<span data-ttu-id="96554-143">Používání metadat</span><span class="sxs-lookup"><span data-stu-id="96554-143">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [<span data-ttu-id="96554-144">Postupy: Publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="96554-144">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
