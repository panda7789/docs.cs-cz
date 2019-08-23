---
title: Chování publikování metadat
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: e0385ec74c9e00472b9ba5fb68f3d97c19f86642
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930427"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="82809-102">Chování publikování metadat</span><span class="sxs-lookup"><span data-stu-id="82809-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="82809-103">Ukázka chování publikování metadat ukazuje, jak řídit funkce publikování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="82809-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="82809-104">Aby nedocházelo k neúmyslnému zveřejnění potenciálně citlivých metadat služby, služba výchozí konfigurace služby Windows Communication Foundation (WCF) zakáže publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="82809-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="82809-105">Toto chování je standardně zabezpečené, ale také znamená, že nemůžete použít nástroj pro import metadat (například Svcutil. exe), aby se vygeneroval kód klienta vyžadovaný pro volání služby, pokud není v konfiguraci explicitně povolený chování publikování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="82809-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="82809-106">Pro přehlednost Tato ukázka ukazuje, jak vytvořit nezabezpečený koncový bod publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="82809-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="82809-107">Tyto koncové body jsou možná dostupné anonymním neověřeným příjemcům a před nasazením těchto koncových bodů je nutné zajistit, aby bylo zajištěno, že bude jejich veřejněné zveřejnění metadat služby vhodné.</span><span class="sxs-lookup"><span data-stu-id="82809-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="82809-108">Ukázku zabezpečení koncového bodu metadat najdete v ukázce pro [Vlastní zabezpečený koncový bod metadat](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="82809-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="82809-109">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje `ICalculator` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="82809-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="82809-110">V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="82809-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82809-111">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="82809-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="82809-112">Aby služba zveřejnila metadata, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> musí být ve službě nakonfigurovaná.</span><span class="sxs-lookup"><span data-stu-id="82809-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="82809-113">Pokud je toto chování k dispozici, můžete publikovat metadata tím, že nakonfigurujete <xref:System.ServiceModel.Description.IMetadataExchange> koncový bod, který zveřejní kontrakt jako implementaci protokolu WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="82809-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="82809-114">V rámci této smlouvy byl uveden zkrácený název konfigurace "IMetadataExchange".</span><span class="sxs-lookup"><span data-stu-id="82809-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="82809-115">Tato ukázka používá `mexHttpBinding`, což je pohodlná standardní vazba, která je ekvivalentní `wsHttpBinding` s režimem zabezpečení nastaveným na `None`.</span><span class="sxs-lookup"><span data-stu-id="82809-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="82809-116">V koncovém bodu se používá relativní adresa "MEX", která při překladu na základě základní adresy služeb má za následek adresu `http://localhost/servicemodelsamples/service.svc/mex`koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="82809-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="82809-117">Následující příklad ukazuje konfiguraci chování:</span><span class="sxs-lookup"><span data-stu-id="82809-117">The following shows the behavior configuration:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="82809-118">Následující příklad ukazuje koncový bod MEX.</span><span class="sxs-lookup"><span data-stu-id="82809-118">The following shows the MEX endpoint.</span></span>  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="82809-119">Tato ukázka nastavuje <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost na `true`, která také zpřístupňuje metadata služby pomocí protokolu HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="82809-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="82809-120">Aby bylo možné povolit koncový bod metadat HTTP GET, musí mít služba základní adresu HTTP.</span><span class="sxs-lookup"><span data-stu-id="82809-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="82809-121">Řetězec `?wsdl` dotazu se používá na základní adrese služby pro přístup k metadatům.</span><span class="sxs-lookup"><span data-stu-id="82809-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="82809-122">Například, chcete-li zobrazit WSDL pro službu ve webovém prohlížeči, použijte tuto adresu `http://localhost/servicemodelsamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="82809-122">For example, to see the WSDL for the service in a Web browser you would use the address `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span> <span data-ttu-id="82809-123">Alternativně můžete toto chování použít k vystavení metadat přes HTTPS <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> nastavením na. `true`</span><span class="sxs-lookup"><span data-stu-id="82809-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="82809-124">Vyžaduje se základní adresa HTTPS.</span><span class="sxs-lookup"><span data-stu-id="82809-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="82809-125">Pokud chcete získat přístup ke koncovému bodu služby MEX, použijte nástroj pro doSvcutilení [metadat (ServiceModel. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="82809-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="82809-126">Tím se vygeneruje klient na základě metadat služby.</span><span class="sxs-lookup"><span data-stu-id="82809-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="82809-127">Pokud chcete získat přístup k metadatům služby pomocí protokolu HTTP GET, najeďte na `http://localhost/servicemodelsamples/service.svc?wsdl`prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="82809-127">To access the service's metadata using HTTP GET, point your browser to `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span>  
  
 <span data-ttu-id="82809-128">Pokud toto chování odstraníte a pokusíte se otevřít službu, získáte výjimku.</span><span class="sxs-lookup"><span data-stu-id="82809-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="82809-129">K této chybě dochází, protože bez chování nemá koncový bod nakonfigurovaný se `IMetadataExchange` smlouvou žádnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="82809-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="82809-130">Pokud nastavíte `HttpGetEnabled` na `false`, zobrazí se stránka s CalculatorService s usnadněním, místo abyste viděli metadata služby.</span><span class="sxs-lookup"><span data-stu-id="82809-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="82809-131">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="82809-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="82809-132">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="82809-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="82809-133">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="82809-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="82809-134">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="82809-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="82809-135">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="82809-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="82809-136">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="82809-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="82809-137">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="82809-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="82809-138">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="82809-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
