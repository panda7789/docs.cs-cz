---
title: 'Postupy: Import metadat do koncových bodů služeb'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: 5a6375f0a0b0f657401a1ac2254be942d4e618aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548674"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="8b3ec-102">Postupy: Import metadat do koncových bodů služeb</span><span class="sxs-lookup"><span data-stu-id="8b3ec-102">How to: Import Metadata into Service Endpoints</span></span>
<span data-ttu-id="8b3ec-103">Toto téma vysvětluje, jak importovat metadata do kolekce koncových bodů služby a použití služby definované v [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8b3ec-103">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="8b3ec-104">V tomto tématu ukazují, jak vytvořit klientskou aplikaci, která importuje metadata ze služby a volání `Add` metodu na službu.</span><span class="sxs-lookup"><span data-stu-id="8b3ec-104">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="8b3ec-105">Import metadat do koncových bodů služeb</span><span class="sxs-lookup"><span data-stu-id="8b3ec-105">To import metadata into service endpoints</span></span>  
  
1.  <span data-ttu-id="8b3ec-106">Deklarovat <xref:System.ServiceModel.EndpointAddress> objektu a inicializovat s identifikátor URI (Uniform Resource) pro exchange (MEX) adresu metadat služby.</span><span class="sxs-lookup"><span data-stu-id="8b3ec-106">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2.  <span data-ttu-id="8b3ec-107">Vytvoření <xref:System.ServiceModel.Description.MetadataExchangeClient>a předejte nebyla určena adresa MEX. a volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b3ec-107">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="8b3ec-108">To načte metadata ze služby.</span><span class="sxs-lookup"><span data-stu-id="8b3ec-108">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3.  <span data-ttu-id="8b3ec-109">Vytvoření <xref:System.ServiceModel.Description.WsdlImporter>a předejte dříve načíst metadata a volání <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b3ec-109">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="8b3ec-110">Tím se vytvoří kolekce <xref:System.ServiceModel.Description.ContractDescription> objekty.</span><span class="sxs-lookup"><span data-stu-id="8b3ec-110">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="8b3ec-111">Lze také volat <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> nebo <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, v závislosti na vašich potřeb.</span><span class="sxs-lookup"><span data-stu-id="8b3ec-111">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    >  <span data-ttu-id="8b3ec-112">Po importu metadat nebudete mít k vytvoření kanálu klienta nebo exportovat metadata.</span><span class="sxs-lookup"><span data-stu-id="8b3ec-112">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="8b3ec-113">To je, protože v tuto chvíli není k dispozici žádné informace o typu.</span><span class="sxs-lookup"><span data-stu-id="8b3ec-113">This is because no type information is available at this point.</span></span> <span data-ttu-id="8b3ec-114">Informace o typu je potřeba ve skutečnosti interakci se službou nebo export metadat.</span><span class="sxs-lookup"><span data-stu-id="8b3ec-114">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="8b3ec-115">Generovat informace o typu, je nutné generovat kód, zobrazený v krocích 4 a 5.</span><span class="sxs-lookup"><span data-stu-id="8b3ec-115">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="8b3ec-116">Alternativně můžete použít <xref:System.ServiceModel.Description.MetadataResolver> pomocná třída.</span><span class="sxs-lookup"><span data-stu-id="8b3ec-116">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> <span data-ttu-id="8b3ec-117">Další informace najdete v tématu [jak: Použití třídy MetadataResolver k dynamickému získání metadat vazby](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span><span class="sxs-lookup"><span data-stu-id="8b3ec-117">For more information, see [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4.  <span data-ttu-id="8b3ec-118">Generovat informace o typu pro každou smlouvu.</span><span class="sxs-lookup"><span data-stu-id="8b3ec-118">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5.  <span data-ttu-id="8b3ec-119">Teď můžete použít tyto informace.</span><span class="sxs-lookup"><span data-stu-id="8b3ec-119">Now you can use this information.</span></span> <span data-ttu-id="8b3ec-120">Následující ukázka generuje C# zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="8b3ec-120">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="8b3ec-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b3ec-121">See also</span></span>
- [<span data-ttu-id="8b3ec-122">Metadata</span><span class="sxs-lookup"><span data-stu-id="8b3ec-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="8b3ec-123">Začínáme</span><span class="sxs-lookup"><span data-stu-id="8b3ec-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
