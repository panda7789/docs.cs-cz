---
title: 'Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 4e0c583eeef4bf068c08b273c833506ce80cbc3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185598"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="6feaa-102">Postupy: Konfigurace vlastních vazeb protokolu WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="6feaa-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="6feaa-103">Toto téma vám vysvětlí, jak nakonfigurovat vlastní vazby výměny ws-metadata.</span><span class="sxs-lookup"><span data-stu-id="6feaa-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="6feaa-104">Windows Communication Foundation (WCF) obsahuje čtyři systémem definované vazby metadat, ale můžete publikovat metadata pomocí libovolné vazby, které chcete.</span><span class="sxs-lookup"><span data-stu-id="6feaa-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="6feaa-105">Toto téma vám ukáže, jak `wsHttpBinding`publikovat metadata pomocí .</span><span class="sxs-lookup"><span data-stu-id="6feaa-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="6feaa-106">Tato vazba poskytuje možnost vystavení metadat bezpečným způsobem.</span><span class="sxs-lookup"><span data-stu-id="6feaa-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="6feaa-107">Kód v tomto článku je založen na [začínáme](../samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="6feaa-107">The code in this article is based on the [Getting Started](../samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="6feaa-108">Použití konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="6feaa-108">Using a configuration file</span></span>  
  
1. <span data-ttu-id="6feaa-109">Do konfiguračního souboru služby přidejte chování služby, které obsahuje `serviceMetadata` značku:</span><span class="sxs-lookup"><span data-stu-id="6feaa-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="6feaa-110">Přidejte `behaviorConfiguration` atribut k výrobníznačce, která odkazuje na toto nové chování:</span><span class="sxs-lookup"><span data-stu-id="6feaa-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">
    ```  
  
3. <span data-ttu-id="6feaa-111">Přidejte koncový bod metadat určující mex `wsHttpBinding` jako adresu, <xref:System.ServiceModel.Description.IMetadataExchange> jako vazbu a jako smlouvu:</span><span class="sxs-lookup"><span data-stu-id="6feaa-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. <span data-ttu-id="6feaa-112">Chcete-li ověřit, zda koncový bod výměny metadat funguje správně, přidejte značku koncového bodu do konfiguračního souboru klienta:</span><span class="sxs-lookup"><span data-stu-id="6feaa-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. <span data-ttu-id="6feaa-113">V metodě Main() klienta <xref:System.ServiceModel.Description.MetadataExchangeClient> vytvořte novou <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> instanci, nastavte její vlastnost na `true`, volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a potom iterace prostřednictvím kolekce vrácených metadat:</span><span class="sxs-lookup"><span data-stu-id="6feaa-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="6feaa-114">Konfigurace podle kódu</span><span class="sxs-lookup"><span data-stu-id="6feaa-114">Configuring by code</span></span>  
  
1. <span data-ttu-id="6feaa-115">Vytvoření <xref:System.ServiceModel.WSHttpBinding> instance vazby:</span><span class="sxs-lookup"><span data-stu-id="6feaa-115">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <span data-ttu-id="6feaa-116">Vytvoření <xref:System.ServiceModel.ServiceHost> instance:</span><span class="sxs-lookup"><span data-stu-id="6feaa-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. <span data-ttu-id="6feaa-117">Přidejte koncový bod služby a přidejte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instanci:</span><span class="sxs-lookup"><span data-stu-id="6feaa-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. <span data-ttu-id="6feaa-118">Přidejte koncový bod výměny metadat <xref:System.ServiceModel.WSHttpBinding> a určete dříve vytvořený:</span><span class="sxs-lookup"><span data-stu-id="6feaa-118">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. <span data-ttu-id="6feaa-119">Chcete-li ověřit, zda koncový bod výměny metadat funguje správně, přidejte značku koncového bodu do konfiguračního souboru klienta:</span><span class="sxs-lookup"><span data-stu-id="6feaa-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. <span data-ttu-id="6feaa-120">V metodě Main() klienta <xref:System.ServiceModel.Description.MetadataExchangeClient> vytvořte novou <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> instanci, nastavte vlastnost na `true`, volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a potom iterace prostřednictvím kolekce vrácených metadat:</span><span class="sxs-lookup"><span data-stu-id="6feaa-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6feaa-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="6feaa-121">See also</span></span>

- [<span data-ttu-id="6feaa-122">Chování publikování metadat</span><span class="sxs-lookup"><span data-stu-id="6feaa-122">Metadata Publishing Behavior</span></span>](../samples/metadata-publishing-behavior.md)
- [<span data-ttu-id="6feaa-123">Načítání metadat</span><span class="sxs-lookup"><span data-stu-id="6feaa-123">Retrieve Metadata</span></span>](../samples/retrieve-metadata.md)
- [<span data-ttu-id="6feaa-124">Metadata</span><span class="sxs-lookup"><span data-stu-id="6feaa-124">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="6feaa-125">Publikování metadat</span><span class="sxs-lookup"><span data-stu-id="6feaa-125">Publishing Metadata</span></span>](../feature-details/publishing-metadata.md)
- [<span data-ttu-id="6feaa-126">Publikování kocových bodů metadat</span><span class="sxs-lookup"><span data-stu-id="6feaa-126">Publishing Metadata Endpoints</span></span>](../publishing-metadata-endpoints.md)
