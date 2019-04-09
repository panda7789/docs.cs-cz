---
title: Víc koncových bodů
ms.date: 03/30/2017
helpviewer_keywords:
- Multiple EndPoints
ms.assetid: 8f0c2e1f-9aee-41c2-8301-c72b7f664412
ms.openlocfilehash: 438c321e44f04060a733b90ccdbf02caba9406c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112707"
---
# <a name="multiple-endpoints"></a><span data-ttu-id="e8be0-102">Víc koncových bodů</span><span class="sxs-lookup"><span data-stu-id="e8be0-102">Multiple Endpoints</span></span>
<span data-ttu-id="e8be0-103">Více koncových bodů Ukázka předvádí, jak konfigurovat několik koncových bodů ve službě a komunikovat s každého koncového bodu z klienta.</span><span class="sxs-lookup"><span data-stu-id="e8be0-103">The Multiple Endpoints sample demonstrates how to configure multiple endpoints on a service and how to communicate with each endpoint from a client.</span></span> <span data-ttu-id="e8be0-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e8be0-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="e8be0-105">Chcete-li definovat dva koncové body, které podporují byla změněna konfigurace služby `ICalculator` smlouvy, ale každý na jinou adresu pomocí jinou vazbou.</span><span class="sxs-lookup"><span data-stu-id="e8be0-105">The service configuration has been modified to define two endpoints that support the `ICalculator` contract, but each at a different address using a different binding.</span></span> <span data-ttu-id="e8be0-106">Konfigurace klienta a kód se upravila tak komunikovat s oběma koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="e8be0-106">The client configuration and code have been modified to communicate with both of the service endpoints.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8be0-107">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e8be0-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e8be0-108">Soubor Web.config služby byla změněna definovat dva koncové body, nichž každá podporuje stejné `ICalculator` smlouvy, ale na různé adresy pomocí různých vazeb.</span><span class="sxs-lookup"><span data-stu-id="e8be0-108">The service Web.config file has been modified to define two endpoints, each supporting the same `ICalculator` contract, but at different addresses using different bindings.</span></span> <span data-ttu-id="e8be0-109">První koncový bod je definována na základní adresu pomocí `basicHttpBinding` vazby, který nemá povoleno zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e8be0-109">The first endpoint is defined at the base address using a `basicHttpBinding` binding, which does not have security enabled.</span></span> <span data-ttu-id="e8be0-110">Druhý je definovaný v {baseaddress} / zabezpečené pomocí `wsHttpBinding` vazby, který je ve výchozím nastavení zabezpečený, pomocí WS-Security s ověřováním Windows.</span><span class="sxs-lookup"><span data-stu-id="e8be0-110">The second endpoint is defined at {baseaddress}/secure using a `wsHttpBinding` binding, which is secure by default, using WS-Security with Windows authentication.</span></span>  
  
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
  
 <span data-ttu-id="e8be0-111">Oba koncové body jsou také nakonfigurovaná na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="e8be0-111">Both endpoints are also configured on the client.</span></span> <span data-ttu-id="e8be0-112">Tyto koncové body jsou křestní jména, aby volající můžete předat název požadovaného koncového bodu do konstruktoru objektu klienta.</span><span class="sxs-lookup"><span data-stu-id="e8be0-112">These endpoints are given names so that the caller can pass the desired endpoint name into the constructor of the client.</span></span>  
  
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
  
 <span data-ttu-id="e8be0-113">Klient použije oba koncové body, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e8be0-113">The client uses both endpoints as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="e8be0-114">Když spustíte klienta, zobrazí se interakce se oba koncové body.</span><span class="sxs-lookup"><span data-stu-id="e8be0-114">When you run the client, interactions with both endpoints are displayed.</span></span>  
  
```  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e8be0-115">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="e8be0-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e8be0-116">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e8be0-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e8be0-117">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e8be0-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="e8be0-118">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e8be0-118">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e8be0-119">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="e8be0-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e8be0-120">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e8be0-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e8be0-121">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e8be0-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e8be0-122">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e8be0-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpoints`  
