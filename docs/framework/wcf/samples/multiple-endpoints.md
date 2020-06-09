---
title: Víc koncových bodů
ms.date: 03/30/2017
helpviewer_keywords:
- Multiple EndPoints
ms.assetid: 8f0c2e1f-9aee-41c2-8301-c72b7f664412
ms.openlocfilehash: 5f2915f4f0170f85c27c6c809575d1c56d40774b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602476"
---
# <a name="multiple-endpoints"></a><span data-ttu-id="a9e68-102">Víc koncových bodů</span><span class="sxs-lookup"><span data-stu-id="a9e68-102">Multiple Endpoints</span></span>
<span data-ttu-id="a9e68-103">Ukázka více koncových bodů ukazuje, jak nakonfigurovat více koncových bodů ve službě a jak komunikovat s každým koncovým bodem z klienta.</span><span class="sxs-lookup"><span data-stu-id="a9e68-103">The Multiple Endpoints sample demonstrates how to configure multiple endpoints on a service and how to communicate with each endpoint from a client.</span></span> <span data-ttu-id="a9e68-104">Tato ukázka je založena na [Začínáme](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a9e68-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="a9e68-105">Konfigurace služby byla změněna tak, aby definovala dva koncové body, které podporují `ICalculator` kontrakt, ale každou na jiné adrese s použitím jiné vazby.</span><span class="sxs-lookup"><span data-stu-id="a9e68-105">The service configuration has been modified to define two endpoints that support the `ICalculator` contract, but each at a different address using a different binding.</span></span> <span data-ttu-id="a9e68-106">Konfigurace a kód klienta byly upraveny tak, aby komunikovaly s oběma koncovými body služby.</span><span class="sxs-lookup"><span data-stu-id="a9e68-106">The client configuration and code have been modified to communicate with both of the service endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9e68-107">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="a9e68-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a9e68-108">Soubor Web. config služby byl změněn tak, aby definoval dva koncové body, z nichž každá podporuje stejný `ICalculator` kontrakt, ale na různých adresách pomocí různých vazeb.</span><span class="sxs-lookup"><span data-stu-id="a9e68-108">The service Web.config file has been modified to define two endpoints, each supporting the same `ICalculator` contract, but at different addresses using different bindings.</span></span> <span data-ttu-id="a9e68-109">První koncový bod je definován na základní adrese pomocí `basicHttpBinding` vazby, která nemá povolenou možnost zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a9e68-109">The first endpoint is defined at the base address using a `basicHttpBinding` binding, which does not have security enabled.</span></span> <span data-ttu-id="a9e68-110">Druhý koncový bod je definovaný na adrese {BaseAddress}/Secure pomocí `wsHttpBinding` vazby, která je standardně zabezpečená pomocí ověřování WS-Security s ověřováním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a9e68-110">The second endpoint is defined at {baseaddress}/secure using a `wsHttpBinding` binding, which is secure by default, using WS-Security with Windows authentication.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- This endpoint is exposed at the base address provided by host:  
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- secure endpoint exposed at {base address}/secure:  
       http://localhost/servicemodelsamples/service.svc/secure -->  
  <endpoint address="secure"  
            binding="wsHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  ...  
</service>  
```  
  
 <span data-ttu-id="a9e68-111">Oba koncové body jsou také nakonfigurovány na klientovi.</span><span class="sxs-lookup"><span data-stu-id="a9e68-111">Both endpoints are also configured on the client.</span></span> <span data-ttu-id="a9e68-112">Tyto koncové body mají křestní jména, aby volající mohl předat do konstruktoru klienta požadovaný název koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a9e68-112">These endpoints are given names so that the caller can pass the desired endpoint name into the constructor of the client.</span></span>  
  
```xml  
<client>  
  <!-- Passing "basic" into the constructor of the CalculatorClient  
       class selects this endpoint.-->  
  <endpoint name="basic"  
            address="http://localhost/servicemodelsamples/service.svc"
            binding="basicHttpBinding"
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- Passing "secure" into the constructor of the CalculatorClient  
       class selects this endpoint.-->  
  <endpoint name="secure"  
            address="http://localhost/servicemodelsamples/service.svc/secure"
            binding="wsHttpBinding"
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 <span data-ttu-id="a9e68-113">Klient používá oba koncové body, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a9e68-113">The client uses both endpoints as shown in the following code.</span></span>  
  
```csharp  
static void Main()  
{  
    // Create a client to the basic endpoint configuration.  
    CalculatorClient client = new CalculatorClient("basic");  
    Console.WriteLine("Communicate with basic endpoint.");  
    // call operations  
    DoCalculations(client);  
  
    // Close the client and release resources.  
    client.Close();  
  
    // Create a client to the secure endpoint configuration.  
    client = new CalculatorClient("secure");  
    Console.WriteLine("Communicate with secure endpoint.");  
    // Call operations.  
    DoCalculations(client);  
  
    // Close the client and release resources.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="a9e68-114">Když spustíte klienta nástroje, zobrazí se interakce s oběma koncovými body.</span><span class="sxs-lookup"><span data-stu-id="a9e68-114">When you run the client, interactions with both endpoints are displayed.</span></span>  
  
```console
Communicate with basic endpoint.  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Communicate with secure endpoint.  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a9e68-115">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="a9e68-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a9e68-116">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a9e68-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a9e68-117">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a9e68-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a9e68-118">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a9e68-118">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a9e68-119">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="a9e68-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a9e68-120">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="a9e68-120">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a9e68-121">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="a9e68-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a9e68-122">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a9e68-122">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpoints`  
