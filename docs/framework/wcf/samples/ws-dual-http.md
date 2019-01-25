---
title: WS Dual Http
ms.date: 03/30/2017
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
ms.openlocfilehash: 93097c5f13a45ba399ec90d6282db8ca277a8ede
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640547"
---
# <a name="ws-dual-http"></a><span data-ttu-id="3ff6d-102">WS Dual Http</span><span class="sxs-lookup"><span data-stu-id="3ff6d-102">WS Dual Http</span></span>
<span data-ttu-id="3ff6d-103">Duální Http Ukázka předvádí, jak nakonfigurovat `WSDualHttpBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-103">The Dual Http sample demonstrates how to configure the `WSDualHttpBinding` binding.</span></span> <span data-ttu-id="3ff6d-104">Tento příklad se skládá z programu konzoly klienta (.exe) a služby knihovny (.dll) hostované v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="3ff6d-104">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="3ff6d-105">Služba implementuje duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-105">The service implements a duplex contract.</span></span> <span data-ttu-id="3ff6d-106">Smlouva je definován `ICalculatorDuplex` rozhraní, které zveřejňuje matematických operací (Přidat odečíst, násobení a dělení).</span><span class="sxs-lookup"><span data-stu-id="3ff6d-106">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="3ff6d-107">V této ukázce `ICalculatorDuplex` rozhraní umožňuje klientovi k provádění matematických operací spuštěných výsledek výpočtu přes relaci.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over the session.</span></span> <span data-ttu-id="3ff6d-108">Nezávisle na sobě, služba vrátí výsledky v `ICalculatorDuplexCallback` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-108">Independently, the service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="3ff6d-109">Duplexní kontrakt vyžaduje relaci, protože kontext musí být stanovena ke korelaci sadu zprávy odesílané mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between client and service.</span></span> <span data-ttu-id="3ff6d-110">`WSDualHttpBinding` Vazba podporuje duplexní komunikaci.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-110">The `WSDualHttpBinding` binding supports duplex communication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ff6d-111">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3ff6d-112">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3ff6d-113">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="3ff6d-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3ff6d-114">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3ff6d-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`  
  
 <span data-ttu-id="3ff6d-116">Konfigurace koncového bodu služby se `WSDualHttpBinding`, zadat vazby v konfiguraci koncového bodu, jak je znázorněno.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-116">To configure a service endpoint with the `WSDualHttpBinding`, specify the binding in the endpoint configuration as shown.</span></span>  
  
```xml  
<endpoint address=""  
         binding="wsDualHttpBinding"  
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
```  
  
 <span data-ttu-id="3ff6d-117">Na straně klienta je nutné nakonfigurovat adresu serveru můžete použít pro připojení ke klientovi, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-117">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="3ff6d-118">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3ff6d-119">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate client once the output is displayed.  
  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 <span data-ttu-id="3ff6d-120">Když spustíte ukázku, uvidíte zpráv vrácených do klienta na rozhraní zpětného volání odeslané ze služby.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-120">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="3ff6d-121">Zobrazí se každý přechodný výsledek, za nímž následuje celou rovnici. Po dokončení všech operací.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-121">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="3ff6d-122">Stiskněte klávesu ENTER pro vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-122">Press ENTER to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3ff6d-123">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="3ff6d-123">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3ff6d-124">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="3ff6d-124">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="3ff6d-125">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3ff6d-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="3ff6d-126">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3ff6d-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="3ff6d-127">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3ff6d-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3ff6d-128">Při spuštění klienta v konfiguraci mezi počítači, je potřeba, místo localhost v obou `address` atribut [koncový bod](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu a `clientBaseAddress` atribut [ \< Vytvoření vazby >](../../../../docs/framework/misc/binding.md) elementu [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element s názvem příslušný počítač, jak je vidět:</span><span class="sxs-lookup"><span data-stu-id="3ff6d-128">When running the client in a cross-machine configuration, be sure to replace localhost in both the `address` attribute of the [endpoint](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element and the `clientBaseAddress` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ff6d-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ff6d-129">See also</span></span>
