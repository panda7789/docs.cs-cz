---
title: Adresování
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 55bb30ba3df80e41986b1337f8732dd8ad3231ff
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463772"
---
# <a name="addressing"></a><span data-ttu-id="67b61-102">Adresování</span><span class="sxs-lookup"><span data-stu-id="67b61-102">Addressing</span></span>
<span data-ttu-id="67b61-103">Adresování ukázka ukazuje různé aspekty a funkce adresy koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="67b61-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="67b61-104">Ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="67b61-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="67b61-105">V této ukázce je služba hostována samostatně.</span><span class="sxs-lookup"><span data-stu-id="67b61-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="67b61-106">Služba i klient jsou konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="67b61-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="67b61-107">Služba definuje více koncových bodů pomocí kombinace relativní a absolutní adresy koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="67b61-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67b61-108">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="67b61-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="67b61-109">Konfigurační soubor služby určuje základní adresu a čtyři koncové body.</span><span class="sxs-lookup"><span data-stu-id="67b61-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="67b61-110">Základní adresa je určena pomocí prvku add, v části service/host/baseAddresses, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="67b61-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service name="Microsoft.ServiceModel.Samples.CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />  
    </baseAddresses>  
  </host>  
</service>  
```  
  
 <span data-ttu-id="67b61-111">První definice koncového bodu zobrazená v následující konfiguraci ukázky určuje relativní adresu, což znamená, že adresa koncového bodu je kombinací základní adresy a relativní adresy podle pravidel složení identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="67b61-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="67b61-112">V tomto případě je relativní adresa prázdná (""), takže adresa koncového bodu je stejná jako základní adresa.</span><span class="sxs-lookup"><span data-stu-id="67b61-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="67b61-113">Skutečná adresa koncového `http://localhost:8000/servicemodelsamples/service`bodu je .</span><span class="sxs-lookup"><span data-stu-id="67b61-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>
  
 <span data-ttu-id="67b61-114">Definice druhého koncového bodu také určuje relativní adresu, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="67b61-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="67b61-115">Relativní adresa "test", je připojen k základní adrese.</span><span class="sxs-lookup"><span data-stu-id="67b61-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="67b61-116">Skutečná adresa koncového `http://localhost:8000/servicemodelsamples/service/test`bodu je .</span><span class="sxs-lookup"><span data-stu-id="67b61-116">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>
  
 <span data-ttu-id="67b61-117">Definice třetího koncového bodu určuje absolutní adresu, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="67b61-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="67b61-118">Základní adresa nehraje žádnou roli v adrese.</span><span class="sxs-lookup"><span data-stu-id="67b61-118">The base address plays no role in the address.</span></span> <span data-ttu-id="67b61-119">Skutečná adresa koncového `http://localhost:8001/hello/servicemodelsamples`bodu je .</span><span class="sxs-lookup"><span data-stu-id="67b61-119">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>
  
 <span data-ttu-id="67b61-120">Čtvrtá adresa koncového bodu určuje absolutní adresu a jiný přenos – TCP.</span><span class="sxs-lookup"><span data-stu-id="67b61-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="67b61-121">Základní adresa nehraje žádnou roli v adrese.</span><span class="sxs-lookup"><span data-stu-id="67b61-121">The base address plays no role in the address.</span></span> <span data-ttu-id="67b61-122">Skutečná adresa koncového `net.tcp://localhost:9000/servicemodelsamples/service`bodu je .</span><span class="sxs-lookup"><span data-stu-id="67b61-122">The actual endpoint address is `net.tcp://localhost:9000/servicemodelsamples/service`.</span></span>
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="67b61-123">Klient přistupuje pouze k jednomu ze čtyř koncových bodů služby, ale všechny čtyři jsou definovány v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="67b61-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="67b61-124">Klient vybere koncový bod při vytvoření `CalculatorProxy` objektu.</span><span class="sxs-lookup"><span data-stu-id="67b61-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="67b61-125">Změnou názvu konfigurace `CalculatorEndpoint1` `CalculatorEndpoint4`z aplikace můžete uplatnit každý z koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="67b61-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="67b61-126">Při spuštění ukázky služba výčet adresu, název vazby a název smlouvy pro každý z jeho koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="67b61-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="67b61-127">Koncový bod výměny metadat (MEX) je pouze další koncový bod z pohledu ServiceHost, takže se zobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="67b61-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
```console  
Service endpoints:  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/test  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8001/hello/servicemodelsamples  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  net.tcp://localhost:9000/servicemodelsamples/service  
           binding:  NetTcpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/mex  
           binding:  MetadataExchangeHttpBinding  
           contract: IMetadataExchange  
  
The service is ready.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="67b61-128">Při spuštění klienta jsou požadavky na operaci a odpovědi zobrazeny v systému Windows služby i klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="67b61-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="67b61-129">Stisknutím klávesy ENTER v každém okně konzoly vypněte službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="67b61-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="67b61-130">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="67b61-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="67b61-131">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="67b61-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="67b61-132">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="67b61-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="67b61-133">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="67b61-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="67b61-134">Pokud používáte Svcutil.exe k obnovení konfigurace pro tuto ukázku, nezapomeňte upravit název koncového bodu v konfiguraci klienta tak, aby odpovídalkódu klienta.</span><span class="sxs-lookup"><span data-stu-id="67b61-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="67b61-135">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="67b61-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="67b61-136">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="67b61-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="67b61-137">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="67b61-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="67b61-138">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="67b61-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
