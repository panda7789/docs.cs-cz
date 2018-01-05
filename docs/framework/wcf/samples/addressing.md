---
title: "Adresování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 21339d071ac26f073d0495814744535bd84f3a22
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="addressing"></a><span data-ttu-id="b0d7a-102">Adresování</span><span class="sxs-lookup"><span data-stu-id="b0d7a-102">Addressing</span></span>
<span data-ttu-id="b0d7a-103">Ukázka Addressing ukazuje různé aspekty a funkce adresy koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="b0d7a-104">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b0d7a-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="b0d7a-105">V této ukázce se hostuje sama službu.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="b0d7a-106">Službu a klienta jsou konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="b0d7a-107">Služby definuje víc koncových bodů pomocí kombinace adresy relativní a absolutní koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0d7a-108">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b0d7a-109">Konfigurační soubor služby definuje čtyři koncové body a základní adresu.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="b0d7a-110">Základní adresa je zadán pomocí elementu přidat pod služby nebo hostitele nebo baseAddresses, jak je předvedeno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="b0d7a-111">První koncový bod definice znázorňuje následující ukázka konfigurace určuje relativní adresu, která znamená, že adresa koncového bodu je kombinací základní adresu a relativní adresy následující pravidla složení identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="b0d7a-112">V takovém případě je relativní adresa prázdná (""), takže adresa koncového bodu je stejný jako základní adresu.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="b0d7a-113">Adresa skutečný koncový bod je http://localhost: 8000/servicemodelsamples nebo služby.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-113">The actual endpoint address is http://localhost:8000/servicemodelsamples/service.</span></span>  
  
 <span data-ttu-id="b0d7a-114">Druhý definice služby endpoint také určuje relativní adresu, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="b0d7a-115">Relativní adresu "test", připojí se k základní adresu.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="b0d7a-116">Adresa skutečný koncový bod je http://localhost: 8000/servicemodelsamples/service/testování.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-116">The actual endpoint address is http://localhost:8000/servicemodelsamples/service/test.</span></span>  
  
 <span data-ttu-id="b0d7a-117">Třetí definice služby endpoint určuje absolutní adresu, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="b0d7a-118">Základní adresa hraje žádný atribut role v adrese.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-118">The base address plays no role in the address.</span></span> <span data-ttu-id="b0d7a-119">Adresa skutečný koncový bod je http://localhost:8001/hello nebo servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-119">The actual endpoint address is http://localhost:8001/hello/servicemodelsamples.</span></span>  
  
 <span data-ttu-id="b0d7a-120">Čtvrtý adresa koncového bodu určuje absolutní adresu a různé přenosové – TCP.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="b0d7a-121">Základní adresa hraje žádný atribut role v adrese.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-121">The base address plays no role in the address.</span></span> <span data-ttu-id="b0d7a-122">Adresa skutečný koncový bod je net.tcp://localhost: 9000/servicemodelsamples nebo služby.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-122">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
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
  
 <span data-ttu-id="b0d7a-123">Klient přistupuje k právě jeden z koncových bodů služby čtyři, ale všechny čtyři jsou definovány v konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="b0d7a-124">Klient vybere koncový bod, když vytváří `CalculatorProxy` objektu.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="b0d7a-125">Změna názvu konfigurace z `CalculatorEndpoint1` prostřednictvím `CalculatorEndpoint4`, mohou vykonávat všechny koncové body.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="b0d7a-126">Při spuštění ukázky, zobrazí služba adresy, vazby název a název kontraktu pro každý z jeho koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="b0d7a-127">Koncový bod metadat exchange (MEX) je právě jiným koncovým bodem z hlediska hostiteli služby, takže se zobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
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
  
 <span data-ttu-id="b0d7a-128">Při spuštění klienta operaci požadavky a odpovědi se zobrazují v oknech konzoly služby a klienta.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="b0d7a-129">Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b0d7a-130">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="b0d7a-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b0d7a-131">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b0d7a-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b0d7a-132">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b0d7a-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b0d7a-133">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b0d7a-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b0d7a-134">Pokud používáte Svcutil.exe znovu vygenerovat konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b0d7a-135">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b0d7a-136">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b0d7a-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b0d7a-137">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b0d7a-138">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b0d7a-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
  
## <a name="see-also"></a><span data-ttu-id="b0d7a-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0d7a-139">See Also</span></span>
