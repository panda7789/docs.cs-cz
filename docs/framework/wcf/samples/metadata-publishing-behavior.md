---
title: Chování publikování metadat
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 20922636f140e0ac9faff55bf94c0b2633a8070d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773919"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="7631b-102">Chování publikování metadat</span><span class="sxs-lookup"><span data-stu-id="7631b-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="7631b-103">Ukázka chování publikování metadat ukazuje, jak řídit funkce publikování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="7631b-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="7631b-104">Pokud chcete zabránit neúmyslnému zveřejnění metadat služby potenciálně citlivých, výchozí konfigurace pro služby Windows Communication Foundation (WCF) zakáže publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="7631b-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="7631b-105">Toto chování je ve výchozím nastavení zabezpečený, ale také znamená, že nemůžete použít metadat importovat nástroj (například Svcutil.exe) ke generování kódu klienta, který je potřeba volat službu, není-li v konfiguraci není explicitně povoleno chování publikování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="7631b-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7631b-106">Pro přehlednost Tato ukázka ukazuje, jak vytvořit koncový bod publikování metadat zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="7631b-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="7631b-107">Tyto koncové body jsou potenciálně dostupné pro anonymní neověřené uživatele a musí tak, aby byl veřejně pocházejí metadata služby odpovídající věnovat pozornost před nasazením tyto koncové body.</span><span class="sxs-lookup"><span data-stu-id="7631b-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="7631b-108">Zobrazit [koncový bod metadat Zabezpečte vlastní](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) Vzorový příklad, který zajišťuje zabezpečení koncových bodů metadat.</span><span class="sxs-lookup"><span data-stu-id="7631b-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="7631b-109">Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje `ICalculator` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="7631b-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="7631b-110">V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="7631b-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7631b-111">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7631b-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7631b-112">Pro službu, která zpřístupňují metadata a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> musí být nakonfigurovaná na službu.</span><span class="sxs-lookup"><span data-stu-id="7631b-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="7631b-113">Když toto chování je k dispozici, můžete publikovat metadat nakonfigurováním zveřejnit koncový bod <xref:System.ServiceModel.Description.IMetadataExchange> kontrakt jako implementaci protokolu WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="7631b-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="7631b-114">Pro zjednodušení této smlouvy se předala zkrácený konfigurační název "IMetadataExchange".</span><span class="sxs-lookup"><span data-stu-id="7631b-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="7631b-115">Této ukázce se používá `mexHttpBinding`, což je usnadnění standardní vazbu, která je ekvivalentní `wsHttpBinding` s režimem zabezpečení nastaveno `None`.</span><span class="sxs-lookup"><span data-stu-id="7631b-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="7631b-116">Relativní adresa "mex" se používá koncový bod, který se při vyřešení proti základní služby adresu výsledkem adresy koncového bodu z `http://localhost/servicemodelsamples/service.svc/mex`.</span><span class="sxs-lookup"><span data-stu-id="7631b-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="7631b-117">Následuje ukázka konfigurace chování:</span><span class="sxs-lookup"><span data-stu-id="7631b-117">The following shows the behavior configuration:</span></span>  
  
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
  
 <span data-ttu-id="7631b-118">Následuje ukázka koncového bodu MEX.</span><span class="sxs-lookup"><span data-stu-id="7631b-118">The following shows the MEX endpoint.</span></span>  
  
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
  
 <span data-ttu-id="7631b-119">Tato ukázka nastaví <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost `true`, což také poskytuje metadata služby pomocí HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="7631b-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="7631b-120">Pokud chcete povolit koncový bod metadat HTTP GET, služba musí mít základní adresu HTTP.</span><span class="sxs-lookup"><span data-stu-id="7631b-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="7631b-121">Řetězec dotazu `?wsdl` se používá na základní adresu služby pro přístup k metadatům.</span><span class="sxs-lookup"><span data-stu-id="7631b-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="7631b-122">Například pokud chcete zobrazit WSDL pro služby ve webovém prohlížeči použijete adresu `http://localhost/servicemodelsamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="7631b-122">For example, to see the WSDL for the service in a Web browser you would use the address `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span> <span data-ttu-id="7631b-123">Alternativně můžete použít toto chování ke zveřejnění metadat prostřednictvím protokolu HTTPS tak, že nastavíte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> k `true`.</span><span class="sxs-lookup"><span data-stu-id="7631b-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="7631b-124">To vyžaduje základní adresu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7631b-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="7631b-125">Pro přístup k použití koncového bodu služby MEX [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7631b-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="7631b-126">Tím se vytvoří klienta na základě metadat služby.</span><span class="sxs-lookup"><span data-stu-id="7631b-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="7631b-127">Chcete-li získat přístup k metadatům služby pomocí HTTP GET, přejděte v prohlížeči na `http://localhost/servicemodelsamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="7631b-127">To access the service's metadata using HTTP GET, point your browser to `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span>  
  
 <span data-ttu-id="7631b-128">Pokud odeberete toto chování a pokusu o otevření služby, obdržíte výjimku.</span><span class="sxs-lookup"><span data-stu-id="7631b-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="7631b-129">K této chybě dochází, protože bez chování, koncový bod nakonfigurovaný s `IMetadataExchange` smlouvy nemá žádnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="7631b-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="7631b-130">Pokud nastavíte `HttpGetEnabled` k `false`, zobrazí se stránka nápovědy CalculatorService místo zobrazení metadat služby.</span><span class="sxs-lookup"><span data-stu-id="7631b-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7631b-131">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="7631b-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7631b-132">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7631b-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7631b-133">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7631b-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7631b-134">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7631b-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7631b-135">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="7631b-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7631b-136">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="7631b-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7631b-137">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="7631b-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7631b-138">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7631b-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
