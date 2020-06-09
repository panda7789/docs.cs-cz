---
title: 'Postupy: Import metadat do koncových bodů služby'
ms.date: 03/30/2017
ms.assetid: b69dbe20-92a1-4911-89d8-ffbc3dad4663
ms.openlocfilehash: 1de316b8e91739d5e3e24ff960e2cdfb33cc7fab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597056"
---
# <a name="how-to-import-metadata-into-service-endpoints"></a><span data-ttu-id="4b021-102">Postupy: Import metadat do koncových bodů služby</span><span class="sxs-lookup"><span data-stu-id="4b021-102">How to: Import Metadata into Service Endpoints</span></span>
<span data-ttu-id="4b021-103">Toto téma vysvětluje, jak importovat metadata do kolekce koncových bodů služby a používat službu definovanou v [Začínáme](../samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4b021-103">This topic explains how to import metadata into a collection of service endpoints and use the service defined in the [Getting Started](../samples/getting-started-sample.md).</span></span> <span data-ttu-id="4b021-104">Toto téma ukazuje, jak vytvořit klientskou aplikaci, která importuje metadata ze služby a pak zavolá `Add` metodu služby.</span><span class="sxs-lookup"><span data-stu-id="4b021-104">This topic show how to create a client application that imports metadata from the service and then calls the `Add` method on the service.</span></span>  
  
### <a name="to-import-metadata-into-service-endpoints"></a><span data-ttu-id="4b021-105">Import metadat do koncových bodů služby</span><span class="sxs-lookup"><span data-stu-id="4b021-105">To import metadata into service endpoints</span></span>  
  
1. <span data-ttu-id="4b021-106">Deklarovat <xref:System.ServiceModel.EndpointAddress> objekt a inicializovat ho pomocí identifikátoru URI (Uniform Resource Identifier) pro adresu výměny metadat (MEX) služby.</span><span class="sxs-lookup"><span data-stu-id="4b021-106">Declare an <xref:System.ServiceModel.EndpointAddress> object and initialize it with the Uniform Resource Identifier (URI) for the metadata exchange (MEX) address of the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#0)]  
  
2. <span data-ttu-id="4b021-107">Vytvořte a <xref:System.ServiceModel.Description.MetadataExchangeClient> předejte adresu MEX a zavolejte <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> .</span><span class="sxs-lookup"><span data-stu-id="4b021-107">Create a <xref:System.ServiceModel.Description.MetadataExchangeClient>, passing in the MEX address, and call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>.</span></span> <span data-ttu-id="4b021-108">Tím se načtou metadata ze služby.</span><span class="sxs-lookup"><span data-stu-id="4b021-108">This retrieves the metadata from the service.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#1)]  
  
3. <span data-ttu-id="4b021-109">Vytvořte a <xref:System.ServiceModel.Description.WsdlImporter> předejte dříve načtená metadata a zavolejte <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> .</span><span class="sxs-lookup"><span data-stu-id="4b021-109">Create a <xref:System.ServiceModel.Description.WsdlImporter>, passing in the metadata previously retrieved, and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>.</span></span> <span data-ttu-id="4b021-110">Tím se vygeneruje kolekce <xref:System.ServiceModel.Description.ContractDescription> objektů.</span><span class="sxs-lookup"><span data-stu-id="4b021-110">This generates a collection of <xref:System.ServiceModel.Description.ContractDescription> objects.</span></span> <span data-ttu-id="4b021-111">Můžete také volat <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> nebo <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A> , v závislosti na vašich potřebách.</span><span class="sxs-lookup"><span data-stu-id="4b021-111">You could also call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllEndpoints%2A> or <xref:System.ServiceModel.Description.WsdlImporter.ImportAllBindings%2A>, depending upon your needs.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="4b021-112">Po importu metadat nebudete moci vytvořit klientský kanál ani exportovat metadata.</span><span class="sxs-lookup"><span data-stu-id="4b021-112">After you have imported the metadata, you will not be able to create a client channel or export the metadata.</span></span> <span data-ttu-id="4b021-113">Důvodem je skutečnost, že v tuto chvíli nejsou k dispozici žádné informace o typu.</span><span class="sxs-lookup"><span data-stu-id="4b021-113">This is because no type information is available at this point.</span></span> <span data-ttu-id="4b021-114">Pro skutečnou interakci se službou nebo exportem metadat jsou vyžadovány informace o typu.</span><span class="sxs-lookup"><span data-stu-id="4b021-114">Type information is required to actually interact with the service or export metadata.</span></span> <span data-ttu-id="4b021-115">Chcete-li vygenerovat informace o typu, je nutné vygenerovat kód, který je zobrazen v krocích 4 a 5.</span><span class="sxs-lookup"><span data-stu-id="4b021-115">To generate the type information, you need to generate code, shown in steps 4 and 5.</span></span> <span data-ttu-id="4b021-116">Alternativně můžete použít <xref:System.ServiceModel.Description.MetadataResolver> pomocnou třídu.</span><span class="sxs-lookup"><span data-stu-id="4b021-116">Alternatively, you could use the <xref:System.ServiceModel.Description.MetadataResolver> helper class.</span></span> <span data-ttu-id="4b021-117">Další informace najdete v tématu [Postupy: použití třídy MetadataResolver k dynamickému získání metadat vazby](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span><span class="sxs-lookup"><span data-stu-id="4b021-117">For more information, see [How to: Use MetadataResolver to Obtain Binding Metadata Dynamically](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md).</span></span>  
  
4. <span data-ttu-id="4b021-118">Generování informací o typu pro každou kontrakt.</span><span class="sxs-lookup"><span data-stu-id="4b021-118">Generate type information for each contract.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#3)]  
  
5. <span data-ttu-id="4b021-119">Nyní můžete použít tyto informace.</span><span class="sxs-lookup"><span data-stu-id="4b021-119">Now you can use this information.</span></span> <span data-ttu-id="4b021-120">Následující ukázka generuje zdrojový kód C#.</span><span class="sxs-lookup"><span data-stu-id="4b021-120">The following sample generates C# source code.</span></span>  
  
     [!code-csharp[UE_ImportMetadata#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/ue_importmetadata/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="4b021-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b021-121">See also</span></span>

- [<span data-ttu-id="4b021-122">Metadata</span><span class="sxs-lookup"><span data-stu-id="4b021-122">Metadata</span></span>](metadata.md)
- [<span data-ttu-id="4b021-123">Začínáme</span><span class="sxs-lookup"><span data-stu-id="4b021-123">Getting Started</span></span>](../samples/getting-started-sample.md)
