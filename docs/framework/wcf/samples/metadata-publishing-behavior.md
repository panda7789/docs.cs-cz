---
title: "Chování publikování metadat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fbccca0bb5db7fa12b5237d19b833e9fe11da0e9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="0d549-102">Chování publikování metadat</span><span class="sxs-lookup"><span data-stu-id="0d549-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="0d549-103">Ukázka chování publikování metadat ukazuje, jak k ovládání funkcí publikování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="0d549-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="0d549-104">Aby se zabránilo neúmyslnému zveřejnění metadata potenciálně citlivých služby, výchozí konfiguraci pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zakáže publikování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="0d549-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services disables metadata publishing.</span></span> <span data-ttu-id="0d549-105">Toto chování je ve výchozím nastavení zabezpečení, ale také znamená, že nelze použít metadata importovat nástroj (například Svcutil.exe) ke generování kódu klienta pro volání služby, pokud není výslovně povolena chování publikování metadat služby v konfiguraci požadován.</span><span class="sxs-lookup"><span data-stu-id="0d549-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0d549-106">Tato ukázka pro přehlednost, ukazuje, jak vytvořit koncový bod publikování zabezpečená metadat.</span><span class="sxs-lookup"><span data-stu-id="0d549-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="0d549-107">Tyto koncové body jsou potenciálně dostupné pro anonymní neověřené spotřebitelů a musí dát pozor před nasazením těchto koncových bodů a zajistit tak veřejně předání metadata služby příslušné.</span><span class="sxs-lookup"><span data-stu-id="0d549-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="0d549-108">Najdete v článku [koncový bod metadat zabezpečení vlastní](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) ukázku pro vzorku, který zabezpečuje koncový bod metadat.</span><span class="sxs-lookup"><span data-stu-id="0d549-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="0d549-109">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje `ICalculator` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="0d549-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="0d549-110">V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="0d549-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d549-111">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="0d549-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0d549-112">Pro službu, která zveřejňuje metadata <xref:System.ServiceModel.Description.ServiceMetadataBehavior> musí být nastaveny na službu.</span><span class="sxs-lookup"><span data-stu-id="0d549-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="0d549-113">Když toto chování je k dispozici, můžete publikovat metadata nakonfigurováním koncový bod ke zveřejnění <xref:System.ServiceModel.Description.IMetadataExchange> kontrakt jako implementaci protokolu WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="0d549-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="0d549-114">V zájmu usnadnění tento kontrakt nebyla zadána konfigurace zkrácený název "IMetadataExchange".</span><span class="sxs-lookup"><span data-stu-id="0d549-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="0d549-115">Této ukázce se používá `mexHttpBinding`, což je pro vaše pohodlí standardní vazby, která je ekvivalentní `wsHttpBinding` s režim zabezpečení nastavený na `None`.</span><span class="sxs-lookup"><span data-stu-id="0d549-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="0d549-116">Relativní adresu "mex" se používá v koncovém bodě, který v případě přeložit proti služby základní adresu výsledkem koncový bod adresy http://localhost/servicemodelsamples/service.svc/mex.</span><span class="sxs-lookup"><span data-stu-id="0d549-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of http://localhost/servicemodelsamples/service.svc/mex.</span></span> <span data-ttu-id="0d549-117">Konfigurace chování obrázku:</span><span class="sxs-lookup"><span data-stu-id="0d549-117">The following shows the behavior configuration:</span></span>  
  
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
  
 <span data-ttu-id="0d549-118">Následující obrázek znázorňuje MEX koncový bod.</span><span class="sxs-lookup"><span data-stu-id="0d549-118">The following shows the MEX endpoint.</span></span>  
  
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
  
 <span data-ttu-id="0d549-119">Nastaví Tato ukázka <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost `true`, který taky zpřístupňuje metadata služby pomocí metody GET protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="0d549-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="0d549-120">Chcete-li povolit koncový bod metadat HTTP GET, musí mít službu základní adresu HTTP.</span><span class="sxs-lookup"><span data-stu-id="0d549-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="0d549-121">Řetězec dotazu `?wsdl` se používá na základní adresa služby přístup k metadatům.</span><span class="sxs-lookup"><span data-stu-id="0d549-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="0d549-122">Například zobrazíte WSDL pro službu ve webovém prohlížeči použijete http://localhost/servicemodelsamples/service.svc?wsdl adresu.</span><span class="sxs-lookup"><span data-stu-id="0d549-122">For example, to see the WSDL for the service in a Web browser you would use the address http://localhost/servicemodelsamples/service.svc?wsdl.</span></span> <span data-ttu-id="0d549-123">Alternativně můžete toto chování vystavit metadat prostřednictvím protokolu HTTPS, nastavením <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> k `true`.</span><span class="sxs-lookup"><span data-stu-id="0d549-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="0d549-124">To vyžaduje základní adresu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0d549-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="0d549-125">Pro přístup k použití pro koncový bod služby MEX [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0d549-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="0d549-126">Tím se vygeneruje na základě metadat služby klienta.</span><span class="sxs-lookup"><span data-stu-id="0d549-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="0d549-127">Chcete-li získat přístup k metadatům pro službu pomocí metody GET protokolu HTTP, přejděte v prohlížeči na http://localhost/servicemodelsamples/service.svc?wsdl.</span><span class="sxs-lookup"><span data-stu-id="0d549-127">To access the service's metadata using HTTP GET, point your browser to http://localhost/servicemodelsamples/service.svc?wsdl.</span></span>  
  
 <span data-ttu-id="0d549-128">Pokud odeberete toto chování a pokuste se spustit službu, dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="0d549-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="0d549-129">K této chybě dojde, protože bez chování, koncový bod nakonfigurovaný s `IMetadataExchange` nemá žádnou implementaci kontraktu.</span><span class="sxs-lookup"><span data-stu-id="0d549-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="0d549-130">Pokud nastavíte `HttpGetEnabled` k `false`, uvidíte na stránce nápovědy CalculatorService místo zobrazuje metadata služby.</span><span class="sxs-lookup"><span data-stu-id="0d549-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0d549-131">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="0d549-131">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0d549-132">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0d549-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0d549-133">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0d549-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="0d549-134">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0d549-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0d549-135">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="0d549-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0d549-136">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="0d549-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0d549-137">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="0d549-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0d549-138">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0d549-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
## <a name="see-also"></a><span data-ttu-id="0d549-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d549-139">See Also</span></span>
