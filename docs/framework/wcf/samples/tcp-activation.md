---
title: Aktivace protokolem TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: 0fa737adbdc7acc51511557877799c89849149bc
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598655"
---
# <a name="tcp-activation"></a><span data-ttu-id="9a017-102">Aktivace protokolem TCP</span><span class="sxs-lookup"><span data-stu-id="9a017-102">TCP Activation</span></span>

<span data-ttu-id="9a017-103">Tato ukázka demonstruje hostování služby, která používá aktivační služby procesů systému Windows (WAS) k aktivaci služby, která komunikuje přes protokol net. TCP.</span><span class="sxs-lookup"><span data-stu-id="9a017-103">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="9a017-104">Tato ukázka je založena na [Začínáme](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="9a017-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9a017-105">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="9a017-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a017-106">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="9a017-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9a017-107">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="9a017-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="9a017-108">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="9a017-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9a017-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9a017-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`

<span data-ttu-id="9a017-110">Ukázka se skládá z programu klientské konzoly (. exe) a knihovny služeb (. dll) hostované v pracovním procesu aktivovaném nástrojem WAS.</span><span class="sxs-lookup"><span data-stu-id="9a017-110">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="9a017-111">Aktivita klienta se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="9a017-111">Client activity is visible in the console window.</span></span>

<span data-ttu-id="9a017-112">Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="9a017-112">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="9a017-113">Kontrakt je definován `ICalculator` rozhraním, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení), jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="9a017-113">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>

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

<span data-ttu-id="9a017-114">Implementace služby vypočítá a vrátí příslušný výsledek:</span><span class="sxs-lookup"><span data-stu-id="9a017-114">The service implementation calculates and returns the appropriate result:</span></span>

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

<span data-ttu-id="9a017-115">Ukázka používá variantu připojení NET. TCP se zapnutým sdílením portů TCP a vypnuté zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9a017-115">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="9a017-116">Pokud chcete použít zabezpečenou vazbu TCP, změňte režim zabezpečení serveru na požadované nastavení a znovu spusťte Svcutil. exe na straně klienta, čímž vygenerujete konfigurační soubor klienta aktualizace.</span><span class="sxs-lookup"><span data-stu-id="9a017-116">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>

<span data-ttu-id="9a017-117">Následující příklad ukazuje konfiguraci služby:</span><span class="sxs-lookup"><span data-stu-id="9a017-117">The following sample shows the configuration for the service:</span></span>

```xml
<system.serviceModel>

    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netTcpBinding>
        <binding name="PortSharingBinding" portSharingEnabled="true">
          <security mode="None" />
        </binding>
      </netTcpBinding>
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

<span data-ttu-id="9a017-118">Koncový bod klienta je nakonfigurován tak, jak je znázorněno v následujícím ukázkovém kódu:</span><span class="sxs-lookup"><span data-stu-id="9a017-118">The client's endpoint is configured as shown in the following sample code:</span></span>

```xml
<system.serviceModel>
    <bindings>
        <netTcpBinding>
          <binding name="NetTcpBinding_ICalculator">
            <security mode="None"/>
          </binding>
        </netTcpBinding>
    </bindings>
    <client>
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />
    </client>
</system.serviceModel>
```

<span data-ttu-id="9a017-119">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="9a017-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9a017-120">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="9a017-120">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9a017-121">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="9a017-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="9a017-122">Ujistěte se, že je nainstalovaná služba IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="9a017-122">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="9a017-123">Pro aktivaci byla požadována služba IIS 7,0.</span><span class="sxs-lookup"><span data-stu-id="9a017-123">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="9a017-124">Ujistěte se, že jste provedli [jednorázovou proceduru nastavení Windows Communication Foundation ukázek](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9a017-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="9a017-125">Kromě toho musíte nainstalovat komponenty WCF, které nejsou součástí aktivace přes protokol HTTP:</span><span class="sxs-lookup"><span data-stu-id="9a017-125">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="9a017-126">V nabídce **Start** klikněte na položku **Ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="9a017-126">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="9a017-127">Vyberte **programy a funkce**.</span><span class="sxs-lookup"><span data-stu-id="9a017-127">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="9a017-128">Klikněte na **zapnout nebo vypnout součásti systému Windows**.</span><span class="sxs-lookup"><span data-stu-id="9a017-128">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="9a017-129">Rozbalte uzel **Microsoft .NET Framework 3,0** a podívejte se na funkci **Windows Communication Foundation aktivace jiným protokolem než http** .</span><span class="sxs-lookup"><span data-stu-id="9a017-129">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="9a017-130">Při konfiguraci byla podpora aktivace protokolem TCP podporována.</span><span class="sxs-lookup"><span data-stu-id="9a017-130">Configure WAS to support TCP activation.</span></span>

    <span data-ttu-id="9a017-131">Následující dva kroky jsou implementovány v dávkovém souboru s názvem AddNetTcpSiteBinding. cmd, který je umístěn v ukázkovém adresáři.</span><span class="sxs-lookup"><span data-stu-id="9a017-131">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="9a017-132">Aby bylo možné podporovat NET. TCP Activation, musí být výchozí webová stránka nejprve svázána s portem NET. TCP.</span><span class="sxs-lookup"><span data-stu-id="9a017-132">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="9a017-133">To lze provést pomocí nástroje Appcmd. exe, který je nainstalován se sadou nástrojů pro správu Internetová informační služba 7,0 (IIS).</span><span class="sxs-lookup"><span data-stu-id="9a017-133">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="9a017-134">Na příkazovém řádku na úrovni správce spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="9a017-134">From an administrator-level command prompt, run the following command:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!TIP]
        > <span data-ttu-id="9a017-135">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="9a017-135">This command is a single line of text.</span></span> <span data-ttu-id="9a017-136">Tento příkaz přidá vazbu sítě NET. TCP na výchozí webovou stránku, která naslouchá na portu TCP 808 s libovolným názvem hostitele.</span><span class="sxs-lookup"><span data-stu-id="9a017-136">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>

    2. <span data-ttu-id="9a017-137">I když všechny aplikace v rámci lokality sdílí společnou vazbu NET. TCP, každá aplikace může povolit podporu NET. TCP samostatně.</span><span class="sxs-lookup"><span data-stu-id="9a017-137">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="9a017-138">Pokud chcete povolit NET. TCP pro aplikaci/ServiceModelSamples, spusťte následující příkaz z příkazového řádku na úrovni správce:</span><span class="sxs-lookup"><span data-stu-id="9a017-138">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp
        ```

        > [!NOTE]
        > <span data-ttu-id="9a017-139">Tento příkaz je jedním řádkem textu.</span><span class="sxs-lookup"><span data-stu-id="9a017-139">This command is a single line of text.</span></span> <span data-ttu-id="9a017-140">Tento příkaz umožňuje, aby aplikace/ServiceModelSamples byla dostupná pomocí `http://localhost/servicemodelsamples` a `net.tcp://localhost/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="9a017-140">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="9a017-141">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9a017-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="9a017-142">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9a017-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    <span data-ttu-id="9a017-143">Odeberte vazbu na lokalitu NET. TCP, kterou jste přidali pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="9a017-143">Remove the net.tcp site binding you added for this sample.</span></span>

    <span data-ttu-id="9a017-144">Následující dva kroky jsou implementovány v dávkovém souboru s názvem RemoveNetTcpSiteBinding. cmd, který je umístěn v ukázkovém adresáři.</span><span class="sxs-lookup"><span data-stu-id="9a017-144">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="9a017-145">Ze seznamu povolených protokolů odeberte NET. TCP spuštěním následujícího příkazu z příkazového řádku na úrovni správce:</span><span class="sxs-lookup"><span data-stu-id="9a017-145">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="9a017-146">Tento příkaz musí být zadán jako jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="9a017-146">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="9a017-147">Odeberte vazbu sítě NET. TCP spuštěním následujícího příkazu z příkazového řádku na úrovni správce:</span><span class="sxs-lookup"><span data-stu-id="9a017-147">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="9a017-148">Tento příkaz musí být zadán jako jeden řádek textu.</span><span class="sxs-lookup"><span data-stu-id="9a017-148">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a017-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a017-149">See also</span></span>

- <span data-ttu-id="9a017-150">[Hostování technologie AppFabric a ukázky trvalosti](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9a017-150">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
