---
title: Adresování
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: a59c3b354404169c2baadd4ab8c2702728d9a891
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002934"
---
# <a name="addressing"></a><span data-ttu-id="b8128-102">Adresování</span><span class="sxs-lookup"><span data-stu-id="b8128-102">Addressing</span></span>
<span data-ttu-id="b8128-103">Příklad adresování ukazuje různé aspekty a vlastnosti adresy koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b8128-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="b8128-104">Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b8128-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="b8128-105">V této ukázce je služba v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="b8128-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="b8128-106">Službu a klienta jsou konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="b8128-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="b8128-107">Služba definuje několik koncových bodů pomocí kombinace relativní a absolutní koncový bod adresy.</span><span class="sxs-lookup"><span data-stu-id="b8128-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8128-108">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b8128-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b8128-109">Konfigurační soubor služby definuje čtyři koncových bodů a základní adresa.</span><span class="sxs-lookup"><span data-stu-id="b8128-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="b8128-110">Základní adresa určena pomocí elementu přidat v části service/hostitele/baseAddresses, jak je ukázáno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b8128-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="b8128-111">První definice koncového bodu je znázorněno v následující ukázková konfigurace určuje relativní adresa, což znamená, že adresa koncového bodu je kombinací základní adresu a relativní adresu dle pravidel složení identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="b8128-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="b8128-112">V takovém případě je relativní adresa prázdná (""), takže adresu koncového bodu je stejný jako základní adresu.</span><span class="sxs-lookup"><span data-stu-id="b8128-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="b8128-113">Adresa skutečný koncový bod je `http://localhost:8000/servicemodelsamples/service`.</span><span class="sxs-lookup"><span data-stu-id="b8128-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>
  
 <span data-ttu-id="b8128-114">Druhá definice koncového bodu také určuje relativní adresa, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b8128-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="b8128-115">Relativní adresa "test", se připojí k základní adrese.</span><span class="sxs-lookup"><span data-stu-id="b8128-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="b8128-116">Adresa skutečný koncový bod je `http://localhost:8000/servicemodelsamples/service/test`.</span><span class="sxs-lookup"><span data-stu-id="b8128-116">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>
  
 <span data-ttu-id="b8128-117">Třetí definice koncového bodu určuje absolutní adresu, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b8128-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="b8128-118">Základní adresa hraje žádná role v adrese.</span><span class="sxs-lookup"><span data-stu-id="b8128-118">The base address plays no role in the address.</span></span> <span data-ttu-id="b8128-119">Adresa skutečný koncový bod je `http://localhost:8001/hello/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="b8128-119">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>
  
 <span data-ttu-id="b8128-120">Na čtvrté adresu koncového bodu určuje absolutní adresu a různé přenosové – TCP.</span><span class="sxs-lookup"><span data-stu-id="b8128-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="b8128-121">Základní adresa hraje žádná role v adrese.</span><span class="sxs-lookup"><span data-stu-id="b8128-121">The base address plays no role in the address.</span></span> <span data-ttu-id="b8128-122">Adresa skutečný koncový bod je `net.tcp://localhost:9000/servicemodelsamples/service`.</span><span class="sxs-lookup"><span data-stu-id="b8128-122">The actual endpoint address is `net.tcp://localhost:9000/servicemodelsamples/service`.</span></span>
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</service>  
```  
  
 <span data-ttu-id="b8128-123">Klient přistupuje k právě jeden z koncových bodů služby čtyři, ale všechny čtyři jsou definovány v jeho konfiguračnímu souboru.</span><span class="sxs-lookup"><span data-stu-id="b8128-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="b8128-124">Klient vybere koncový bod, když vytváří `CalculatorProxy` objektu.</span><span class="sxs-lookup"><span data-stu-id="b8128-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="b8128-125">Tak, že změníte název konfigurace z `CalculatorEndpoint1` prostřednictvím `CalculatorEndpoint4`, je také možné získat jednotlivé koncové body.</span><span class="sxs-lookup"><span data-stu-id="b8128-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="b8128-126">Při spuštění ukázky služby zobrazí adresy, vazby název a název smlouvy pro každý z jeho koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="b8128-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="b8128-127">Koncový bod metadat exchange (MEX) je jenom další koncový bod z pohledu hostitele ServiceHost, zobrazí se v seznamu.</span><span class="sxs-lookup"><span data-stu-id="b8128-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
```  
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
  
 <span data-ttu-id="b8128-128">Když spustíte klienta, operace žádosti a odpovědi se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="b8128-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="b8128-129">Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="b8128-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8128-130">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="b8128-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b8128-131">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8128-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b8128-132">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8128-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b8128-133">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8128-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b8128-134">Pokud používáte Svcutil.exe k opětovnému vytvoření konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly klientský kód.</span><span class="sxs-lookup"><span data-stu-id="b8128-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8128-135">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="b8128-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b8128-136">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b8128-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b8128-137">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b8128-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8128-138">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b8128-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
