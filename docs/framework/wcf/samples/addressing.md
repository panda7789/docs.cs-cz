---
title: Adresování
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 3221a12a21aebe20e0f6822554937623dc3fbb8d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575963"
---
# <a name="addressing"></a><span data-ttu-id="01b33-102">Adresování</span><span class="sxs-lookup"><span data-stu-id="01b33-102">Addressing</span></span>
<span data-ttu-id="01b33-103">Ukázka adresování znázorňuje různé aspekty a funkce adres koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="01b33-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="01b33-104">Ukázka je založena na [Začínáme](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="01b33-104">The sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="01b33-105">V této ukázce je služba hostovaná v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="01b33-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="01b33-106">Služba i klient jsou konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="01b33-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="01b33-107">Služba definuje více koncových bodů pomocí kombinace relativních a absolutních adres koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="01b33-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01b33-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="01b33-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="01b33-109">Konfigurační soubor služby určuje základní adresu a čtyři koncové body.</span><span class="sxs-lookup"><span data-stu-id="01b33-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="01b33-110">Základní adresa je určena pomocí elementu add v části Služba/Hostitel/adres BaseAddresses, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="01b33-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="01b33-111">První definice koncového bodu uvedená v následující ukázkové konfiguraci Určuje relativní adresu, což znamená, že adresa koncového bodu je kombinací základní adresy a relativní adresy podle pravidel složení identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="01b33-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="01b33-112">V tomto případě je relativní adresa prázdná (""), takže adresa koncového bodu je stejná jako základní adresa.</span><span class="sxs-lookup"><span data-stu-id="01b33-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="01b33-113">Skutečná adresa koncového bodu je `http://localhost:8000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="01b33-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>
  
 <span data-ttu-id="01b33-114">Druhá definice koncového bodu také určuje relativní adresu, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="01b33-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="01b33-115">Relativní adresa "test" se připojí k základní adrese.</span><span class="sxs-lookup"><span data-stu-id="01b33-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="01b33-116">Skutečná adresa koncového bodu je `http://localhost:8000/servicemodelsamples/service/test` .</span><span class="sxs-lookup"><span data-stu-id="01b33-116">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>
  
 <span data-ttu-id="01b33-117">Třetí definice koncového bodu určuje absolutní adresu, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="01b33-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="01b33-118">Základní adresa nehraje v adrese žádnou roli.</span><span class="sxs-lookup"><span data-stu-id="01b33-118">The base address plays no role in the address.</span></span> <span data-ttu-id="01b33-119">Skutečná adresa koncového bodu je `http://localhost:8001/hello/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="01b33-119">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>
  
 <span data-ttu-id="01b33-120">Čtvrtá adresa koncového bodu určuje absolutní adresu a jiný přenos – TCP.</span><span class="sxs-lookup"><span data-stu-id="01b33-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="01b33-121">Základní adresa nehraje v adrese žádnou roli.</span><span class="sxs-lookup"><span data-stu-id="01b33-121">The base address plays no role in the address.</span></span> <span data-ttu-id="01b33-122">Skutečná adresa koncového bodu je `net.tcp://localhost:9000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="01b33-122">The actual endpoint address is `net.tcp://localhost:9000/servicemodelsamples/service`.</span></span>
  
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
  
 <span data-ttu-id="01b33-123">Klient přistupuje pouze k jednomu ze čtyř koncových bodů služby, ale všechny čtyři jsou definovány v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="01b33-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="01b33-124">Klient vybere koncový bod při vytváření `CalculatorProxy` objektu.</span><span class="sxs-lookup"><span data-stu-id="01b33-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="01b33-125">Změnou názvu konfigurace z nástroje `CalculatorEndpoint1` `CalculatorEndpoint4` můžete uplatnit jednotlivé koncové body.</span><span class="sxs-lookup"><span data-stu-id="01b33-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="01b33-126">Při spuštění ukázky služba vytvoří výčet adresy, názvu vazby a názvu kontraktu pro každý z jeho koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="01b33-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="01b33-127">Koncový bod výměny metadat (MEX) je pouze jiný koncový bod od perspektivy hostitele, takže se zobrazí v seznamu.</span><span class="sxs-lookup"><span data-stu-id="01b33-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
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
  
 <span data-ttu-id="01b33-128">Když spustíte klienta nástroje, požadavky na operace a odpovědi se zobrazí v oknech služba i klientská konzola.</span><span class="sxs-lookup"><span data-stu-id="01b33-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="01b33-129">V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.</span><span class="sxs-lookup"><span data-stu-id="01b33-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="01b33-130">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="01b33-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="01b33-131">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="01b33-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="01b33-132">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="01b33-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="01b33-133">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="01b33-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="01b33-134">Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídal kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="01b33-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="01b33-135">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="01b33-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="01b33-136">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="01b33-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="01b33-137">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="01b33-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="01b33-138">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="01b33-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
