---
title: Spolehlivá relace s vlastními vazbami
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: 3ccf0c603c4710c3cdac1e0dd68a4a6a2e04c2d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33500760"
---
# <a name="custom-binding-reliable-session"></a><span data-ttu-id="d72a1-102">Spolehlivá relace s vlastními vazbami</span><span class="sxs-lookup"><span data-stu-id="d72a1-102">Custom Binding Reliable Session</span></span>
<span data-ttu-id="d72a1-103">Vlastní vazby je definována seřazený seznam prvky diskrétní vazby.</span><span class="sxs-lookup"><span data-stu-id="d72a1-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="d72a1-104">Tento příklad ukazuje, jak nakonfigurovat vlastní vazby s různými přenosu a zpráva kódování elementy, zejména povolení spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="d72a1-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d72a1-105">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="d72a1-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d72a1-106">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="d72a1-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d72a1-107">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d72a1-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d72a1-108">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d72a1-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`  
  
## <a name="sample-details"></a><span data-ttu-id="d72a1-109">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d72a1-109">Sample Details</span></span>  
 <span data-ttu-id="d72a1-110">Spolehlivé relace poskytují funkce pro spolehlivé zasílání zpráv a relace.</span><span class="sxs-lookup"><span data-stu-id="d72a1-110">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="d72a1-111">Spolehlivé zasílání zpráv opakování komunikace při selhání a umožňuje záruky doručení, jako je například v daném pořadí doručení zpráv, které mají být zadán.</span><span class="sxs-lookup"><span data-stu-id="d72a1-111">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="d72a1-112">Relace uchování stavu pro klienty mezi volání.</span><span class="sxs-lookup"><span data-stu-id="d72a1-112">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="d72a1-113">Ukázka implementuje relace pro zachování stavu klienta a určuje záruky doručení v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d72a1-113">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="d72a1-114">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="d72a1-114">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="d72a1-115">Spolehlivá relace funkcí jsou povolené a nakonfigurované v konfiguračních souborech aplikace pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="d72a1-115">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d72a1-116">Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d72a1-116">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d72a1-117">Řazení elementů vazby je důležité k definování vlastní vazby, protože každý představuje vrstvy v zásobníku kanál (viz [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="d72a1-117">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span>  
  
 <span data-ttu-id="d72a1-118">Konfigurace služby pro ukázku je definována, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="d72a1-118">The service configuration for the sample is defined as shown in the following code example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
        <!-- specify customBinding binding and a binding configuration to use -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <reliableSession />  
          <security authenticationMode="SecureConversation"  
                     requireSecurityContextCancellation="true">  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />  
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"  
                        hostNameComparisonMode="StrongWildcard"   
                        proxyAuthenticationScheme="Anonymous" realm=""   
                        useDefaultWebProxy="true" />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="d72a1-119">Při spuštění ve scénáři mezi počítači, musíte změnit adresa koncového bodu klienta podle názvu hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="d72a1-119">When running in a cross-machine scenario, you must change client's endpoint address to reflect the host name of the service.</span></span>  
  
 <span data-ttu-id="d72a1-120">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="d72a1-120">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d72a1-121">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="d72a1-121">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d72a1-122">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="d72a1-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d72a1-123">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="d72a1-123">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command:</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="d72a1-124">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d72a1-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="d72a1-125">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d72a1-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="d72a1-126">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d72a1-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d72a1-127">Při spuštění klienta v počítači konfiguraci, nezapomeňte nahradit "localhost" v obou `address` atribut [ \<endpoint >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu a `clientBaseAddress` atribut [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) s názvem příslušný počítač, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d72a1-127">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element and the `clientBaseAddress` attribute of the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) with the name of the appropriate machine, as shown in the following example.</span></span>  
  
    ```xml  
    <endpoint name = ""  
    address="http://service_machine_name/servicemodelsamples/service.svc"  
    ... />  
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d72a1-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d72a1-128">See Also</span></span>
