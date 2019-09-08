---
title: 'Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: c3582ba3c434bb763889faebcc27407f67af7b1e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795650"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="3998b-102">Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="3998b-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="3998b-103">V tomto tématu se dozvíte, jak nakonfigurovat vlastní vazbu WS-Metadata Exchange.</span><span class="sxs-lookup"><span data-stu-id="3998b-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="3998b-104">Windows Communication Foundation (WCF) zahrnuje čtyři uživatelsky definované vazby metadat, ale můžete publikovat metadata pomocí libovolné požadované vazby.</span><span class="sxs-lookup"><span data-stu-id="3998b-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="3998b-105">V `wsHttpBinding`tomto tématu se dozvíte, jak publikovat metadata pomocí.</span><span class="sxs-lookup"><span data-stu-id="3998b-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="3998b-106">Tato vazba vám dává možnost vystavovat metadata zabezpečeným způsobem.</span><span class="sxs-lookup"><span data-stu-id="3998b-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="3998b-107">Kód v tomto článku je založen na [Začínáme](../samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3998b-107">The code in this article is based on the [Getting Started](../samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="3998b-108">Použití konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="3998b-108">Using a configuration file</span></span>  
  
1. <span data-ttu-id="3998b-109">V konfiguračním souboru služby přidejte chování služby, které obsahuje `serviceMetadata` značku:</span><span class="sxs-lookup"><span data-stu-id="3998b-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="3998b-110">`behaviorConfiguration` Přidejte atribut do značky služby, který odkazuje na toto nové chování:</span><span class="sxs-lookup"><span data-stu-id="3998b-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3. <span data-ttu-id="3998b-111">Přidejte koncový bod metadat zadáním formátu MEX jako adresy `wsHttpBinding` , vazby a <xref:System.ServiceModel.Description.IMetadataExchange> jako kontraktu:</span><span class="sxs-lookup"><span data-stu-id="3998b-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. <span data-ttu-id="3998b-112">Chcete-li ověřit, zda koncový bod výměny metadat funguje správně, přidejte do konfiguračního souboru klienta značku koncového bodu:</span><span class="sxs-lookup"><span data-stu-id="3998b-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. <span data-ttu-id="3998b-113">V metodě Main () klienta vytvořte <xref:System.ServiceModel.Description.MetadataExchangeClient> novou instanci, nastavte její <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> vlastnost na `true`, zavolejte <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a potom Iterujte pomocí kolekce vrácených metadat:</span><span class="sxs-lookup"><span data-stu-id="3998b-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="3998b-114">Konfigurace podle kódu</span><span class="sxs-lookup"><span data-stu-id="3998b-114">Configuring by code</span></span>  
  
1. <span data-ttu-id="3998b-115">Vytvořte instanci <xref:System.ServiceModel.WSHttpBinding> vazby:</span><span class="sxs-lookup"><span data-stu-id="3998b-115">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <span data-ttu-id="3998b-116"><xref:System.ServiceModel.ServiceHost> Vytvoření instance:</span><span class="sxs-lookup"><span data-stu-id="3998b-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. <span data-ttu-id="3998b-117">Přidejte koncový bod služby a přidejte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instanci:</span><span class="sxs-lookup"><span data-stu-id="3998b-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. <span data-ttu-id="3998b-118">Přidejte koncový bod výměny metadat a určete <xref:System.ServiceModel.WSHttpBinding> dříve vytvořený:</span><span class="sxs-lookup"><span data-stu-id="3998b-118">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. <span data-ttu-id="3998b-119">Chcete-li ověřit, zda koncový bod výměny metadat funguje správně, přidejte do konfiguračního souboru klienta značku koncového bodu:</span><span class="sxs-lookup"><span data-stu-id="3998b-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. <span data-ttu-id="3998b-120">V metodě Main () <xref:System.ServiceModel.Description.MetadataExchangeClient> klienta vytvořte novou instanci, <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> nastavte vlastnost na `true`, zavolejte <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a potom Iterujte pomocí kolekce vrácených metadat:</span><span class="sxs-lookup"><span data-stu-id="3998b-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3998b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3998b-121">See also</span></span>

- [<span data-ttu-id="3998b-122">Chování při publikování metadat</span><span class="sxs-lookup"><span data-stu-id="3998b-122">Metadata Publishing Behavior</span></span>](../samples/metadata-publishing-behavior.md)
- [<span data-ttu-id="3998b-123">Načítání metadat</span><span class="sxs-lookup"><span data-stu-id="3998b-123">Retrieve Metadata</span></span>](../samples/retrieve-metadata.md)
- [<span data-ttu-id="3998b-124">Metadata</span><span class="sxs-lookup"><span data-stu-id="3998b-124">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="3998b-125">Publikování metadat</span><span class="sxs-lookup"><span data-stu-id="3998b-125">Publishing Metadata</span></span>](../feature-details/publishing-metadata.md)
- [<span data-ttu-id="3998b-126">Publikování koncových bodů metadat</span><span class="sxs-lookup"><span data-stu-id="3998b-126">Publishing Metadata Endpoints</span></span>](../publishing-metadata-endpoints.md)
