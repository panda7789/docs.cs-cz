---
title: WS Dual Http
ms.date: 03/30/2017
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
ms.openlocfilehash: bc8958ab092f97e94a75bc366d576441c1a5bbbd
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424545"
---
# <a name="ws-dual-http"></a><span data-ttu-id="33027-102">WS Dual Http</span><span class="sxs-lookup"><span data-stu-id="33027-102">WS Dual Http</span></span>

<span data-ttu-id="33027-103">Dvojitá ukázka HTTP ukazuje, jak nakonfigurovat vazbu `WSDualHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="33027-103">The Dual Http sample demonstrates how to configure the `WSDualHttpBinding` binding.</span></span> <span data-ttu-id="33027-104">Tato ukázka se skládá z programu klientské konzoly (. exe) a knihovny služeb (. dll) hostované službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="33027-104">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="33027-105">Služba implementuje oboustranný kontrakt.</span><span class="sxs-lookup"><span data-stu-id="33027-105">The service implements a duplex contract.</span></span> <span data-ttu-id="33027-106">Kontrakt je definován rozhraním `ICalculatorDuplex`, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení).</span><span class="sxs-lookup"><span data-stu-id="33027-106">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="33027-107">V této ukázce rozhraní `ICalculatorDuplex` umožňuje klientovi provádět matematické operace, které vypočítávají výsledek spuštění přes relaci.</span><span class="sxs-lookup"><span data-stu-id="33027-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over the session.</span></span> <span data-ttu-id="33027-108">Nezávisle služba vrátí výsledky v rozhraní `ICalculatorDuplexCallback`.</span><span class="sxs-lookup"><span data-stu-id="33027-108">Independently, the service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="33027-109">Duplexní smlouva vyžaduje relaci, protože je nutné vytvořit kontext, který bude korelovat sadu zpráv odesílaných mezi klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="33027-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between client and service.</span></span> <span data-ttu-id="33027-110">Vazba `WSDualHttpBinding` podporuje duplexní komunikaci.</span><span class="sxs-lookup"><span data-stu-id="33027-110">The `WSDualHttpBinding` binding supports duplex communication.</span></span>

> [!NOTE]
> <span data-ttu-id="33027-111">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="33027-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="33027-112">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="33027-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="33027-113">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="33027-113">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="33027-114">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="33027-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="33027-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="33027-115">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`

<span data-ttu-id="33027-116">Pokud chcete nakonfigurovat koncový bod služby s `WSDualHttpBinding`, zadejte vazbu v konfiguraci koncového bodu, jak je znázorněno na obrázku.</span><span class="sxs-lookup"><span data-stu-id="33027-116">To configure a service endpoint with the `WSDualHttpBinding`, specify the binding in the endpoint configuration as shown.</span></span>

```xml
<endpoint address=""
         binding="wsDualHttpBinding"
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
```

<span data-ttu-id="33027-117">Na straně klienta je nutné nakonfigurovat adresu, kterou může server používat pro připojení ke klientovi, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="33027-117">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>

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

<span data-ttu-id="33027-118">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="33027-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="33027-119">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="33027-119">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate client once the output is displayed.

Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

<span data-ttu-id="33027-120">Při spuštění ukázky se zobrazí zprávy vracené klientovi do rozhraní zpětného volání odeslaného ze služby.</span><span class="sxs-lookup"><span data-stu-id="33027-120">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="33027-121">Po dokončení všech operací se zobrazí každý mezilehlé výsledek následovaný celým vzorcem.</span><span class="sxs-lookup"><span data-stu-id="33027-121">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="33027-122">Pro vypnutí klienta stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="33027-122">Press ENTER to shut down the client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="33027-123">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="33027-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="33027-124">Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.</span><span class="sxs-lookup"><span data-stu-id="33027-124">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="33027-125">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33027-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="33027-126">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33027-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="33027-127">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33027-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="33027-128">Pokud spouštíte klienta v konfiguraci mezi počítači, nezapomeňte nahradit localhost v atributu `address` [\<koncového bodu > \<elementu klienta >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) a `clientBaseAddress` atributu\<[vazby](../../../../docs/framework/misc/binding.md) > prvek prvku [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) s názvem příslušného počítače, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="33027-128">When running the client in a cross-machine configuration, be sure to replace localhost in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown:</span></span>

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
