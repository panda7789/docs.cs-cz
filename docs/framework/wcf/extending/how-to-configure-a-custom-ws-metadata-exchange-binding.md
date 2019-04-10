---
title: 'Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: ab659e7e586b28f5c06b9b6ba12b313f318c6542
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210500"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="5fa1c-102">Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="5fa1c-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="5fa1c-103">Toto téma vysvětluje, jak nakonfigurovat vlastní WS-Metadata exchange vazby.</span><span class="sxs-lookup"><span data-stu-id="5fa1c-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="5fa1c-104">Zahrnuje čtyři vazby metadata definovaná uživatelem systému Windows Communication Foundation (WCF), ale můžete publikovat metadat pomocí všechny vazby, který chcete.</span><span class="sxs-lookup"><span data-stu-id="5fa1c-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="5fa1c-105">V tomto tématu ukazují, jak publikovat pomocí metadat `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="5fa1c-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="5fa1c-106">Tato vazba získáte možnost bezpečně doručovat jestli vystavuje metadata.</span><span class="sxs-lookup"><span data-stu-id="5fa1c-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="5fa1c-107">Kód v tomto článku je založený na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5fa1c-107">The code in this article is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="5fa1c-108">Použití konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="5fa1c-108">Using a configuration file</span></span>  
  
1.  <span data-ttu-id="5fa1c-109">V konfiguračním souboru služby, přidejte chování služby, který obsahuje `serviceMetadata` značky:</span><span class="sxs-lookup"><span data-stu-id="5fa1c-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  <span data-ttu-id="5fa1c-110">Přidat `behaviorConfiguration` atribut ke značce služby, který odkazuje na toto nové chování:</span><span class="sxs-lookup"><span data-stu-id="5fa1c-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  <span data-ttu-id="5fa1c-111">Přidat koncový bod metadat zadání mex jako adresu, `wsHttpBinding` jako vazbu, a <xref:System.ServiceModel.Description.IMetadataExchange> jako kontrakt:</span><span class="sxs-lookup"><span data-stu-id="5fa1c-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  <span data-ttu-id="5fa1c-112">Chcete-li ověřit, že je koncový bod výměny metadat pracovních správně přidání značky koncového bodu v konfiguračním souboru klienta:</span><span class="sxs-lookup"><span data-stu-id="5fa1c-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  <span data-ttu-id="5fa1c-113">V metodě Main() klienta, vytvořte nový <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, nastavte jeho <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> vlastnost `true`, volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a potom iteraci prostřednictvím kolekce metadat vrátil:</span><span class="sxs-lookup"><span data-stu-id="5fa1c-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="5fa1c-114">Konfigurace kódu</span><span class="sxs-lookup"><span data-stu-id="5fa1c-114">Configuring by code</span></span>  
  
1.  <span data-ttu-id="5fa1c-115">Vytvoření <xref:System.ServiceModel.WSHttpBinding> instanci vazby:</span><span class="sxs-lookup"><span data-stu-id="5fa1c-115">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  <span data-ttu-id="5fa1c-116">Vytvoření <xref:System.ServiceModel.ServiceHost> instance:</span><span class="sxs-lookup"><span data-stu-id="5fa1c-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  <span data-ttu-id="5fa1c-117">Přidání koncového bodu služby a přidejte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instanci:</span><span class="sxs-lookup"><span data-stu-id="5fa1c-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  <span data-ttu-id="5fa1c-118">Přidat koncový bod výměny metadat, určení <xref:System.ServiceModel.WSHttpBinding> vytvořili dříve:</span><span class="sxs-lookup"><span data-stu-id="5fa1c-118">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  <span data-ttu-id="5fa1c-119">Pokud chcete ověřit, že koncový bod výměny metadat pracuje správně, přidejte značku koncový bod v konfiguračním souboru klienta:</span><span class="sxs-lookup"><span data-stu-id="5fa1c-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  <span data-ttu-id="5fa1c-120">V metodě Main() klienta, vytvořte nový <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, nastavte <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> vlastnost `true`, volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a potom iteraci prostřednictvím kolekce metadat vrátil:</span><span class="sxs-lookup"><span data-stu-id="5fa1c-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5fa1c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fa1c-121">See also</span></span>

- [<span data-ttu-id="5fa1c-122">Chování publikování metadat</span><span class="sxs-lookup"><span data-stu-id="5fa1c-122">Metadata Publishing Behavior</span></span>](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
- [<span data-ttu-id="5fa1c-123">Načítání metadat</span><span class="sxs-lookup"><span data-stu-id="5fa1c-123">Retrieve Metadata</span></span>](../../../../docs/framework/wcf/samples/retrieve-metadata.md)
- [<span data-ttu-id="5fa1c-124">Metadata</span><span class="sxs-lookup"><span data-stu-id="5fa1c-124">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="5fa1c-125">Publikování metadat</span><span class="sxs-lookup"><span data-stu-id="5fa1c-125">Publishing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)
- [<span data-ttu-id="5fa1c-126">Publikování kocových bodů metadat</span><span class="sxs-lookup"><span data-stu-id="5fa1c-126">Publishing Metadata Endpoints</span></span>](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
