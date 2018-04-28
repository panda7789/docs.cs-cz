---
title: 'Postupy: Import metadat do koncových bodů služby'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b86f31217812767b0fbbd785a0f3ff96c2948854
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="51937-102">Postupy: Import metadat do koncových bodů služby</span><span class="sxs-lookup"><span data-stu-id="51937-102">How to: Import Metadata into Service Endpoints</span></span>
<span data-ttu-id="51937-103">Toto téma vysvětluje, jak importovat metadata do kolekce koncové body služby a používat službu definované v [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="51937-103">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="51937-104">V tomto tématu ukazují, jak vytvořit klientskou aplikaci, která importuje metadata ze služby a poté zavolá `Add` metoda ve službě.</span><span class="sxs-lookup"><span data-stu-id="51937-104">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="51937-105">Import metadat do koncových bodů služby</span><span class="sxs-lookup"><span data-stu-id="51937-105">To import metadata into service endpoints</span></span>  
  
1.  <span data-ttu-id="51937-106">Deklarace <xref:System.ServiceModel.EndpointAddress> objektu a provést jeho inicializaci s identifikátor URI (Uniform Resource) pro adresu exchange (MEX) metadata služby.</span><span class="sxs-lookup"><span data-stu-id="51937-106">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2.  <span data-ttu-id="51937-107">Vytvoření <xref:System.ServiceModel.Description.MetadataExchangeClient>, předejte v MEX adresu a volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="51937-107">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="51937-108">Tato metadata načte ze služby.</span><span class="sxs-lookup"><span data-stu-id="51937-108">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3.  <span data-ttu-id="51937-109">Vytvoření <xref:System.ServiceModel.Description.WsdlImporter>a předejte dříve načíst metadata a volání <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span><span class="sxs-lookup"><span data-stu-id="51937-109">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="51937-110">Tento postup vytvoří kolekci <xref:System.ServiceModel.Description.ContractDescription> objekty.</span><span class="sxs-lookup"><span data-stu-id="51937-110">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="51937-111">Může také zavolat <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> nebo <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, v závislosti na vašich potřeb.</span><span class="sxs-lookup"><span data-stu-id="51937-111">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    >  <span data-ttu-id="51937-112">Po importu metadat, nebude možné vytvořit kanál klienta nebo exportovat metadata.</span><span class="sxs-lookup"><span data-stu-id="51937-112">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="51937-113">Je to proto, že v tomto okamžiku je k dispozici žádné informace o typu.</span><span class="sxs-lookup"><span data-stu-id="51937-113">This is because no type information is available at this point.</span></span> <span data-ttu-id="51937-114">Informace o typu, je potřeba ve skutečnosti komunikovat se službou nebo export metadat.</span><span class="sxs-lookup"><span data-stu-id="51937-114">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="51937-115">Chcete-li generovat informace o typu, je potřeba generovat kód, uvedené v kroku 4 a 5.</span><span class="sxs-lookup"><span data-stu-id="51937-115">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="51937-116">Alternativně můžete použít <xref:System.ServiceModel.Description.MetadataResolver> pomocná třída.</span><span class="sxs-lookup"><span data-stu-id="51937-116">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> <span data-ttu-id="51937-117">Další informace najdete v tématu [postupy: použití třídy MetadataResolver k získání vazby Metadata dynamicky](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span><span class="sxs-lookup"><span data-stu-id="51937-117">For more information, see [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4.  <span data-ttu-id="51937-118">Generovat informace o typu pro každý kontrakt.</span><span class="sxs-lookup"><span data-stu-id="51937-118">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5.  <span data-ttu-id="51937-119">Nyní můžete tyto informace.</span><span class="sxs-lookup"><span data-stu-id="51937-119">Now you can use this information.</span></span> <span data-ttu-id="51937-120">Následující příklad vytvoří zdrojový kód C#.</span><span class="sxs-lookup"><span data-stu-id="51937-120">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="51937-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="51937-121">See Also</span></span>  
 [<span data-ttu-id="51937-122">Metadata</span><span class="sxs-lookup"><span data-stu-id="51937-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="51937-123">Začínáme</span><span class="sxs-lookup"><span data-stu-id="51937-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
