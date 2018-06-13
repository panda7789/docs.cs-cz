---
title: 'Postupy: Konfigurace vlastních metadat WS Exchange vazby'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 0596e91204a2a9dbaed2fdbe85387ec3785fd3db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488696"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="9dd48-102">Postupy: Konfigurace vlastních metadat WS Exchange vazby</span><span class="sxs-lookup"><span data-stu-id="9dd48-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="9dd48-103">Toto téma vysvětluje, jak nakonfigurovat vlastní WS-Metadata exchange vazby.</span><span class="sxs-lookup"><span data-stu-id="9dd48-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="9dd48-104">Windows Communication Foundation (WCF) zahrnuje čtyři metadata definovaná systémem vazby, ale můžete metadat pomocí žádné vazby, které chcete publikovat.</span><span class="sxs-lookup"><span data-stu-id="9dd48-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="9dd48-105">Toto téma vám ukáže, jak publikovat pomocí metadat `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="9dd48-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="9dd48-106">Tato vazba vám dává možnost vystavení metadata zabezpečené způsobem.</span><span class="sxs-lookup"><span data-stu-id="9dd48-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="9dd48-107">Kód v tomto článku je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="9dd48-107">The code in this article is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="9dd48-108">Použití konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="9dd48-108">Using a configuration file</span></span>  
  
1.  <span data-ttu-id="9dd48-109">V konfiguračním souboru služby, přidat chování služby, který obsahuje `serviceMetadata` značky:</span><span class="sxs-lookup"><span data-stu-id="9dd48-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  <span data-ttu-id="9dd48-110">Přidat `behaviorConfiguration` atribut ke značce služby, který odkazuje toto nové chování:</span><span class="sxs-lookup"><span data-stu-id="9dd48-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  <span data-ttu-id="9dd48-111">Přidat koncový bod metadat zadání mex jako adresu, `wsHttpBinding` jako vazba, a <xref:System.ServiceModel.Description.IMetadataExchange> jako kontraktu:</span><span class="sxs-lookup"><span data-stu-id="9dd48-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  <span data-ttu-id="9dd48-112">Ověřte, zda má koncový bod metadat exchange pracovní správně přidejte značku koncového bodu v konfiguračním souboru klienta:</span><span class="sxs-lookup"><span data-stu-id="9dd48-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  <span data-ttu-id="9dd48-113">Metoda Main() klienta, vytvořte novou <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, nastavte jeho <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> vlastnost `true`, volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a pak iteraci prostřednictvím kolekce metadat vrátil:</span><span class="sxs-lookup"><span data-stu-id="9dd48-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="9dd48-114">Konfigurace v kódu</span><span class="sxs-lookup"><span data-stu-id="9dd48-114">Configuring by code</span></span>  
  
1.  <span data-ttu-id="9dd48-115">Vytvoření <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> instanci vazby:</span><span class="sxs-lookup"><span data-stu-id="9dd48-115">Create a <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> binding instance:</span></span>  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  <span data-ttu-id="9dd48-116">Vytvoření <xref:System.ServiceModel.ServiceHost> instance:</span><span class="sxs-lookup"><span data-stu-id="9dd48-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  <span data-ttu-id="9dd48-117">Přidání koncového bodu služby a přidejte <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span><span class="sxs-lookup"><span data-stu-id="9dd48-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  <span data-ttu-id="9dd48-118">Přidat koncový bod metadat systému exchange, určení <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> vytvořili dříve:</span><span class="sxs-lookup"><span data-stu-id="9dd48-118">Add a metadata exchange endpoint, specifying the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> created earlier:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  <span data-ttu-id="9dd48-119">Ověřte, zda je koncovým bodem metadat exchange funguje správně, přidejte značku koncového bodu v konfiguračním souboru klienta:</span><span class="sxs-lookup"><span data-stu-id="9dd48-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  <span data-ttu-id="9dd48-120">Metoda Main() klienta, vytvořte novou <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, nastavte <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> vlastnost `true`, volání <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> a pak iteraci prostřednictvím kolekce metadat vrátil:</span><span class="sxs-lookup"><span data-stu-id="9dd48-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9dd48-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="9dd48-121">See Also</span></span>  
 [<span data-ttu-id="9dd48-122">Chování při publikování metadat</span><span class="sxs-lookup"><span data-stu-id="9dd48-122">Metadata Publishing Behavior</span></span>](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)  
 [<span data-ttu-id="9dd48-123">Načítání metadat</span><span class="sxs-lookup"><span data-stu-id="9dd48-123">Retrieve Metadata</span></span>](../../../../docs/framework/wcf/samples/retrieve-metadata.md)  
 [<span data-ttu-id="9dd48-124">Metadata</span><span class="sxs-lookup"><span data-stu-id="9dd48-124">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="9dd48-125">Publikování metadat</span><span class="sxs-lookup"><span data-stu-id="9dd48-125">Publishing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [<span data-ttu-id="9dd48-126">Publikování koncových bodů metadat</span><span class="sxs-lookup"><span data-stu-id="9dd48-126">Publishing Metadata Endpoints</span></span>](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
