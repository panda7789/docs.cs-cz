---
title: Chování publikování metadat
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: dade6d1a53fd99b994fb3c027db4e51392bfdcda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144393"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="6e988-102">Chování publikování metadat</span><span class="sxs-lookup"><span data-stu-id="6e988-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="6e988-103">Ukázka chování publikování metadat ukazuje, jak řídit funkce publikování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="6e988-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="6e988-104">Chcete-li zabránit neúmyslnému zveřejnění potenciálně citlivých metadat služby, výchozí konfigurace pro služby WCF (Windows Communication Foundation) zakáže publikování metadat.</span><span class="sxs-lookup"><span data-stu-id="6e988-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="6e988-105">Toto chování je ve výchozím nastavení zabezpečené, ale také znamená, že nelze použít nástroj pro import metadat (například Svcutil.exe) ke generování klientského kódu potřebného k volání služby, pokud není v konfiguraci explicitně povoleno chování publikování metadat služby.</span><span class="sxs-lookup"><span data-stu-id="6e988-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6e988-106">Pro přehlednost tato ukázka ukazuje, jak vytvořit koncový bod publikování nezabezpečených metadat.</span><span class="sxs-lookup"><span data-stu-id="6e988-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="6e988-107">Tyto koncové body jsou potenciálně k dispozici anonymní matné neověřené spotřebitele a je třeba dbát na to před nasazením těchto koncových bodů, aby bylo zajištěno, že je vhodné veřejně zveřejnit metadata služby.</span><span class="sxs-lookup"><span data-stu-id="6e988-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="6e988-108">Viz [ukázka ukázně vlastních zabezpečených metadat](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) koncového bodu pro ukázku, která zabezpečuje koncový bod metadat.</span><span class="sxs-lookup"><span data-stu-id="6e988-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="6e988-109">Ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` který implementuje servisní smlouvy.</span><span class="sxs-lookup"><span data-stu-id="6e988-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="6e988-110">V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována internetovou informační službou (IIS).</span><span class="sxs-lookup"><span data-stu-id="6e988-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e988-111">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="6e988-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6e988-112">Pro službu vystavit metadata, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> musí být nakonfigurován ve službě.</span><span class="sxs-lookup"><span data-stu-id="6e988-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="6e988-113">Pokud je toto chování k dispozici, můžete publikovat metadata <xref:System.ServiceModel.Description.IMetadataExchange> konfigurací koncového bodu vystavit smlouvy jako implementace protokolu WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="6e988-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="6e988-114">Pro pohodlí, tato smlouva byla dána zkrácený název konfigurace "IMetadataExchange".</span><span class="sxs-lookup"><span data-stu-id="6e988-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="6e988-115">Tato ukázka `mexHttpBinding`používá , což je standardní vazba pohodlí, která je ekvivalentní `wsHttpBinding` s režimem zabezpečení nastavena na `None`.</span><span class="sxs-lookup"><span data-stu-id="6e988-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="6e988-116">V koncovém bodě se používá relativní adresa "mex", která při vyřešení oproti základní `http://localhost/servicemodelsamples/service.svc/mex`adrese služeb vede k adrese koncového bodu .</span><span class="sxs-lookup"><span data-stu-id="6e988-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="6e988-117">Následující ukazuje konfiguraci chování:</span><span class="sxs-lookup"><span data-stu-id="6e988-117">The following shows the behavior configuration:</span></span>  
  
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
  
 <span data-ttu-id="6e988-118">Následující ukazuje koncový bod MEX.</span><span class="sxs-lookup"><span data-stu-id="6e988-118">The following shows the MEX endpoint.</span></span>  
  
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
  
 <span data-ttu-id="6e988-119">Tato ukázka <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> nastaví vlastnost `true`, která také zveřejňuje metadata služby pomocí HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="6e988-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="6e988-120">Chcete-li povolit koncový bod metadat HTTP GET, musí mít služba základní adresu HTTP.</span><span class="sxs-lookup"><span data-stu-id="6e988-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="6e988-121">Řetězec `?wsdl` dotazu se používá na základní adresu služby pro přístup k metadatům.</span><span class="sxs-lookup"><span data-stu-id="6e988-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="6e988-122">Chcete-li například zobrazit WSDL pro službu ve webovém prohlížeči, použijte adresu `http://localhost/servicemodelsamples/service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="6e988-122">For example, to see the WSDL for the service in a Web browser you would use the address `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span> <span data-ttu-id="6e988-123">Toto chování můžete také použít k vystavení metadat <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> `true`přes protokol HTTPS nastavením na .</span><span class="sxs-lookup"><span data-stu-id="6e988-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="6e988-124">To vyžaduje základní adresu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6e988-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="6e988-125">Chcete-li získat přístup ke koncovému bodu MEX služby, použijte [nástroj ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)</span><span class="sxs-lookup"><span data-stu-id="6e988-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="6e988-126">Tím se vygeneruje klient na základě metadat služby.</span><span class="sxs-lookup"><span data-stu-id="6e988-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="6e988-127">Chcete-li získat přístup k metadatům služby `http://localhost/servicemodelsamples/service.svc?wsdl`pomocí protokolu HTTP GET, přejděte do prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="6e988-127">To access the service's metadata using HTTP GET, point your browser to `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span>  
  
 <span data-ttu-id="6e988-128">Pokud toto chování odeberete a pokusíte se otevřít službu, získáte výjimku.</span><span class="sxs-lookup"><span data-stu-id="6e988-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="6e988-129">K této chybě dochází, protože bez chování `IMetadataExchange` koncový bod nakonfigurovaný se smlouvou nemá žádnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="6e988-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="6e988-130">Pokud nastavíte `HttpGetEnabled` na `false`, zobrazí se místo zobrazení metadat služby na stránce nápovědy Služby.</span><span class="sxs-lookup"><span data-stu-id="6e988-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6e988-131">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="6e988-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6e988-132">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6e988-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="6e988-133">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6e988-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6e988-134">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6e988-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6e988-135">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="6e988-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6e988-136">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="6e988-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6e988-137">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="6e988-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6e988-138">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="6e988-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
