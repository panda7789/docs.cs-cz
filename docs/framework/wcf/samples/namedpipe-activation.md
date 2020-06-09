---
title: Aktivace pojmenovaného kanálu
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: 8d9a10b94c52514db611144352653b911d109056
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602463"
---
# <a name="namedpipe-activation"></a><span data-ttu-id="2cb4b-102">Aktivace pojmenovaného kanálu</span><span class="sxs-lookup"><span data-stu-id="2cb4b-102">NamedPipe Activation</span></span>

<span data-ttu-id="2cb4b-103">Tato ukázka demonstruje hostování služby, která používá aktivační službu procesů systému Windows (WAS) k aktivaci služby, která komunikuje s kanály názvů.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-103">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over names pipes.</span></span> <span data-ttu-id="2cb4b-104">Tato ukázka je založená na [Začínáme](getting-started-sample.md) a vyžaduje spuštění systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-104">This sample is based on the [Getting Started](getting-started-sample.md) and requires Windows Vista to run.</span></span>

> [!NOTE]
> <span data-ttu-id="2cb4b-105">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2cb4b-106">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2cb4b-107">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="2cb4b-108">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2cb4b-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a><span data-ttu-id="2cb4b-110">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="2cb4b-110">Sample Details</span></span>

<span data-ttu-id="2cb4b-111">Ukázka se skládá z programu klientské konzoly (. exe) a knihovny služeb (. dll) hostované v pracovním procesu aktivovaném službami aktivace procesů systému Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="2cb4b-111">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="2cb4b-112">Aktivita klienta se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-112">Client activity is visible in the console window.</span></span>

<span data-ttu-id="2cb4b-113">Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="2cb4b-114">Kontrakt je definován `ICalculator` rozhraním, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení), jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="2cb4b-115">Klient provádí synchronní požadavky na danou matematickou operaci a implementace služby vypočítá a vrátí příslušný výsledek.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-115">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="2cb4b-116">Ukázka používá upravenou `netNamedPipeBinding` vazbu bez zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-116">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="2cb4b-117">Vazba je určena v konfiguračních souborech pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-117">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="2cb4b-118">Typ vazby pro službu je zadán v atributu elementu koncového bodu `binding` , jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-118">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>

<span data-ttu-id="2cb4b-119">Pokud chcete použít zabezpečenou vazbu pojmenovaného kanálu, změňte režim zabezpečení serveru na požadované nastavení zabezpečení a znovu spusťte Svcutil. exe v klientovi, aby se získal aktualizovaný konfigurační soubor klienta.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-119">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>

```xml
<system.serviceModel>
        <services>
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">

        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->
        <endpoint address=""
                  binding="netNamedPipeBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexNamedPipeBinding"
                  contract="IMetadataExchange" />
      </service>
        </services>
        <bindings>
            <netNamedPipeBinding>
                <binding name="Binding1" >
                    <security mode = "None">
                    </security>
                </binding >
            </netNamedPipeBinding>
        </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="2cb4b-120">Informace o koncovém bodu klienta jsou konfigurovány tak, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-120">The client’s endpoint information is configured as shown in the following sample code.</span></span>

```xml
<system.serviceModel>

    <client>
      <endpoint name=""
                          address="net.pipe://localhost/servicemodelsamples/service.svc"
                          binding="netNamedPipeBinding"
                          bindingConfiguration="Binding1"
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>

    <bindings>

      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.
            Each property is configured with the default value. -->

      <netNamedPipeBinding>
        <binding name="Binding1"
                         maxBufferSize="65536"
                         maxConnections="10">
          <security mode = "None">
          </security>
        </binding >

      </netNamedPipeBinding>
    </bindings>

  </system.serviceModel>
```

<span data-ttu-id="2cb4b-121">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2cb4b-122">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-122">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2cb4b-123">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="2cb4b-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="2cb4b-124">Ujistěte se, že je nainstalovaná služba IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-124">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="2cb4b-125">Pro aktivaci byla požadována služba IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-125">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="2cb4b-126">Ujistěte se, že jste v [Windows Communication Foundation Samples provedli postup jednorázového nastavení](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2cb4b-126">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="2cb4b-127">Kromě toho musíte nainstalovat komponenty WCF, které nejsou součástí aktivace přes protokol HTTP:</span><span class="sxs-lookup"><span data-stu-id="2cb4b-127">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="2cb4b-128">V nabídce **Start** klikněte na položku **Ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-128">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="2cb4b-129">Vyberte **programy a funkce**.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-129">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="2cb4b-130">Klikněte na **zapnout nebo vypnout součásti systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-130">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="2cb4b-131">Rozbalte uzel **Microsoft .NET Framework 3,0** a podívejte se na funkci **Windows Communication Foundation aktivace jiným protokolem než http** .</span><span class="sxs-lookup"><span data-stu-id="2cb4b-131">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="2cb4b-132">Nakonfigurujte aktivační službu procesů systému Windows (WAS) pro podporu aktivace pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-132">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>

    <span data-ttu-id="2cb4b-133">Následující dva kroky jsou implementovány v dávkovém souboru s názvem AddNetPipeSiteBinding. cmd, který je umístěn v ukázkovém adresáři.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-133">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="2cb4b-134">Aby bylo možné podporovat aktivaci NET. Pipes, musí být výchozí webová stránka nejprve svázána s protokolem NET. pipe.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-134">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="2cb4b-135">To lze provést pomocí nástroje Appcmd. exe, který je nainstalován se sadou nástrojů pro správu služby IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-135">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="2cb4b-136">Na příkazovém řádku se zvýšenými oprávněními (správce) spusťte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-136">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="2cb4b-137">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-137">This command is a single line of text.</span></span>

        <span data-ttu-id="2cb4b-138">Tento příkaz přidá vazbu lokality NET. pipe k výchozímu webovému serveru.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-138">This command adds a net.pipe site binding to the default Web site.</span></span>

    2. <span data-ttu-id="2cb4b-139">I když všechny aplikace v rámci lokality sdílejí společnou vazbu NET. pipe, může každá aplikace povolit podporu NET. pipe jednotlivě.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-139">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="2cb4b-140">Pokud chcete povolit NET. pipe pro aplikaci/ServiceModelSamples, spusťte z příkazového řádku se zvýšenými oprávněními následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-140">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > <span data-ttu-id="2cb4b-141">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-141">This command is a single line of text.</span></span>

        <span data-ttu-id="2cb4b-142">Tento příkaz umožňuje, aby aplikace/ServiceModelSamples byla dostupná pomocí `http://localhost/servicemodelsamples` a `net.tcp://localhost/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="2cb4b-142">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="2cb4b-143">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2cb4b-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="2cb4b-144">Odeberte vazbu na lokalitu NET. pipe, kterou jste přidali pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-144">Remove the net.pipe site binding you added for this sample.</span></span>

    <span data-ttu-id="2cb4b-145">Pro usnadnění jsou v dávkovém souboru s názvem RemoveNetPipeSiteBinding. cmd, který se nachází v ukázkovém adresáři, implementované tyto dva kroky:</span><span class="sxs-lookup"><span data-stu-id="2cb4b-145">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="2cb4b-146">Ze seznamu povolených protokolů odeberte NET. TCP spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-146">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="2cb4b-147">Tento příkaz musí být zadán jako jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-147">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="2cb4b-148">Odeberte vazbu sítě NET. TCP spuštěním následujícího příkazu z příkazového řádku se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-148">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="2cb4b-149">Tento příkaz musí být zadán jako jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="2cb4b-149">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="2cb4b-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="2cb4b-150">See also</span></span>

- <span data-ttu-id="2cb4b-151">[Hostování technologie AppFabric a ukázky trvalosti](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2cb4b-151">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
