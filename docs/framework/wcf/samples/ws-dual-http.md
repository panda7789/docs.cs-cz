---
title: WS Dual Http
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57fea95db5bf1536b41b282bedab55a9deef8e8c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ws-dual-http"></a><span data-ttu-id="b27d6-102">WS Dual Http</span><span class="sxs-lookup"><span data-stu-id="b27d6-102">WS Dual Http</span></span>
<span data-ttu-id="b27d6-103">Ukázka duální Http ukazuje, jak nakonfigurovat `WSDualHttpBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="b27d6-103">The Dual Http sample demonstrates how to configure the `WSDualHttpBinding` binding.</span></span> <span data-ttu-id="b27d6-104">Tato ukázka se skládá z konzoly programu klienta (.exe) a služby knihovny (DLL) hostované Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="b27d6-104">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="b27d6-105">Služba se implementuje duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b27d6-105">The service implements a duplex contract.</span></span> <span data-ttu-id="b27d6-106">Kontrakt je definována `ICalculatorDuplex` rozhraní, která zpřístupňuje matematické operace (přidat, odečíst, násobit a dělit).</span><span class="sxs-lookup"><span data-stu-id="b27d6-106">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="b27d6-107">V této ukázce `ICalculatorDuplex` rozhraní, které umožňuje provádět matematické operace, výpočet výsledku běžící přes relaci klienta.</span><span class="sxs-lookup"><span data-stu-id="b27d6-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over the session.</span></span> <span data-ttu-id="b27d6-108">Služba nezávisle, vrátí výsledky na `ICalculatorDuplexCallback` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b27d6-108">Independently, the service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="b27d6-109">Duplexní kontrakt vyžaduje relaci, protože kontextu musí být stanovena ke korelaci sadu zprávy odesílané mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="b27d6-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between client and service.</span></span> <span data-ttu-id="b27d6-110">`WSDualHttpBinding` Vazba podporuje duplexní komunikace.</span><span class="sxs-lookup"><span data-stu-id="b27d6-110">The `WSDualHttpBinding` binding supports duplex communication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b27d6-111">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b27d6-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b27d6-112">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="b27d6-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b27d6-113">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b27d6-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b27d6-114">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b27d6-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b27d6-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b27d6-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`  
  
 <span data-ttu-id="b27d6-116">Ke konfiguraci koncového bodu služby pomocí `WSDualHttpBinding`, zadejte vazby v konfiguraci koncového bodu, jak je vidět.</span><span class="sxs-lookup"><span data-stu-id="b27d6-116">To configure a service endpoint with the `WSDualHttpBinding`, specify the binding in the endpoint configuration as shown.</span></span>  
  
```xml  
<endpoint address=""  
         binding="wsDualHttpBinding"  
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
```  
  
 <span data-ttu-id="b27d6-117">Na klientovi je nutné nakonfigurovat adresu, která server můžete použít pro připojení k klienta, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b27d6-117">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
         "http://localhost/servicemodelsamples/service.svc"   
         binding="wsDualHttpBinding"   
         bindingConfiguration="Binding1"   
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
  </client>  
  
  <bindings>  
    <!-- Configure a WSDualHttpBinding that supports duplex -->  
    <!-- communication. -->  
    <wsDualHttpBinding>  
      <binding name="Binding1"  
               clientBaseAddress="http://localhost:8000/myClient/"  
               useDefaultWebProxy="true"  
               bypassProxyOnLocal="false">  
      </binding>  
    </wsDualHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="b27d6-118">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="b27d6-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b27d6-119">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="b27d6-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate client once the output is displayed.  
  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 <span data-ttu-id="b27d6-120">Když spustíte ukázku, uvidíte zprávy vrácen do klienta na rozhraní zpětné volání odeslaných ze služby.</span><span class="sxs-lookup"><span data-stu-id="b27d6-120">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="b27d6-121">Zobrazí se každý zprostředkující výsledek, za nímž následuje celý rovnice po dokončení všech operací.</span><span class="sxs-lookup"><span data-stu-id="b27d6-121">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="b27d6-122">Stisknutím klávesy ENTER vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="b27d6-122">Press ENTER to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b27d6-123">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="b27d6-123">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b27d6-124">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="b27d6-124">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="b27d6-125">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b27d6-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="b27d6-126">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b27d6-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="b27d6-127">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b27d6-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b27d6-128">Při spuštění klienta v počítači konfiguraci, nezapomeňte nahradit localhost v obou `address` atribut [koncový bod](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu a `clientBaseAddress` atribut [ \< Vazba >](../../../../docs/framework/misc/binding.md) element [ \<– wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element s názvem příslušný počítač, jak je uvedené:</span><span class="sxs-lookup"><span data-stu-id="b27d6-128">When running the client in a cross-machine configuration, be sure to replace localhost in both the `address` attribute of the [endpoint](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element and the `clientBaseAddress` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown:</span></span>  
  
    ```xml  
    <client>  
        <endpoint name = ""  
          address=  
         "http://service_machine_name/servicemodelsamples/service.svc"  
        />  
    </client>  
    ...  
    <wsDualHttpBinding>  
        <binding name="DuplexBinding" clientBaseAddress=  
            "http://client_machine_name:8000/myClient/">  
        </binding>  
    </wsDualHttpBinding>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b27d6-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="b27d6-129">See Also</span></span>
